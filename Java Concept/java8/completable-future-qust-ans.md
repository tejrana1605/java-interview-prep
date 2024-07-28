# Completable Future types of constructor

In Java, the `CompletableFuture` class is part of the `java.util.concurrent` package and provides several ways to create and manage futures. However, `CompletableFuture` itself doesn't provide traditional constructors for instantiation directly with a value or task. Instead, it provides various static factory methods to create instances.

Here are the main ways to create instances of `CompletableFuture`:

### 1. `CompletableFuture<Void>`

This creates a `CompletableFuture` that is not associated with any value. This can be useful for representing futures that only signal completion.

```java
CompletableFuture<Void> future = new CompletableFuture<>();
```

### 2. `CompletableFuture.completedFuture(T value)`

This creates a `CompletableFuture` that is already completed with the given value.

```java
CompletableFuture<String> completedFuture = CompletableFuture.completedFuture("Hello, World!");
```

### 3. `CompletableFuture.supplyAsync(Supplier<U> supplier)`

This creates a `CompletableFuture` that runs the given supplier asynchronously using the common ForkJoinPool.

```java
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    // Simulate long-running task
    return "Result";
});
```

### 4. `CompletableFuture.supplyAsync(Supplier<U> supplier, Executor executor)`

This creates a `CompletableFuture` that runs the given supplier asynchronously using the provided executor.

```java
Executor executor = Executors.newFixedThreadPool(2);
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    // Simulate long-running task
    return "Result";
}, executor);
```

### 5. `CompletableFuture.runAsync(Runnable runnable)`

This creates a `CompletableFuture` that runs the given `Runnable` asynchronously using the common ForkJoinPool. It doesn't return any result.

```java
CompletableFuture<Void> future = CompletableFuture.runAsync(() -> {
    // Simulate long-running task
    System.out.println("Task completed");
});
```

### 6. `CompletableFuture.runAsync(Runnable runnable, Executor executor)`

This creates a `CompletableFuture` that runs the given `Runnable` asynchronously using the provided executor. It doesn't return any result.

```java
Executor executor = Executors.newFixedThreadPool(2);
CompletableFuture<Void> future = CompletableFuture.runAsync(() -> {
    // Simulate long-running task
    System.out.println("Task completed");
}, executor);
```

### Combining CompletableFutures

You can combine multiple `CompletableFuture` instances using various methods:

- `thenApply(Function<T, U>)`: Transforms the result of a future.
- `thenCompose(Function<T, CompletionStage<U>>)` : Flattens nested futures.
- `thenCombine(CompletionStage<U>, BiFunction<T, U, V>)`: Combines results of two futures.
- `allOf(CompletableFuture<?>...)`: Waits for all futures to complete.
- `anyOf(CompletableFuture<?>...)`: Waits for any one of the futures to complete.

### Example Usage

Combining two `CompletableFuture` instances:

```java
CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
    return "Hello";
});

CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> {
    return "World";
});

CompletableFuture<String> combinedFuture = future1.thenCombine(future2, (s1, s2) -> s1 + " " + s2);

combinedFuture.thenAccept(result -> {
    System.out.println(result); // Prints "Hello World"
});
```

### Exception Handling

Handling exceptions in `CompletableFuture` can be done using methods like `exceptionally`, `handle`, and `whenComplete`.

```java
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    if (Math.random() > 0.5) {
        throw new RuntimeException("Error occurred");
    }
    return "Success";
});

future.exceptionally(ex -> {
    System.out.println("Exception: " + ex.getMessage());
    return "Default Value";
}).thenAccept(result -> {
    System.out.println("Result: " + result);
});
```

### Summary

- **`CompletableFuture` Creation**: Use static factory methods such as `completedFuture`, `supplyAsync`, and `runAsync` for instantiation.
- **Combining Futures**: Use methods like `thenCombine`, `allOf`, and `anyOf` to work with multiple futures.
- **Exception Handling**: Use `exceptionally`, `handle`, and `whenComplete` to manage exceptions.

These methods provide a powerful way to manage asynchronous computations and handle their results efficiently in a non-blocking manner.

# Completable Future all methods name

The `CompletableFuture` class in Java provides a wide range of methods for creating, combining, and handling asynchronous computations. Here is a comprehensive list of the methods available in the `CompletableFuture` class, categorized by their functionality:

### Creation Methods

- `CompletableFuture<U> supplyAsync(Supplier<U> supplier)`

- `CompletableFuture<U> supplyAsync(Supplier<U> supplier, Executor executor)`

- `CompletableFuture<Void> runAsync(Runnable runnable)`

- `CompletableFuture<Void> runAsync(Runnable runnable, Executor executor)`

- `CompletableFuture<T> completedFuture(T value)`

### Completion Methods
- `void complete(T value)`

- `void completeExceptionally(Throwable ex)`

- `boolean isDone()`

- `boolean isCompletedExceptionally()`

- `boolean isCancelled()`

- `boolean cancel(boolean mayInterruptIfRunning)`

### Combination Methods

- `CompletableFuture<T> thenApply(Function<? super T,? extends U> fn)`

- `CompletableFuture<T> thenApplyAsync(Function<? super T,? extends U> fn)`

- `CompletableFuture<T> thenApplyAsync(Function<? super T,? extends U> fn, Executor executor)`

- `CompletableFuture<Void> thenAccept(Consumer<? super T> action)`

- `CompletableFuture<Void> thenAcceptAsync(Consumer<? super T> action)`

- `CompletableFuture<Void> thenAcceptAsync(Consumer<? super T> action, Executor executor)`

- `CompletableFuture<Void> thenRun(Runnable action)`

- `CompletableFuture<Void> thenRunAsync(Runnable action)`

- `CompletableFuture<Void> thenRunAsync(Runnable action, Executor executor)`

- `CompletableFuture<U> thenCompose(Function<? super T,? extends CompletionStage<U>> fn)`

- `CompletableFuture<U> thenComposeAsync(Function<? super T,? extends CompletionStage<U>> fn)`

- `CompletableFuture<U> thenComposeAsync(Function<? super T,? extends CompletionStage<U>> fn, Executor executor)`

### Combination Methods with Two Stages

- `CompletableFuture<U> thenCombine(CompletionStage<? extends U> other, BiFunction<? super T,? super U,? extends V> fn)`

- `CompletableFuture<U> thenCombineAsync(CompletionStage<? extends U> other, BiFunction<? super T,? super U,? extends V> fn)`

- `CompletableFuture<U> thenCombineAsync(CompletionStage<? extends U> other, BiFunction<? super T,? super U,? extends V> fn, Executor executor)`

- `CompletableFuture<Void> thenAcceptBoth(CompletionStage<? extends U> other, BiConsumer<? super T,? super U> action)`

- `CompletableFuture<Void> thenAcceptBothAsync(CompletionStage<? extends U> other, BiConsumer<? super T,? super U> action)`

- `CompletableFuture<Void> thenAcceptBothAsync(CompletionStage<? extends U> other, BiConsumer<? super T,? super U> action, Executor executor)`

- `CompletableFuture<Void> runAfterBoth(CompletionStage<?> other, Runnable action)`

- `CompletableFuture<Void> runAfterBothAsync(CompletionStage<?> other, Runnable action)`

- `CompletableFuture<Void> runAfterBothAsync(CompletionStage<?> other, Runnable action, Executor executor)`

### Either Methods

- `CompletableFuture<T> applyToEither(CompletionStage<? extends T> other, Function<? super T,? extends U> fn)`

- `CompletableFuture<T> applyToEitherAsync(CompletionStage<? extends T> other, Function<? super T,? extends U> fn)`

- `CompletableFuture<T> applyToEitherAsync(CompletionStage<? extends T> other, Function<? super T,? extends U> fn, Executor executor)`

- `CompletableFuture<Void> acceptEither(CompletionStage<? extends T> other, Consumer<? super T> action)`

- `CompletableFuture<Void> acceptEitherAsync(CompletionStage<? extends T> other, Consumer<? super T> action)`

- `CompletableFuture<Void> acceptEitherAsync(CompletionStage<? extends T> other, Consumer<? super T> action, Executor executor)`

- `CompletableFuture<Void> runAfterEither(CompletionStage<?> other, Runnable action)`

- `CompletableFuture<Void> runAfterEitherAsync(CompletionStage<?> other, Runnable action)`

- `CompletableFuture<Void> runAfterEitherAsync(CompletionStage<?> other, Runnable action, Executor executor)`

### Exception Handling Methods

- `CompletableFuture<T> exceptionally(Function<Throwable,? extends T> fn)`

- `CompletableFuture<T> whenComplete(BiConsumer<? super T,? super Throwable> action)`

- `CompletableFuture<T> whenCompleteAsync(BiConsumer<? super T,? super Throwable> action)`

- `CompletableFuture<T> whenCompleteAsync(BiConsumer<? super T,? super Throwable> action, Executor executor)`

- `CompletableFuture<U> handle(BiFunction<? super T, Throwable,? extends U> fn)`

- `CompletableFuture<U> handleAsync(BiFunction<? super T, Throwable,? extends U> fn)`

- `CompletableFuture<U> handleAsync(BiFunction<? super T, Throwable,? extends U> fn, Executor executor)`

### Combining Multiple CompletableFutures

- `static CompletableFuture<Void> allOf(CompletableFuture<?>... cfs)`

- `static CompletableFuture<Object> anyOf(CompletableFuture<?>... cfs)`

### Blocking Methods

- `T get() throws InterruptedException, ExecutionException`

- `T get(long timeout, TimeUnit unit) throws InterruptedException, ExecutionException, TimeoutException`

- `T join()`

- `T getNow(T valueIfAbsent)`

### Utility Methods

- `boolean complete(T value)`

- `boolean completeExceptionally(Throwable ex)`

- `boolean obtrudeValue(T value)`

- `boolean obtrudeException(Throwable ex)`

- `int getNumberOfDependents()`

- `static Executor delayedExecutor(long delay, TimeUnit unit)`

- `static Executor delayedExecutor(long delay, TimeUnit unit, Executor executor)`

### Timeout Methods (Java 9+)

- `CompletableFuture<T> completeOnTimeout(T value, long timeout, TimeUnit unit)`

- `CompletableFuture<T> orTimeout(long timeout, TimeUnit unit)`

### Summary

The `CompletableFuture` class in Java provides a comprehensive set of methods for asynchronous programming, including creation, combination, exception handling, and blocking methods. This allows for flexible and powerful handling of asynchronous computations, making it easier to write non-blocking and concurrent code.

# How to efficiently use CompletableFuture to map async task per input?

Using `CompletableFuture` in Java allows you to handle asynchronous tasks efficiently. If you want to map an async task to each input, you can use the `CompletableFuture` API to execute these tasks concurrently and then combine the results. Here’s a step-by-step guide on how to do this:

1. **Create a CompletableFuture for each task:**
   Use `CompletableFuture.supplyAsync` to create a `CompletableFuture` for each task. This allows you to run tasks asynchronously.

2. **Collect the CompletableFutures into a list:**
   Store each `CompletableFuture` in a list.

3. **Combine the CompletableFutures:**
   Use `CompletableFuture.allOf` to combine all the `CompletableFutures` into a single `CompletableFuture` that completes when all the individual `CompletableFutures` complete.

4. **Process the results:**
   Once all tasks are complete, process the results.

Here’s an example of how you can achieve this:

```java
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.stream.Collectors;

public class CompletableFutureExample {

    public static void main(String[] args) {
        // Example inputs
        List<Integer> inputs = List.of(1, 2, 3, 4, 5);

        // Create a list of CompletableFutures
        List<CompletableFuture<Integer>> futures = inputs.stream()
            .map(input -> CompletableFuture.supplyAsync(() -> asyncTask(input)))
            .collect(Collectors.toList());

        // Combine all the CompletableFutures into one
        CompletableFuture<Void> allOf = CompletableFuture.allOf(futures.toArray(new CompletableFuture[0]));

        // When all tasks are complete, collect the results
        CompletableFuture<List<Integer>> allResults = allOf.thenApply(v ->
            futures.stream()
                .map(CompletableFuture::join)
                .collect(Collectors.toList())
        );

        // Process the results
        try {
            List<Integer> results = allResults.get();
            results.forEach(result -> System.out.println("Result: " + result));
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }

    // Example async task
    private static Integer asyncTask(Integer input) {
        // Simulate a delay
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        return input * 2;
    }
}
```

### Explanation:

1. **Create a list of CompletableFutures:**
   - For each input, `CompletableFuture.supplyAsync(() -> asyncTask(input))` creates a new `CompletableFuture` that runs `asyncTask` asynchronously.

2. **Combine the CompletableFutures:**
   - `CompletableFuture.allOf(futures.toArray(new CompletableFuture[0]))` returns a new `CompletableFuture` that completes when all the `futures` complete.

3. **Collect the results:**
   - `allOf.thenApply(v -> futures.stream().map(CompletableFuture::join).collect(Collectors.toList()))` transforms the combined `CompletableFuture` to a `CompletableFuture<List<Integer>>` containing the results of the individual `CompletableFutures`.

4. **Process the results:**
   - `allResults.get()` blocks until the combined `CompletableFuture` is complete and returns the list of results.

This approach efficiently handles multiple asynchronous tasks, making use of `CompletableFuture`'s capabilities to manage concurrency and combine results.

# How to execute an Array of CompletableFuture and compose their results

To execute an array of `CompletableFuture` objects and compose their results, you can use a similar approach to the one described previously, but with an array instead of a list. Here's a detailed guide on how to achieve this:

1. **Create an array of `CompletableFuture` objects:**
   Each element in the array represents an asynchronous task.

2. **Combine the `CompletableFuture` objects:**
   Use `CompletableFuture.allOf` to create a single `CompletableFuture` that completes when all the individual `CompletableFuture` objects complete.

3. **Compose the results:**
   Once all tasks are complete, process the results from each `CompletableFuture`.

Here’s an example of how you can do this in Java:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CompletableFutureArrayExample {

    public static void main(String[] args) {
        // Example inputs
        Integer[] inputs = {1, 2, 3, 4, 5};

        // Create an array of CompletableFutures
        CompletableFuture<Integer>[] futures = Stream.of(inputs)
            .map(input -> CompletableFuture.supplyAsync(() -> asyncTask(input)))
            .toArray(CompletableFuture[]::new);

        // Combine all the CompletableFutures into one
        CompletableFuture<Void> allOf = CompletableFuture.allOf(futures);

        // When all tasks are complete, collect the results
        CompletableFuture<Integer[]> allResults = allOf.thenApply(v ->
            Stream.of(futures)
                .map(CompletableFuture::join)
                .toArray(Integer[]::new)
        );

        // Process the results
        try {
            Integer[] results = allResults.get();
            for (Integer result : results) {
                System.out.println("Result: " + result);
            }
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }

    // Example async task
    private static Integer asyncTask(Integer input) {
        // Simulate a delay
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        return input * 2;
    }
}
```

### Explanation:

1. **Create an array of `CompletableFuture` objects:**
   - `Stream.of(inputs).map(input -> CompletableFuture.supplyAsync(() -> asyncTask(input))).toArray(CompletableFuture[]::new)` converts the input array to a stream, maps each input to an asynchronous task using `CompletableFuture.supplyAsync`, and collects the results into an array of `CompletableFuture` objects.

2. **Combine the `CompletableFuture` objects:**
   - `CompletableFuture.allOf(futures)` returns a new `CompletableFuture` that completes when all the `futures` complete.

3. **Compose the results:**
   - `allOf.thenApply(v -> Stream.of(futures).map(CompletableFuture::join).toArray(Integer[]::new))` transforms the combined `CompletableFuture` to a `CompletableFuture<Integer[]>` containing the results of the individual `CompletableFuture` objects.

4. **Process the results:**
   - `allResults.get()` blocks until the combined `CompletableFuture` is complete and returns the array of results.

This approach ensures that all asynchronous tasks are executed concurrently and their results are composed into a single array.

# Why use completableFuture If tasks are dependent

If tasks are dependent on each other, `CompletableFuture` can still be very useful. It allows you to chain asynchronous computations in a clear and manageable way. You can specify actions to perform once a `CompletableFuture` completes, and these actions can themselves return new `CompletableFuture` objects, creating a chain of dependent tasks. This approach can help to avoid callback hell and make the code more readable and maintainable.

Here are some key methods of `CompletableFuture` that are particularly useful for chaining dependent tasks:

- `thenApply(Function)`: Transforms the result of a `CompletableFuture` once it completes.
- `thenCompose(Function)`: Flattens nested `CompletableFuture` objects by chaining another `CompletableFuture` to run after the first one.
- `thenCombine(CompletableFuture, BiFunction)`: Combines the results of two `CompletableFuture` objects once both complete.

Here’s an example demonstrating how to use `CompletableFuture` for dependent tasks:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureDependentExample {

    public static void main(String[] args) {
        try {
            // Start the first async task
            CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> asyncTask1());

            // Chain the second task to run after the first one completes
            CompletableFuture<Integer> future2 = future1.thenCompose(result1 -> 
                CompletableFuture.supplyAsync(() -> asyncTask2(result1))
            );

            // Chain the third task to run after the second one completes
            CompletableFuture<Integer> future3 = future2.thenCompose(result2 -> 
                CompletableFuture.supplyAsync(() -> asyncTask3(result2))
            );

            // Get the final result
            Integer result = future3.get();
            System.out.println("Final result: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }

    // Example async task 1
    private static Integer asyncTask1() {
        // Simulate a delay
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("Task 1 completed");
        return 1;
    }

    // Example async task 2, dependent on the result of task 1
    private static Integer asyncTask2(Integer input) {
        // Simulate a delay
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("Task 2 completed with input: " + input);
        return input + 1;
    }

    // Example async task 3, dependent on the result of task 2
    private static Integer asyncTask3(Integer input) {
        // Simulate a delay
        try {
            Thread.sleep(1000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        System.out.println("Task 3 completed with input: " + input);
        return input + 1;
    }
}
```

### Explanation:

1. **Task 1:**
   - `CompletableFuture.supplyAsync(() -> asyncTask1())` starts the first asynchronous task. This task returns an `Integer`.

2. **Task 2:**
   - `future1.thenCompose(result1 -> CompletableFuture.supplyAsync(() -> asyncTask2(result1)))` chains the second task to run after the first task completes. The result of the first task (`result1`) is passed as an input to the second task.

3. **Task 3:**
   - `future2.thenCompose(result2 -> CompletableFuture.supplyAsync(() -> asyncTask3(result2)))` chains the third task to run after the second task completes. The result of the second task (`result2`) is passed as an input to the third task.

4. **Final Result:**
   - `future3.get()` blocks until the final `CompletableFuture` completes and returns the final result.

By chaining dependent tasks with `thenCompose`, you can ensure that each task runs only after the previous one completes and its result is available. This makes the code more modular and easier to read and maintain.

# Does completableFuture in Java 8 scale to multiple cores?

Yes, `CompletableFuture` in Java 8 is designed to work well with multiple cores and can be used to perform concurrent tasks, taking advantage of the parallelism provided by modern multi-core processors. By default, `CompletableFuture` uses the common ForkJoinPool, which is a multi-threaded executor that scales across all available processor cores.

Here's how `CompletableFuture` can scale to multiple cores:

1. **Default ForkJoinPool:**
   When you use methods like `CompletableFuture.supplyAsync`, it submits tasks to the common ForkJoinPool. The ForkJoinPool uses a work-stealing algorithm to efficiently balance the load across all available cores.

2. **Custom Executor:**
   You can provide a custom `Executor` to the `CompletableFuture` methods to control how tasks are executed. This allows you to tailor the concurrency settings to match your application's needs.

### Example Using Default ForkJoinPool

Here's a simple example showing how `CompletableFuture` can perform tasks concurrently using the default ForkJoinPool:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureExample {

    public static void main(String[] args) {
        // Start multiple asynchronous tasks
        CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> longRunningTask(1));
        CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> longRunningTask(2));
        CompletableFuture<Integer> future3 = CompletableFuture.supplyAsync(() -> longRunningTask(3));

        // Wait for all tasks to complete and get their results
        CompletableFuture<Void> allOf = CompletableFuture.allOf(future1, future2, future3);

        try {
            // Block until all tasks are complete
            allOf.get();
            
            // Process the results
            System.out.println("Result from task 1: " + future1.get());
            System.out.println("Result from task 2: " + future2.get());
            System.out.println("Result from task 3: " + future3.get());
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }

    // Simulated long-running task
    private static Integer longRunningTask(int taskNumber) {
        try {
            // Simulate a long-running task
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        return taskNumber * 2;
    }
}
```

### Example Using Custom Executor

If you want more control over the execution, you can provide a custom `Executor`:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class CompletableFutureCustomExecutorExample {

    public static void main(String[] args) {
        // Create a custom executor with a fixed thread pool
        ExecutorService executor = Executors.newFixedThreadPool(4);

        // Start multiple asynchronous tasks using the custom executor
        CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> longRunningTask(1), executor);
        CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> longRunningTask(2), executor);
        CompletableFuture<Integer> future3 = CompletableFuture.supplyAsync(() -> longRunningTask(3), executor);

        // Wait for all tasks to complete and get their results
        CompletableFuture<Void> allOf = CompletableFuture.allOf(future1, future2, future3);

        try {
            // Block until all tasks are complete
            allOf.get();
            
            // Process the results
            System.out.println("Result from task 1: " + future1.get());
            System.out.println("Result from task 2: " + future2.get());
            System.out.println("Result from task 3: " + future3.get());
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            // Shutdown the executor
            executor.shutdown();
        }
    }

    // Simulated long-running task
    private static Integer longRunningTask(int taskNumber) {
        try {
            // Simulate a long-running task
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        return taskNumber * 2;
    }
}
```

### Explanation:

1. **Default ForkJoinPool:**
   - `CompletableFuture.supplyAsync(() -> longRunningTask(1))` uses the common ForkJoinPool to execute tasks concurrently. The ForkJoinPool scales across multiple cores by default.

2. **Custom Executor:**
   - `Executors.newFixedThreadPool(4)` creates a custom thread pool with 4 threads.
   - `CompletableFuture.supplyAsync(() -> longRunningTask(1), executor)` uses the custom executor to execute tasks. This allows you to control the number of threads and other execution parameters.

### Performance Considerations:

- **Work-Stealing:**
  The ForkJoinPool uses a work-stealing algorithm, which helps in efficiently utilizing all available cores by redistributing tasks from busy threads to idle ones.

- **Thread Pool Size:**
  Adjusting the size of the thread pool in the custom executor allows you to fine-tune the degree of parallelism. However, setting it too high can lead to contention and overhead, while setting it too low might underutilize available cores.

By using `CompletableFuture` with either the default ForkJoinPool or a custom executor, you can effectively scale your asynchronous tasks across multiple cores, thereby improving the performance of concurrent operations in your application.

# CompletableFuture thenApplyAsync vs thenCompose and their use cases

