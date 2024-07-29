# Java Executor Framework

The ExecutorService in Java provides a flexible and efficient framework for asynchronous task execution. It abstracts away the complexities of managing threads manually and allows developers to focus on the logic of their tasks. 

## Overview

The ExecutorService interface is part of the java.util.concurrent package and represents an asynchronous task execution service. It extends the Executor interface, which defines a single method execute(Runnable command) for executing tasks.

## Executors

Executors is a utility class in Java that provides factory methods for creating and managing different types of ExecutorService instances. It simplifies the process of instantiating thread pools and allows developers to easily create and manage executor instances with various configurations.

The Executors class provides several static factory methods for creating different types of executor services:

1. **FixedThreadPool**: Creates an ExecutorService with a fixed number of threads. Tasks submitted to this executor are executed concurrently by the specified number of threads. If a thread is idle and no tasks are available, it remains alive but dormant until needed.

```java
ExecutorService executor = Executors.newFixedThreadPool(5);
```

2. **CachedThreadPool**: Creates an ExecutorService with an unbounded thread pool that automatically adjusts its size based on the workload. Threads are created as needed and reused for subsequent tasks. If a thread remains idle for a certain period, it may be terminated to reduce resource consumption. 

In a cached thread pool, submitted tasks are not queued but immediately handed off to a thread for execution. If no threads are available, a new one is created. If a server is so heavily loaded that all of its CPUs are fully utilized, and more tasks arrive, more threads will be created, which will only make matters worse. Idle time of threads is default to 60s, after which if they don't have any task thread will be terminated.

Therefore, in a heavily loaded production server, you are much better off using Executors.newFixedThreadPool, which gives you a pool with a fixed number of threads, or using the ThreadPoolExecutor class directly, for maximum control.

```java
ExecutorService executor = Executors.newCachedThreadPool();
```

3. **SingleThreadExecutor**: Creates an ExecutorService with a single worker thread. Tasks are executed sequentially by this thread in the order they are submitted. This executor is useful for tasks that require serialization or have dependencies on each other.

```java
ExecutorService executor = Executors.newSingleThreadExecutor();
```

4. **ScheduledThreadPool**: Creates an ExecutorService that can schedule tasks to run after a specified delay or at regular intervals. It provides methods for scheduling tasks with fixed delay or fixed rate, allowing for periodic execution of tasks.

5. **newWorkStealingPool**: Creates a work-stealing thread pool with the target parallelism level. This executor is based on the ForkJoinPool and is capable of dynamically adjusting its thread pool size to utilize all available processor cores efficiently.

Overall, the Executors class simplifies the creation and management of executor instances.

## ExecutorService

Tasks can be submitted to an ExecutorService for execution. These tasks are typically instances of Runnable or Callable, representing units of work that need to be executed asynchronously. 

Below are the methods in ExecutorService.

   1. **execute(Runnable command)**: Executes the given task asynchronously.

```java
ExecutorService executor = Executors.newFixedThreadPool(5);
executor.execute(() -> {
    System.out.println("Task executed asynchronously");
});
```

  2. **submit(Callable<T> task)**: Submits a task for execution and returns a Future representing the pending result of the task.
```java
ExecutorService executor = Executors.newSingleThreadExecutor();
Future<Integer> future = executor.submit(() -> {
    // Task logic
    return 42;
});
```

  3. **shutdown()**: Initiates an orderly shutdown of the ExecutorService, allowing previously submitted tasks to execute before terminating.

  4. **shutdownNow()**: Attempts to stop all actively executing tasks, halts the processing of waiting tasks, and returns a list of the tasks that were awaiting execution.

```java
List<Runnable> pendingTasks = executor.shutdownNow();
```

 5. **awaitTermination(long timeout, TimeUnit unit)**: Blocks until all tasks have completed execution after a shutdown request, or the timeout occurs, or the current thread is interrupted, whichever happens first.

```java
boolean terminated = executor.awaitTermination(10, TimeUnit.SECONDS);
if (terminated) {
    System.out.println("All tasks have completed execution");
} else {
    System.out.println("Timeout occurred before all tasks completed");
}
```

  6. **invokeAny(Collection<? extends Callable<T>> tasks)**: Executes the given tasks, returning the result of one that successfully completes. This method is useful when we have multiple tasks to run but we only care about the result of whichever one completes first.  All other tasks are terminated.

