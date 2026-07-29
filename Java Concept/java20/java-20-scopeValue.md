# Scope Values
Scoped Values were developed – together with Virtual Threads and Structured Concurrency – in Project Loom. They have been included in the JDK since Java 20 as an incubator feature and since Java 21 as a preview feature. They have been finalized in Java 25 without any changes.

## What is a Scoped Value?

Scoped Values are a form of implicit method parameters that allow one or more values (i.e., arbitrary objects) to be passed to one or more remote methods without having to add them as explicit parameters to each method in the call chain.

Scoped Values are usually created as public static fields, so they can be retrieved from any method.

If multiple threads use the same ScopedValue field, then it may contain a different value from the point of view of each thread.

If you are familiar with ThreadLocal variables, this will sound familiar. In fact, Scoped Values are a modern alternative for thread locals.

## ScopedValue Example
A classic usage scenario is a web framework that authenticates the user on an incoming request and makes the logged-in user's data available to the code that processes the request.

That can be done, for example, using a method argument.

Now, in complex applications, the processing of a request can extend over hundreds of methods – but the information about the logged-in user may only be required in a few methods. Nevertheless, we would have to pass the user through all methods that eventually lead to invoking a method for which the logged-in user is relevant.

In the following example, the logged-in user is passed from the Server through the RestAdapter and UseCase to the Repository, where it is eventually evaluated:

```java
class Server {
  private void serve(Request request) {
    // ...
    User user = authenticateUser(request);
    restAdapter.processRequest(request, user);
    // ...
  }
}

class RestAdapter {
  public void processRequest(Request request, User loggedInUser) { 
    // ...
    UUID id = extractId(request);
    useCase.invoke(id, loggedInUser);
    // ...
  }
}

class UseCase {
  public void invoke(UUID id, User loggedInUser) {
    // ...
    Data data = repository.getData(id, loggedInUser);
    // ...
  }
}

class Repository {
  public Data getData(UUID id, User loggedInUser) {
    Data data = findById(id);
    if (loggedInUser.isAdmin()) {
      enrichDataWithAdminInfos(data);
    }
  }
}
```

The additional loggedInUser parameter makes our code noisy quite quickly. Most of the methods do not need the user at all – and there might even be methods that should not be able to access the user at all for security reasons.

And what if, at some point deep in the call stack, we also needed the user's IP address? Then we would have to pass another argument through countless methods.

The alternative is to store the user in a Scoped Value that can be accessed from anywhere.

This works as follows:

We create a static field of type ScopedValue in a publicly accessible place. With ScopedValue.where(), we bind the Scoped Value to the concrete user object; and to the run() method, we supply – in the form of a Runnable – the code for whose call duration the Scoped Value should be valid:

```java
class Server {
  public final static ScopedValue<User> LOGGED_IN_USER = ScopedValue.newInstance();
 
  private void serve(Request request) {
    // ...
    User loggedInUser = authenticateUser(request);
    ScopedValue.where(LOGGED_IN_USER, loggedInUser)
               .run(() -> restAdapter.processRequest(request));
    // ...
  }
```

```java
Up to and including Java 23, we can alternatively use the convenience method runWhere() and pass the Runnable to this method as a third parameter:

ScopedValue.runWhere(
  LOGGED_IN_USER,
  loggedInUser,
  () -> restAdapter.processRequest(request) // ⟵ the Runnable as 3rd parameter
);

This variant was removed in Java 24 to make the ScopedValue interface completely “fluent”.
```

We can then remove the loggedInUser parameter from all method signatures:

```java
class RestAdapter {
  public void processRequest(Request request) { 
    // ...
    UUID id = extractId(request);
    useCase.invoke(id);
    // ...
  }
}

class UseCase {
  public void invoke(UUID id) {
    // ...
    Data data = repository.getData(id);
    // ...
  }
}
```

And where we need the logged-in user, we can read it with ScopedValue.get():

```java
class Repository {
  public Data getData(UUID id) {
    Data data = findById(id);
    User loggedInUser = Server.LOGGED_IN_USER.get();
    if (loggedInUser.isAdmin()) {
      enrichDataWithAdminInfos(data);
    }
  }
}

```

That makes the code much more readable and maintainable, as we no longer have to pass the logged-in user from one method to the next but can access it exactly where we need it.

## Calling a Method with a Return Value

If the called code has a return value, you can call the method call(CallableOp op) after ScopedValue.where() instead of run(Runnable op).

CallableOp is a functional, generic interface defined as follows:

```java
@FunctionalInterface
public static interface CallableOp<T, X extends Throwable> {
    T call() throws X
}
```

The interface includes both the return value and a potentially thrown exception as type parameters. Thus, the compiler can recognize what kind of exception the invocation of call(...) can throw.