`CompletableFuture` in Java provides various methods to handle asynchronous operations, with `thenApplyAsync` and `thenCompose` being two of the commonly used methods. Understanding the differences between these two methods and their appropriate use cases is crucial for writing efficient and maintainable asynchronous code.

### `thenApplyAsync`

- **Purpose:**
  - `thenApplyAsync` is used to process the result of a `CompletableFuture` once it is completed. It applies a function to the result and returns a new `CompletableFuture` that holds the transformed result.
  - It is typically used when you want to perform further computation on the result of an async operation in a non-blocking way.

- **Behavior:**
  - The function passed to `thenApplyAsync` runs asynchronously, using either the common ForkJoinPool or a provided custom executor.

- **Example:**

  ```java
  CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
      // Simulate a long-running task
      return 42;
  });

  CompletableFuture<String> transformedFuture = future.thenApplyAsync(result -> {
      // Transform the result
      return "Result: " + result;
  });

  transformedFuture.thenAccept(result -> {
      // Process the transformed result
      System.out.println(result);
  });
  ```

### `thenCompose`

- **Purpose:**
  - `thenCompose` is used to chain dependent asynchronous operations. It allows you to flatten nested `CompletableFuture` instances by combining them into a single `CompletableFuture`.
  - It is typically used when the next asynchronous operation depends on the result of the previous one.

- **Behavior:**
  - The function passed to `thenCompose` returns a `CompletableFuture`. The resulting `CompletableFuture` is not nested but instead represents the completion of both operations.

- **Example:**

  ```java
  CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
      // Simulate a long-running task
      return 42;
  });

  CompletableFuture<String> combinedFuture = future.thenCompose(result -> {
      // Start another async operation based on the result of the first one
      return CompletableFuture.supplyAsync(() -> "Result: " + result);
  });

  combinedFuture.thenAccept(result -> {
      // Process the final result
      System.out.println(result);
  });
  ```

### Key Differences and Use Cases:

1. **Return Types:**
   - `thenApplyAsync`: The function you pass returns a regular value, which is wrapped in a `CompletableFuture` by the method.
   - `thenCompose`: The function you pass returns a `CompletableFuture`, and `thenCompose` effectively flattens this into a single `CompletableFuture`.

2. **Nesting of Futures:**
   - `thenApplyAsync` can lead to nested `CompletableFuture` instances if used to chain asynchronous tasks that themselves return `CompletableFuture` objects.
   - `thenCompose` avoids nesting by directly returning the `CompletableFuture` from the next async operation, making it easier to manage dependent tasks.

3. **Use Cases:**
   - **thenApplyAsync:**
     - Use when you need to transform the result of a `CompletableFuture` and want to run the transformation asynchronously.
     - Ideal for scenarios where you have a simple transformation that doesn’t involve further asynchronous operations.
   - **thenCompose:**
     - Use when you have a sequence of dependent asynchronous operations.
     - Ideal for scenarios where the next async operation depends on the result of the previous one and you want to avoid nesting `CompletableFuture` objects.

### Summary

- **`thenApplyAsync`:** For transforming results asynchronously.
- **`thenCompose`:** For chaining dependent asynchronous operations.

Choosing between `thenApplyAsync` and `thenCompose` depends on whether you need to transform a result or chain further asynchronous tasks. Use `thenApplyAsync` for non-blocking transformations and `thenCompose` for dependent asynchronous operations.

# Async variants of thenXXXX methods

In Java's `CompletableFuture`, there are several methods prefixed with `then`, which are used to process the result of an asynchronous computation once it completes. These methods come in both synchronous and asynchronous variants. The asynchronous variants, denoted by the suffix `Async`, run the provided function or action in a separate thread, typically using the common ForkJoinPool or a custom executor.

Here are the primary `thenXXXXAsync` methods:

### `thenApplyAsync`

- **Purpose:**
  - Transforms the result of a `CompletableFuture` asynchronously.
- **Signature:**
  ```java
  public <U> CompletableFuture<U> thenApplyAsync(Function<? super T, ? extends U> fn)
  public <U> CompletableFuture<U> thenApplyAsync(Function<? super T, ? extends U> fn, Executor executor)
  ```
- **Example:**
  ```java
  CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 42);
  CompletableFuture<String> transformedFuture = future.thenApplyAsync(result -> "Result: " + result);
  ```

### `thenAcceptAsync`

- **Purpose:**
  - Consumes the result of a `CompletableFuture` asynchronously.
- **Signature:**
  ```java
  public CompletableFuture<Void> thenAcceptAsync(Consumer<? super T> action)
  public CompletableFuture<Void> thenAcceptAsync(Consumer<? super T> action, Executor executor)
  ```
- **Example:**
  ```java
  CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 42);
  future.thenAcceptAsync(result -> System.out.println("Result: " + result));
  ```

### `thenRunAsync`

- **Purpose:**
  - Runs a provided `Runnable` asynchronously after the `CompletableFuture` completes.
- **Signature:**
  ```java
  public CompletableFuture<Void> thenRunAsync(Runnable action)
  public CompletableFuture<Void> thenRunAsync(Runnable action, Executor executor)
  ```
- **Example:**
  ```java
  CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 42);
  future.thenRunAsync(() -> System.out.println("Computation finished"));
  ```

### `thenComposeAsync`

- **Purpose:**
  - Chains another `CompletableFuture` asynchronously after the current one completes.
- **Signature:**
  ```java
  public <U> CompletableFuture<U> thenComposeAsync(Function<? super T, ? extends CompletionStage<U>> fn)
  public <U> CompletableFuture<U> thenComposeAsync(Function<? super T, ? extends CompletionStage<U>> fn, Executor executor)
  ```
- **Example:**
  ```java
  CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 42);
  CompletableFuture<String> combinedFuture = future.thenComposeAsync(result ->
      CompletableFuture.supplyAsync(() -> "Result: " + result)
  );
  ```

### `thenCombineAsync`

- **Purpose:**
  - Combines the result of this `CompletableFuture` with another asynchronously.
- **Signature:**
  ```java
  public <U,V> CompletableFuture<V> thenCombineAsync(CompletionStage<? extends U> other, BiFunction<? super T,? super U,? extends V> fn)
  public <U,V> CompletableFuture<V> thenCombineAsync(CompletionStage<? extends U> other, BiFunction<? super T,? super U,? extends V> fn, Executor executor)
  ```
- **Example:**
  ```java
  CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> 42);
  CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> 24);
  CompletableFuture<Integer> combinedFuture = future1.thenCombineAsync(future2, (result1, result2) -> result1 + result2);
  ```

### `thenAcceptBothAsync`

- **Purpose:**
  - Consumes the results of this `CompletableFuture` and another asynchronously.
- **Signature:**
  ```java
  public <U> CompletableFuture<Void> thenAcceptBothAsync(CompletionStage<? extends U> other, BiConsumer<? super T, ? super U> action)
  public <U> CompletableFuture<Void> thenAcceptBothAsync(CompletionStage<? extends U> other, BiConsumer<? super T, ? super U> action, Executor executor)
  ```
- **Example:**
  ```java
  CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> 42);
  CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> 24);
  future1.thenAcceptBothAsync(future2, (result1, result2) -> System.out.println(result1 + result2));
  ```

### `runAfterBothAsync`

- **Purpose:**
  - Runs a `Runnable` asynchronously after both `CompletableFutures` complete.
- **Signature:**
  ```java
  public CompletableFuture<Void> runAfterBothAsync(CompletionStage<?> other, Runnable action)
  public CompletableFuture<Void> runAfterBothAsync(CompletionStage<?> other, Runnable action, Executor executor)
  ```
- **Example:**
  ```java
  CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> 42);
  CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> 24);
  future1.runAfterBothAsync(future2, () -> System.out.println("Both computations finished"));
  ```

### `runAfterEitherAsync`

- **Purpose:**
  - Runs a `Runnable` asynchronously after either of the `CompletableFutures` completes.
- **Signature:**
  ```java
  public CompletableFuture<Void> runAfterEitherAsync(CompletionStage<?> other, Runnable action)
  public CompletableFuture<Void> runAfterEitherAsync(CompletionStage<?> other, Runnable action, Executor executor)
  ```
- **Example:**
  ```java
  CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> 42);
  CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> 24);
  future1.runAfterEitherAsync(future2, () -> System.out.println("One of the computations finished"));
  ```

### Choosing Between Async and Non-Async Variants

- **Async Variants:**
  - Use `thenXXXXAsync` variants when you want to ensure that the next stage runs asynchronously, potentially on a different thread. This can help in offloading computation to another thread pool and prevent blocking the current thread.
  - They are useful when the subsequent task is computationally intensive or when you want to avoid blocking the current thread.

- **Non-Async Variants:**
  - Use non-async `thenXXXX` variants when the next stage can run on the same thread as the previous stage. This is generally more efficient if the subsequent computation is lightweight and doesn't block.

### Custom Executors

You can pass a custom `Executor` to any of the `Async` methods to control how and where the asynchronous computation will be executed. This provides flexibility in managing thread pools and optimizing performance based on your application's requirements.

### Example with Custom Executor

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class CompletableFutureCustomExecutorExample {

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(4);

        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
            // Simulate a long-running task
            return 42;
        }, executor);

        CompletableFuture<String> transformedFuture = future.thenApplyAsync(result -> {
            // Transform the result
            return "Result: " + result;
        }, executor);

        transformedFuture.thenAcceptAsync(result -> {
            // Process the transformed result
            System.out.println(result);
        }, executor);

        executor.shutdown();
    }
}
```

In summary, the `Async` variants of `CompletableFuture` methods allow for better control over threading and can help improve the scalability and responsiveness of your application by utilizing multiple threads effectively. Use them when you need to ensure that tasks are executed asynchronously, especially for computationally intensive or blocking operations.

**OR**

In CompletableFuture, several methods are provided to handle asynchronous tasks. Each of these methods has a synchronous variant (e.g., thenApply, thenAccept, etc.) and an asynchronous variant (e.g., thenApplyAsync, thenAcceptAsync, etc.). The asynchronous variants run the provided function asynchronously using either the common ForkJoinPool or a custom Executor.

## Common Async Methods in CompletableFuture

1. thenApplyAsync

2. thenAcceptAsync

3. thenRunAsync

4. thenCombineAsync

5. thenAcceptBothAsync

6. runAfterBothAsync

7. thenComposeAsync

8. applyToEitherAsync

9. acceptEitherAsync

10. runAfterEitherAsync

11. handleAsync

12. whenCompleteAsync

# In which thread do CompletableFuture's completion handlers execute?

The thread in which `CompletableFuture`'s completion handlers execute depends on the specific method used to attach the handler and whether an `Executor` is provided. Here’s a detailed breakdown:

### Synchronous Methods (`thenApply`, `thenAccept`, etc.)

- **Current Thread or Task's Completion Thread:**
  - If the `CompletableFuture` is already completed when the handler is attached, the handler executes in the current thread.
  - If the `CompletableFuture` is not yet completed, the handler typically executes in the thread that completes the `CompletableFuture`.

### Asynchronous Methods (`thenApplyAsync`, `thenAcceptAsync`, etc.)

- **Common ForkJoinPool or Custom Executor:**
  - If no `Executor` is provided, the handler executes in the common ForkJoinPool, which is a pool of worker threads.
  - If an `Executor` is provided, the handler executes in a thread from the provided `Executor`.

### Detailed Examples:

#### Synchronous Completion Handlers

```java
import java.util.concurrent.CompletableFuture;

public class SyncCompletionExample {
    public static void main(String[] args) {
        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 42);

        // This handler may execute in the same thread that completes the future
        future.thenApply(result -> {
            System.out.println("Thread in thenApply: " + Thread.currentThread().getName());
            return result * 2;
        }).thenAccept(result -> {
            System.out.println("Thread in thenAccept: " + Thread.currentThread().getName());
            System.out.println("Result: " + result);
        });

        // Wait for the tasks to complete (not needed in real applications)
        future.join();
    }
}
```

#### Asynchronous Completion Handlers (Common ForkJoinPool)

```java
import java.util.concurrent.CompletableFuture;

public class AsyncCompletionExample {
    public static void main(String[] args) {
        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 42);

        // This handler executes in the common ForkJoinPool
        future.thenApplyAsync(result -> {
            System.out.println("Thread in thenApplyAsync: " + Thread.currentThread().getName());
            return result * 2;
        }).thenAcceptAsync(result -> {
            System.out.println("Thread in thenAcceptAsync: " + Thread.currentThread().getName());
            System.out.println("Result: " + result);
        });

        // Wait for the tasks to complete (not needed in real applications)
        future.join();
    }
}
```

#### Asynchronous Completion Handlers (Custom Executor)

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class AsyncCompletionCustomExecutorExample {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(4);

        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 42);

        // This handler executes in the custom executor
        future.thenApplyAsync(result -> {
            System.out.println("Thread in thenApplyAsync with custom executor: " + Thread.currentThread().getName());
            return result * 2;
        }, executor).thenAcceptAsync(result -> {
            System.out.println("Thread in thenAcceptAsync with custom executor: " + Thread.currentThread().getName());
            System.out.println("Result: " + result);
        }, executor);

        // Wait for the tasks to complete and shut down the executor (not needed in real applications)
        future.join();
        executor.shutdown();
    }
}
```

### Summary

- **Synchronous methods (`thenApply`, `thenAccept`, etc.):**
  - May execute in the thread that completes the `CompletableFuture` or the current thread if the `CompletableFuture` is already completed when the handler is attached.

- **Asynchronous methods (`thenApplyAsync`, `thenAcceptAsync`, etc.):**
  - Execute in the common ForkJoinPool if no `Executor` is provided.
  - Execute in the provided custom `Executor` if one is specified.

Using asynchronous methods with a custom executor gives you control over the threading model and can help you manage the performance and concurrency characteristics of your application more precisely.

# CompletableFuture on Single core machine

Using `CompletableFuture` on a single-core machine requires a good understanding of its asynchronous behavior and the thread pool it uses. While `CompletableFuture` is designed to run tasks concurrently, on a single-core machine, this concurrency is simulated by time-slicing the CPU among multiple tasks, since only one thread can run at a time.

### Key Points to Consider:

1. **Thread Pool Usage:**
   - The default `CompletableFuture.supplyAsync` method uses the common ForkJoinPool. This pool will still create multiple threads, but on a single-core machine, only one thread can execute at any given time.
   - Providing a custom executor can help you manage how tasks are scheduled and executed.

2. **Task Scheduling:**
   - Even on a single-core machine, using multiple threads can improve the responsiveness of applications, as tasks can be interleaved. However, the overall execution time may not significantly improve since the core still needs to switch context between threads.

3. **Avoiding Blocking Calls:**
   - To make the best use of `CompletableFuture` on a single-core machine, avoid blocking calls within your tasks. Blocking a thread on a single-core machine can significantly degrade performance.

### Examples:

#### Default Executor (ForkJoinPool)

```java
import java.util.concurrent.CompletableFuture;

public class SingleCoreExample {
    public static void main(String[] args) {
        // SupplyAsync uses the common ForkJoinPool
        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
            simulateWork("Task 1");
            return 42;
        });

        future.thenApplyAsync(result -> {
            simulateWork("Task 2");
            return result * 2;
        }).thenAcceptAsync(result -> {
            simulateWork("Task 3");
            System.out.println("Result: " + result);
        });

        // Block to wait for completion
        future.join();
    }

    private static void simulateWork(String taskName) {
        try {
            System.out.println(taskName + " is running in thread: " + Thread.currentThread().getName());
            Thread.sleep(1000); // Simulate work
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

#### Custom Executor

Using a custom executor can help you manage task execution more explicitly.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class SingleCoreCustomExecutorExample {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(2); // Create a custom thread pool

        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
            simulateWork("Task 1");
            return 42;
        }, executor);

        future.thenApplyAsync(result -> {
            simulateWork("Task 2");
            return result * 2;
        }, executor).thenAcceptAsync(result -> {
            simulateWork("Task 3");
            System.out.println("Result: " + result);
        }, executor);

        // Block to wait for completion
        future.join();
        executor.shutdown();
    }

    private static void simulateWork(String taskName) {
        try {
            System.out.println(taskName + " is running in thread: " + Thread.currentThread().getName());
            Thread.sleep(1000); // Simulate work
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

### Summary

- **Thread Management:**
  On a single-core machine, the benefits of multithreading with `CompletableFuture` come from improved task interleaving rather than true parallelism. Using a custom executor allows for better control over how tasks are managed and executed.

- **Avoid Blocking:**
  Ensure that tasks do not block the CPU for long periods to avoid degrading performance. Use non-blocking or asynchronous I/O operations where possible.

- **Task Scheduling:**
  Understand that while `CompletableFuture` can create multiple threads, the single core can only execute one thread at a time, meaning the benefits of concurrency are limited to better responsiveness rather than faster execution. 

By using `CompletableFuture` judiciously, even a single-core machine can handle multiple asynchronous tasks more effectively, improving the responsiveness and manageability of your applications.

# How to run multiple service calls in parallel using CompletableFuture?

To run multiple service calls in parallel using `CompletableFuture` in Java, you can create individual `CompletableFuture` instances for each service call and then combine them. Here's a step-by-step guide on how to achieve this:

1. **Create Individual `CompletableFuture` Instances:**
   Each service call will be wrapped in a `CompletableFuture`.

2. **Combine `CompletableFuture` Instances:**
   Use methods like `allOf`, `anyOf`, or `thenCombine` to combine these futures.

3. **Process the Results:**
   Once all futures are complete, you can process the results.

### Example

Let's consider an example where we call three different services in parallel and then process their combined results.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.List;
import java.util.stream.Collectors;

public class CompletableFutureExample {

    public static void main(String[] args) {
        // Create a custom executor for managing threads
        ExecutorService executor = Executors.newFixedThreadPool(3);

        // Create CompletableFuture instances for service calls
        CompletableFuture<String> serviceCall1 = CompletableFuture.supplyAsync(() -> callService1(), executor);
        CompletableFuture<String> serviceCall2 = CompletableFuture.supplyAsync(() -> callService2(), executor);
        CompletableFuture<String> serviceCall3 = CompletableFuture.supplyAsync(() -> callService3(), executor);

        // Combine the futures
        CompletableFuture<Void> allFutures = CompletableFuture.allOf(serviceCall1, serviceCall2, serviceCall3);

        // Process the results once all futures are complete
        CompletableFuture<List<String>> allResults = allFutures.thenApply(v -> {
            return List.of(serviceCall1, serviceCall2, serviceCall3).stream()
                    .map(CompletableFuture::join) // Join to get results
                    .collect(Collectors.toList());
        });

        // Print the results
        try {
            List<String> results = allResults.get();
            results.forEach(System.out::println);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }

        // Shutdown the executor
        executor.shutdown();
    }

    // Simulate a service call
    private static String callService1() {
        try {
            Thread.sleep(1000); // Simulate delay
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        return "Service 1 Result";
    }

    // Simulate another service call
    private static String callService2() {
        try {
            Thread.sleep(1500); // Simulate delay
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        return "Service 2 Result";
    }

    // Simulate a third service call
    private static String callService3() {
        try {
            Thread.sleep(2000); // Simulate delay
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        return "Service 3 Result";
    }
}
```

### Explanation

1. **ExecutorService:**
   - A custom `ExecutorService` is created to manage the threads.

2. **CompletableFuture for Each Service Call:**
   - `CompletableFuture.supplyAsync` is used to make each service call asynchronously. Each call simulates a delay using `Thread.sleep`.

3. **Combining Futures:**
   - `CompletableFuture.allOf` is used to wait for all futures to complete. This method returns a `CompletableFuture<Void>` that completes when all the provided futures complete.

4. **Processing Results:**
   - `thenApply` is used on the combined future to process the results. Here, we collect the results from each individual future using `CompletableFuture::join`.

5. **Handling Results:**
   - `allResults.get()` is used to block and retrieve the final list of results. These results are then printed.

6. **Shutting Down the Executor:**
   - The custom executor is shut down to release resources.

### Notes

- **Exception Handling:**
  This example uses `join`, which throws unchecked exceptions. For more robust error handling, consider using `handle`, `exceptionally`, or `whenComplete`.

- **ExecutorService:**
  A custom executor is used to control the number of threads. The common ForkJoinPool can also be used by not providing an executor to `supplyAsync`.

- **Parallel Execution:**
  Even on a single-core machine, using multiple threads can help interleave IO-bound tasks efficiently.

This approach ensures that multiple service calls run in parallel, and their results are processed once all calls are complete, leveraging the capabilities of `CompletableFuture` in Java.

# CompletableFuture allof(..).join() vs CompletableFuture.join()

When using `CompletableFuture` in Java, there are different ways to wait for multiple futures to complete. Specifically, you can use `CompletableFuture.allOf(...).join()` and `CompletableFuture.join()`. These two approaches are used in different contexts and have distinct differences in behavior.

### CompletableFuture.allOf(...).join()

`CompletableFuture.allOf(...)` is used to wait for multiple `CompletableFuture` instances to complete. It returns a new `CompletableFuture<Void>` that completes when all the given `CompletableFuture`s complete. The `join()` method is then used to block until the combined future is complete.

#### Usage:

- **Combines multiple futures**: Waits for all the provided `CompletableFuture` instances to complete.
- **Returns a new `CompletableFuture<Void>`**: This new future completes when all the combined futures complete.
- **Use case**: When you need to wait for multiple asynchronous tasks to complete before proceeding.

