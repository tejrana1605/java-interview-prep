# ExecutorService all type of constructor

`ExecutorService` is an interface in Java, so it does not have constructors of its own. Instead, the implementations of `ExecutorService` provide various constructors. The most commonly used implementations are:

1. `ThreadPoolExecutor`
2. `ScheduledThreadPoolExecutor`
3. `ForkJoinPool`

Here is a detailed overview of the constructors for each of these implementations:

### 1. `ThreadPoolExecutor`

`ThreadPoolExecutor` is the most flexible and widely used implementation of `ExecutorService`.

#### Constructors
```java
public ThreadPoolExecutor(int corePoolSize,
                          int maximumPoolSize,
                          long keepAliveTime,
                          TimeUnit unit,
                          BlockingQueue<Runnable> workQueue)
                          
public ThreadPoolExecutor(int corePoolSize,
                          int maximumPoolSize,
                          long keepAliveTime,
                          TimeUnit unit,
                          BlockingQueue<Runnable> workQueue,
                          ThreadFactory threadFactory)
                          
public ThreadPoolExecutor(int corePoolSize,
                          int maximumPoolSize,
                          long keepAliveTime,
                          TimeUnit unit,
                          BlockingQueue<Runnable> workQueue,
                          RejectedExecutionHandler handler)
                          
public ThreadPoolExecutor(int corePoolSize,
                          int maximumPoolSize,
                          long keepAliveTime,
                          TimeUnit unit,
                          BlockingQueue<Runnable> workQueue,
                          ThreadFactory threadFactory,
                          RejectedExecutionHandler handler)
```

#### Example
```java
ExecutorService executor = new ThreadPoolExecutor(
    2,                      // core pool size
    4,                      // maximum pool size
    60L,                    // keep-alive time
    TimeUnit.SECONDS,       // time unit for keep-alive
    new LinkedBlockingQueue<Runnable>()  // work queue
);
```

### 2. `ScheduledThreadPoolExecutor`

`ScheduledThreadPoolExecutor` is an implementation of `ExecutorService` that supports scheduling tasks to run after a delay or periodically.

#### Constructors
```java
public ScheduledThreadPoolExecutor(int corePoolSize)
public ScheduledThreadPoolExecutor(int corePoolSize, ThreadFactory threadFactory)
public ScheduledThreadPoolExecutor(int corePoolSize, RejectedExecutionHandler handler)
public ScheduledThreadPoolExecutor(int corePoolSize, ThreadFactory threadFactory, RejectedExecutionHandler handler)
```

#### Example
```java
ScheduledExecutorService scheduler = new ScheduledThreadPoolExecutor(
    2,                      // core pool size
    Executors.defaultThreadFactory(),
    new ThreadPoolExecutor.AbortPolicy()
);
```

### 3. `ForkJoinPool`

`ForkJoinPool` is designed for work-stealing algorithms and is particularly useful for parallel processing.

#### Constructors
```java
public ForkJoinPool()
public ForkJoinPool(int parallelism)
public ForkJoinPool(int parallelism, ForkJoinPool.ForkJoinWorkerThreadFactory factory, Thread.UncaughtExceptionHandler handler, boolean asyncMode)
public ForkJoinPool(int parallelism, ForkJoinPool.ForkJoinWorkerThreadFactory factory, Thread.UncaughtExceptionHandler handler, boolean asyncMode, int corePoolSize, int maximumPoolSize, int keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue, ForkJoinPool.ForkJoinWorkerThreadFactory forkJoinWorkerThreadFactory)
```

#### Example
```java
ForkJoinPool forkJoinPool = new ForkJoinPool(
    4,                                   // parallelism level
    ForkJoinPool.defaultForkJoinWorkerThreadFactory,
    null,                                // handler for uncaught exceptions
    false                                // async mode
);
```

### Utility Methods in Executors Class

The `Executors` class provides several utility methods to create `ExecutorService` instances.

#### Example
```java
ExecutorService fixedThreadPool = Executors.newFixedThreadPool(4);
ExecutorService cachedThreadPool = Executors.newCachedThreadPool();
ScheduledExecutorService scheduledThreadPool = Executors.newScheduledThreadPool(4);
ExecutorService singleThreadExecutor = Executors.newSingleThreadExecutor();
```

### Summary

The `ExecutorService` interface itself does not have constructors, but its implementations, such as `ThreadPoolExecutor`, `ScheduledThreadPoolExecutor`, and `ForkJoinPool`, provide a variety of constructors to configure the behavior of the thread pools. Additionally, the `Executors` utility class offers convenient factory methods to create common types of executor services.