So, if we want to call, for example, the following method in the context of a Scoped Value:

```java
Result doSomethingSmart() throws SpecificException {
  . . .
}
```

Then the compiler recognizes that call() can only throw a SpecificException as well, and we can catch it as follows:

```java
try {
  Result result = ScopedValue.where(USER, loggedInUser).call(() -> doSomethingSmart());
} catch (SpecificException e) {  // ⟵ Catching SpecificException
  . . .
}
```

And if the called method does not throw an exception, we don't need to catch any.

```java
In Java 21 and 22, the CallableOp interface did not yet exist. Instead, a Callable was used. However, the call() method of the Callable interface throws a generic Exception:

@FunctionalInterface
public interface Callable {
  V call() throws Exception;
}

And thus, in Java 21 and 22, when calling ScopedValue.call(), we always had to catch Exception – even if the called method could only throw a specific exception or none at all.

Until Java 23, we could alternatively use the convenience method callWhere(). This method was removed in Java 24 along with runWhere() (see above).
```

## Rebinding Scoped Values

ScopedValue has no set(...) method to change the stored value. This is intentional because the immutability of a value makes complex code much more readable and maintainable.

Instead, you can rebind the value for the invocation of a limited code section (e.g., for the invocation of a sub-method). That means that, for this limited code section, another value is visible ... and as soon as that section is terminated, the original value is visible again.

For example, our RestAdapter method might want to hide the information about the logged-in user from the extractId method. To do this, we can call ScopedValue.where(...) again and set the logged-in user to null during the sub-method call:

```java
class RestAdapter {
  public void processRequest(Request request) { 
    // ...
    UUID id = ScopedValue.where(LOGGED_IN_USER, null)
                         .call(() -> extractId(request));
    useCase.invoke(id);
    // ...
  }
}
```

Here you can also see how we use call(...) instead of run(...) and pass a Callable (i.e., a method with a return value) instead of a Runnable.

## Inheriting Scoped Values

Scoped Values are automatically inherited by all child threads created via a Structured Task Scope.

Using StructuredTaskScope, our use case could, for example, call an external service in parallel to the repository method:

```java
class UseCase {
  public void invoke(UUID id) {
    // ...
    try (var scope = new StructuredTaskScope.ShutdownOnFailure()) {
      Future<Data>    dataFuture    = scope.fork(() -> repository.getData(id));
      Future<ExtData> extDataFuture = scope.fork(() -> remoteService.getExtData(id));
 
      scope.join();
      scope.throwIfFailed();

      Data    data    = dataFuture.resultNow();
      ExtData extData = extDataFuture.resultNow();
      // ...
    }
  }
}
```

This way, we can also access the logged-in user from the child threads created via fork(...) using LOGGED_IN_USER.get().

Since the StructuredTaskScope is not completed until all child threads are finished, it fits very well into the concept of Scoped Values.

## What Is the Difference Between ScopedValue and ThreadLocal?

Those who have solved the requirements of these examples so far with thread locals may now wonder: Why do we need Scoped Values? What can they do that thread locals can't?

Scoped Values have the following advantages:

- They are only valid during the lifetime of the Runnable passed to the run(...) method, and they are released for garbage collection immediately afterward (unless further references to them exist). A thread-local value, on the other hand, remains in memory until either the thread is terminated (which may never be the case when using a thread pool) or it is explicitly deleted with ThreadLocal.remove(). Since many developers forget to do this (or don't do it because the program is so complex that it's not obvious when a thread-local value is no longer needed), memory leaks are often the result.

- A Scoped Value is immutable – it can only be reset for a new scope by rebinding, as mentioned above. This improves the understandability and maintainability of the code considerably compared to thread locals, which can be changed at any time using set().

- The child threads created by StructuredTaskScope have access to the Scoped Value of the parent thread. If, on the other hand, we use InheritableThreadLocal, its value is copied to each child thread so that a child thread cannot change the thread local value of the parent thread. This can significantly increase the memory footprint.

Like thread locals, Scoped Values are available for both platform and virtual threads. Especially when there are thousands to millions of virtual child threads, the memory savings from accessing the Scoped Value of the parent thread (instead of creating a copy) can be significant.

## Summary
With Scoped Values, we get a handy construct to provide a thread (and, if needed, a group of child threads) with a read-only, thread-specific value during their lifetime.

Please note that until Java 24, Scoped Values are in the preview stage and need to be explicitly enabled using --enable-preview --source <Java version>.

## Enabling Preview Features before Java 25
If you want to use Scoped Values before Java 25, you need to explicitly enable preview features. To do this, you must call the java and javac commands with the following VM options:

```java
$ javac --enable-preview --source <Java version> <.java file to compile>
$ java --enable-preview <.java file or compiled class to execute>
```