#### Example:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureAllOfExample {

    public static void main(String[] args) {
        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
            try { Thread.sleep(1000); } catch (InterruptedException e) { e.printStackTrace(); }
            return "Future 1";
        });

        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> {
            try { Thread.sleep(1500); } catch (InterruptedException e) { e.printStackTrace(); }
            return "Future 2";
        });

        CompletableFuture<String> future3 = CompletableFuture.supplyAsync(() -> {
            try { Thread.sleep(2000); } catch (InterruptedException e) { e.printStackTrace(); }
            return "Future 3";
        });

        // Combine all futures and wait for all of them to complete
        CompletableFuture<Void> allOf = CompletableFuture.allOf(future1, future2, future3);
        allOf.join(); // Wait for all to complete

        // Get the results of the individual futures
        try {
            System.out.println("Result 1: " + future1.get());
            System.out.println("Result 2: " + future2.get());
            System.out.println("Result 3: " + future3.get());
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

### CompletableFuture.join()

`CompletableFuture.join()` is used to block until a single `CompletableFuture` completes and then returns the result (or throws an unchecked exception if the future completed exceptionally).

#### Usage:

- **Waits for a single future**: Blocks until the `CompletableFuture` is complete and retrieves its result.
- **Returns the result directly**: Unlike `allOf`, it doesn't combine multiple futures.
- **Use case**: When you need to wait for and retrieve the result of a single asynchronous task.

#### Example:

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureJoinExample {

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            try { Thread.sleep(1000); } catch (InterruptedException e) { e.printStackTrace(); }
            return "Future result";
        });

        // Wait for the future to complete and get the result
        String result = future.join();
        System.out.println("Result: " + result);
    }
}
```

### Key Differences

1. **Scope of Waiting**:
   - `CompletableFuture.allOf(...).join()`: Waits for multiple `CompletableFuture`s to complete.
   - `CompletableFuture.join()`: Waits for a single `CompletableFuture` to complete.

2. **Return Type**:
   - `CompletableFuture.allOf(...).join()`: Returns a `Void` future, meaning you need to manually retrieve the results of individual futures using their respective `join()` or `get()` methods.
   - `CompletableFuture.join()`: Directly returns the result of the single future it waits for.

3. **Usage Context**:
   - `CompletableFuture.allOf(...).join()`: Useful when coordinating multiple parallel tasks and ensuring all have completed before proceeding.
   - `CompletableFuture.join()`: Useful for waiting on and retrieving the result of a single asynchronous computation.

### Practical Example: Combining Both Approaches

You might often combine the two approaches, waiting for all futures to complete using `allOf` and then retrieving individual results using `join` on each future.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.List;
import java.util.stream.Collectors;

public class CombinedExample {

    public static void main(String[] args) {
        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
            try { Thread.sleep(1000); } catch (InterruptedException e) { e.printStackTrace(); }
            return "Future 1";
        });

        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> {
            try { Thread.sleep(1500); } catch (InterruptedException e) { e.printStackTrace(); }
            return "Future 2";
        });

        CompletableFuture<String> future3 = CompletableFuture.supplyAsync(() -> {
            try { Thread.sleep(2000); } catch (InterruptedException e) { e.printStackTrace(); }
            return "Future 3";
        });

        // Combine all futures and wait for all of them to complete
        CompletableFuture<Void> allOf = CompletableFuture.allOf(future1, future2, future3);
        allOf.join(); // Wait for all to complete

        // Get the results of the individual futures
        List<String> results = List.of(future1, future2, future3).stream()
                                   .map(CompletableFuture::join)
                                   .collect(Collectors.toList());

        // Print the results
        results.forEach(System.out::println);
    }
}
```

In this example, `CompletableFuture.allOf(...).join()` ensures that all futures have completed, and then individual results are retrieved using `CompletableFuture.join()` on each future. This approach is particularly useful for coordinating multiple asynchronous tasks and processing their results once all tasks are done.

# How to apply a function to multiple CompletableFutures?

Applying a function to multiple `CompletableFuture` instances typically involves combining their results and then applying the function. You can use methods like `thenCombine`, `thenCombineAsync`, or `thenApply` in conjunction with `CompletableFuture.allOf` to achieve this.

Here’s how you can do it in different ways:

### Example Using `thenCombine`

If you have two `CompletableFuture` instances and want to combine their results and then apply a function, you can use `thenCombine` or `thenCombineAsync`.

#### Two `CompletableFuture` Instances

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureCombineExample {

    public static void main(String[] args) {
        CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> 2);
        CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> 3);

        // Combine two futures and apply a function
        CompletableFuture<Integer> resultFuture = future1.thenCombine(future2, (result1, result2) -> result1 + result2);

        // Get the result
        int result = resultFuture.join();
        System.out.println("Result: " + result); // Output: Result: 5
    }
}
```

### Example Using `allOf` and `thenApply`

If you have more than two `CompletableFuture` instances, you can use `CompletableFuture.allOf` to wait for all futures to complete, then apply a function to the combined results.

#### Multiple `CompletableFuture` Instances

```java
import java.util.concurrent.CompletableFuture;
import java.util.List;
import java.util.stream.Collectors;
import java.util.Arrays;

public class CompletableFutureAllOfExample {

    public static void main(String[] args) {
        CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> 2);
        CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> 3);
        CompletableFuture<Integer> future3 = CompletableFuture.supplyAsync(() -> 5);

        // Combine all futures and apply a function to their results
        CompletableFuture<Void> allOf = CompletableFuture.allOf(future1, future2, future3);

        CompletableFuture<List<Integer>> resultFuture = allOf.thenApply(v -> {
            return List.of(future1, future2, future3).stream()
                    .map(CompletableFuture::join)
                    .collect(Collectors.toList());
        });

        // Apply a function to the combined results
        CompletableFuture<Integer> sumFuture = resultFuture.thenApply(results -> {
            return results.stream().mapToInt(Integer::intValue).sum();
        });

        // Get the final result
        int sum = sumFuture.join();
        System.out.println("Sum: " + sum); // Output: Sum: 10
    }
}
```

### Using Custom Executor

Using a custom executor can help manage threads more efficiently, especially if you have many tasks.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.List;
import java.util.stream.Collectors;
import java.util.Arrays;

public class CompletableFutureCustomExecutorExample {

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(3);

        CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> 2, executor);
        CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> 3, executor);
        CompletableFuture<Integer> future3 = CompletableFuture.supplyAsync(() -> 5, executor);

        // Combine all futures and apply a function to their results
        CompletableFuture<Void> allOf = CompletableFuture.allOf(future1, future2, future3);

        CompletableFuture<List<Integer>> resultFuture = allOf.thenApplyAsync(v -> {
            return List.of(future1, future2, future3).stream()
                    .map(CompletableFuture::join)
                    .collect(Collectors.toList());
        }, executor);

        // Apply a function to the combined results
        CompletableFuture<Integer> sumFuture = resultFuture.thenApplyAsync(results -> {
            return results.stream().mapToInt(Integer::intValue).sum();
        }, executor);

        // Get the final result
        int sum = sumFuture.join();
        System.out.println("Sum: " + sum); // Output: Sum: 10

        // Shutdown the executor
        executor.shutdown();
    }
}
```

### Explanation

1. **Creating CompletableFutures:**
   - Multiple `CompletableFuture` instances are created using `supplyAsync`.

2. **Combining Futures:**
   - `CompletableFuture.allOf` is used to wait for all futures to complete. This returns a `CompletableFuture<Void>`.

3. **Applying Function to Combined Results:**
   - Use `thenApply` or `thenApplyAsync` to process the results of the combined futures. In the example, the results are collected into a list, and a sum function is applied.

4. **Handling the Result:**
   - The final result is retrieved using `join`.

5. **Using Custom Executor:**
   - A custom `ExecutorService` is used to manage threads, which can be beneficial for controlling the thread pool size and improving performance.

By combining these techniques, you can effectively apply a function to the results of multiple `CompletableFuture` instances, handling asynchronous computations in a clean and efficient manner.

# Use of join method in CompletableFuture class vs get method

The `join()` and `get()` methods in the `CompletableFuture` class in Java are used to retrieve the result of a computation once it is complete. However, they have some differences in behavior, especially when it comes to exception handling.

### `join()` Method

- **Return Type**: Returns the result of the computation directly.
- **Exception Handling**: Throws an unchecked exception (`CompletionException`) if the computation completed exceptionally. This exception wraps the original exception that caused the failure.
- **Blocking**: Blocks until the computation is complete.
- **Usage**: Preferred when you don't want to handle checked exceptions.

### `get()` Method

- **Return Type**: Returns the result of the computation directly.
- **Exception Handling**: Throws checked exceptions (`InterruptedException` and `ExecutionException`) if the computation is interrupted or completed exceptionally.
- **Blocking**: Blocks until the computation is complete.
- **Usage**: Preferred when you need to handle checked exceptions explicitly.

### Example Code

Here's an example demonstrating the use of both `join()` and `get()` methods:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureExample {

    public static void main(String[] args) {
        // Create a CompletableFuture that completes normally
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            try {
                Thread.sleep(1000); // Simulate long-running task
            } catch (InterruptedException e) {
                throw new IllegalStateException(e);
            }
            return "Hello, World!";
        });

        // Using join() method
        try {
            String result = future.join();
            System.out.println("Result using join(): " + result);
        } catch (Exception e) {
            System.err.println("Exception using join(): " + e.getMessage());
        }

        // Create a CompletableFuture that completes exceptionally
        CompletableFuture<String> exceptionalFuture = CompletableFuture.supplyAsync(() -> {
            throw new RuntimeException("Something went wrong!");
        });

        // Using join() method for exceptional future
        try {
            exceptionalFuture.join();
        } catch (Exception e) {
            System.err.println("Exception using join() with exceptional future: " + e.getMessage());
        }

        // Using get() method
        try {
            String result = future.get();
            System.out.println("Result using get(): " + result);
        } catch (InterruptedException | ExecutionException e) {
            System.err.println("Exception using get(): " + e.getMessage());
        }

        // Using get() method for exceptional future
        try {
            exceptionalFuture.get();
        } catch (InterruptedException | ExecutionException e) {
            System.err.println("Exception using get() with exceptional future: " + e.getMessage());
        }
    }
}
```

### Key Differences

#### Exception Handling:

- **join()**:
  - Throws an unchecked `CompletionException`.
  - Easier to use when you prefer not to deal with checked exceptions.
  - Suitable for quick prototyping or when you have a consistent error handling strategy.

- **get()**:
  - Throws checked exceptions (`InterruptedException` and `ExecutionException`).
  - Provides more control and clarity over what kind of exceptions are being handled.
  - Necessary for codebases that require detailed and explicit exception handling.

#### Blocking Behavior:

Both methods block until the `CompletableFuture` completes, so there is no difference in how they block the calling thread.

#### Usage Context:

- **join()**: More concise, and preferred when you want to avoid checked exceptions. Commonly used in cases where the calling method itself does not declare any checked exceptions.
- **get()**: More verbose, requiring handling of checked exceptions. Useful in contexts where precise exception handling is necessary.

### Practical Considerations

When choosing between `join()` and `get()`, consider your application's error handling strategy and the context in which you're using the `CompletableFuture`.

- **For quick prototypes or simple applications**: `join()` is convenient and results in cleaner code.
- **For robust production systems**: `get()` is usually better as it forces you to handle exceptions explicitly, making the code more resilient and maintainable.

By understanding the differences and use cases of `join()` and `get()`, you can choose the appropriate method to manage the completion of asynchronous tasks in your Java applications effectively.

# CompletableFuture get result without blocking

To retrieve the result of a `CompletableFuture` without blocking, you can use methods that allow you to handle the result asynchronously. Some common methods are `thenApply`, `thenAccept`, `thenRun`, and their `Async` variants. These methods allow you to specify a callback that will be executed when the `CompletableFuture` completes, without blocking the calling thread.

Here’s a brief overview of these methods:

- **`thenApply(Function<T, U>)`**: Transforms the result of the `CompletableFuture` when it completes.
- **`thenAccept(Consumer<T>)`**: Consumes the result of the `CompletableFuture` when it completes.
- **`thenRun(Runnable)`**: Runs a task after the `CompletableFuture` completes, without access to the result.
- **`handle(BiFunction<T, Throwable, U>)`**: Handles both the result and exceptions of the `CompletableFuture`.
- **`whenComplete(BiConsumer<T, Throwable>)`**: Executes a callback when the `CompletableFuture` completes, regardless of whether it was completed successfully or exceptionally.

### Example: Using `thenApply` and `thenAccept`

Let's see an example using `thenApply` to transform the result and `thenAccept` to consume it.

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureAsyncExample {

    public static void main(String[] args) {
        // Create a CompletableFuture that completes normally
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            try {
                Thread.sleep(1000); // Simulate long-running task
            } catch (InterruptedException e) {
                throw new IllegalStateException(e);
            }
            return "Hello, World!";
        });

        // Transform the result asynchronously
        CompletableFuture<String> transformedFuture = future.thenApply(result -> {
            return result + " - Transformed";
        });

        // Consume the result asynchronously
        transformedFuture.thenAccept(result -> {
            System.out.println("Result: " + result);
        });

        // Keep the main thread alive for async operations to complete
        try {
            Thread.sleep(2000); // Wait for enough time for the async tasks to complete
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

### Example: Using `handle` to Handle Both Result and Exceptions

The `handle` method can be used to handle both the result and any exceptions that may occur.

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureHandleExample {

    public static void main(String[] args) {
        // Create a CompletableFuture that completes exceptionally
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            throw new RuntimeException("Something went wrong!");
        });

        // Handle the result and exceptions
        future.handle((result, ex) -> {
            if (ex != null) {
                System.err.println("Exception: " + ex.getMessage());
                return "Default Value"; // Provide a default value in case of an exception
            } else {
                return result;
            }
        }).thenAccept(result -> {
            System.out.println("Result: " + result);
        });

        // Keep the main thread alive for async operations to complete
        try {
            Thread.sleep(2000); // Wait for enough time for the async tasks to complete
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

### Example: Using `whenComplete` to Execute a Callback Regardless of Outcome

The `whenComplete` method allows you to execute a callback whether the `CompletableFuture` completes normally or exceptionally.

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureWhenCompleteExample {

    public static void main(String[] args) {
        // Create a CompletableFuture that completes normally
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            try {
                Thread.sleep(1000); // Simulate long-running task
            } catch (InterruptedException e) {
                throw new IllegalStateException(e);
            }
            return "Hello, World!";
        });

        // Execute a callback regardless of the outcome
        future.whenComplete((result, ex) -> {
            if (ex != null) {
                System.err.println("Exception: " + ex.getMessage());
            } else {
                System.out.println("Result: " + result);
            }
        });

        // Keep the main thread alive for async operations to complete
        try {
            Thread.sleep(2000); // Wait for enough time for the async tasks to complete
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

### Summary

- Use `thenApply`, `thenAccept`, `thenRun`, and their `Async` variants to handle the result of a `CompletableFuture` asynchronously.
- Use `handle` to manage both the result and exceptions.
- Use `whenComplete` to execute a callback regardless of whether the `CompletableFuture` completed normally or exceptionally.

These methods allow you to work with the results of `CompletableFuture` instances without blocking the calling thread, making your code more efficient and responsive.

# Using CompleteableFuture for executing two methods async

Using `CompletableFuture` to execute two methods asynchronously and handle their results can be done effectively by using `supplyAsync`, `thenCombine`, and other chaining methods. Below is an example demonstrating how to run two methods asynchronously and then combine their results.

### Step-by-Step Example

1. **Define the methods to be executed asynchronously**:
   These methods will be simple and return some values. For demonstration, let's assume we have two methods: `method1` and `method2`.

2. **Use `CompletableFuture.supplyAsync` to run the methods asynchronously**:
   We use `CompletableFuture.supplyAsync` to run each method in a separate thread.

3. **Combine the results of both futures**:
   We use `thenCombine` to combine the results of both `CompletableFuture` instances once they are completed.

### Code Example

Here is a complete example demonstrating this:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureAsyncExample {

    public static void main(String[] args) {
        // Run method1 asynchronously
        CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> {
            return method1();
        });

        // Run method2 asynchronously
        CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> {
            return method2();
        });

        // Combine the results of both futures
        CompletableFuture<Integer> combinedFuture = future1.thenCombine(future2, (result1, result2) -> {
            return result1 + result2;
        });

        // Handle the result
        combinedFuture.thenAccept(result -> {
            System.out.println("Combined Result: " + result);
        });

        // Keep the main thread alive for async operations to complete
        try {
            // Waiting for all futures to complete
            combinedFuture.get();
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }

    // Sample method1
    private static Integer method1() {
        try {
            Thread.sleep(1000); // Simulate long-running task
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        return 5;
    }

    // Sample method2
    private static Integer method2() {
        try {
            Thread.sleep(1000); // Simulate long-running task
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
        return 10;
    }
}
```

### Explanation

1. **Asynchronous Execution**:
   - `CompletableFuture.supplyAsync(() -> method1())`: Executes `method1` asynchronously.
   - `CompletableFuture.supplyAsync(() -> method2())`: Executes `method2` asynchronously.

2. **Combining Results**:
   - `future1.thenCombine(future2, (result1, result2) -> result1 + result2)`: Combines the results of `future1` and `future2` using the provided lambda function. In this case, it sums the results of `method1` and `method2`.

3. **Handling the Combined Result**:
   - `combinedFuture.thenAccept(result -> System.out.println("Combined Result: " + result))`: Prints the combined result once both futures are complete.

4. **Waiting for Completion**:
   - `combinedFuture.get()`: Ensures the main thread waits for the combined future to complete before terminating. This step is crucial in a real application to keep the JVM running until all asynchronous tasks are completed. In a production application, you may want to handle this more gracefully.

### Notes

- **Exception Handling**: The example uses `try-catch` blocks to handle potential exceptions. In a real-world scenario, you should handle exceptions appropriately, possibly using `exceptionally` or `handle` methods of `CompletableFuture`.
- **Custom Executor**: You can provide a custom `Executor` to `supplyAsync` to control the thread pool, which can be beneficial for tuning performance and managing resources.

This approach allows you to run multiple methods asynchronously, combine their results, and handle them efficiently without blocking the main thread.

# CompletableFuture exceptionally breaks the work chain

Using `CompletableFuture.exceptionally` can indeed break the work chain if not used correctly because it handles exceptions by providing a fallback value and continues the chain from that point. If you want to handle exceptions and continue processing, you might want to use `handle`, `whenComplete`, or `thenCompose` combined with proper exception handling.

### Handling Exceptions Without Breaking the Chain

Here's how you can handle exceptions in a way that allows the chain to continue processing:

1. **Using `exceptionally`**: Handles exceptions and provides a fallback value.
2. **Using `handle`**: Handles both the result and exceptions and allows further processing based on the outcome.
3. **Using `whenComplete`**: Performs an action upon completion, regardless of success or failure.
4. **Using `thenCompose` with exception handling**: Allows chaining additional futures even when an exception occurs.

### Example Code

Below is an example demonstrating how to handle exceptions properly without breaking the chain using `handle` and `thenCompose`.

#### Using `handle`:

