# Java 20 New Feature

It mainly refined several preview and incubator features, especially related to concurrency, pattern matching, and performance.

## Virtual Threads (Second Preview)

Virtual Threads introduced in Java SE 19 were improved in Java 20.

Virtual threads are lightweight threads managed by JVM instead of the operating system.

Example

```java
Thread.startVirtualThread(() -> {
    System.out.println("Running in virtual thread");
});
```

Benefits

✅ Handle millions of concurrent requests
✅ Less memory usage
✅ Ideal for microservices and web applications

Example usage:

- Web servers

- Database calls

- High-concurrency systems

## Structured Concurrency (Second Incubator)

Structured concurrency improves how multiple concurrent tasks are managed.

Example

```java
try (var scope = new StructuredTaskScope.ShutdownOnFailure()) {
    Future<String> user = scope.fork(() -> findUser());
    Future<Integer> order = scope.fork(() -> fetchOrder());

    scope.join();
}
```

Benefits:

- Better error handling

- Easier debugging

- Clear lifecycle of tasks

## Record Patterns (Second Preview)

Record patterns introduced in Java SE 19 were improved.

Example record:

```java
record Point(int x, int y) {}
```

Example usage

```java
if (obj instanceof Point(int x, int y)) {
    System.out.println(x + y);
}
```

Benefits:

- Cleaner code

- Automatic variable extraction from records

## Pattern Matching for switch (Fourth Preview)

Further improvements to pattern matching in switch statements.

Example:

```java
static String check(Object obj) {
    return switch (obj) {
        case Integer i -> "Integer: " + i;
        case String s -> "String: " + s;
        default -> "Unknown";
    };
}
```

Benefits:

- Eliminates casting

- More readable code

## Scoped Values (Incubator)

Scoped values allow sharing immutable data between threads safely.

A large number of Java applications have components or modules that need to share data among themselves. Often, these modules are thread based, so we must protect the data they share from any change.

We’ve been using variables of the type ThreadLocal to allow components to share data.

But it has some consequences:

- A ThreadLocal variable is mutable. The ThreadLocal API allows access to both get() and set() methods of its variable type.

- We may face memory leak issues since the value of the ThreadLocal variables is retained until we explicitly call the remove() method on it or the thread exits. Thus, there’s no binding to the lifetime of these per-thread variables.

- They may lead to excessive memory footprints in case of using large numbers of threads. This is because the child threads can inherit the ThreadLocal variables of parent threads, thus allocating memory for every ThreadLocal variable.

To overcome these problems of ThreadLocal variables, Java 20 has introduced scoped values for sharing data within and across threads.

Scoped values provide a simple, immutable, and inheritable data-sharing option, specifically in situations where we’re working with a large number of threads.

A ScopedValue is an immutable value that is available for reading for a bounded period of execution by a thread. Since it’s immutable, it allows safe and easy data-sharing for a limited period of thread execution. Also, we need not pass the values as method arguments.

We can use the where() method of the class ScopedValue to set the value of a variable for the bounded period of thread execution. Moreover, once we get the data using the get() method, we cannot access it again.

Once the run() method of a thread finishes execution, the scoped value reverts to the unbound state. We can use the get() method to read the value of a scoped-value variable inside a thread.

Example concept:

```java
ScopedValue<String> USER = ScopedValue.newInstance();
```

Benefits:

- Safer alternative to ThreadLocal

- Works well with Virtual Threads

### What Problem Scoped Values Solve

Normally, when we want to pass some data (like userId, requestId, transactionId) through multiple methods or threads, we must pass it as method parameters.

Example without scoped values:

```java
void processRequest(String userId){
    serviceA(userId);
}

void serviceA(String userId){
    serviceB(userId);
}

void serviceB(String userId){
    System.out.println(userId);
}
```

Problems:

- Too many parameters

- Hard to maintain

- Not good for multi-threaded code

Earlier Java used ThreadLocal, but it has issues:

- Mutable

- Memory leaks

- Hard to manage in large thread pools.

**ScopedValue solves these problems.**

### What is a Scoped Value

A ScopedValue is:

- Immutable (cannot change)

- Thread-safe

- Available only inside a specific execution scope

- Automatically removed after execution

So it behaves like a **temporary thread context variable.**

## Basic Example of ScopedValue

### Step 1: Declare a scoped value

```java
static final ScopedValue<String> USER = ScopedValue.newInstance();
```

### Step 2: Bind value using where()

```java
ScopedValue.where(USER, "Tej")
           .run(() -> {
               processRequest();
           });
```

Inside this scope, the value "Tej" is available.

### Step 3: Access using get()

```java
void processRequest() {
    System.out.println("User: " + USER.get());
}

Output:
User: Tej
```

## Complete Working Example

```java
import java.lang.ScopedValue;

public class ScopedValueExample {

    static final ScopedValue<String> USER = ScopedValue.newInstance();

    public static void main(String[] args) {

        ScopedValue.where(USER, "Tej Singh")
                   .run(() -> {
                       serviceA();
                   });
    }

    static void serviceA(){
        serviceB();
    }

    static void serviceB(){
        System.out.println("Current User: " + USER.get());
    }
}

Output
Current User: Tej Singh
```
**Notice:**

We did not pass the value as a parameter.

## Example with Multiple Threads

Scoped values are inheritable to child threads.

```java
ScopedValue.where(USER, "Admin")
           .run(() -> {

               Thread t = new Thread(() -> {
                   System.out.println(USER.get());
               });

               t.start();
           });

Output
Admin
```
The child thread can read the value safely.

## Lifecycle of ScopedValue

1️⃣ Create variable

```java
ScopedValue.newInstance()
```

2️⃣ Bind value

```java
ScopedValue.where()
```

3️⃣ Execute code

```java
run()
```

4️⃣ Access value

```java
get()
```

5️⃣ Scope ends → value disappears

## Real Backend Example

Imagine HTTP request handling.

We store requestId once:

```java
ScopedValue<String> REQUEST_ID
```

Then anywhere in service layer:

```java
log("Request id: " + REQUEST_ID.get());
```

Without passing requestId everywhere.

## Interview Answer (Short)

ScopedValue is an immutable, thread-safe variable introduced to share data across methods and threads within a bounded execution scope. It is safer than ThreadLocal because its lifecycle is limited to a specific scope and it avoids memory leaks.

## Foreign Function & Memory API (Second Preview)

This API allows Java to interact with native code (C/C++) without JNI.

Benefits:

- Simpler than JNI

- Better performance

- Safer memory access

## Vector API (Sixth Incubator)

Vector API improved again for high-performance computing.

Use cases:

- AI/ML workloads

- big data processing

- scientific computing

## Interview Insight

In Java 20, the most important concepts are:

⭐ Virtual Threads
⭐ Record Patterns
⭐ Pattern Matching
⭐ Scoped Values