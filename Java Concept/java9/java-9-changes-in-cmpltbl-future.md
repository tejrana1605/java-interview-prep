# Java CompletableFuture API Improvements in 9

The **CompletableFuture in java** was introduced in java 8. It is the enhanced version of the **Future interface**.  Java 9 provides some more functions to improve it and solve problems raised in Java SE 8. Java 9 provides methods for delays and timeouts, some utility methods, and better sub-classing.

It Java completablefuture added 8 new methods, they are:

1. Executor defaultExecutor()

2. CompletableFuture<U> newIncompleteFuture()

3. CompletableFuture<T> copy()

4. CompletionStage<T> minimalCompletionStage()

5. CompletableFuture<T> completeAsync(Supplier<? extends T> supplier, Executor executor)

6. CompletableFuture<T> completeAsync(Supplier<? extends T> supplier)

7. CompletableFuture<T> orTimeout(long timeout, TimeUnit unit)

8. CompletableFuture<T> completeOnTimeout(T value, long timeout, TimeUnit unit)

## 1. Executor defaultExecutor()

This method returns the default executors for asynchronized methods that don’t specify the executor. This method can be overridden in subclasses and return an Executor.

```java
new CompletableFuture().defaultExecutor()
```

## 2. Method newIncompleteFuture()
This method returns an object of a new incomplete CompletableFuture of the same type.  The subclasses override the method and return an instance of the same class as this CompletableFuture.

```java
public <U> CompletableFuture<U> newIncompleteFuture() {
        return new CompletableFuture<U>();
    }
```

## 3. Method copy()
This method is used to get a copy of CompletableFuture. It returns a new object of CompletableFuture :

1. If the existing CompletableFuture gets completed normally, then the new object is also completely normal.   


2. If the existing CompletableFuture completes exceptionally then it will return CompletableFuture exceptionally.

```java
public CompletableFuture<T> copy() {
        return uniCopyStage(this);
    }
```

## 4. Method minimalCompletionStage()

This method is used to get the new object of CompletionStage. It works similarly as described by the copy method.  It throws UnsupportedOperationException in every attempt to retrieve or set the resolved value.


```java
public CompletionStage<T> minimalCompletionStage() {
        return uniAsMinimalStage();
    }
```

## 5.  Methods completeAsync()
This method is used to complete the execution of CompletableFuture with a given supplier. It is an overloaded method.

```java
public CompletableFuture<T> completeAsync(Supplier<? extends T> supplier) {
        return completeAsync(supplier, defaultExecutor());
    }
```

This method takes only one parameter of Supplier type.

```java
public CompletableFuture<T> completeAsync(Supplier<? extends T> supplier,
                                              Executor executor) {
        if (supplier == null || executor == null)
            throw new NullPointerException();
        executor.execute(new AsyncSupply<T>(this, supplier));
        return this;
    }
```

This method takes two parameters Supplier and Executor.

## 6. Methods orTimeout()

This method is used to complete the CompletableFuture Exceptionally when given time out. It can complete before time also.

```java
public CompletableFuture<T> orTimeout(long timeout, TimeUnit unit) {
        if (unit == null)
            throw new NullPointerException();
        if (result == null)
            whenComplete(new Canceller(Delayer.delay(new Timeout(this),
                                                     timeout, unit)));
        return this;
    }
```

## 7. Method completeOnTimeout()

This method is used to Complete the CompletableFuture normally with the specified value unless it is completed before the specified timeout. It returns an object of completeOnTimeout.

```java
public CompletableFuture<T> completeOnTimeout(T value, long timeout,
                                                  TimeUnit unit) {
        if (unit == null)
            throw new NullPointerException();
        if (result == null)
            whenComplete(new Canceller(Delayer.delay(
                                           new DelayedCompleter<T>(this, value),
                                           timeout, unit)));
        return this;
    }
```