The `handle` method can be used to handle both the result and exceptions, allowing the chain to continue processing.

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureHandleExample {

    public static void main(String[] args) {
        // Create a CompletableFuture that completes exceptionally
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            if (true) { // Simulating an exception
                throw new RuntimeException("Something went wrong!");
            }
            return "Hello, World!";
        });

        // Handle the result and exceptions
        CompletableFuture<String> handledFuture = future.handle((result, ex) -> {
            if (ex != null) {
                System.err.println("Exception: " + ex.getMessage());
                return "Default Value"; // Provide a default value in case of an exception
            } else {
                return result;
            }
        });

        // Continue processing
        handledFuture.thenAccept(result -> {
            System.out.println("Result: " + result);
        });

        // Keep the main thread alive for async operations to complete
        try {
            Thread.sleep(2000); // Wait for enough time for the async tasks to complete
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

#### Using `thenCompose` with Exception Handling:

The `thenCompose` method allows chaining additional futures. You can handle exceptions and decide whether to continue processing based on the outcome.

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureThenComposeExample {

    public static void main(String[] args) {
        // Create a CompletableFuture that completes exceptionally
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            if (true) { // Simulating an exception
                throw new RuntimeException("Something went wrong!");
            }
            return "Hello, World!";
        });

        // Handle the exception and return a fallback future
        CompletableFuture<String> composedFuture = future.exceptionally(ex -> {
            System.err.println("Exception: " + ex.getMessage());
            return "Fallback Value";
        }).thenCompose(result -> {
            // Continue processing with the result or fallback value
            return CompletableFuture.supplyAsync(() -> result + " - Continued");
        });

        // Consume the final result
        composedFuture.thenAccept(result -> {
            System.out.println("Final Result: " + result);
        });

        // Keep the main thread alive for async operations to complete
        try {
            Thread.sleep(2000); // Wait for enough time for the async tasks to complete
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

### Summary

- **`exceptionally`**: Handles exceptions and provides a fallback value, but can potentially break the chain if not used carefully.
- **`handle`**: Provides a way to handle both the result and exceptions and allows the chain to continue.
- **`whenComplete`**: Executes a callback upon completion, regardless of the outcome, without altering the result.
- **`thenCompose`**: Allows chaining of additional futures with exception handling to continue processing.

Using these methods, you can handle exceptions in a `CompletableFuture` chain without breaking the workflow, ensuring that subsequent operations can still be performed based on the outcome.

# Mocking the CompletableFuture.join() for IntegrationTests

Mocking `CompletableFuture.join()` for integration tests can be useful to control the behavior of asynchronous operations. This can be done using testing frameworks like Mockito. By mocking the `CompletableFuture` itself, you can simulate different scenarios like successful completion, exceptions, or timeouts.

Here's an example of how to mock `CompletableFuture.join()` using Mockito.

### Step-by-Step Example

1. **Add Mockito to your project**: Ensure you have Mockito and a testing framework (like JUnit) in your project's dependencies.

   For Maven:

   ```xml
   <dependency>
       <groupId>org.mockito</groupId>
       <artifactId>mockito-core</artifactId>
       <version>4.0.0</version>
       <scope>test</scope>
   </dependency>
   <dependency>
       <groupId>org.junit.jupiter</groupId>
       <artifactId>junit-jupiter-api</artifactId>
       <version>5.8.1</version>
       <scope>test</scope>
   </dependency>
   <dependency>
       <groupId>org.junit.jupiter</groupId>
       <artifactId>junit-jupiter-engine</artifactId>
       <version>5.8.1</version>
       <scope>test</scope>
   </dependency>
   ```

2. **Mocking `CompletableFuture`**: Create a test class where you will mock `CompletableFuture`.

```java
import org.junit.jupiter.api.Test;
import org.mockito.Mockito;
import java.util.concurrent.CompletableFuture;
import static org.mockito.Mockito.*;

class MyServiceTest {

    @Test
    void testCompletableFutureJoin() {
        // Create a mock of CompletableFuture
        CompletableFuture<String> completableFutureMock = mock(CompletableFuture.class);

        // Define the behavior of join() method
        when(completableFutureMock.join()).thenReturn("Mocked Result");

        // Use the mocked CompletableFuture in your test
        MyService myService = new MyService(completableFutureMock);
        String result = myService.performAsyncOperation();

        // Assert the result
        assertEquals("Mocked Result", result);
    }

    @Test
    void testCompletableFutureJoinException() {
        // Create a mock of CompletableFuture
        CompletableFuture<String> completableFutureMock = mock(CompletableFuture.class);

        // Define the behavior of join() method to throw an exception
        when(completableFutureMock.join()).thenThrow(new RuntimeException("Mocked Exception"));

        // Use the mocked CompletableFuture in your test
        MyService myService = new MyService(completableFutureMock);

        // Assert that the exception is handled correctly
        assertThrows(RuntimeException.class, myService::performAsyncOperation);
    }

    // Example service class using CompletableFuture
    static class MyService {
        private final CompletableFuture<String> completableFuture;

        public MyService(CompletableFuture<String> completableFuture) {
            this.completableFuture = completableFuture;
        }

        public String performAsyncOperation() {
            return completableFuture.join();
        }
    }
}
```

### Explanation

1. **Dependencies**: Ensure that Mockito and JUnit are added to your project's dependencies.

2. **Mocking `CompletableFuture`**: 
   - `mock(CompletableFuture.class)`: Creates a mock instance of `CompletableFuture`.
   - `when(completableFutureMock.join()).thenReturn("Mocked Result")`: Defines the behavior of the `join()` method to return a mocked result.
   - `when(completableFutureMock.join()).thenThrow(new RuntimeException("Mocked Exception"))`: Defines the behavior of the `join()` method to throw a mocked exception.

3. **Using Mock in Service**: The `MyService` class uses the mocked `CompletableFuture` to simulate asynchronous operations.

4. **Testing with Mock**:
   - In the `testCompletableFutureJoin()` method, the mocked `CompletableFuture` returns a predefined result.
   - In the `testCompletableFutureJoinException()` method, the mocked `CompletableFuture` throws a predefined exception.
   - The `assertEquals` and `assertThrows` methods are used to verify the expected outcomes.

### Notes

- **Behavior Verification**: You can also verify if certain methods were called using `verify`.
- **Advanced Mocking**: For more complex scenarios, consider using argument captors or defining more sophisticated behaviors.
- **Real Asynchronous Testing**: In some cases, you might want to test real asynchronous behavior. Use tools like `CountDownLatch` or `CompletableFuture.completedFuture` for such scenarios.

By following these steps, you can effectively mock `CompletableFuture.join()` for integration tests, allowing you to control the behavior of asynchronous operations and test various scenarios without relying on real asynchronous execution.

# Replacing ListenableFuture with CompletableFuture in Kafka producer/consumer

Replacing `ListenableFuture` with `CompletableFuture` in a Kafka producer/consumer setup can help modernize your codebase, especially when leveraging the benefits of Java's `CompletableFuture` for better async handling and chaining.

Here's how you can go about making this replacement.

### Kafka Producer with CompletableFuture

Assuming you have a Kafka producer that previously used `ListenableFuture`, you can replace it with `CompletableFuture`.

#### Step-by-Step

1. **Add Kafka Producer Dependencies**: Ensure your project has the necessary Kafka dependencies.
2. **Convert Producer to Use `CompletableFuture`**: Use `CompletableFuture` to handle the result of the Kafka producer send operation.

#### Example Code

```java
import org.apache.kafka.clients.producer.KafkaProducer;
import org.apache.kafka.clients.producer.ProducerRecord;
import org.apache.kafka.clients.producer.RecordMetadata;

import java.util.Properties;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class KafkaProducerExample {

    public static void main(String[] args) {
        Properties props = new Properties();
        props.put("bootstrap.servers", "localhost:9092");
        props.put("key.serializer", "org.apache.kafka.common.serialization.StringSerializer");
        props.put("value.serializer", "org.apache.kafka.common.serialization.StringSerializer");

        KafkaProducer<String, String> producer = new KafkaProducer<>(props);

        ProducerRecord<String, String> record = new ProducerRecord<>("my-topic", "key", "value");

        CompletableFuture<RecordMetadata> future = sendMessage(producer, record);

        future.thenAccept(recordMetadata -> {
            System.out.println("Message sent successfully: " + recordMetadata);
        }).exceptionally(ex -> {
            System.err.println("Failed to send message: " + ex.getMessage());
            return null;
        });

        // Close the producer after use
        producer.close();
    }

    public static CompletableFuture<RecordMetadata> sendMessage(KafkaProducer<String, String> producer, ProducerRecord<String, String> record) {
        CompletableFuture<RecordMetadata> completableFuture = new CompletableFuture<>();
        producer.send(record, (metadata, exception) -> {
            if (exception == null) {
                completableFuture.complete(metadata);
            } else {
                completableFuture.completeExceptionally(exception);
            }
        });
        return completableFuture;
    }
}
```

### Kafka Consumer with CompletableFuture

For a Kafka consumer, you generally process records synchronously within the poll loop. To use `CompletableFuture`, you can process records asynchronously.

#### Example Code

```java
import org.apache.kafka.clients.consumer.ConsumerConfig;
import org.apache.kafka.clients.consumer.ConsumerRecords;
import org.apache.kafka.clients.consumer.KafkaConsumer;
import org.apache.kafka.clients.consumer.ConsumerRecord;

import java.time.Duration;
import java.util.Collections;
import java.util.Properties;
import java.util.concurrent.CompletableFuture;

public class KafkaConsumerExample {

    public static void main(String[] args) {
        Properties props = new Properties();
        props.put(ConsumerConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");
        props.put(ConsumerConfig.GROUP_ID_CONFIG, "test-group");
        props.put(ConsumerConfig.KEY_DESERIALIZER_CLASS_CONFIG, "org.apache.kafka.common.serialization.StringDeserializer");
        props.put(ConsumerConfig.VALUE_DESERIALIZER_CLASS_CONFIG, "org.apache.kafka.common.serialization.StringDeserializer");

        KafkaConsumer<String, String> consumer = new KafkaConsumer<>(props);
        consumer.subscribe(Collections.singletonList("my-topic"));

        try {
            while (true) {
                ConsumerRecords<String, String> records = consumer.poll(Duration.ofMillis(100));
                for (ConsumerRecord<String, String> record : records) {
                    processRecordAsync(record)
                        .thenAccept(result -> {
                            System.out.println("Processed record successfully: " + result);
                        })
                        .exceptionally(ex -> {
                            System.err.println("Failed to process record: " + ex.getMessage());
                            return null;
                        });
                }
            }
        } finally {
            consumer.close();
        }
    }

    public static CompletableFuture<String> processRecordAsync(ConsumerRecord<String, String> record) {
        return CompletableFuture.supplyAsync(() -> {
            // Simulate processing
            return "Processed record with key: " + record.key() + " and value: " + record.value();
        });
    }
}
```

### Summary

- **Kafka Producer**: Replace `ListenableFuture` with `CompletableFuture` by wrapping the `send` method.
- **Kafka Consumer**: Process records asynchronously using `CompletableFuture.supplyAsync`.

These changes help modernize your Kafka producer and consumer to use Java's `CompletableFuture`, allowing for more expressive asynchronous programming and better integration with the rest of your Java application.

# Stored Procedure call with CompletableFuture

Calling a stored procedure asynchronously with `CompletableFuture` in Java involves using a combination of JDBC for database access and `CompletableFuture` for handling the asynchronous execution. Here's how you can achieve this:

1. **Set up your JDBC connection**: Ensure you have the necessary JDBC driver and connection setup.
2. **Create a method to call the stored procedure**: Use JDBC to call the stored procedure and return a `CompletableFuture`.
3. **Handle the results asynchronously**: Use `CompletableFuture` methods to process the results.

### Example Code

#### Step 1: Set Up JDBC Connection

Ensure your project includes the necessary JDBC driver dependencies. For example, if you're using MySQL, you need the MySQL connector.

```xml
<dependency>
    <groupId>mysql</groupId>
    <artifactId>mysql-connector-java</artifactId>
    <version>8.0.26</version>
</dependency>
```

#### Step 2: Create a Method to Call the Stored Procedure

Here's a complete example demonstrating how to call a stored procedure asynchronously:

```java
import java.sql.*;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class AsyncStoredProcedureExample {

    private static final String JDBC_URL = "jdbc:mysql://localhost:3306/yourdatabase";
    private static final String JDBC_USER = "yourusername";
    private static final String JDBC_PASSWORD = "yourpassword";

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(10); // Or use a more appropriate executor for your use case

        CompletableFuture<Void> future = callStoredProcedureAsync(executor)
                .thenAccept(resultSet -> {
                    try {
                        while (resultSet.next()) {
                            System.out.println("Column1: " + resultSet.getString(1));
                            System.out.println("Column2: " + resultSet.getString(2));
                        }
                    } catch (SQLException e) {
                        e.printStackTrace();
                    }
                })
                .exceptionally(ex -> {
                    System.err.println("Failed to call stored procedure: " + ex.getMessage());
                    return null;
                });

        // Wait for the CompletableFuture to complete
        future.join();

        executor.shutdown();
    }

    public static CompletableFuture<ResultSet> callStoredProcedureAsync(ExecutorService executor) {
        return CompletableFuture.supplyAsync(() -> {
            try (Connection conn = DriverManager.getConnection(JDBC_URL, JDBC_USER, JDBC_PASSWORD);
                 CallableStatement stmt = conn.prepareCall("{call your_stored_procedure(?)}")) {

                // Set input parameters if needed
                stmt.setInt(1, 123);

                boolean hasResults = stmt.execute();
                if (hasResults) {
                    return stmt.getResultSet();
                } else {
                    throw new SQLException("No results returned from stored procedure");
                }
            } catch (SQLException e) {
                throw new RuntimeException(e);
            }
        }, executor);
    }
}
```

### Explanation

1. **JDBC Setup**:
    - Replace `JDBC_URL`, `JDBC_USER`, and `JDBC_PASSWORD` with your database details.
    - The stored procedure is called using a `CallableStatement`. Adjust the procedure name and parameters accordingly.

2. **CompletableFuture for Asynchronous Execution**:
    - `callStoredProcedureAsync` method wraps the JDBC call in a `CompletableFuture` using `supplyAsync` which runs in a separate thread managed by the provided executor.
    - The `executor` ensures that the asynchronous tasks run in a separate thread pool instead of the main thread, allowing better resource management and scalability.

3. **Handling Results**:
    - The result of the stored procedure call is processed asynchronously in the `thenAccept` block.
    - If an exception occurs during the stored procedure call, it is handled in the `exceptionally` block.

4. **Waiting for Completion**:
    - `future.join()` is used to wait for the `CompletableFuture` to complete. In a real application, you might handle this differently to avoid blocking the main thread.

5. **Executor Service**:
    - The `ExecutorService` is used to manage threads for the asynchronous tasks. It's important to shut down the executor after the tasks are completed to release resources.

### Notes

- **Error Handling**: Ensure proper error handling is in place for production code, especially for database operations.
- **Resource Management**: Always close JDBC resources (like `Connection`, `Statement`, and `ResultSet`) to avoid resource leaks. The try-with-resources statement is used in the example to manage this.
- **Database Driver**: Ensure the correct database driver is included in your project dependencies.

By following this example, you can effectively call stored procedures asynchronously using `CompletableFuture` and handle the results without blocking the main thread.

# Calling ExecutorService.shutdownNow from CompletableFuture

Calling `ExecutorService.shutdownNow()` from within a `CompletableFuture` can be useful when you want to stop all currently executing tasks and prevent new tasks from being submitted. However, it must be done carefully to avoid potential issues, such as abruptly terminating important tasks or causing inconsistencies.

Below is an example demonstrating how you can manage an `ExecutorService` within a `CompletableFuture` and call `shutdownNow()` safely.

### Example Code

```java
import java.util.List;
import java.util.concurrent.*;

public class CompletableFutureShutdownExample {

    private static final String JDBC_URL = "jdbc:mysql://localhost:3306/yourdatabase";
    private static final String JDBC_USER = "yourusername";
    private static final String JDBC_PASSWORD = "yourpassword";

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(10);

        // Simulating multiple async tasks
        CompletableFuture<Void> future1 = callStoredProcedureAsync(executor)
                .thenAccept(resultSet -> processResultSet(resultSet, "Task1"));

        CompletableFuture<Void> future2 = callStoredProcedureAsync(executor)
                .thenAccept(resultSet -> processResultSet(resultSet, "Task2"));

        CompletableFuture<Void> combinedFuture = CompletableFuture.allOf(future1, future2)
                .exceptionally(ex -> {
                    System.err.println("Exception: " + ex.getMessage());
                    return null;
                });

        combinedFuture.join();  // Wait for all tasks to complete

        // Calling shutdownNow safely after tasks completion
        shutdownExecutorService(executor);
    }

    public static CompletableFuture<ResultSet> callStoredProcedureAsync(ExecutorService executor) {
        return CompletableFuture.supplyAsync(() -> {
            try (Connection conn = DriverManager.getConnection(JDBC_URL, JDBC_USER, JDBC_PASSWORD);
                 CallableStatement stmt = conn.prepareCall("{call your_stored_procedure(?)}")) {

                stmt.setInt(1, 123);  // Set input parameter
                boolean hasResults = stmt.execute();
                if (hasResults) {
                    return stmt.getResultSet();
                } else {
                    throw new SQLException("No results returned from stored procedure");
                }
            } catch (SQLException e) {
                throw new RuntimeException(e);
            }
        }, executor);
    }

    public static void processResultSet(ResultSet resultSet, String taskName) {
        try {
            while (resultSet.next()) {
                System.out.println(taskName + " - Column1: " + resultSet.getString(1));
                System.out.println(taskName + " - Column2: " + resultSet.getString(2));
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    public static void shutdownExecutorService(ExecutorService executor) {
        List<Runnable> notExecutedTasks = executor.shutdownNow();  // Call shutdownNow
        System.out.println("ExecutorService shut down. Pending tasks: " + notExecutedTasks.size());

        try {
            if (!executor.awaitTermination(60, TimeUnit.SECONDS)) {
                System.err.println("Executor did not terminate in the specified time.");
                List<Runnable> droppedTasks = executor.shutdownNow();  // Reattempt shutdown
                System.out.println("ExecutorService reattempted shutdown. Pending tasks: " + droppedTasks.size());
            }
        } catch (InterruptedException e) {
            System.err.println("Executor shutdown interrupted.");
            List<Runnable> interruptedTasks = executor.shutdownNow();
            System.out.println("ExecutorService shutdown after interruption. Pending tasks: " + interruptedTasks.size());
            Thread.currentThread().interrupt();
        }
    }
}
```

### Explanation

1. **Creating the ExecutorService**:
   - `ExecutorService executor = Executors.newFixedThreadPool(10);`: Creates a fixed thread pool with 10 threads.

2. **Asynchronous Stored Procedure Call**:
   - `callStoredProcedureAsync(executor)`: Submits a task to the executor to call a stored procedure asynchronously.

3. **Processing Results**:
   - `processResultSet(resultSet, "Task1")`: Processes the `ResultSet` in the `thenAccept` callback of `CompletableFuture`.

4. **Combining Multiple Futures**:
   - `CompletableFuture.allOf(future1, future2)`: Combines multiple `CompletableFuture` instances to wait for all of them to complete.

5. **Shutdown ExecutorService**:
   - `shutdownExecutorService(executor)`: Shuts down the executor service safely. It tries to stop all actively executing tasks and halts the processing of waiting tasks.
   - `shutdownNow()`: Attempts to stop all actively executing tasks, halts the processing of waiting tasks, and returns a list of tasks that were awaiting execution.
   - `awaitTermination`: Waits for the previously submitted tasks to complete execution after a shutdown request.

### Notes

- **Exception Handling**: Proper exception handling is crucial. Use `exceptionally` or `handle` to manage exceptions in `CompletableFuture`.
- **Resource Management**: Ensure all JDBC resources are closed properly using try-with-resources to avoid leaks.
- **Thread Interruption**: Handle `InterruptedException` properly to manage thread interruption and ensure that the current thread's interrupted status is preserved using `Thread.currentThread().interrupt()`.
- **Timeout**: The timeout in `awaitTermination` ensures the program does not hang indefinitely.

By using this approach, you can manage `ExecutorService` lifecycles effectively within asynchronous operations, ensuring resources are cleaned up properly and tasks are handled as expected.

# JDK8 CompletableFuture.supplyAsync how to deal with interruptedException

Handling `InterruptedException` in a `CompletableFuture.supplyAsync` task can be a bit tricky, but it's crucial to do it properly to avoid issues such as thread leaks or tasks that hang indefinitely.

Here's a detailed approach on how to manage `InterruptedException` within a `CompletableFuture.supplyAsync` task:

1. **Propagate the Interrupted Status**: If a thread is interrupted, the interrupted status should be preserved so that higher-level code can detect the interruption.
2. **Handle Interruption Gracefully**: Perform any necessary cleanup and either propagate the exception or return a default value.

### Example Code

Let's see how you can handle `InterruptedException` within a `CompletableFuture.supplyAsync`:

```java
import java.sql.*;
import java.util.concurrent.*;

public class CompletableFutureInterruptedExceptionExample {

    private static final String JDBC_URL = "jdbc:mysql://localhost:3306/yourdatabase";
    private static final String JDBC_USER = "yourusername";
    private static final String JDBC_PASSWORD = "yourpassword";

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(10);

        CompletableFuture<Void> future = callStoredProcedureAsync(executor)
                .thenAccept(resultSet -> {
                    if (resultSet != null) {
                        processResultSet(resultSet, "Task");
                    }
                })
                .exceptionally(ex -> {
                    System.err.println("Failed to call stored procedure: " + ex.getMessage());
                    return null;
                });

        // Wait for the CompletableFuture to complete
        future.join();

        // Shutdown the executor service
        shutdownExecutorService(executor);
    }

    public static CompletableFuture<ResultSet> callStoredProcedureAsync(ExecutorService executor) {
        return CompletableFuture.supplyAsync(() -> {
            try (Connection conn = DriverManager.getConnection(JDBC_URL, JDBC_USER, JDBC_PASSWORD);
                 CallableStatement stmt = conn.prepareCall("{call your_stored_procedure(?)}")) {

                // Simulate long-running task
                if (Thread.currentThread().isInterrupted()) {
                    throw new InterruptedException("Task was interrupted before starting the database call.");
                }

                stmt.setInt(1, 123);  // Set input parameter
                boolean hasResults = stmt.execute();
                if (hasResults) {
                    return stmt.getResultSet();
                } else {
                    throw new SQLException("No results returned from stored procedure");
                }
            } catch (SQLException | InterruptedException e) {
                throw new RuntimeException(e);
            }
        }, executor).handle((result, throwable) -> {
            if (throwable != null) {
                if (throwable.getCause() instanceof InterruptedException) {
                    System.err.println("Task was interrupted: " + throwable.getMessage());
                    // Preserve the interrupt status
                    Thread.currentThread().interrupt();
                }
                throw new CompletionException(throwable);
            }
            return result;
        });
    }

    public static void processResultSet(ResultSet resultSet, String taskName) {
        try {
            while (resultSet.next()) {
                System.out.println(taskName + " - Column1: " + resultSet.getString(1));
                System.out.println(taskName + " - Column2: " + resultSet.getString(2));
            }
        } catch (SQLException e) {
            e.printStackTrace();
        }
    }

    public static void shutdownExecutorService(ExecutorService executor) {
        List<Runnable> notExecutedTasks = executor.shutdownNow();  // Call shutdownNow
        System.out.println("ExecutorService shut down. Pending tasks: " + notExecutedTasks.size());

        try {
            if (!executor.awaitTermination(60, TimeUnit.SECONDS)) {
                System.err.println("Executor did not terminate in the specified time.");
                List<Runnable> droppedTasks = executor.shutdownNow();  // Reattempt shutdown
                System.out.println("ExecutorService reattempted shutdown. Pending tasks: " + droppedTasks.size());
            }
        } catch (InterruptedException e) {
            System.err.println("Executor shutdown interrupted.");
            List<Runnable> interruptedTasks = executor.shutdownNow();
            System.out.println("ExecutorService shutdown after interruption. Pending tasks: " + interruptedTasks.size());
            Thread.currentThread().interrupt();
        }
    }
}
```

### Explanation

1. **CompletableFuture.supplyAsync**:
    - The `supplyAsync` method submits a task to the executor. Inside this task, we handle both `SQLException` and `InterruptedException`.
    - If the thread is interrupted before starting the database call, we throw an `InterruptedException`.
    - If the task is interrupted while waiting for a database call or any other operation, we catch the `InterruptedException`.

2. **Handle Method**:
    - The `handle` method is used to handle the result or exception of the `CompletableFuture`.
    - If an `InterruptedException` occurs, the interrupt status of the thread is preserved using `Thread.currentThread().interrupt()`.
    - We rethrow the exception wrapped in a `CompletionException` to propagate it up the chain.

3. **Process ResultSet**:
    - The `processResultSet` method processes the `ResultSet` if the stored procedure call completes successfully.

4. **Shutdown ExecutorService**:
    - The `shutdownExecutorService` method attempts to stop all actively executing tasks and halts the processing of waiting tasks using `shutdownNow`.
    - It ensures that the executor is properly shut down and handles any potential interruptions.

### Notes

- **Interrupt Handling**: Always preserve the interrupt status by calling `Thread.currentThread().interrupt()` when catching an `InterruptedException`.
- **Resource Management**: Use try-with-resources to ensure JDBC resources are closed properly.
- **Exception Propagation**: Use `CompletionException` to propagate exceptions in `CompletableFuture`.

By following this approach, you can handle `InterruptedException` properly in `CompletableFuture.supplyAsync` tasks, ensuring that your application behaves correctly under interruption scenarios.

# How to combine the result of execution of two CompletableFutures?

Combining the results of two `CompletableFuture` instances can be achieved using various methods provided by the `CompletableFuture` class. The most common methods are `thenCombine` and `thenCompose`.

- **`thenCombine`**: Combines the results of two independent `CompletableFutures` when they both complete.
- **`thenCompose`**: Chains two `CompletableFutures` where the result of the first `CompletableFuture` is used as input to the second `CompletableFuture`.

### Example with thenCombine

Here's an example that demonstrates how to use `thenCombine` to combine the results of two `CompletableFuture` instances:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CombineCompletableFutureExample {

    public static void main(String[] args) {
        CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> {
            // Simulate long-running task
            return 5;
        });

        CompletableFuture<Integer> future2 = CompletableFuture.supplyAsync(() -> {
            // Simulate another long-running task
            return 10;
        });

        CompletableFuture<Integer> combinedFuture = future1.thenCombine(future2, (result1, result2) -> {
            // Combine the results of both futures
            return result1 + result2;
        });

        try {
            Integer combinedResult = combinedFuture.get();
            System.out.println("Combined Result: " + combinedResult); // Output: Combined Result: 15
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

### Explanation

1. **Create CompletableFuture Instances**:
    - `future1` and `future2` simulate long-running tasks returning integers.
  
2. **Combine Results Using thenCombine**:
    - `thenCombine` takes two arguments: the second `CompletableFuture` and a `BiFunction` to combine the results of both futures.
  
3. **Retrieve Combined Result**:
    - The `get` method is used to block and retrieve the combined result. In real applications, you might handle this differently to avoid blocking the main thread.

### Example with thenCompose

Here's an example using `thenCompose` to chain two `CompletableFuture` instances:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class ComposeCompletableFutureExample {

    public static void main(String[] args) {
        CompletableFuture<Integer> future1 = CompletableFuture.supplyAsync(() -> {
            // Simulate long-running task
            return 5;
        });

        CompletableFuture<Integer> combinedFuture = future1.thenCompose(result1 -> {
            // Chain another CompletableFuture based on result1
            return CompletableFuture.supplyAsync(() -> {
                // Use result1 to compute the final result
                return result1 * 2;
            });
        });

        try {
            Integer combinedResult = combinedFuture.get();
            System.out.println("Combined Result: " + combinedResult); // Output: Combined Result: 10
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

### Explanation

1. **Create CompletableFuture Instance**:
    - `future1` simulates a long-running task returning an integer.

2. **Chain Future Using thenCompose**:
    - `thenCompose` takes a `Function` that returns a new `CompletableFuture` based on the result of `future1`.

3. **Retrieve Combined Result**:
    - The `get` method is used to block and retrieve the combined result.

### Notes

- **Exception Handling**: In a real-world application, consider using `exceptionally`, `handle`, or `whenComplete` to manage exceptions in `CompletableFuture`.
- **Non-Blocking**: Using `get` blocks the current thread until the result is available. In asynchronous programming, prefer non-blocking approaches like using callbacks or chaining further asynchronous operations.
- **Resource Management**: Ensure proper resource management, especially when dealing with long-running tasks or external resources.

By using these methods, you can efficiently combine the results of two or more `CompletableFuture` instances, allowing for more complex asynchronous workflows in your Java applications.

# How to add futures by for loop for CompletableFuture.allOf?

To add multiple `CompletableFuture` instances to `CompletableFuture.allOf` using a for loop, you can follow these steps:

1. Create a list to store your `CompletableFuture` instances.
2. Use a for loop to create and add each `CompletableFuture` to the list.
3. Convert the list to an array and pass it to `CompletableFuture.allOf`.
4. Process the results after all futures have completed.

Here's an example demonstrating this approach:

### Example Code

```java
import java.util.ArrayList;
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class CompletableFutureAllOfExample {

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(10);

        // List to hold CompletableFutures
        List<CompletableFuture<Integer>> futureList = new ArrayList<>();

        // Adding 5 CompletableFuture tasks using a for loop
        for (int i = 0; i < 5; i++) {
            final int index = i; // Final variable to use inside lambda
            CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
                // Simulate long-running task
                return index * 10;
            }, executor);
            futureList.add(future);
        }

        // Combine all futures using allOf
        CompletableFuture<Void> allOfFuture = CompletableFuture.allOf(futureList.toArray(new CompletableFuture[0]));

        // Process the results after all futures have completed
        CompletableFuture<List<Integer>> allResults = allOfFuture.thenApply(v -> {
            List<Integer> results = new ArrayList<>();
            for (CompletableFuture<Integer> future : futureList) {
                try {
                    results.add(future.get()); // Get the result of each CompletableFuture
                } catch (InterruptedException | ExecutionException e) {
                    e.printStackTrace();
                }
            }
            return results;
        });

        // Wait for the combined future to complete and print the results
        try {
            List<Integer> results = allResults.get();
            results.forEach(result -> System.out.println("Result: " + result));
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }

        // Shutdown the executor service
        executor.shutdown();
    }
}
```

### Explanation

1. **ExecutorService Setup**:
   - `ExecutorService executor = Executors.newFixedThreadPool(10);`: Creates a fixed thread pool with 10 threads for running the asynchronous tasks.

2. **Creating CompletableFuture Instances in a Loop**:
   - A `for` loop is used to create and add `CompletableFuture` instances to a list.
   - Each `CompletableFuture` runs a task that simulates a long-running operation and returns a computed result.

3. **Combining Futures Using allOf**:
   - `CompletableFuture.allOf` is used to create a new `CompletableFuture` that completes when all the `CompletableFuture` instances in the list have completed.
   - The list of futures is converted to an array using `futureList.toArray(new CompletableFuture[0])`.

4. **Processing Results**:
   - The `thenApply` method is used to process the results of all futures once they have completed.
   - The results are collected into a list by calling `future.get()` for each `CompletableFuture`.

5. **Handling Exceptions**:
   - Exceptions are handled inside the loop that processes the results. In a real application, consider using better exception handling mechanisms.

6. **Waiting for Completion and Printing Results**:
   - The `get` method is called on the combined future to block until all tasks are complete, and then the results are printed.

7. **Shutting Down the ExecutorService**:
   - `executor.shutdown()` is called to shut down the executor service after all tasks are completed.

### Notes

- **Non-Blocking**: Using `get` blocks the current thread. For non-blocking operations, consider using other methods like `thenAccept` or further chaining asynchronous operations.
- **Exception Handling**: Ensure proper exception handling in production code. Using `handle` or `exceptionally` on individual `CompletableFuture` instances can help manage exceptions more gracefully.
- **Thread Safety**: Ensure that the tasks and the processing of results are thread-safe, especially when dealing with shared resources.

By following this approach, you can efficiently manage and combine multiple `CompletableFuture` instances created in a loop, allowing for more complex asynchronous workflows in your Java applications.

# Why doesn't completeable future logs exception?

The `CompletableFuture` class in Java does not log exceptions by default because it is designed to handle asynchronous computations and their results, including exceptions. Instead of logging exceptions automatically, it allows you to handle them explicitly using its various methods.

### Handling Exceptions in CompletableFuture

To handle exceptions in `CompletableFuture`, you can use methods like `exceptionally`, `handle`, or `whenComplete`.

- **exceptionally**: Provides a fallback value if an exception occurs.
- **handle**: Handles the result of the computation, whether it completes normally or with an exception.
- **whenComplete**: Allows you to perform additional actions upon completion, regardless of whether it completed normally or with an exception.

### Example Code

Below are examples showing how to handle exceptions using these methods.

#### Using `exceptionally`

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureExceptionExample {

    public static void main(String[] args) {
        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
            if (Math.random() > 0.5) {
                throw new RuntimeException("Something went wrong!");
            }
            return 42;
        });

        future.exceptionally(ex -> {
            System.err.println("Exception: " + ex.getMessage());
            return -1; // Fallback value
        }).thenAccept(result -> {
            System.out.println("Result: " + result);
        });
    }
}
```

#### Using `handle`

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureHandleExample {

    public static void main(String[] args) {
        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
            if (Math.random() > 0.5) {
                throw new RuntimeException("Something went wrong!");
            }
            return 42;
        });

        future.handle((result, ex) -> {
            if (ex != null) {
                System.err.println("Exception: " + ex.getMessage());
                return -1; // Fallback value
            }
            return result;
        }).thenAccept(result -> {
            System.out.println("Result: " + result);
        });
    }
}
```

#### Using `whenComplete`

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureWhenCompleteExample {

    public static void main(String[] args) {
        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
            if (Math.random() > 0.5) {
                throw new RuntimeException("Something went wrong!");
            }
            return 42;
        });

        future.whenComplete((result, ex) -> {
            if (ex != null) {
                System.err.println("Exception: " + ex.getMessage());
            } else {
                System.out.println("Result: " + result);
            }
        });
    }
}
```

### Explanation

1. **CompletableFuture.supplyAsync**:
   - A task is submitted asynchronously which may throw a `RuntimeException`.

2. **Exception Handling Methods**:
   - **exceptionally**: This method handles exceptions and provides a fallback value. If an exception occurs, it logs the exception message and returns `-1`.
   - **handle**: This method handles both the result and exceptions. It checks if an exception occurred and logs it, otherwise, it returns the result.
   - **whenComplete**: This method logs the exception if it occurs or logs the result if the computation completes successfully.

3. **Logging Exceptions**:
   - Exceptions are logged using `System.err.println` inside the exception handling methods. You can replace this with a proper logging framework like `Log4j` or `SLF4J` in a real-world application.

### Why CompletableFuture Doesn't Log Exceptions Automatically

- **Flexibility**: By not logging exceptions automatically, `CompletableFuture` provides flexibility to the developer to handle exceptions in a way that fits the application's requirements.
- **Separation of Concerns**: `CompletableFuture` focuses on managing asynchronous computations and their results, leaving logging and exception handling to be managed separately.
- **Custom Handling**: Different applications may have different ways of handling and logging exceptions. Providing explicit methods like `exceptionally`, `handle`, and `whenComplete` allows developers to implement custom exception handling strategies.

By explicitly handling exceptions using these methods, you can ensure that exceptions are logged and managed according to your application's specific needs.

# Async method followed by a parallelly executed method in Java 8

To execute an asynchronous method followed by a method that runs tasks in parallel, you can use `CompletableFuture` in Java 8. You will create an initial asynchronous task and then use `thenCompose` to chain another asynchronous task, which runs multiple tasks in parallel.

Here's an example that demonstrates this pattern:

### Example Code

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class AsyncParallelExample {

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(10);

        // Initial asynchronous task
        CompletableFuture<Void> initialTask = CompletableFuture.runAsync(() -> {
            System.out.println("Initial async task started by thread: " + Thread.currentThread().getName());
            // Simulate some initial async work
            try {
                Thread.sleep(1000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            System.out.println("Initial async task completed by thread: " + Thread.currentThread().getName());
        }, executor);

        // Follow-up task that runs multiple tasks in parallel
        CompletableFuture<List<Integer>> combinedFuture = initialTask.thenCompose(v -> {
            List<CompletableFuture<Integer>> futures = Arrays.asList(
                CompletableFuture.supplyAsync(() -> {
                    System.out.println("Parallel task 1 started by thread: " + Thread.currentThread().getName());
                    // Simulate some work
                    try {
                        Thread.sleep(500);
                    } catch (InterruptedException e) {
                        Thread.currentThread().interrupt();
                    }
                    System.out.println("Parallel task 1 completed by thread: " + Thread.currentThread().getName());
                    return 1;
                }, executor),
                CompletableFuture.supplyAsync(() -> {
                    System.out.println("Parallel task 2 started by thread: " + Thread.currentThread().getName());
                    // Simulate some work
                    try {
                        Thread.sleep(500);
                    } catch (InterruptedException e) {
                        Thread.currentThread().interrupt();
                    }
                    System.out.println("Parallel task 2 completed by thread: " + Thread.currentThread().getName());
                    return 2;
                }, executor),
                CompletableFuture.supplyAsync(() -> {
                    System.out.println("Parallel task 3 started by thread: " + Thread.currentThread().getName());
                    // Simulate some work
                    try {
                        Thread.sleep(500);
                    } catch (InterruptedException e) {
                        Thread.currentThread().interrupt();
                    }
                    System.out.println("Parallel task 3 completed by thread: " + Thread.currentThread().getName());
                    return 3;
                }, executor)
            );

            // Combine the results of the parallel tasks
            CompletableFuture<Void> allOf = CompletableFuture.allOf(futures.toArray(new CompletableFuture[0]));
            return allOf.thenApply(v2 -> futures.stream()
                .map(CompletableFuture::join)
                .toList()
            );
        });

        // Handle the combined results
        combinedFuture.thenAccept(results -> {
            System.out.println("Combined results: " + results);
        }).exceptionally(ex -> {
            System.err.println("Exception: " + ex.getMessage());
            return null;
        });

        // Wait for the combined future to complete
        try {
            combinedFuture.get();
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }

        // Shutdown the executor service
        executor.shutdown();
    }
}
```

### Explanation

1. **ExecutorService Setup**:
   - `ExecutorService executor = Executors.newFixedThreadPool(10);`: Creates a fixed thread pool with 10 threads for running asynchronous tasks.

2. **Initial Asynchronous Task**:
   - `CompletableFuture.runAsync`: Starts an asynchronous task that simulates some initial work.

3. **Follow-up Task with Parallel Execution**:
   - `initialTask.thenCompose`: Chains another task after the initial task completes.
   - Inside the `thenCompose` method, three parallel tasks are started using `CompletableFuture.supplyAsync`. Each task simulates some work and returns a result.

4. **Combining Parallel Tasks**:
   - `CompletableFuture.allOf`: Combines all the parallel tasks into a single `CompletableFuture`.
   - `thenApply`: Processes the results of all parallel tasks once they complete. The results are collected into a list using `stream().map(CompletableFuture::join).toList()`.

5. **Handling Combined Results**:
   - `combinedFuture.thenAccept`: Processes the combined results of all tasks.
   - `exceptionally`: Handles any exceptions that occur during the execution of the tasks.

6. **Waiting for Completion and Shutdown**:
   - `combinedFuture.get()`: Blocks until the combined future completes.
   - `executor.shutdown()`: Shuts down the executor service after all tasks are completed.

### Notes

- **Exception Handling**: Properly handle exceptions using `exceptionally` or `handle` to ensure that any errors during task execution are managed gracefully.
- **Thread Safety**: Ensure that tasks and result processing are thread-safe, especially when dealing with shared resources.
- **Non-Blocking**: While `get` blocks the current thread, consider using non-blocking approaches like further chaining of asynchronous operations if blocking is not desired.

By following this pattern, you can execute an initial asynchronous task followed by multiple parallel tasks in Java 8 using `CompletableFuture`, enabling complex asynchronous workflows in your applications.

# How add assertion on Completablefuture<boolean> Junit Mockito

To add assertions on a `CompletableFuture<Boolean>` using JUnit and Mockito, you can follow these steps:

1. Use Mockito to mock dependencies.
2. Use JUnit to write test cases.
3. Use assertions to verify the result of the `CompletableFuture`.

Here's an example that demonstrates this approach:

### Example Code

```java
import org.junit.jupiter.api.Test;
import org.junit.jupiter.api.extension.ExtendWith;
import org.mockito.InjectMocks;
import org.mockito.Mock;
import org.mockito.junit.jupiter.MockitoExtension;

import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

import static org.junit.jupiter.api.Assertions.assertTrue;
import static org.mockito.Mockito.when;

@ExtendWith(MockitoExtension.class)
public class CompletableFutureTest {

    @Mock
    private SomeService someService;

    @InjectMocks
    private SomeClassUnderTest classUnderTest;

    @Test
    public void testCompletableFuture() throws ExecutionException, InterruptedException {
        // Arrange
        when(someService.someAsyncMethod()).thenReturn(CompletableFuture.completedFuture(true));

        // Act
        CompletableFuture<Boolean> futureResult = classUnderTest.methodUnderTest();

        // Assert
        assertTrue(futureResult.get());
    }
}

// Mocked service class
class SomeService {
    public CompletableFuture<Boolean> someAsyncMethod() {
        return CompletableFuture.completedFuture(false); // Default implementation
    }
}

// Class under test
class SomeClassUnderTest {
    private final SomeService someService;

    SomeClassUnderTest(SomeService someService) {
        this.someService = someService;
    }

    public CompletableFuture<Boolean> methodUnderTest() {
        return someService.someAsyncMethod();
    }
}
```

### Explanation

1. **Mockito Setup**:
   - **@ExtendWith(MockitoExtension.class)**: Integrates Mockito with JUnit 5.
   - **@Mock**: Annotates the `someService` dependency as a mock.
   - **@InjectMocks**: Creates an instance of `SomeClassUnderTest` and injects the mocked `someService` dependency into it.

2. **Arrange Phase**:
   - **when(someService.someAsyncMethod()).thenReturn(CompletableFuture.completedFuture(true))**: Configures the mock to return a completed `CompletableFuture` with `true` as its result when `someAsyncMethod` is called.

3. **Act Phase**:
   - **classUnderTest.methodUnderTest()**: Calls the method under test, which returns a `CompletableFuture<Boolean>`.

4. **Assert Phase**:
   - **assertTrue(futureResult.get())**: Asserts that the result of the `CompletableFuture` is `true`. The `get` method is used to block and wait for the result.

### Notes

- **CompletableFuture.completedFuture(value)**: Creates a completed `CompletableFuture` with the specified value.
- **Blocking for the Result**: The `get` method blocks the test until the `CompletableFuture` is complete. For non-blocking tests, consider using timeouts or other asynchronous testing mechanisms.
- **Exception Handling**: Ensure that exceptions are properly handled in your test. In the example, the `throws` clause in the test method signature handles potential `ExecutionException` and `InterruptedException`.

This example shows how to use Mockito to mock asynchronous methods and JUnit to assert the result of a `CompletableFuture<Boolean>`. By following this pattern, you can effectively test asynchronous code in your Java applications.

# CompletableFuture.join() to block list of CompletableFutures

To block and wait for a list of `CompletableFuture` instances to complete, you can use `CompletableFuture.allOf` combined with `join`. This method ensures that all the `CompletableFuture` instances in the list have completed before proceeding. You can then collect and process the results of these futures.

Here’s an example demonstrating this approach:

### Example Code

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.stream.Collectors;

public class CompletableFutureJoinExample {

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(10);

        // Create a list of CompletableFuture instances
        List<CompletableFuture<Integer>> futureList = Arrays.asList(
            CompletableFuture.supplyAsync(() -> {
                // Simulate a long-running task
                sleep(1000);
                return 1;
            }, executor),
            CompletableFuture.supplyAsync(() -> {
                // Simulate a long-running task
                sleep(2000);
                return 2;
            }, executor),
            CompletableFuture.supplyAsync(() -> {
                // Simulate a long-running task
                sleep(3000);
                return 3;
            }, executor)
        );

        // Use CompletableFuture.allOf to combine the futures
        CompletableFuture<Void> allOf = CompletableFuture.allOf(futureList.toArray(new CompletableFuture[0]));

        // Wait for all futures to complete
        allOf.join();

        // Collect results from the completed futures
        List<Integer> results = futureList.stream()
            .map(CompletableFuture::join)
            .collect(Collectors.toList());

        // Print the results
        System.out.println("Results: " + results);

        // Shutdown the executor service
        executor.shutdown();
    }

    // Helper method to simulate a delay
    private static void sleep(int milliseconds) {
        try {
            Thread.sleep(milliseconds);
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

### Explanation

1. **ExecutorService Setup**:
   - `ExecutorService executor = Executors.newFixedThreadPool(10);`: Creates a fixed thread pool with 10 threads for running asynchronous tasks.

2. **Creating CompletableFuture Instances**:
   - A list of `CompletableFuture` instances is created, each simulating a long-running task using `supplyAsync`. The tasks return integers after sleeping for a specified duration.

3. **Combining Futures Using allOf**:
   - `CompletableFuture.allOf`: Combines all the futures into a single `CompletableFuture`. This combined future completes when all the futures in the list have completed.
   - `allOf.join()`: Blocks until all the futures are complete.

4. **Collecting Results**:
   - The results from the completed futures are collected using `futureList.stream().map(CompletableFuture::join).collect(Collectors.toList())`. The `join` method is used to retrieve the result of each future.

5. **Printing Results**:
   - The results are printed to the console.

6. **Shutting Down the ExecutorService**:
   - `executor.shutdown()`: Shuts down the executor service after all tasks are completed.

### Notes

- **Exception Handling**: The example does not include exception handling. In a real-world application, consider handling exceptions using `exceptionally`, `handle`, or `whenComplete` to manage potential errors in the futures.
- **Blocking vs. Non-Blocking**: Using `join` blocks the current thread until the futures complete. For non-blocking operations, consider using asynchronous callbacks or further chaining of asynchronous operations.
- **Thread Safety**: Ensure that tasks and result processing are thread-safe, especially when dealing with shared resources.

By following this approach, you can effectively block and wait for a list of `CompletableFuture` instances to complete, allowing you to collect and process their results in a synchronous manner.

# How to use Completable Future to make External API calls?

Using `CompletableFuture` to make external API calls allows you to perform asynchronous HTTP requests and handle the results without blocking the main thread. You can achieve this using libraries like `java.net.http.HttpClient` (available since Java 11) or other third-party libraries like `Apache HttpClient` or `OkHttp`.

Here, I’ll demonstrate how to use `CompletableFuture` with `java.net.http.HttpClient` to make external API calls.

### Example Code

First, ensure you are using Java 11 or later to have access to the `java.net.http` package.

```java
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureApiCallExample {

    public static void main(String[] args) {
        HttpClient client = HttpClient.newHttpClient();

        // Create a list of URIs to make API calls
        List<String> urls = Arrays.asList(
            "https://jsonplaceholder.typicode.com/posts/1",
            "https://jsonplaceholder.typicode.com/posts/2",
            "https://jsonplaceholder.typicode.com/posts/3"
        );

        // Create a list of CompletableFutures for each API call
        List<CompletableFuture<String>> futures = urls.stream()
            .map(url -> makeApiCall(client, url))
            .collect(Collectors.toList());

        // Combine all CompletableFutures
        CompletableFuture<Void> allOf = CompletableFuture.allOf(futures.toArray(new CompletableFuture[0]));

        // Process the results once all futures are complete
        CompletableFuture<List<String>> allResults = allOf.thenApply(v -> 
            futures.stream()
                .map(CompletableFuture::join)
                .collect(Collectors.toList())
        );

        // Handle the combined results
        try {
            List<String> results = allResults.get();
            results.forEach(result -> System.out.println("Response: " + result));
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }

    private static CompletableFuture<String> makeApiCall(HttpClient client, String url) {
        HttpRequest request = HttpRequest.newBuilder()
            .uri(URI.create(url))
            .build();

        return client.sendAsync(request, HttpResponse.BodyHandlers.ofString())
            .thenApply(HttpResponse::body)
            .exceptionally(ex -> {
                ex.printStackTrace();
                return "Error: " + ex.getMessage();
            });
    }
}
```

### Explanation

1. **HttpClient Setup**:
   - `HttpClient client = HttpClient.newHttpClient();`: Creates an `HttpClient` instance.

2. **List of URLs**:
   - A list of URLs is created to make multiple API calls.

3. **Creating CompletableFutures for Each API Call**:
   - The `makeApiCall` method is called for each URL, returning a `CompletableFuture<String>`.
   - The `map` function converts each URL to a `CompletableFuture<String>`, and `collect(Collectors.toList())` collects these futures into a list.

4. **Combining CompletableFutures**:
   - `CompletableFuture.allOf`: Combines all the futures into a single `CompletableFuture`. This combined future completes when all the individual futures have completed.

5. **Processing Results**:
   - `allOf.thenApply`: Processes the results once all futures are complete. It collects the results using `stream().map(CompletableFuture::join).collect(Collectors.toList())`.
   - `allResults.get()`: Blocks until all futures are complete and retrieves the results.

6. **Exception Handling**:
   - `exceptionally`: Handles any exceptions that occur during the API call, logs the exception, and returns an error message.

7. **Printing Results**:
   - The results are printed to the console.

### Notes

- **Exception Handling**: Ensure proper exception handling using `exceptionally`, `handle`, or `whenComplete` to manage potential errors during API calls.
- **Non-Blocking**: While `get` blocks the current thread, consider using further chaining of asynchronous operations if non-blocking behavior is desired.
- **Thread Safety**: Ensure thread safety when handling shared resources or updating shared state.

By following this approach, you can make multiple asynchronous external API calls using `CompletableFuture`, allowing you to handle their results efficiently without blocking the main thread.

# What is the use of Mono.fromCompletionStage with eager execution?

In the context of reactive programming with Project Reactor, `Mono.fromCompletionStage` is used to convert a `CompletionStage` (such as `CompletableFuture`) into a `Mono`, which is a Reactor type representing a single asynchronous value or empty.

### Eager Execution with `Mono.fromCompletionStage`

When we talk about eager execution in the context of `Mono.fromCompletionStage`, it means that the `CompletionStage` (or `CompletableFuture`) is already started or completed when we create the `Mono`. This is in contrast to lazy execution, where the asynchronous computation would start only when the `Mono` is subscribed to.

### Example Use Case

Let's illustrate the use of `Mono.fromCompletionStage` with eager execution through an example:

```java
import reactor.core.publisher.Mono;

import java.util.concurrent.CompletableFuture;
import java.util.concurrent.CompletionStage;

public class MonoFromCompletionStageExample {

    public static void main(String[] args) {
        // Create a CompletableFuture that is already completed
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate some asynchronous computation
            try {
                Thread.sleep(1000); // Simulate delay
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            return "Hello, World!";
        });

        // Convert the CompletableFuture to a Mono
        Mono<String> mono = Mono.fromCompletionStage(future);

        // Subscribe to the Mono and print the result
        mono.subscribe(result -> System.out.println("Result: " + result));
    }
}
```

### Explanation

1. **Creating a CompletableFuture**:
   - `CompletableFuture.supplyAsync(() -> { ... })`: Starts an asynchronous computation immediately. This means the computation is already running by the time the `CompletableFuture` is created.

2. **Converting to a Mono**:
   - `Mono.fromCompletionStage(future)`: Converts the `CompletableFuture` to a `Mono`. Since the `CompletableFuture` is eagerly executed (already running or completed), the `Mono` will emit the result once the `CompletableFuture` completes.

3. **Subscribing to the Mono**:
   - `mono.subscribe(result -> System.out.println("Result: " + result));`: Subscribes to the `Mono` to receive the result. The `Mono` will emit the result as soon as the `CompletableFuture` completes.

### Advantages

- **Seamless Integration**: Integrates seamlessly between reactive programming (`Mono`) and traditional futures (`CompletableFuture`).
- **Eager Execution**: Useful when the `CompletableFuture` is already running or completed, avoiding the need to trigger the computation lazily.
- **Async to Reactive Conversion**: Converts non-reactive asynchronous operations to reactive ones, enabling composition with other reactive streams.

### Use Case Scenarios

1. **Bridging Legacy Code**: When you have existing code that returns `CompletableFuture` and you want to integrate it into a reactive stream pipeline.
2. **Asynchronous Service Calls**: Making async calls (like HTTP requests) using `CompletableFuture` and converting the result to `Mono` for further reactive processing.
3. **Database Queries**: Executing database queries asynchronously using `CompletableFuture` and then processing the results in a reactive manner.

### Summary

`Mono.fromCompletionStage` is a powerful utility for converting a `CompletionStage` (like `CompletableFuture`) to a `Mono` in Project Reactor. With eager execution, it allows you to bridge between traditional asynchronous programming and reactive programming, making it easier to compose and process asynchronous results in a reactive pipeline.

# Is it possible to use Java 8 Streams API for asynchronous processing?

Java 8 Streams API is primarily designed for synchronous and parallel processing of data streams. However, it does not natively support asynchronous processing. That being said, you can still achieve asynchronous processing by combining Java 8 Streams with `CompletableFuture` and other concurrency utilities.

Here is how you can use Java 8 Streams API for asynchronous processing by leveraging `CompletableFuture`:

### Example Code

```java
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class AsyncStreamProcessingExample {

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        // Executor service for async tasks
        ExecutorService executor = Executors.newFixedThreadPool(10);

        // List of tasks to process asynchronously
        List<Integer> taskList = List.of(1, 2, 3, 4, 5);

        // Process tasks asynchronously using CompletableFuture and Streams API
        List<CompletableFuture<Integer>> futureList = taskList.stream()
            .map(task -> CompletableFuture.supplyAsync(() -> processTask(task), executor))
            .collect(Collectors.toList());

        // Combine all CompletableFuture instances
        CompletableFuture<Void> allOf = CompletableFuture.allOf(futureList.toArray(new CompletableFuture[0]));

        // Wait for all tasks to complete and collect results
        CompletableFuture<List<Integer>> allResults = allOf.thenApply(v -> 
            futureList.stream()
                .map(CompletableFuture::join)
                .collect(Collectors.toList())
        );

        // Get and print the results
        List<Integer> results = allResults.get();
        results.forEach(result -> System.out.println("Result: " + result));

        // Shutdown the executor service
        executor.shutdown();
    }

    private static Integer processTask(Integer task) {
        // Simulate processing task
        System.out.println("Processing task: " + task + " by thread: " + Thread.currentThread().getName());
        try {
            Thread.sleep(1000); // Simulate delay
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        return task * 2; // Example result
    }
}
```

### Explanation

1. **ExecutorService Setup**:
   - `ExecutorService executor = Executors.newFixedThreadPool(10);`: Creates a fixed thread pool with 10 threads for running asynchronous tasks.

2. **List of Tasks**:
   - `List<Integer> taskList = List.of(1, 2, 3, 4, 5);`: A list of tasks to process asynchronously.

3. **Processing Tasks Asynchronously**:
   - `taskList.stream().map(task -> CompletableFuture.supplyAsync(() -> processTask(task), executor))`: Maps each task to a `CompletableFuture` that processes the task asynchronously using the executor service.
   - `collect(Collectors.toList())`: Collects the `CompletableFuture` instances into a list.

4. **Combining CompletableFutures**:
   - `CompletableFuture.allOf(futureList.toArray(new CompletableFuture[0]))`: Combines all the `CompletableFuture` instances into a single `CompletableFuture<Void>`.

5. **Collecting Results**:
   - `allOf.thenApply(v -> futureList.stream().map(CompletableFuture::join).collect(Collectors.toList()))`: Once all the futures are complete, collects the results into a list.
   - `allResults.get()`: Blocks until all tasks are complete and retrieves the results.

6. **Processing Task**:
   - `processTask(Integer task)`: Simulates processing a task with a delay and returns the result.

7. **Shutdown ExecutorService**:
   - `executor.shutdown()`: Shuts down the executor service after all tasks are completed.

### Notes

- **Blocking vs. Non-Blocking**: `allResults.get()` blocks the main thread until all tasks are complete. For non-blocking operations, consider using further chaining of asynchronous operations.
- **Exception Handling**: Proper exception handling should be implemented using methods like `exceptionally`, `handle`, or `whenComplete` on `CompletableFuture`.
- **Thread Safety**: Ensure that the processing logic in `processTask` is thread-safe, especially when dealing with shared resources.

By combining Java 8 Streams with `CompletableFuture`, you can achieve asynchronous processing while still using the functional programming style of the Streams API. This approach allows you to process tasks concurrently and handle their results in a streamlined manner.

# Controller waiting even after using async and completable future

If your controller in a Spring Boot application is still waiting even after using `@Async` and `CompletableFuture`, there might be a few common issues or misunderstandings causing this behavior. Here are a few things to check:

### Ensure `@Async` is Properly Configured

1. **Enable Async Support**:
   Ensure that you have enabled asynchronous support in your Spring Boot application. You can do this by adding `@EnableAsync` to one of your configuration classes:

   ```java
   import org.springframework.context.annotation.Configuration;
   import org.springframework.scheduling.annotation.EnableAsync;

   @Configuration
   @EnableAsync
   public class AsyncConfig {
   }
   ```

2. **Use `@Async` on Service Method**:
   The `@Async` annotation should be placed on a method in a service class, not directly on the controller method. Here’s an example:

   ```java
   import org.springframework.scheduling.annotation.Async;
   import org.springframework.stereotype.Service;

   import java.util.concurrent.CompletableFuture;

   @Service
   public class AsyncService {

       @Async
       public CompletableFuture<String> performAsyncTask() {
           return CompletableFuture.supplyAsync(() -> {
               // Simulate a long-running task
               try {
                   Thread.sleep(2000);
               } catch (InterruptedException e) {
                   Thread.currentThread().interrupt();
               }
               return "Task Completed";
           });
       }
   }
   ```

3. **Controller Method**:
   The controller method should call the asynchronous service method and return the `CompletableFuture`:

   ```java
   import org.springframework.beans.factory.annotation.Autowired;
   import org.springframework.web.bind.annotation.GetMapping;
   import org.springframework.web.bind.annotation.RestController;

   import java.util.concurrent.CompletableFuture;

   @RestController
   public class AsyncController {

       @Autowired
       private AsyncService asyncService;

       @GetMapping("/async")
       public CompletableFuture<String> getAsync() {
           return asyncService.performAsyncTask();
       }
   }
   ```

### Ensure Web Configuration for Async Support

Ensure that the Spring MVC is configured to support asynchronous request processing. This is typically done automatically, but it’s good to verify your configuration.

```java
import org.springframework.context.annotation.Configuration;
import org.springframework.web.servlet.config.annotation.EnableWebMvc;
import org.springframework.web.servlet.config.annotation.WebMvcConfigurer;

@Configuration
@EnableWebMvc
public class WebConfig implements WebMvcConfigurer {
}
```

### Using CompletableFuture Correctly

Ensure that your use of `CompletableFuture` is correct. Here’s a simple example of using `CompletableFuture` for async processing in a service:

```java
import org.springframework.scheduling.annotation.Async;
import org.springframework.stereotype.Service;

import java.util.concurrent.CompletableFuture;

@Service
public class AsyncService {

    @Async
    public CompletableFuture<String> performAsyncTask() {
        return CompletableFuture.supplyAsync(() -> {
            // Simulate a long-running task
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            return "Task Completed";
        });
    }
}
```

### Check for Blocking Calls

Ensure that there are no blocking calls that could cause the controller to wait. For example, avoid using `.get()` on the `CompletableFuture` in the controller:

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.concurrent.CompletableFuture;

@RestController
public class AsyncController {

    @Autowired
    private AsyncService asyncService;

    @GetMapping("/async")
    public CompletableFuture<String> getAsync() {
        return asyncService.performAsyncTask();
    }
}
```

### Example Project Structure

Here is a complete example to demonstrate how to correctly set up asynchronous processing in a Spring Boot application:

**1. Configuration Class:**

```java
import org.springframework.context.annotation.Configuration;
import org.springframework.scheduling.annotation.EnableAsync;

@Configuration
@EnableAsync
public class AsyncConfig {
}
```

**2. Service Class:**

```java
import org.springframework.scheduling.annotation.Async;
import org.springframework.stereotype.Service;

import java.util.concurrent.CompletableFuture;

@Service
public class AsyncService {

    @Async
    public CompletableFuture<String> performAsyncTask() {
        return CompletableFuture.supplyAsync(() -> {
            // Simulate a long-running task
            try {
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
            return "Task Completed";
        });
    }
}
```

**3. Controller Class:**

```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.concurrent.CompletableFuture;

@RestController
public class AsyncController {

    @Autowired
    private AsyncService asyncService;

    @GetMapping("/async")
    public CompletableFuture<String> getAsync() {
        return asyncService.performAsyncTask();
    }
}
```

**4. Main Application Class:**

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class AsyncApplication {

    public static void main(String[] args) {
        SpringApplication.run(AsyncApplication.class, args);
    }
}
```

### Summary

By ensuring that your `@Async` configuration is correct and that your controller method returns a `CompletableFuture` directly, you can achieve asynchronous processing in your Spring Boot application. This approach helps to avoid blocking the controller while waiting for the async task to complete.

# What is different between join/get and allOf in completable future?

`CompletableFuture` in Java provides several methods to handle asynchronous computations, including `join()`, `get()`, and `allOf()`. Understanding the differences between these methods can help you choose the appropriate one for your needs.

### `CompletableFuture.join()`

- **Purpose**: To retrieve the result of a `CompletableFuture` once it completes.
- **Blocking**: Yes, it blocks the calling thread until the computation is complete.
- **Exception Handling**: Throws a `CompletionException` if the computation completed exceptionally. The underlying exception can be retrieved using `getCause()`.
- **Usage**: Typically used when you want to block and wait for the result of a single `CompletableFuture`.

Example:
```java
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> "Hello, World!");
String result = future.join(); // Blocks until the future completes
System.out.println(result);
```

### `CompletableFuture.get()`

- **Purpose**: To retrieve the result of a `CompletableFuture` once it completes.
- **Blocking**: Yes, it blocks the calling thread until the computation is complete.
- **Exception Handling**: Throws `ExecutionException` if the computation completed exceptionally and `InterruptedException` if the current thread was interrupted while waiting.
- **Usage**: Typically used when you want to block and wait for the result of a single `CompletableFuture`, similar to `join()`, but with more traditional checked exceptions.

Example:
```java
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> "Hello, World!");
try {
    String result = future.get(); // Blocks until the future completes
    System.out.println(result);
} catch (InterruptedException | ExecutionException e) {
    e.printStackTrace();
}
```

### `CompletableFuture.allOf()`

- **Purpose**: To combine multiple `CompletableFuture` instances into a single `CompletableFuture<Void>` that completes when all the provided futures complete.
- **Blocking**: `allOf()` itself is non-blocking, but you can block on the resulting `CompletableFuture<Void>` to wait for all futures to complete.
- **Exception Handling**: If any of the provided futures complete exceptionally, the resulting `CompletableFuture<Void>` from `allOf()` will also complete exceptionally.
- **Usage**: Used when you have multiple `CompletableFuture` instances and you want to wait for all of them to complete.

Example:
```java
CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> "Task 1");
CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> "Task 2");
CompletableFuture<String> future3 = CompletableFuture.supplyAsync(() -> "Task 3");

CompletableFuture<Void> allOf = CompletableFuture.allOf(future1, future2, future3);
allOf.join(); // Blocks until all futures complete

// Collect results
List<String> results = Stream.of(future1, future2, future3)
    .map(CompletableFuture::join)
    .collect(Collectors.toList());

System.out.println(results);
```

### Key Differences

1. **Scope**:
   - `join()` and `get()` are used for individual `CompletableFuture` instances.
   - `allOf()` is used to combine multiple `CompletableFuture` instances into one.

2. **Exception Handling**:
   - `join()` throws an unchecked `CompletionException` if the computation completed exceptionally.
   - `get()` throws checked `ExecutionException` and `InterruptedException`.

3. **Blocking Behavior**:
   - Both `join()` and `get()` block the calling thread until the `CompletableFuture` completes.
   - `allOf()` itself is non-blocking, but you can block on the resulting `CompletableFuture<Void>` to wait for all futures to complete.

4. **Use Cases**:
   - Use `join()` or `get()` when you need the result of a single `CompletableFuture`.
   - Use `allOf()` when you need to wait for multiple `CompletableFuture` instances to complete.

### Summary

- **`join()`**: Simple blocking call, throws `CompletionException` on failure.
- **`get()`**: Similar to `join()` but throws checked exceptions (`ExecutionException` and `InterruptedException`).
- **`allOf()`**: Combines multiple futures into one, useful for waiting for multiple tasks to complete, with its own blocking and exception handling mechanisms.

Choosing the right method depends on your specific requirements for exception handling, blocking behavior, and whether you're dealing with single or multiple asynchronous tasks.

# CompletableFuture allOF, missing results the result list

When using `CompletableFuture.allOf` to wait for multiple futures to complete, the resulting `CompletableFuture<Void>` itself does not carry the results of the individual futures. You need to collect the results from the individual futures separately. This is a common issue when working with `CompletableFuture.allOf`.

### Example Solution

Here’s a complete example demonstrating how to properly collect results from multiple `CompletableFuture` instances when using `CompletableFuture.allOf`:

```java
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CompletableFutureAllOfExample {

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        // Create a list of CompletableFuture instances
        List<CompletableFuture<String>> futures = List.of(
            CompletableFuture.supplyAsync(() -> "Task 1"),
            CompletableFuture.supplyAsync(() -> "Task 2"),
            CompletableFuture.supplyAsync(() -> "Task 3")
        );

        // Combine all futures into a single CompletableFuture<Void>
        CompletableFuture<Void> allOf = CompletableFuture.allOf(futures.toArray(new CompletableFuture[0]));

        // Use thenApply to transform the combined CompletableFuture<Void> into CompletableFuture<List<String>>
        CompletableFuture<List<String>> allResults = allOf.thenApply(v -> 
            futures.stream()
                .map(CompletableFuture::join)  // Join each CompletableFuture to get the result
                .collect(Collectors.toList())  // Collect results into a list
        );

        // Get the results
        List<String> results = allResults.get();
        results.forEach(result -> System.out.println("Result: " + result));
    }
}
```

### Explanation

1. **Create a List of `CompletableFuture` Instances**:
   - Create a list of `CompletableFuture` instances representing your asynchronous tasks.

2. **Combine All Futures Using `CompletableFuture.allOf`**:
   - `CompletableFuture<Void> allOf = CompletableFuture.allOf(futures.toArray(new CompletableFuture[0]));`
   - `allOf` will complete when all the individual futures complete, but it does not carry the results of the individual futures.

3. **Transform Combined Future to Collect Results**:
   - Use `thenApply` to transform the `CompletableFuture<Void>` into a `CompletableFuture<List<String>>`.
   - `futures.stream().map(CompletableFuture::join).collect(Collectors.toList())` is used to join each future and collect the results into a list.

4. **Get the Results**:
   - `List<String> results = allResults.get();` blocks until all tasks are complete and retrieves the list of results.
   - Print or process the results as needed.

### Important Points

- **`CompletableFuture.allOf`**: Combines multiple futures into one `CompletableFuture<Void>`, which completes when all provided futures complete. It does not contain the results of the individual futures.
- **`thenApply` Transformation**: Used to transform the combined `CompletableFuture<Void>` into a `CompletableFuture<List<T>>` that contains the results of the individual futures.
- **Exception Handling**: Ensure proper exception handling when using `join()` inside the `thenApply` transformation. Using `join()` will throw a `CompletionException` if any future completes exceptionally. You might want to handle exceptions using `exceptionally`, `handle`, or `whenComplete`.

### Handling Exceptions

To handle exceptions properly, you can modify the example to catch exceptions from each future:

```java
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CompletableFutureAllOfExample {

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        // Create a list of CompletableFuture instances
        List<CompletableFuture<String>> futures = List.of(
            CompletableFuture.supplyAsync(() -> "Task 1"),
            CompletableFuture.supplyAsync(() -> "Task 2"),
            CompletableFuture.supplyAsync(() -> {
                throw new RuntimeException("Task 3 failed");
            })
        );

        // Combine all futures into a single CompletableFuture<Void>
        CompletableFuture<Void> allOf = CompletableFuture.allOf(futures.toArray(new CompletableFuture[0]));

        // Use thenApply to transform the combined CompletableFuture<Void> into CompletableFuture<List<String>>
        CompletableFuture<List<String>> allResults = allOf.thenApply(v -> 
            futures.stream()
                .map(future -> future.exceptionally(ex -> "Error: " + ex.getMessage()).join())
                .collect(Collectors.toList())
        );

        // Get the results
        List<String> results = allResults.get();
        results.forEach(result -> System.out.println("Result: " + result));
    }
}
```

This example shows how to handle exceptions within each `CompletableFuture` and ensure the process continues even if one of the tasks fails.

# Java Completable future code optimization

Optimizing `CompletableFuture` code involves writing efficient, readable, and maintainable asynchronous operations. Here are several strategies for optimizing your `CompletableFuture` usage in Java:

### Best Practices and Optimization Strategies

1. **Avoid Blocking Operations**
   - Avoid using `join()` or `get()` to prevent blocking the calling thread. Instead, chain asynchronous callbacks.

2. **Use `thenCompose` for Dependent Futures**
   - `thenCompose` is useful for chaining dependent asynchronous tasks to avoid nested futures.

3. **Use `thenCombine` for Independent Futures**
   - Use `thenCombine` to combine results from two independent futures.

4. **Handle Exceptions Gracefully**
   - Use `exceptionally`, `handle`, or `whenComplete` to handle exceptions without blocking.

5. **Use `allOf` for Multiple Futures**
   - Use `CompletableFuture.allOf` to wait for multiple futures to complete and then combine their results.

6. **Use Custom Executors**
   - For better control and performance, provide a custom executor instead of relying on the default ForkJoinPool.

7. **Avoid Nesting CompletableFutures**
   - Keep your code flat and readable by using `thenCompose` and `thenCombine`.

### Optimized Example

Here’s an example that incorporates these best practices:

```java
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.stream.Collectors;

public class CompletableFutureOptimization {

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        ExecutorService executor = Executors.newFixedThreadPool(10);

        // Example tasks
        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
            // Simulate long-running task
            sleep(1000);
            return "Task 1 completed";
        }, executor);

        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> {
            // Simulate long-running task
            sleep(2000);
            return "Task 2 completed";
        }, executor);

        CompletableFuture<String> future3 = CompletableFuture.supplyAsync(() -> {
            // Simulate long-running task
            sleep(3000);
            return "Task 3 completed";
        }, executor);

        // Combine results of multiple futures
        CompletableFuture<Void> allOf = CompletableFuture.allOf(future1, future2, future3);

        // Collect results into a list
        CompletableFuture<List<String>> allResults = allOf.thenApply(v -> 
            List.of(future1, future2, future3).stream()
                .map(CompletableFuture::join)
                .collect(Collectors.toList())
        );

        // Handle results and exceptions
        allResults.thenAccept(results -> results.forEach(System.out::println))
                  .exceptionally(ex -> {
                      System.err.println("Exception occurred: " + ex.getMessage());
                      return null;
                  });

        // Ensure main thread waits for completion
        allResults.join();

        // Shutdown executor
        executor.shutdown();
    }

    // Helper method to simulate a long-running task
    private static void sleep(long millis) {
        try {
            Thread.sleep(millis);
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

### Key Points:

1. **Executor Service**: 
   - Use `Executors.newFixedThreadPool(10)` to create a custom executor service to manage threads.
   
2. **Asynchronous Tasks**:
   - Create `CompletableFuture` instances using `supplyAsync` with a custom executor.

3. **Combining Results**:
   - Use `CompletableFuture.allOf` to wait for all futures to complete.
   - Use `thenApply` to collect results from the individual futures.

4. **Exception Handling**:
   - Handle exceptions using `exceptionally` to provide a fallback mechanism in case of errors.

5. **Shutdown Executor**:
   - Ensure to shut down the executor service to release resources.

### Additional Tips:

- **Avoid Blocking Main Thread**: If you need to block the main thread (e.g., in a console application), use `join()` on the combined future. For web applications, avoid blocking the main thread.
- **Optimize Thread Pool Size**: Adjust the size of the thread pool according to your application's needs to balance between concurrency and resource utilization.
- **Logging and Monitoring**: Incorporate proper logging and monitoring to track the progress and performance of your asynchronous tasks.

By following these best practices and strategies, you can optimize your `CompletableFuture` code to be efficient, scalable, and maintainable.

**OR**

# Java Completable future code optimization

Optimizing code that uses `CompletableFuture` in Java involves ensuring efficient, clean, and maintainable async operations. Here are some best practices and strategies for optimizing `CompletableFuture` usage:

### 1. Avoid Blocking Operations
Avoid blocking operations (like `join()` or `get()`) whenever possible, as they defeat the purpose of asynchronous programming.

### 2. Use `thenCompose` for Dependent Futures
When you have dependent tasks, use `thenCompose` to avoid nested futures and keep the code clean.

Example:
```java
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> "Hello")
    .thenCompose(result -> CompletableFuture.supplyAsync(() -> result + " World"))
    .thenApply(String::toUpperCase);

future.thenAccept(System.out::println);
```

### 3. Use `thenCombine` for Independent Futures
When you have independent futures and want to combine their results, use `thenCombine`.

Example:
```java
CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> "Hello");
CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> "World");

CompletableFuture<String> combinedFuture = future1.thenCombine(future2, (result1, result2) -> result1 + " " + result2);

combinedFuture.thenAccept(System.out::println);
```

### 4. Handle Exceptions Gracefully
Use methods like `exceptionally`, `handle`, or `whenComplete` to handle exceptions without blocking.

Example:
```java
CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
    if (new Random().nextBoolean()) {
        throw new RuntimeException("Something went wrong!");
    }
    return "Success!";
}).exceptionally(ex -> "Recovered from: " + ex.getMessage());