```java
ExecutorService executor = Executors.newCachedThreadPool();
Set<Callable<String>> callables = new HashSet<>();
callables.add(() -> "Task 1");
callables.add(() -> "Task 2");
String result = executor.invokeAny(callables);
System.out.println("Result: " + result);
```

7. **invokeAll(Collection<? extends Callable<T>> tasks)**: Executes the given tasks, returning a list of Future objects representing their pending results.

```java
List<Callable<Integer>> tasks = Arrays.asList(() -> 1, () -> 2, () -> 3);
List<Future<Integer>> futures = executor.invokeAll(tasks);
for (Future<Integer> future : futures) {
    System.out.println("Result: " + future.get());
}
```

## Implementations

The ExecutorService interface is typically implemented by various classes provided by the Java concurrency framework, such as ThreadPoolExecutor, ScheduledThreadPoolExecutor, and ForkJoinPool.

## Considerations

- Careful configuration of thread pool size to avoid underutilization or excessive resource consumption.

- Consider factors such as task submission rate, task priority, resource constraints, and the desired behavior in case of queue overflow. Choose the queue type that best meets your application's requirements for scalability, performance, and resource utilization.

- Proper handling of exceptions and task cancellation to ensure robustness and reliability.

- Understanding the concurrency semantics and potential thread safety issues in concurrent code.

To create an instance of ExecutorService, we can pass ThreadFactory and task queue to be used while creating the pool. 

A ThreadFactory is an interface used to create new threads. It provides a way to encapsulate the logic for creating threads, allowing for customization of thread creation behavior. The primary purpose of a ThreadFactory is to decouple the thread creation process from the rest of the application logic, making it easier to manage and customize thread creation. It is preferred to pass custom Thread factory, as helps in setting thread prefix and priority if required.

```java
static final String prefix = "app.name.task";
ExecutorService executorService = Executors.newFixedThreadPool(5, () -> {  
    Thread t = new Thread(r);
    t.setName(prefix + "-" + t.getId()); // Customize thread name if needed
    return t;
});
```

## TaskQueues

When tasks are submitted to ExecutorService, if none of the threads in pool are available to process the tasks, they get stored in a queue, below are the different queue options to choose from.

1. **Unbounded Queue**: An unbounded queue, such as LinkedBlockingQueue, has no fixed capacity and can grow dynamically to accommodate an unlimited number of tasks. It is suitable for scenarios where the task submission rate is unpredictable or where tasks need to be queued indefinitely without the risk of rejection due to queue overflow. However, keep in mind that unbounded queues can potentially lead to memory exhaustion if tasks are submitted at a faster rate than they can be processed.

2. **Bounded Queue**: A bounded queue, such as ArrayBlockingQueue  with a specified capacity, has a fixed size limit and can only hold a finite number of tasks. It is suitable for scenarios where resource constraints or backpressure mechanisms need to be enforced to prevent excessive memory usage or system overload. Tasks may be rejected or handled according to a specified rejection policy when the queue reaches its capacity.

3. **Priority Queue**: A priority queue, such as PriorityBlockingQueue, orders tasks based on their priority or a specified comparator. It is suitable for scenarios where tasks have different levels of importance or urgency, and higher-priority tasks need to be processed before lower-priority ones. Priority queues ensure that tasks are executed in the order of their priority, regardless of their submission order.

4. **Synchronous Queue**: A synchronous queue, such as SynchronousQueue, is a special type of queue that enables one-to-one task handoff between producer and consumer threads. It has a capacity of zero and requires both a producer and a consumer to be available simultaneously for task exchange to occur. Synchronous queues are suitable for scenarios where strict synchronization and coordination between threads are required, such as handoff between thread pools or bounded resource access.

## ScheduledThreadPool

The ScheduledThreadPoolExecutor inherits thread pool management capabilities from ThreadPoolExecutor and provides functionalities for scheduling tasks to run after a given delay or periodically at defined intervals. Here's a detailed explanation:

- **Runnable and Callable Tasks**: You define tasks you want to schedule using these interfaces, similar to a regular ExecutorService.

- **ScheduledFuture**: This interface represents the result of a scheduled task submission. It allows checking the task's completion status, canceling the task before execution, and (for Callable tasks) retrieving the result upon completion.

## Scheduling Capabilities

- **schedule(Runnable task, long delay, TimeUnit unit)**: Schedules a Runnable task to be executed after a specified delay in the given time unit (e.g., seconds, milliseconds).

- **scheduleAtFixedRate(Runnable command, long initialDelay, long period, TimeUnit unit)**: Schedules a fixed-rate execution of a Runnable task. The task is first executed after the initialDelay, and subsequent executions occur with a constant period between them.

- **scheduleWithFixedDelay(Runnable command, long initialDelay, long delay, TimeUnit unit)**: Schedules a fixed-delay execution of a Runnable task. Similar to scheduleAtFixedRate, but the delay is measured between the completion of the previous execution and the start of the next.

## Key Considerations

- **Thread Pool Management**: ScheduledThreadPoolExecutor maintains a fixed-sized thread pool by default. You can configure the pool size during object creation.

- **Delayed Execution**: Scheduled tasks are not guaranteed to execute precisely at the specified time. The actual execution time might be slightly different due to factors like thread availability and workload.

- **Missed Executions**: With fixed-rate scheduling, if the task execution time exceeds the period, subsequent executions might be skipped to maintain the fixed rate.

- **Cancellation**: You can cancel a scheduled task using the cancel method of the returned ScheduledFuture object. However, cancellation success depends on the task's state (not yet started, running, etc.).

```java
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class ScheduledThreadPoolExample {

    public static void main(String[] args) throws InterruptedException {

        // Create a ScheduledThreadPoolExecutor with 2 threads
        ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(2);

        // Schedule a task with a 2-second delay
        Runnable task1 = () -> System.out.println("Executing task 1 after a delay");
        scheduler.schedule(task1, 2, TimeUnit.SECONDS);

        // Schedule a task to run every 5 seconds with a fixed rate
        Runnable task2 = () -> System.out.println("Executing task 2 at fixed rate");
        scheduler.scheduleAtFixedRate(task2, 1, 5, TimeUnit.SECONDS);

        // Schedule a task to run every 3 seconds with a fixed delay
        Runnable task3 = () -> System.out.println("Executing task 3 with fixed delay");
        scheduler.scheduleWithFixedDelay(task3, 0, 3, TimeUnit.SECONDS);

        // Wait for some time to allow tasks to be executed
        Thread.sleep(15000);

        // Shutdown the scheduler
        scheduler.shutdown();
    }
}
```

## Shut Down ExecutorService Gracefully

To efficiently shut down an **ExecutorService**, you can follow these steps:

1. Call the **shutdown()** method to initiate the shutdown process. This method allows previously submitted tasks to execute before terminating but prevents the submission of new tasks.

2. Call the **shutdownNow()** method if you want to force the **ExecutorService** to terminate immediately. This method attempts to stop all actively executing tasks, halts the processing of waiting tasks, and returns a list of the tasks that were awaiting execution but were never started.

3. Await termination by calling the **awaitTermination()** method. This method blocks until all tasks have completed execution after a shutdown request, or the timeout occurs, or the current thread is interrupted, whichever happens first.

```java
ExecutorService executor = Executors.newFixedThreadPool(10);

// Execute tasks using the executor

// Shutdown the executor
executor.shutdown();

try {
    // Wait for all tasks to complete or timeout after a certain period
    if (!executor.awaitTermination(60, TimeUnit.SECONDS)) {
        // If the timeout occurs, force shutdown
        executor.shutdownNow();
        // Optionally, wait for the tasks to be forcefully terminated
        if (!executor.awaitTermination(60, TimeUnit.SECONDS)) {
            // Log a message indicating that some tasks failed to terminate
        }
    }
} catch (InterruptedException ex) {
    // Log interruption exception
    executor.shutdownNow();
    // Preserve interrupt status
    Thread.currentThread().interrupt();
}
```

In summary, ExecutorService is a versatile framework that helps developers write efficient, scalable, and maintainable concurrent code.