future.thenAccept(System.out::println);
```

### 5. Combine Multiple Futures with `allOf`
When you need to wait for multiple futures, use `CompletableFuture.allOf`, but remember to collect their results properly.

Example:
```java
List<CompletableFuture<String>> futures = List.of(
    CompletableFuture.supplyAsync(() -> "Task 1"),
    CompletableFuture.supplyAsync(() -> "Task 2"),
    CompletableFuture.supplyAsync(() -> "Task 3")
);

CompletableFuture<Void> allOf = CompletableFuture.allOf(futures.toArray(new CompletableFuture[0]));

CompletableFuture<List<String>> allResults = allOf.thenApply(v ->
    futures.stream()
        .map(CompletableFuture::join)
        .collect(Collectors.toList())
);

allResults.thenAccept(results -> results.forEach(System.out::println));
```

### 6. Use Custom Executors for Better Performance
By default, `CompletableFuture` uses the common ForkJoinPool, but for better control and performance, you can provide a custom executor.

Example:
```java
ExecutorService executor = Executors.newFixedThreadPool(10);

CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> "Hello", executor)
    .thenApplyAsync(result -> result + " World", executor);

future.thenAcceptAsync(System.out::println, executor);

// Don't forget to shut down the executor
executor.shutdown();
```

### 7. Combine Asynchronous Calls Efficiently
For more complex scenarios, combine async calls using a combination of `thenCompose`, `thenCombine`, `allOf`, and `anyOf`.

### Summary
Here's a comprehensive example that incorporates some of these best practices:

```java
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.stream.Collectors;

public class CompletableFutureOptimization {

    public static void main(String[] args) throws ExecutionException, InterruptedException {
        ExecutorService executor = Executors.newFixedThreadPool(10);

        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> "Task 1", executor);
        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> "Task 2", executor);
        CompletableFuture<String> future3 = CompletableFuture.supplyAsync(() -> "Task 3", executor);

        CompletableFuture<Void> allOf = CompletableFuture.allOf(future1, future2, future3);

        CompletableFuture<List<String>> allResults = allOf.thenApply(v -> 
            List.of(future1, future2, future3).stream()
                .map(CompletableFuture::join)
                .collect(Collectors.toList())
        );

        allResults.thenAccept(results -> results.forEach(System.out::println));

        allResults.join();  // Ensure main thread waits for completion

        executor.shutdown();
    }
}
```

### Key Points
- **Avoid blocking operations** (`get()`, `join()`) whenever possible.
- **Use `thenCompose` for dependent futures** to avoid nesting.
- **Use `thenCombine` for combining independent futures**.
- **Handle exceptions gracefully** using `exceptionally`, `handle`, or `whenComplete`.
- **Collect results properly** when using `CompletableFuture.allOf`.
- **Consider custom executors** for better performance and control.

# Add a description to CompletableFuture orTimeout

`CompletableFuture.orTimeout` is a method introduced in Java 9 that allows you to specify a timeout for the completion of a `CompletableFuture`. If the `CompletableFuture` does not complete within the specified timeout, it will be completed exceptionally with a `TimeoutException`.

### Key Points of `CompletableFuture.orTimeout`

- **Purpose**: To ensure a `CompletableFuture` completes within a specified time limit, otherwise, it completes exceptionally with a `TimeoutException`.
- **Non-Blocking**: The method is non-blocking and does not block the calling thread.
- **Chaining**: It can be chained with other `CompletableFuture` methods to form a complete pipeline of asynchronous tasks with timeout handling.
- **Exception Handling**: When the timeout is reached, a `TimeoutException` is thrown, which can be handled using `exceptionally`, `handle`, or `whenComplete`.

### Syntax
```java
public CompletableFuture<T> orTimeout(long timeout, TimeUnit unit)
```

- `timeout`: The time duration after which the `CompletableFuture` should be completed exceptionally.
- `unit`: The time unit of the timeout (e.g., `TimeUnit.SECONDS`).

### Example Usage

Here’s an example that demonstrates how to use `CompletableFuture.orTimeout` to set a timeout for an asynchronous task:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.TimeoutException;

public class CompletableFutureOrTimeoutExample {

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate a long-running task
            try {
                Thread.sleep(3000); // 3 seconds
            } catch (InterruptedException e) {
                throw new IllegalStateException(e);
            }
            return "Task completed";
        });

        // Set a timeout of 2 seconds
        future = future.orTimeout(2, TimeUnit.SECONDS);

        // Handle the result or exception
        future.whenComplete((result, ex) -> {
            if (ex != null) {
                if (ex instanceof TimeoutException) {
                    System.out.println("The task timed out.");
                } else {
                    System.out.println("An error occurred: " + ex.getMessage());
                }
            } else {
                System.out.println("Result: " + result);
            }
        });

        // Prevent main thread from exiting immediately
        try {
            future.join();
        } catch (Exception e) {
            // Handle or log the exception if necessary
        }
    }
}
```

### Explanation:

1. **Asynchronous Task**: A `CompletableFuture` is created using `supplyAsync` which simulates a long-running task with a 3-second sleep.
2. **Setting Timeout**: The `orTimeout` method is used to set a timeout of 2 seconds for the `CompletableFuture`. If the task takes longer than 2 seconds, it will be completed exceptionally with a `TimeoutException`.
3. **Handling Result or Exception**: The `whenComplete` method is used to handle the result or exception. If a `TimeoutException` occurs, a specific message is printed. Other exceptions are also handled accordingly.
4. **Blocking Main Thread**: The `join` method is used to prevent the main thread from exiting immediately, allowing the asynchronous task to complete.

### Benefits:

- **Timeout Control**: Provides control over the maximum time allowed for an asynchronous operation, helping to avoid indefinitely hanging tasks.
- **Non-Blocking**: The main thread is not blocked while waiting for the completion of the future.
- **Exception Handling**: Allows handling of timeout exceptions separately from other types of exceptions, providing more granular control over error handling.

Using `CompletableFuture.orTimeout` is a practical way to add timeout constraints to your asynchronous operations, making your code more robust and responsive.

# How to log completeOnTimeout of completable-future?

To log the behavior of `CompletableFuture.completeOnTimeout`, you can use Java's built-in logging framework or any other logging library like SLF4J. `completeOnTimeout` is a method that completes the `CompletableFuture` with a given value if it does not complete within the specified timeout. 

### Key Points of `CompletableFuture.completeOnTimeout`

- **Purpose**: To complete a `CompletableFuture` with a specified value if it does not complete within the given timeout.
- **Non-Blocking**: The method is non-blocking and does not block the calling thread.
- **Chaining**: It can be chained with other `CompletableFuture` methods to form a complete pipeline of asynchronous tasks with timeout handling.

### Example Usage

Here’s an example that demonstrates how to use `CompletableFuture.completeOnTimeout` and log its behavior using Java's `java.util.logging` framework:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.TimeUnit;
import java.util.logging.Level;
import java.util.logging.Logger;

public class CompletableFutureCompleteOnTimeoutExample {

    private static final Logger logger = Logger.getLogger(CompletableFutureCompleteOnTimeoutExample.class.getName());

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate a long-running task
            try {
                Thread.sleep(3000); // 3 seconds
            } catch (InterruptedException e) {
                throw new IllegalStateException(e);
            }
            return "Task completed";
        });

        // Set a timeout of 2 seconds with a fallback value
        future = future.completeOnTimeout("Timeout occurred, default value", 2, TimeUnit.SECONDS);

        // Log the result or the fact that the timeout fallback was used
        future.whenComplete((result, ex) -> {
            if (ex != null) {
                logger.log(Level.SEVERE, "An error occurred: ", ex);
            } else if ("Timeout occurred, default value".equals(result)) {
                logger.log(Level.WARNING, "The task timed out and completed with the default value.");
            } else {
                logger.log(Level.INFO, "Result: {0}", result);
            }
        });

        // Prevent main thread from exiting immediately
        try {
            future.join();
        } catch (Exception e) {
            logger.log(Level.SEVERE, "An error occurred while joining the future: ", e);
        }
    }
}
```

### Explanation:

1. **Asynchronous Task**: A `CompletableFuture` is created using `supplyAsync` which simulates a long-running task with a 3-second sleep.
2. **Setting Timeout**: The `completeOnTimeout` method is used to set a timeout of 2 seconds for the `CompletableFuture`. If the task takes longer than 2 seconds, it will be completed with the specified value "Timeout occurred, default value".
3. **Logging**: The `whenComplete` method is used to handle the result or exception. If the result is the timeout fallback value, a warning message is logged. Other results and exceptions are also logged accordingly.
4. **Blocking Main Thread**: The `join` method is used to prevent the main thread from exiting immediately, allowing the asynchronous task to complete.

### Benefits:

- **Timeout Control**: Provides control over the maximum time allowed for an asynchronous operation, helping to avoid indefinitely hanging tasks.
- **Non-Blocking**: The main thread is not blocked while waiting for the completion of the future.
- **Logging**: Allows logging of both normal completion and timeout fallback, providing better insight into the behavior of the asynchronous operations.

By using `CompletableFuture.completeOnTimeout` along with proper logging, you can ensure that your asynchronous operations are robust and provide valuable debugging information in case of timeouts.

# correct way of using CompletableFuture on void method

Using `CompletableFuture` with methods that return `void` can be a bit tricky because `CompletableFuture` is designed to work with return values. However, it is entirely possible and commonly done using the `runAsync` method for tasks that do not produce a result.

### Key Points:

- **runAsync**: Use `runAsync` to run a `Runnable` asynchronously when the task does not return a result.
- **handle Exceptions**: Handle exceptions gracefully using `exceptionally`, `handle`, or `whenComplete`.

### Example Usage:

Here’s an example of using `CompletableFuture` with a method that returns `void` and includes logging:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;
import java.util.logging.Level;
import java.util.logging.Logger;

public class CompletableFutureVoidExample {

    private static final Logger logger = Logger.getLogger(CompletableFutureVoidExample.class.getName());

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(5);

        // Asynchronous void method using runAsync
        CompletableFuture<Void> future = CompletableFuture.runAsync(() -> {
            // Simulate a long-running task
            try {
                logger.info("Task started...");
                Thread.sleep(2000); // 2 seconds
                logger.info("Task completed");
            } catch (InterruptedException e) {
                logger.log(Level.SEVERE, "Task interrupted", e);
                Thread.currentThread().interrupt();
            }
        }, executor);

        // Handle result and exceptions
        future.whenComplete((result, ex) -> {
            if (ex != null) {
                logger.log(Level.SEVERE, "An error occurred: ", ex);
            } else {
                logger.info("Task finished successfully.");
            }
        });

        // Adding a timeout to the void method
        CompletableFuture<Void> timeoutFuture = future.orTimeout(3, TimeUnit.SECONDS)
                .exceptionally(ex -> {
                    logger.log(Level.WARNING, "Task timed out", ex);
                    return null; // Void method, return null
                });

        // Prevent main thread from exiting immediately
        try {
            timeoutFuture.join();
        } catch (Exception e) {
            logger.log(Level.SEVERE, "An error occurred while joining the future: ", e);
        }

        // Shutdown executor
        executor.shutdown();
    }
}
```

### Explanation:

1. **Executor Service**:
   - Created a custom executor service using `Executors.newFixedThreadPool(5)`.

2. **Asynchronous Task**:
   - Used `CompletableFuture.runAsync` to run a `Runnable` task asynchronously. This task simulates a long-running operation by sleeping for 2 seconds.

3. **Handling Completion and Exceptions**:
   - Used `whenComplete` to handle the completion of the task and log the result. If an exception occurs, it is logged.

4. **Setting a Timeout**:
   - Used `orTimeout` to set a timeout of 3 seconds. If the task does not complete within this time, it completes exceptionally, and the timeout exception is handled by `exceptionally`.

5. **Prevent Main Thread from Exiting**:
   - Used `join` on `timeoutFuture` to prevent the main thread from exiting immediately, ensuring that the asynchronous task completes.

6. **Shutdown Executor**:
   - Shut down the executor service to release resources.

### Summary

By using `CompletableFuture.runAsync` for methods that return `void` and handling exceptions and timeouts appropriately, you can ensure robust asynchronous execution. This approach also includes proper logging to help with debugging and monitoring the execution of your asynchronous tasks.

# Java Return Future that gets executed first with a specific condition, or process both

To handle a scenario where you want to return the result of the first completed `CompletableFuture` that meets a specific condition or process both results if neither meets the condition, you can use the `anyOf` method combined with condition checks. Here’s a structured approach:

### Key Steps

1. **Create Multiple CompletableFutures**: Define the futures you want to run concurrently.
2. **Use `anyOf`**: Utilize `CompletableFuture.anyOf` to get the result of the first completed future.
3. **Check Condition**: Check if the result meets the specific condition.
4. **Fallback to Processing Both**: If the first result doesn't meet the condition, process both results.

### Example Implementation

Here’s a complete example demonstrating this approach:

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.TimeoutException;
import java.util.logging.Level;
import java.util.logging.Logger;

public class CompletableFutureConditionalExample {

    private static final Logger logger = Logger.getLogger(CompletableFutureConditionalExample.class.getName());

    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(3);

        // Define two CompletableFutures
        CompletableFuture<String> future1 = CompletableFuture.supplyAsync(() -> {
            sleep(2); // Simulate a task
            return "Result from Future 1";
        }, executor);

        CompletableFuture<String> future2 = CompletableFuture.supplyAsync(() -> {
            sleep(3); // Simulate a task
            return "Result from Future 2";
        }, executor);

        // Define the specific condition
        String specificCondition = "ConditionMet";

        // Process the first future that completes with the condition or process both
        CompletableFuture<String> resultFuture = CompletableFuture.anyOf(future1, future2)
            .thenCompose(firstCompleted -> {
                String result = (String) firstCompleted;

                if (result.equals(specificCondition)) {
                    return CompletableFuture.completedFuture(result);
                } else {
                    // Process both results if the condition is not met
                    return CompletableFuture.allOf(future1, future2)
                            .thenApply(v -> {
                                String result1 = future1.join();
                                String result2 = future2.join();
                                // Process both results as needed
                                return "Processed both results: " + result1 + " and " + result2;
                            });
                }
            });

        // Handle result and exceptions
        resultFuture.whenComplete((result, ex) -> {
            if (ex != null) {
                logger.log(Level.SEVERE, "An error occurred: ", ex);
            } else {
                logger.log(Level.INFO, "Result: {0}", result);
            }
        });

        // Prevent main thread from exiting immediately
        try {
            resultFuture.join();
        } catch (Exception e) {
            logger.log(Level.SEVERE, "An error occurred while joining the future: ", e);
        }

        // Shutdown executor
        executor.shutdown();
    }

    // Helper method to simulate a long-running task
    private static void sleep(int seconds) {
        try {
            TimeUnit.SECONDS.sleep(seconds);
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

### Explanation

1. **Executor Service**:
   - A custom executor service with a fixed thread pool is created to manage the threads.

2. **Asynchronous Tasks**:
   - Two `CompletableFuture` instances (`future1` and `future2`) are created using `supplyAsync`, simulating tasks with different sleep durations.

3. **Condition Check**:
   - `CompletableFuture.anyOf` is used to wait for the first future to complete. The `thenCompose` method checks if the result of the first completed future meets the specific condition.
   - If the condition is met, a completed future with the result is returned.
   - If the condition is not met, `CompletableFuture.allOf` is used to wait for both futures to complete, and both results are processed.

4. **Result Handling**:
   - The result or exception is logged using `whenComplete`.

5. **Prevent Main Thread from Exiting**:
   - The `join` method is called on `resultFuture` to prevent the main thread from exiting immediately, allowing the asynchronous tasks to complete.

6. **Shutdown Executor**:
   - The executor service is shut down to release resources.

### Summary

By combining `CompletableFuture.anyOf` with condition checks and fallback processing, you can handle asynchronous tasks efficiently, ensuring that the first completed future meeting the condition is processed, or both results are processed if the condition is not met. This approach provides a robust and flexible way to manage concurrent tasks and their results.

# How to handle an instant response from an external API and a callback response in a single controller in Spring Boot?

To handle both an instant response from an external API and a delayed callback response in a single Spring Boot controller, you need to design your controller to manage these asynchronous operations effectively. Here’s a structured approach:

### Key Steps

1. **Make an Instant API Call**: Immediately call the external API and get the instant response.
2. **Register for Callback**: Register or set up the callback endpoint to receive the delayed response.
3. **Handle Callback**: Implement the callback endpoint to process the delayed response.
4. **Store and Correlate Responses**: Use a mechanism (like a map or a database) to correlate the instant response and the callback response.

### Example Implementation

Here's an example of how you can achieve this in a Spring Boot application:

#### 1. Define the Controller

```java
import org.springframework.web.bind.annotation.*;
import org.springframework.web.client.RestTemplate;
import org.springframework.http.ResponseEntity;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ConcurrentHashMap;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.TimeoutException;
import java.util.Map;
import java.util.UUID;

@RestController
@RequestMapping("/api")
public class MyController {

    private final RestTemplate restTemplate;
    private final Map<String, CompletableFuture<String>> futureResponses = new ConcurrentHashMap<>();

    public MyController(RestTemplate restTemplate) {
        this.restTemplate = restTemplate;
    }

    @PostMapping("/externalApi")
    public ResponseEntity<String> callExternalApi() {
        // Generate a unique ID for correlating the responses
        String requestId = UUID.randomUUID().toString();
        
        // Make the instant API call
        String instantResponse = restTemplate.getForObject("https://external-api.com/instant", String.class);

        // Register for the callback
        CompletableFuture<String> futureResponse = new CompletableFuture<>();
        futureResponses.put(requestId, futureResponse);

        // Return the instant response along with a request ID
        return ResponseEntity.ok("Instant response: " + instantResponse + ", requestId: " + requestId);
    }

    @PostMapping("/callback")
    public ResponseEntity<String> handleCallback(@RequestParam String requestId, @RequestBody String callbackResponse) {
        // Retrieve the corresponding future and complete it with the callback response
        CompletableFuture<String> futureResponse = futureResponses.get(requestId);
        if (futureResponse != null) {
            futureResponse.complete(callbackResponse);
            return ResponseEntity.ok("Callback processed successfully");
        } else {
            return ResponseEntity.status(404).body("Request ID not found");
        }
    }

    @GetMapping("/response")
    public ResponseEntity<String> getResponse(@RequestParam String requestId) {
        try {
            // Wait for the callback response (with a timeout)
            CompletableFuture<String> futureResponse = futureResponses.get(requestId);
            if (futureResponse == null) {
                return ResponseEntity.status(404).body("Request ID not found");
            }

            String callbackResponse = futureResponse.get(10, TimeUnit.SECONDS);
            return ResponseEntity.ok("Callback response: " + callbackResponse);
        } catch (TimeoutException e) {
            return ResponseEntity.status(408).body("Callback response timed out");
        } catch (Exception e) {
            return ResponseEntity.status(500).body("An error occurred: " + e.getMessage());
        }
    }
}
```

### Explanation

1. **Instant API Call**:
   - In `callExternalApi`, an instant API call is made using `RestTemplate`, and a unique `requestId` is generated to correlate responses.
   - A `CompletableFuture` is registered in a concurrent map (`futureResponses`) to handle the delayed response.

2. **Callback Endpoint**:
   - In `handleCallback`, the callback response is received, and the corresponding `CompletableFuture` is completed using the `requestId`.

3. **Retrieve Combined Response**:
   - In `getResponse`, the client can query the combined response using the `requestId`. This endpoint waits for the callback response, with a timeout to handle delays.

### Benefits:

- **Separation of Concerns**: The controller separates the logic of making instant API calls and handling callbacks.
- **Asynchronous Handling**: `CompletableFuture` is used to handle asynchronous callbacks without blocking threads.
- **Timeout Handling**: The `getResponse` method includes timeout handling to avoid indefinite waits for callbacks.
- **Scalability**: Using a concurrent map to manage `CompletableFuture` instances ensures thread safety and scalability.

This approach provides a robust way to handle both instant and delayed responses in a single Spring Boot controller, leveraging `CompletableFuture` for asynchronous processing and response correlation.

# How to prevent multiple CompletableFuture#whenComplete concat?

When working with `CompletableFuture`, you might encounter situations where multiple `whenComplete` handlers are unintentionally concatenated, leading to redundant or unintended executions. To prevent this, you need to ensure that you chain your `CompletableFuture` operations correctly and avoid adding multiple `whenComplete` handlers for the same future.

Here are a few strategies to prevent multiple `CompletableFuture#whenComplete` concatenation:

### 1. Chain CompletableFuture Operations Properly

Ensure that you chain `CompletableFuture` operations in a single pipeline, avoiding the creation of multiple `whenComplete` handlers unnecessarily.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureExample {

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate a task
            return "Task result";
        });

        future
            .thenApply(result -> {
                // Process result
                return "Processed " + result;
            })
            .whenComplete((result, ex) -> {
                if (ex != null) {
                    System.out.println("An error occurred: " + ex.getMessage());
                } else {
                    System.out.println("Final result: " + result);
                }
            });

        // Ensure main thread waits for the future to complete
        try {
            future.join();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### 2. Use a Single Completion Handler

If you need to handle completion in multiple places, consolidate the completion logic into a single `whenComplete` or `handle` block to avoid redundancy.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureExample {

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate a task
            return "Task result";
        });

        CompletableFuture<String> processedFuture = future.thenApply(result -> {
            // Process result
            return "Processed " + result;
        });

        processedFuture.whenComplete((result, ex) -> {
            if (ex != null) {
                System.out.println("An error occurred: " + ex.getMessage());
            } else {
                System.out.println("Final result: " + result);
            }
        });

        // Ensure main thread waits for the future to complete
        try {
            processedFuture.join();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### 3. Avoid Side Effects in CompletableFuture Chains

Minimize side effects within `CompletableFuture` chains to prevent unintended behaviors. Instead of using `whenComplete` multiple times, use it once at the end of your chain.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureExample {

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate a task
            return "Task result";
        });

        future
            .thenApply(result -> "Processed " + result)
            .whenComplete((result, ex) -> {
                if (ex != null) {
                    System.out.println("An error occurred: " + ex.getMessage());
                } else {
                    System.out.println("Final result: " + result);
                }
            });

        // Ensure main thread waits for the future to complete
        try {
            future.join();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### 4. Use Dedicated Methods for CompletableFuture Stages

Encapsulate different stages of your `CompletableFuture` processing in dedicated methods to avoid re-attaching completion handlers.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureExample {

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate a task
            return "Task result";
        });

        processFuture(future);

        // Ensure main thread waits for the future to complete
        try {
            future.join();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }

    private static void processFuture(CompletableFuture<String> future) {
        future
            .thenApply(result -> "Processed " + result)
            .whenComplete((result, ex) -> {
                if (ex != null) {
                    System.out.println("An error occurred: " + ex.getMessage());
                } else {
                    System.out.println("Final result: " + result);
                }
            });
    }
}
```

### Summary

To prevent multiple `CompletableFuture#whenComplete` concatenations:

- Chain your `CompletableFuture` operations properly.
- Consolidate completion handling in a single `whenComplete` or `handle` block.
- Minimize side effects and avoid multiple completion handlers.
- Use dedicated methods to encapsulate different stages of `CompletableFuture` processing.

By following these practices, you can ensure that your `CompletableFuture` chains remain clean and efficient without redundant or unintended executions.

# Is it good industry practice to use whenComplete to mark completion of CompletableFuture?

Using `whenComplete` to mark the completion of a `CompletableFuture` is a common practice in Java and can be appropriate depending on the context. However, it is essential to understand the different completion methods and their intended use cases to apply them correctly. Here are some considerations and best practices:

### Common Completion Methods

1. **`whenComplete`**:
   - **Usage**: Runs a callback when the `CompletableFuture` completes, regardless of the outcome (normal completion or exception).
   - **Example**:
     ```java
     future.whenComplete((result, exception) -> {
         if (exception == null) {
             System.out.println("Completed successfully with result: " + result);
         } else {
             System.out.println("Completed with exception: " + exception.getMessage());
         }
     });
     ```

2. **`handle`**:
   - **Usage**: Similar to `whenComplete`, but it allows transforming the result or exception into a different value. Useful for continuing the computation with a fallback value in case of an exception.
   - **Example**:
     ```java
     future.handle((result, exception) -> {
         if (exception != null) {
             return "Fallback value";
         }
         return result;
     });
     ```

3. **`thenApply`, `thenApplyAsync`**:
   - **Usage**: Transforms the result of the `CompletableFuture` if it completes normally. The `Async` variant runs the transformation on a different thread.
   - **Example**:
     ```java
     future.thenApply(result -> "Processed " + result);
     ```

4. **`thenAccept`, `thenAcceptAsync`**:
   - **Usage**: Consumes the result of the `CompletableFuture` if it completes normally. The `Async` variant runs the consumption on a different thread.
   - **Example**:
     ```java
     future.thenAccept(result -> System.out.println("Result: " + result));
     ```

5. **`thenRun`, `thenRunAsync`**:
   - **Usage**: Runs a `Runnable` after the `CompletableFuture` completes, without accessing the result.
   - **Example**:
     ```java
     future.thenRun(() -> System.out.println("Future completed"));
     ```

### When to Use `whenComplete`

- **Logging**: `whenComplete` is suitable for logging the result or exception of a `CompletableFuture`.
- **Side Effects**: It can be used for side effects that should occur whether the future completes normally or exceptionally.
- **Non-Transformation**: Use `whenComplete` when you need to perform an action without transforming the result or propagating exceptions.

### Best Practices

1. **Avoid Business Logic in `whenComplete`**: Use `whenComplete` for side effects such as logging, but avoid placing significant business logic within it. Use `handle` or `thenApply` for business logic transformations.
2. **Handle Exceptions**: Ensure exceptions are properly handled to avoid silent failures.
3. **Prefer Functional Composition**: For chaining transformations and continuations, prefer methods like `thenApply`, `thenCompose`, and `handle` for clear and functional composition.

### Example

Here’s an example demonstrating the correct use of `whenComplete`:

```java
import java.util.concurrent.CompletableFuture;

public class CompletableFutureExample {

    public static void main(String[] args) {
        CompletableFuture<String> future = CompletableFuture.supplyAsync(() -> {
            // Simulate a task
            return "Task result";
        });

        // Log completion
        future.whenComplete((result, exception) -> {
            if (exception == null) {
                System.out.println("Completed successfully with result: " + result);
            } else {
                System.out.println("Completed with exception: " + exception.getMessage());
            }
        });

        // Further processing
        CompletableFuture<String> processedFuture = future.thenApply(result -> {
            // Process result
            return "Processed " + result;
        });

        // Handle exceptions and provide a fallback
        processedFuture.handle((result, exception) -> {
            if (exception != null) {
                return "Fallback value";
            }
            return result;
        }).thenAccept(finalResult -> {
            // Consume the final result
            System.out.println("Final result: " + finalResult);
        });

        // Ensure main thread waits for the future to complete
        try {
            processedFuture.join();
        } catch (Exception e) {
            e.printStackTrace();
        }
    }
}
```

### Summary

- **`whenComplete`** is suitable for logging and side effects.
- **Use dedicated methods** (`thenApply`, `handle`, etc.) for transformations and business logic.
- **Handle exceptions** properly to ensure robust error handling.
- **Prefer functional composition** to maintain clear and maintainable asynchronous workflows.

By following these guidelines, you can use `whenComplete` effectively while maintaining clean and efficient `CompletableFuture` chains.

# Java 8 to Java 17 ThreadLocal issue

Moving from Java 8 to Java 17 can introduce several changes and improvements in how the Java runtime manages resources, including changes in how `ThreadLocal` works. Here are some considerations and steps to address `ThreadLocal` issues when upgrading from Java 8 to Java 17:

### Common Issues with `ThreadLocal`

1. **Memory Leaks**: `ThreadLocal` variables can cause memory leaks if not managed properly, as they can hold references to objects for the lifetime of a thread.
2. **Thread Pools**: In environments using thread pools, `ThreadLocal` variables may not be cleared correctly, leading to stale or unintended data being retained.
3. **Behavior Changes**: Java 17 might introduce subtle behavior changes due to optimizations or changes in the garbage collection mechanism.

### Steps to Address `ThreadLocal` Issues

1. **Review and Clean Up `ThreadLocal` Usage**: Ensure that all `ThreadLocal` variables are properly cleaned up when they are no longer needed.
2. **Use `remove()` Method**: Always call the `remove()` method on `ThreadLocal` variables to clear the values explicitly when done.
3. **Consider Alternatives**: For certain use cases, alternatives like `InheritableThreadLocal`, `CompletableFuture`, or passing data explicitly might be more appropriate.
4. **Upgrade Dependencies**: Ensure all third-party libraries and frameworks are compatible with Java 17 and handle `ThreadLocal` correctly.

### Example

Here’s an example of how to use `ThreadLocal` correctly:

```java
public class ThreadLocalExample {

    private static final ThreadLocal<String> threadLocalValue = ThreadLocal.withInitial(() -> null);

    public static void main(String[] args) {
        Runnable task = () -> {
            try {
                threadLocalValue.set("Value for " + Thread.currentThread().getName());
                System.out.println(Thread.currentThread().getName() + ": " + threadLocalValue.get());
            } finally {
                // Always remove the value to prevent memory leaks
                threadLocalValue.remove();
            }
        };

        Thread thread1 = new Thread(task, "Thread-1");
        Thread thread2 = new Thread(task, "Thread-2");

        thread1.start();
        thread2.start();

        try {
            thread1.join();
            thread2.join();
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

### Best Practices for `ThreadLocal`

1. **Limit the Scope**: Keep the usage of `ThreadLocal` variables limited to where they are absolutely necessary.
2. **Explicit Cleanup**: Always use `remove()` in a `finally` block to ensure cleanup happens regardless of how the thread completes.
3. **Avoid Complex Logic**: Keep the logic involving `ThreadLocal` simple to reduce the risk of bugs and memory leaks.
4. **Document Usage**: Clearly document why `ThreadLocal` is used and how it is managed, especially in large codebases or when working in teams.

### Upgrading to Java 17: Key Considerations

1. **Check for Deprecated APIs**: Ensure you are not using deprecated APIs that have been removed or changed in Java 17.
2. **Update Build Tools**: Update your build tools (e.g., Maven, Gradle) to use Java 17.
3. **Run Tests**: Run your unit and integration tests on Java 17 to catch any compatibility issues.
4. **Performance Tuning**: Java 17 includes various performance improvements; review and adjust your JVM tuning parameters if needed.

### Summary

When upgrading from Java 8 to Java 17, addressing `ThreadLocal` issues involves:

- **Reviewing and Cleaning Up**: Ensure proper usage and cleanup of `ThreadLocal` variables.
- **Explicit Removal**: Use the `remove()` method to clear values explicitly.
- **Considering Alternatives**: Evaluate if alternatives to `ThreadLocal` are more appropriate for your use case.
- **Testing and Validation**: Thoroughly test your application on Java 17 to ensure compatibility and performance.

By following these practices, you can manage `ThreadLocal` variables effectively and ensure a smooth transition from Java 8 to Java 17.

# Java code race condition multi-threaded?

Race conditions in multi-threaded Java applications occur when two or more threads access shared data concurrently and try to change it simultaneously. The outcome of these operations depends on the timing of their execution, which can lead to inconsistent or incorrect results.

To demonstrate and address race conditions, let's consider an example where multiple threads increment a shared counter.

### Example of a Race Condition

Here's a simple Java program that demonstrates a race condition:

```java
public class RaceConditionExample {

    private static int counter = 0;

    public static void main(String[] args) throws InterruptedException {
        Thread thread1 = new Thread(RaceConditionExample::incrementCounter);
        Thread thread2 = new Thread(RaceConditionExample::incrementCounter);

        thread1.start();
        thread2.start();

        thread1.join();
        thread2.join();

        System.out.println("Final counter value: " + counter);
    }

    private static void incrementCounter() {
        for (int i = 0; i < 1000; i++) {
            counter++;
        }
    }
}
```

In this example, `thread1` and `thread2` both increment the `counter` variable 1000 times. Due to the race condition, the final value of `counter` may not be 2000, as expected.

### Fixing the Race Condition

To fix the race condition, you need to ensure that the increment operation is atomic, meaning it cannot be interrupted by other threads. This can be achieved using various synchronization techniques:

#### 1. Using `synchronized` Keyword

You can use the `synchronized` keyword to make the increment operation atomic:

```java
public class RaceConditionExample {

    private static int counter = 0;

    public static void main(String[] args) throws InterruptedException {
        Thread thread1 = new Thread(RaceConditionExample::incrementCounter);
        Thread thread2 = new Thread(RaceConditionExample::incrementCounter);

        thread1.start();
        thread2.start();

        thread1.join();
        thread2.join();

        System.out.println("Final counter value: " + counter);
    }

    private synchronized static void incrementCounter() {
        for (int i = 0; i < 1000; i++) {
            counter++;
        }
    }
}
```

By synchronizing the `incrementCounter` method, you ensure that only one thread can execute the method at a time.

#### 2. Using `ReentrantLock`

Another approach is to use the `ReentrantLock` from the `java.util.concurrent.locks` package:

```java
import java.util.concurrent.locks.ReentrantLock;

public class RaceConditionExample {

    private static int counter = 0;
    private static final ReentrantLock lock = new ReentrantLock();

    public static void main(String[] args) throws InterruptedException {
        Thread thread1 = new Thread(RaceConditionExample::incrementCounter);
        Thread thread2 = new Thread(RaceConditionExample::incrementCounter);

        thread1.start();
        thread2.start();

        thread1.join();
        thread2.join();

        System.out.println("Final counter value: " + counter);
    }

    private static void incrementCounter() {
        for (int i = 0; i < 1000; i++) {
            lock.lock();
            try {
                counter++;
            } finally {
                lock.unlock();
            }
        }
    }
}
```

Using `ReentrantLock`, you can explicitly lock and unlock the critical section.

#### 3. Using `AtomicInteger`

For simple atomic operations, Java provides the `AtomicInteger` class, which supports atomic increment operations:

```java
import java.util.concurrent.atomic.AtomicInteger;

public class RaceConditionExample {

    private static final AtomicInteger counter = new AtomicInteger(0);

    public static void main(String[] args) throws InterruptedException {
        Thread thread1 = new Thread(RaceConditionExample::incrementCounter);
        Thread thread2 = new Thread(RaceConditionExample::incrementCounter);

        thread1.start();
        thread2.start();

        thread1.join();
        thread2.join();

        System.out.println("Final counter value: " + counter.get());
    }

    private static void incrementCounter() {
        for (int i = 0; i < 1000; i++) {
            counter.incrementAndGet();
        }
    }
}
```

`AtomicInteger` provides methods like `incrementAndGet` which are atomic and safe to use in a concurrent environment.

### Summary

- **Race conditions** occur when multiple threads access shared data concurrently without proper synchronization.
- **Synchronized blocks/methods**: Use the `synchronized` keyword to prevent race conditions by ensuring that only one thread can execute a critical section at a time.
- **Locks**: Use `ReentrantLock` for more advanced locking mechanisms.
- **Atomic variables**: Use classes like `AtomicInteger` for simple atomic operations.

By using these techniques, you can ensure that your multi-threaded Java applications run correctly without encountering race conditions.

# spring integration publish subscribe between beans

Spring Integration provides a robust framework for building message-driven applications, including support for publish-subscribe messaging between beans. Using Spring Integration, you can create a publish-subscribe channel where multiple subscribers (beans) can listen to messages published by a producer bean. Here's how you can set up a simple publish-subscribe pattern between beans in a Spring application.

### Step-by-Step Guide

1. **Add Spring Integration Dependencies**

First, ensure you have the necessary Spring Integration dependencies in your `pom.xml` (for Maven) or `build.gradle` (for Gradle).

**Maven**:
```xml
<dependency>
    <groupId>org.springframework.integration</groupId>
    <artifactId>spring-integration-core</artifactId>
</dependency>
```

**Gradle**:
```groovy
implementation 'org.springframework.integration:spring-integration-core'
```

2. **Configure the Publish-Subscribe Channel**

Create a Spring configuration class to define a publish-subscribe channel.

```java
import org.springframework.context.annotation.Bean;
import org.springframework.context.annotation.Configuration;
import org.springframework.integration.channel.PublishSubscribeChannel;
import org.springframework.messaging.MessageChannel;

@Configuration
public class IntegrationConfig {

    @Bean
    public MessageChannel pubSubChannel() {
        return new PublishSubscribeChannel();
    }
}
```

3. **Create Producer and Subscriber Beans**

Define your producer and subscriber beans. The producer will send messages to the channel, and the subscribers will listen to the messages.

**Producer Bean**:
```java
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.integration.support.MessageBuilder;
import org.springframework.messaging.MessageChannel;
import org.springframework.stereotype.Component;

@Component
public class MessageProducer {

    @Autowired
    private MessageChannel pubSubChannel;

    public void sendMessage(String message) {
        pubSubChannel.send(MessageBuilder.withPayload(message).build());
    }
}
```

**Subscriber Beans**:
```java
import org.springframework.integration.annotation.ServiceActivator;
import org.springframework.stereotype.Component;

@Component
public class SubscriberOne {

    @ServiceActivator(inputChannel = "pubSubChannel")
    public void handleMessage(String message) {
        System.out.println("Subscriber One received: " + message);
    }
}

@Component
public class SubscriberTwo {

    @ServiceActivator(inputChannel = "pubSubChannel")
    public void handleMessage(String message) {
        System.out.println("Subscriber Two received: " + message);
    }
}
```

4. **Enable Integration Configuration**

Enable Spring Integration's configuration in your main application class.

```java
import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;
import org.springframework.context.ConfigurableApplicationContext;

@SpringBootApplication
public class SpringIntegrationApplication {

    public static void main(String[] args) {
        ConfigurableApplicationContext context = SpringApplication.run(SpringIntegrationApplication.class, args);
        
        // Get the producer bean and send a message
        MessageProducer producer = context.getBean(MessageProducer.class);
        producer.sendMessage("Hello, Spring Integration!");
    }
}
```

### Explanation

1. **Dependencies**: Ensure Spring Integration dependencies are included.
2. **Channel Configuration**: Define a `PublishSubscribeChannel` bean, which is a special type of channel that broadcasts messages to all subscribers.
3. **Producer**: Create a producer bean that sends messages to the `pubSubChannel`.
4. **Subscribers**: Create subscriber beans that listen to messages from the `pubSubChannel`. Use `@ServiceActivator` to designate methods as message handlers for the channel.
5. **Main Application**: Send messages using the producer bean to see how subscribers handle them.

### Testing the Setup

When you run the application, you should see output indicating that both subscribers received the message:

```plaintext
Subscriber One received: Hello, Spring Integration!
Subscriber Two received: Hello, Spring Integration!
```

### Summary

Using Spring Integration's `PublishSubscribeChannel`, you can set up a simple publish-subscribe mechanism where multiple subscriber beans can listen to messages sent by a producer bean. This setup allows for a decoupled architecture where message producers and consumers do not need to know about each other, making the system more modular and scalable.

# Understanding Java concurrency in spring mvc

Understanding concurrency in a Spring MVC application involves knowing how the framework handles HTTP requests, how threads are managed, and how to safely handle shared resources. Here’s a guide to help you understand Java concurrency in Spring MVC.

### 1. Spring MVC Request Handling

Spring MVC is inherently multi-threaded. Each HTTP request to a Spring MVC application is handled by a separate thread from a pool managed by the web container (such as Tomcat, Jetty, etc.). The default pool size and other configurations depend on the container settings, but Spring MVC doesn’t handle threading directly.

### 2. Thread Safety in Controllers

Since each HTTP request is handled by a separate thread, controllers should be stateless. Any instance variables in a controller should not be shared across requests or threads.

**Example of Thread-Safe Controller**:
```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestParam;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class GreetingController {

    @GetMapping("/greet")
    public String greet(@RequestParam(value = "name", defaultValue = "World") String name) {
        return "Hello, " + name;
    }
}
```

In this example, the `GreetingController` is thread-safe because it does not maintain any state that could be shared between requests.

### 3. Handling Shared Resources

If your application needs to access shared resources (e.g., shared in-memory data, files, etc.), you need to ensure thread safety by using appropriate synchronization mechanisms.

#### 3.1. Synchronized Blocks
You can use `synchronized` blocks to control access to shared resources.

**Example**:
```java
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class CounterController {

    private int counter = 0;

    @GetMapping("/increment")
    public synchronized String incrementCounter() {
        counter++;
        return "Counter: " + counter;
    }
}
```

#### 3.2. Using `ReentrantLock`
For more fine-grained control, you can use `ReentrantLock` from the `java.util.concurrent.locks` package.

**Example**:
```java
import java.util.concurrent.locks.ReentrantLock;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class LockCounterController {

    private int counter = 0;
    private final ReentrantLock lock = new ReentrantLock();

    @GetMapping("/increment")
    public String incrementCounter() {
        lock.lock();
        try {
            counter++;
            return "Counter: " + counter;
        } finally {
            lock.unlock();
        }
    }
}
```

#### 3.3. Using `AtomicInteger`
For atomic operations on single variables, use `AtomicInteger` from `java.util.concurrent.atomic`.

**Example**:
```java
import java.util.concurrent.atomic.AtomicInteger;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class AtomicCounterController {

    private final AtomicInteger counter = new AtomicInteger(0);

    @GetMapping("/increment")
    public String incrementCounter() {
        return "Counter: " + counter.incrementAndGet();
    }
}
```

### 4. Asynchronous Request Handling

Spring MVC supports asynchronous request processing to handle long-running requests without blocking the main thread.

#### 4.1. Using `DeferredResult`
`DeferredResult` allows you to process a request asynchronously.

**Example**:
```java
import java.util.concurrent.ForkJoinPool;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;
import org.springframework.web.context.request.async.DeferredResult;

@RestController
public class AsyncController {

    @GetMapping("/async")
    public DeferredResult<String> async() {
        DeferredResult<String> deferredResult = new DeferredResult<>();
        ForkJoinPool.commonPool().submit(() -> {
            try {
                Thread.sleep(2000); // Simulate a long-running task
                deferredResult.setResult("Async Response");
            } catch (InterruptedException e) {
                deferredResult.setErrorResult(e);
            }
        });
        return deferredResult;
    }
}
```

#### 4.2. Using `Callable`
Another way to handle asynchronous requests is by using `Callable`.

**Example**:
```java
import java.util.concurrent.Callable;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class CallableController {

    @GetMapping("/callable")
    public Callable<String> callable() {
        return () -> {
            Thread.sleep(2000); // Simulate a long-running task
            return "Callable Response";
        };
    }
}
```

### 5. Using `@Async` for Asynchronous Processing

Spring provides the `@Async` annotation to run methods asynchronously. This requires enabling asynchronous processing in your configuration.

#### 5.1. Enable Async Processing
Enable asynchronous processing in your Spring configuration.

```java
import org.springframework.context.annotation.Configuration;
import org.springframework.scheduling.annotation.EnableAsync;

@Configuration
@EnableAsync
public class AsyncConfig {
}
```

#### 5.2. Define Async Method
Define a method with the `@Async` annotation.

**Example**:
```java
import java.util.concurrent.CompletableFuture;
import org.springframework.scheduling.annotation.Async;
import org.springframework.stereotype.Service;

@Service
public class AsyncService {

    @Async
    public CompletableFuture<String> performAsyncTask() {
        try {
            Thread.sleep(2000); // Simulate a long-running task
            return CompletableFuture.completedFuture("Async Service Response");
        } catch (InterruptedException e) {
            return CompletableFuture.completedExceptionally(e);
        }
    }
}
```

#### 5.3. Call Async Method
Call the async method from a controller.

**Example**:
```java
import java.util.concurrent.CompletableFuture;
import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RestController;

@RestController
public class AsyncMethodController {

    @Autowired
    private AsyncService asyncService;

    @GetMapping("/async-method")
    public CompletableFuture<String> asyncMethod() {
        return asyncService.performAsyncTask();
    }
}
```

### Summary

- **Spring MVC is multi-threaded**: Each HTTP request is handled by a separate thread.
- **Stateless Controllers**: Ensure your controllers are stateless to avoid concurrency issues.
- **Thread Safety**: Use synchronization mechanisms like `synchronized`, `ReentrantLock`, or `AtomicInteger` to handle shared resources safely.
- **Asynchronous Processing**: Use `DeferredResult`, `Callable`, or `@Async` for non-blocking, asynchronous request processing.

By following these guidelines, you can effectively manage concurrency in your Spring MVC applications, ensuring thread safety and efficient request handling.