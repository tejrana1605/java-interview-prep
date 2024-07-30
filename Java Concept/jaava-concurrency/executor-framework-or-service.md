# Executor Framework Java

A framework having a bunch of components that are used for managing worker threads efficiently is referred to as **Executor Framework**. The **Executor** API reduces the execution of the task from the actual task to be executed through the **Executors**. The executor framework is an implementation of the **Producer-Consumer** pattern. The **java.util.concurrent.Executors** class provides a set of methods for creating **ThreadPools** of worker threads.

In order to use the executor framework, we have to create a thread pool for executing the task by submitting that task to that thread pool.

Now, the question which comes to our mind is why we have to create such thread pools when we already have **the java.lang.Thread** class for creating an object and **Runnable/Callable** interface for achieving parallelism by implementing them. So, the reason for creating such thread pools are as follows:

- We need to create a large number of threads for adding a new thread without any throttling for each and every process. Due to which it requires more memory and cause wastage of resource. When each thread is swapped, the CPU starts to spend too much time.

- When we create a new thread for executing a new task cause overhead of thread creation. In order to manage this thread life-cycle, the execution time increase respectively.

## Types of Executors

In Java, there are different types of executors available which are as follows:


<a href="#" target="_blank"><img src="https://static.javatpoint.com/core/images/executor-framework-java.png" alt="Executor Service"/></a>

1) **SingleThreadExecutor**

The **SingleThreadExecutor** is a special type of executor that has only a single thread. It is used when we need to execute tasks in sequential order. In case when a thread dies due to some error or exception at the time of executing a task, a new thread is created, and all the subsequent tasks execute in that new one.

```java
ExecutorService executor = Executors.newSingleThreadExecutor()  
```

2) **FixedThreadPool(n)**

**FixedThreadPool** is another special type of executor that is a thread pool having a fixed number of threads. By this executor, the submitted task is executed by the n thread. In case when we need to execute more tasks after submitting previous tasks, they store in the LinkedBlockingQueue until previous tasks are not completed. The n denotes the total number of thread which are supported by the underlying processor.

```java
ExecutorService executor = Executors.newFixedThreadPool(4);  
```

3) **CachedThreadPool**

The **CachedThreadPool** is a special type of thread pool that is used to execute short-lived parallel tasks. The cached thread pool doesn't have a fixed number of threads. When a new task comes at a time when all the threads are busy in executing some other tasks, a new thread creates by the pool and add to the executor. When a thread becomes free, it carries out the execution of the new tasks. Threads are terminated and removed from the cached when they remain idle for sixty seconds.

```java
ExecutorService executor = Executors.newCachedThreadPool();  
```

4) **ScheduledExecutor**

The **ScheduledExecutor** is another special type of executor which we use to run a certain task at regular intervals. It is also used when we need to delay a certain task.

```java
ScheduledExecutorService scheduledExecService = Executors.newScheduledThreadPool(1);
```

The **scheduleAtFixedRate** and **scheduleWithFixedDelay** are the two methods that are used to schedule the task in **ScheduledExecutor**. The **scheduleAtFixedRate** method executes the task with a fixed interval when the previous task ended. The **scheduleWithFixedDelay** method starts the delay count after the current task complete. The main difference between these two methods is their interpretation of the delay between successive executions of a scheduled job. Both the methods are used in the following way:

```java
scheduledExecService.scheduleAtFixedRate(Runnable command, long initialDelay, long period, TimeUnit unit)  
```

```java
scheduledExecService.scheduleWithFixedDelay(Runnable command, long initialDelay, long period, TimeUnit unit)  
```

Let's take an example to understand how executors are actually used to execute a task. We will simply create a task and try to execute it by the simple executor and ThreadPoolExecutor one by one.

**Task1.java**

```java
//creating Task1 class that implements the Runnable interface  
public class Task1 implements Runnable {  
      
    //initialize threadNo variable   
    private String threadNo;  
      
    //using constructor to set value to the threadNo variable  
    public Task1(String no){  
        this.threadNo = no;  
    }  
      
    //using run() method by overriding it  
    @Override  
    public void run() {  
        //printing thread information   
        System.out.println(Thread.currentThread().getName()+" start execution. Thread No = "+threadNo);  
          
        //calling processThread() method for processing thread  
        processThread();  
          
        //printing a statement to show the end of the thread  
        System.out.println(Thread.currentThread().getName()+" stop execution.");  
    }  
      
    //creating processThread() method to execute thread  
    private void processThread() {  
        try {  
            Thread.sleep(5000);  
        } catch (InterruptedException e) {  
            e.printStackTrace();  
        }  
    }  
      
    //overriding toString() method   
    @Override  
    public String toString(){  
        return this.threadNo;  
    }  
}  
```

**SimpleExecutor.java**

```java
//importing classes   
import java.util.concurrent.ExecutorService;  
import java.util.concurrent.Executors;  
  
//creating SimpleExecutor class  
public class SimpleExecutor {  
    //main() method start  
    public static void main(String[] args) {  
        //creating an object of ExecutorService with fixed thread pool 5  
        ExecutorService executorService = Executors.newFixedThreadPool(5);  
        for (int j = 0; j < 5; j++) {  
            //creating instance of the Task1 class and pass a value to its constructor   
            Runnable task = new Task1("" + j);  
              
            //executing task using execute() method of the executor  
            executorService.execute(task);  
          }  
        //closing executor  
        executorService.shutdown();  
          
        while (!executorService.isTerminated()) {  
        }  
        System.out.println("Finished all threads");  
    }  
}  
```

**Output:**

<a href="#" target="_blank"><img src="https://static.javatpoint.com/core/images/executor-framework-java2.png" alt="Executor Service"/></a>


Let's take an example of **ThreadPoolExecutor** to understand how it is different from the **SimpleExecutor**.

**RejectedExecutionHandlerDemo.java**

The **RejectedExecutionHandlerDemo** class is used for handling the jobs that are rejected from the worker queue. When the limit of the thread pool size reach, RejectedExecutionHandler handles those jobs that cannot fit in the worker thread. We will implement the RejectedExecutionHandler.java class in the following way:

```java
//importing RejectedExecutionHandler, and ThreadPoolExecutor classes   
import java.util.concurrent.RejectedExecutionHandler;  
import java.util.concurrent.ThreadPoolExecutor;  
  
//creating RejectedExecutionHandlerDemo class to handle rejected execution  
public class RejectedExecutionHandlerDemo implements RejectedExecutionHandler {  
  
    //defining abstract method of RejectedExecutionHandler class  
    @Override  
    public void rejectedExecution(Runnable runnableObject, ThreadPoolExecutor executorObjet) {  
        //printing the rejected thread  
        System.out.println(runnableObject.toString() + " is rejected");  
    }  
  
}  
```

**NewTask.java**

We create the NewTask.java class to create a thread that monitors the executor and prints its information at a certain time interval. There are several methods available in the ThreadPoolExecutor class that is used to get the current state of the executor, number of active threads, number of tasks, and pool size. We create the monitor thread in the following way:

```java
//importing ThreadPoolExecutor class  
import java.util.concurrent.ThreadPoolExecutor;  
  
//creating NewTask class that implements the Runnable interface  
public class NewTask implements Runnable  
{  
    private ThreadPoolExecutor exe;//creating a private variable of type ThreadPoolExecutor  
    private int delay; //creating a private variable of type integer for delay  
    private boolean run = true; //creating a private boolean variable to determine whether   
      
    //using constructor to set the value to the exe and delay variable  
    public NewTask(ThreadPoolExecutor exe, int delay)  
    {  
        this.exe = exe;  
        this.delay = delay;  
    }  
      
    //creating shutdown() method to update the value of the boolean variable run   
    public void shutdown(){  
        this.run = false;  
    }  
      
    //overriding the run() method of the Runnable interface  
    @Override  
    public void run()  
    {  
        //running task  
        while(run){  
                System.out.println(  
                    String.format("[monitor [%d/%d] Number of active threads = %d, Number of completed tasks = %d, Number of tasks = %d, Shutdown = %s, Terminated = %s",  
                        this.exe.getPoolSize(),  
                        this.exe.getCorePoolSize(),  
                        this.exe.getActiveCount(),  
                        this.exe.getCompletedTaskCount(),  
                        this.exe.getTaskCount(),  
                        this.exe.isShutdown(),  
                        this.exe.isTerminated()));  
                try {  
                    Thread.sleep(this.delay*1000);  
                } catch (InterruptedException e) {  
                    e.printStackTrace();  
                }  
        }  
              
    }  
}  
```

**ThreadPoolExecutorExample.java**

It is used to create the thread pool using the ThreadPoolExecutor.

```java
//importing classes required for implementing ThreadPoolExecutor  
import java.util.concurrent.ArrayBlockingQueue;  
import java.util.concurrent.Executors;  
import java.util.concurrent.ThreadFactory;  
import java.util.concurrent.ThreadPoolExecutor;  
import java.util.concurrent.TimeUnit;  
  
//creating ThreadPoolExecutorExample to execute task  
public class ThreadPoolExecutorExample {  
      
    //main method start  
    public static void main(String args[]) throws InterruptedException{  
          
        //creating an instance of the RejectedExecutionHandlerExample class  
        RejectedExecutionHandlerDemo rejectionHandlerObj = new RejectedExecutionHandlerDemo();  
          
        //creating an instance of the ThreadFactory class  
        ThreadFactory t1 = Executors.defaultThreadFactory();  
          
        //creating an instance of the ThreadPoolExecutor class  
        ThreadPoolExecutor exePool = new ThreadPoolExecutor(2, 4, 10, TimeUnit.SECONDS, new ArrayBlockingQueue<Runnable>(2), t1, rejectionHandlerObj);  
          
        //starting the NewTask thread  
        NewTask task = new NewTask(exePool, 3);  
        Thread th = new Thread(task);  
        th.start();  
        //submit job to the pool  
        for(int j=0; j<10; j++){  
            exePool.execute(new Task1("cmd"+j));  
        }  
          
        Thread.sleep(30000);  
        //shutting down the job pool  
        exePool.shutdown();  
          
        //shutting down the th thread  
        Thread.sleep(5000);  
        task.shutdown();  
          
    }  
}  
```

**Output:**

<a href="#" target="_blank"><img src="https://static.javatpoint.com/core/images/executor-framework-java3.png
" alt="Executor Service"/></a>

Notice the change in the number of active threads, the number of the completed task, and the number of tasks. The shutdown() method is used to finish the execution of all the submitted tasks and terminate the thread pool.


# Java ExecutorService

The Java ExecutorService is the interface which allows us to execute tasks on threads asynchronously. The Java ExecutorService interface is present in the java.util.concurrent package. The ExecutorService helps in maintaining a pool of threads and assigns them tasks. It also provides the facility to queue up tasks until there is a free thread available if the number of tasks is more than the threads available.


<a href="#" target="_blank"><img src="https://static.javatpoint.com/core/images/java-executorservice.png" alt="Executor Service"/></a>

## Methods of Java ExecutorService

| Method      |  Method      |
|-------------|--------------|
|boolean awaitTermination(long timeout, TimeUnit unit)|This method blocks the task to enter ExecutorService until all the tasks have completed after the shutdown request, or the given timeout occurs, or the current thread is interrupted, whichever happens first.|
|<T> List invokeAll(Collection<? extends Callable<T>> tasks)|This method executes the list of tasks given and returns the list of Futures which contain the results of all the tasks when completed.|
|<T> List invokeAll(Collection<? extends Callable<T>> tasks, long timeout, TimeUnit unit)|This method executes the list of tasks given and returns the list of Futures which contain the results of all the tasks when completed or the timeout expires, whichever occurs first.|
|<T> T invokeAny(Collection<? extends Callable<T>> tasks)|This method executes the list of tasks given and returns the result of one task which gets completed without throwing any exception.|
|<T> T invokeAny(Collection<? extends Callable<T>> tasks, long timeout,TimeUnit unit)|This method executes the list of tasks given and returns the result of one task which gets completed without throwing any exception before the timeout elapses.|
|boolean isShutdown()|This method returns whether the given executor is shut down or not.|
|boolean isTerminated()|This method returns true if all tasks have executed after shutdown.|
|void shutdown()|This method allows completion of previously submitted tasks to the ExecutorService and doesn?t allow any other tasks to be accepted.|
|List shutdownNow()|This method stops all the actively executing tasks, stops the execution of queued up tasks, and returns the list of tasks which are queued up.|
|<T> Future<T> submit(Callable<T> task)|This method submits a value-returning task for execution and returns the Future, which represents the pending result of the task.|
|Future<?> submit(Runnable task)|This method submits a task for execution and returns a Future representing that task. It returns null upon successful completion.|
|<T> Future<T> submit(Runnable task, T result)|This method submits a task for execution and returns a Future representing that task.|

## A simple program of Java ExecutorService

```java
public class ExecutorServiceExample {  
  
    public static void main(String[] args) {  
        ExecutorService executorService = Executors.newFixedThreadPool(10);  
        executorService.execute(new Runnable() {  
              
            @Override  
            public void run() {  
                System.out.println("ExecutorService");  
                  
            }  
        });  
        executorService.shutdown();  
    }  
  
}  
```

**OUTPUT:**

<a href="#" target="_blank"><img src="https://static.javatpoint.com/core/images/java-executorservice-output.png" alt="Executor Service"/></a>

In this program, we are creating an ExecutorService with ten threads and assigning it an anonymous runnable implementation which performs a task to print "ExecutorService" and after its task is over, we are shutting down the executor service.

## How to use Java ExecutorService

### Instantiating ExecutorService

We can use Java ExecutorService to create a single thread, a pool of threads, or a scheduled pool of threads. The Executors class provides factory methods to instantiate an ExecutorService as follows-

```java
ExecutorService executorService1 = Executors.newSingleThreadExecutor(); //Creates //a ExecutorService object having a single thread.  
```

```java
ExecutorService executorService2 = Executors.newFixedThreadPool(10);  // Creates a //ExecutorService object having a pool of 10 threads.  
```

```java
ExecutorService executorService3 = Executors.newScheduledThreadPool(10); //Creates a scheduled thread pool executor with 10 threads. In scheduled thread //pool, we can schedule tasks of the threads.  
```

## Assigning tasks to ExecutorServices

To assign a task to ExecutorService, we can use the following methods-

- execute(Runnable task)

- submit(Runnable task) / submit(Callable<T> task)

- invokeAny(Collection<? extends Callable<T>> tasks)

- invokeAll(Collection<? extends Callable<T>> tasks)

**Example of assigning a task to ExecutorService using execute() method**

The Java ExecutorService's execute() method takes in a runnable object and performs its task asynchronously. After making the call to execute method, we call the shutdown method, which blocks any other task to queue up in the executorService.

```java
public class ExecutorServiceExample {  
  
    public static void main(String[] args) {  
        ExecutorService executorService = Executors.newSingleThreadExecutor();  
        executorService.execute(new Runnable() {  
              
            @Override  
            public void run() {  
                System.out.println("ExecutorService");  
                  
            }  
        });  
        executorService.shutdown();  
    }  
}  
```

```java
OUTPUT:

ExecutorService
```

**Example of assigning a task to ExecutorService using submit()**

The submit() method takes in a runnable object and returns a Future object. This object is later on used to check the status of Runnable whether it has completed execution or not.

```java
public class ExecutorServiceExample {  
  
    public static void main(String[] args) {  
        ExecutorService executorService = Executors.newSingleThreadExecutor();  
        executorService.submit(new Runnable() {  
              
            @Override  
            public void run() {  
                System.out.println("ExecutorService");  
                  
            }  
        });  
    }  
}  
```

**Example of assigning a task to ExecutorService using invokeAny() method**

The invokeAny() method takes a collection of Callablle objects or objects of classes implementing Callable. This method returns the future object of the callable object which gets successfully executed first.

```java
public class ExecutorServiceExample {  
  
    public static void main(String[] args) throws InterruptedException, ExecutionException {  
        ExecutorService executorService = Executors.newSingleThreadExecutor();  
        Set<Callable<String>> callables = new HashSet<Callable<String>>();  
        callables.add(new Callable<String>() {  
            public String call() throws Exception {  
                return "Task 1";  
            }  
        });  
        callables.add(new Callable<String>() {  
            public String call() throws Exception {  
                return "Task 2";  
            }  
        });  
        callables.add(new Callable<String>() {  
            public String call() throws Exception {  
                return "Task 3";  
            }  
        });  
  
        String result = executorService.invokeAny(callables);  
  
        System.out.println("result = " + result);  
  
        executorService.shutdown();  
    }  
}  
```

```java
OUTPUT:

result = Task 1
```

The result stores Task 1 as the first callable object is successfully executed first.

**Example of assigning a task to ExecutorService using invokeAll() method**

The invokeAll() method takes in a Collection of Callable objects having tasks and returns a list of Future objects containing the result of all the tasks.

```java
public class ExecutorServiceExample {  
  
    public static void main(String[] args) throws InterruptedException, ExecutionException {  
        ExecutorService executorService = Executors.newSingleThreadExecutor();  
  
        Set<Callable<String>> callables = new HashSet<Callable<String>>();  
  
        callables.add(new Callable<String>() {  
            public String call() throws Exception {  
                return "Task 1";  
            }  
        });  
        callables.add(new Callable<String>() {  
            public String call() throws Exception {  
                return "Task 2";  
            }  
        });  
        callables.add(new Callable<String>() {  
            public String call() throws Exception {  
                return "Task 3";  
            }  
        });  
  
        java.util.List<Future<String>> futures = executorService.invokeAll(callables);  
  
        for(Future<String> future : futures){  
            System.out.println("future.get = " + future.get());  
        }  
  
        executorService.shutdown();  
  
    }  
}  
```
```java
Output:

future.get = Task 1
future.get = Task 3
future.get = Task 2
```

## How to shut down ExecutorService

Once we are done with our tasks given to ExecutorService, then we have to shut it down because ExecutorService performs the task on different threads. If we don't shut down the ExecutorService, the threads will keep running, and the JVM won?t shut down.

The process of shutting down can be done by the following three methods-

- shutdown() method

- shutdownNow() method

- awaitTermination() method

# Executor Framework

The Executor Framework in Java is a powerful tool for managing and controlling the execution of asynchronous tasks. Introduced in Java 5 as part of the `java.util.concurrent` package, it simplifies the creation and management of thread pools, task execution, and resource allocation. Here's an overview of its key components and usage:

### Key Components

1. **Executor Interface**
   - The base interface with a single method:
     ```java
     void execute(Runnable command);
     ```

2. **ExecutorService Interface**
   - Extends the `Executor` interface and provides methods for managing lifecycle and task submission.
   - Common methods:
     ```java
     Future<?> submit(Runnable task);
     <T> Future<T> submit(Callable<T> task);
     <T> List<Future<T>> invokeAll(Collection<? extends Callable<T>> tasks) throws InterruptedException;
     void shutdown();
     List<Runnable> shutdownNow();
     ```

3. **ScheduledExecutorService Interface**
   - Extends `ExecutorService` to support scheduling tasks for future execution.
   - Common methods:
     ```java
     ScheduledFuture<?> schedule(Runnable command, long delay, TimeUnit unit);
     <V> ScheduledFuture<V> schedule(Callable<V> callable, long delay, TimeUnit unit);
     ScheduledFuture<?> scheduleAtFixedRate(Runnable command, long initialDelay, long period, TimeUnit unit);
     ScheduledFuture<?> scheduleWithFixedDelay(Runnable command, long initialDelay, long delay, TimeUnit unit);
     ```

4. **ThreadPoolExecutor Class**
   - Provides a flexible thread pool implementation.
   - Key constructors and methods:
     ```java
     ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit,
                        BlockingQueue<Runnable> workQueue, ThreadFactory threadFactory, RejectedExecutionHandler handler);
     ```

5. **ScheduledThreadPoolExecutor Class**
   - A concrete implementation of `ScheduledExecutorService`.
   - Useful for recurring tasks.

6. **Executors Utility Class**
   - Factory methods for creating different types of `ExecutorService` instances:
     ```java
     ExecutorService newFixedThreadPool(int nThreads);
     ExecutorService newCachedThreadPool();
     ScheduledExecutorService newScheduledThreadPool(int corePoolSize);
     ExecutorService newSingleThreadExecutor();
     ```

### Basic Usage Example

```java
import java.util.concurrent.*;

public class ExecutorFrameworkExample {
    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(5);

        for (int i = 0; i < 10; i++) {
            executorService.execute(new Task());
        }

        executorService.shutdown();
    }
}

class Task implements Runnable {
    @Override
    public void run() {
        System.out.println("Executing task by " + Thread.currentThread().getName());
    }
}
```

### Scheduled Task Example

```java
import java.util.concurrent.*;

public class ScheduledExecutorExample {
    public static void main(String[] args) {
        ScheduledExecutorService scheduledExecutorService = Executors.newScheduledThreadPool(2);

        Runnable task = () -> System.out.println("Executing task at " + System.currentTimeMillis());

        scheduledExecutorService.scheduleAtFixedRate(task, 0, 1, TimeUnit.SECONDS);
    }
}
```

### Benefits
- **Simplified Thread Management**: Reduces the complexity of managing thread lifecycle and synchronization.
- **Resource Optimization**: Reuses a pool of threads, reducing the overhead of thread creation and destruction.
- **Task Scheduling**: Provides mechanisms to schedule tasks with delays or at fixed rates.

### Conclusion
The Executor Framework is a robust and flexible way to handle asynchronous task execution in Java, promoting better resource management, ease of use, and scalability.

# Executors Class

The `Executors` class in Java provides factory methods for creating different types of `Executor`, `ExecutorService`, `ScheduledExecutorService`, and `ThreadFactory` instances. These utility methods simplify the creation of thread pools and other related services. Here's an overview of the key methods provided by the `Executors` class:

### Factory Methods for ExecutorService

1. **newFixedThreadPool(int nThreads)**
   - Creates a thread pool with a fixed number of threads.
   - Example:
     ```java
     ExecutorService executor = Executors.newFixedThreadPool(10);
     ```

2. **newWorkStealingPool(int parallelism)**
   - Creates a work-stealing thread pool using all available processors as its target parallelism level.
   - Example:
     ```java
     ExecutorService executor = Executors.newWorkStealingPool();
     ```

3. **newCachedThreadPool()**
   - Creates a thread pool that creates new threads as needed but will reuse previously constructed threads when they are available.
   - Example:
     ```java
     ExecutorService executor = Executors.newCachedThreadPool();
     ```

4. **newSingleThreadExecutor()**
   - Creates an executor that uses a single worker thread operating off an unbounded queue.
   - Example:
     ```java
     ExecutorService executor = Executors.newSingleThreadExecutor();
     ```

### Factory Methods for ScheduledExecutorService

1. **newScheduledThreadPool(int corePoolSize)**
   - Creates a thread pool that can schedule commands to run after a given delay or to execute periodically.
   - Example:
     ```java
     ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(5);
     ```

2. **newSingleThreadScheduledExecutor()**
   - Creates a single-threaded executor that can schedule commands to run after a given delay or to execute periodically.
   - Example:
     ```java
     ScheduledExecutorService scheduler = Executors.newSingleThreadScheduledExecutor();
     ```

### Factory Methods for ThreadFactory

1. **defaultThreadFactory()**
   - Returns a default thread factory used to create new threads.
   - Example:
     ```java
     ThreadFactory threadFactory = Executors.defaultThreadFactory();
     ```

2. **privilegedThreadFactory()**
   - Returns a thread factory used to create new threads with the same permissions as the current thread.
   - Example:
     ```java
     ThreadFactory threadFactory = Executors.privilegedThreadFactory();
     ```

### Example Usage

#### Fixed Thread Pool

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class FixedThreadPoolExample {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(5);

        for (int i = 0; i < 10; i++) {
            executor.execute(() -> {
                System.out.println("Executing task by " + Thread.currentThread().getName());
            });
        }

        executor.shutdown();
    }
}
```

#### Scheduled Thread Pool

```java
import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class ScheduledThreadPoolExample {
    public static void main(String[] args) {
        ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(2);

        Runnable task = () -> System.out.println("Executing task at " + System.currentTimeMillis());

        scheduler.scheduleAtFixedRate(task, 0, 1, TimeUnit.SECONDS);
    }
}
```

### Benefits

- **Simplicity**: Provides a straightforward way to create and manage thread pools.
- **Reusability**: Reuses previously created threads, reducing overhead.
- **Flexibility**: Offers different types of executors for various use cases, such as fixed thread pools, cached thread pools, and scheduled thread pools.
- **Performance**: Optimizes resource usage and improves the performance of multi-threaded applications.

### Conclusion

The `Executors` class is a convenient and powerful utility for creating and managing different types of executor services in Java. It helps in simplifying the management of thread pools, making it easier to implement concurrent programming.

# ExecutorService

`ExecutorService` is a subinterface of `Executor` in Java, providing a higher-level replacement for working with threads directly. It offers lifecycle management methods and the ability to submit tasks that return results, handle exceptions, and control the shutdown process. Here’s a comprehensive overview of `ExecutorService`:

### Key Methods of ExecutorService

#### Task Submission

1. **`void execute(Runnable command)`**
   - Executes a given task at some time in the future.

2. **`Future<?> submit(Runnable task)`**
   - Submits a `Runnable` task for execution and returns a `Future` representing that task.
   - Example:
     ```java
     Future<?> future = executorService.submit(new RunnableTask());
     ```

3. **`<T> Future<T> submit(Callable<T> task)`**
   - Submits a `Callable` task for execution and returns a `Future` representing the pending result of the task.
   - Example:
     ```java
     Future<Integer> future = executorService.submit(new CallableTask());
     ```

4. **`<T> List<Future<T>> invokeAll(Collection<? extends Callable<T>> tasks)`**
   - Executes the given tasks, returning a list of `Future` objects representing the tasks.
   - Example:
     ```java
     List<CallableTask> tasks = Arrays.asList(new CallableTask(), new CallableTask());
     List<Future<Integer>> futures = executorService.invokeAll(tasks);
     ```

5. **`<T> T invokeAny(Collection<? extends Callable<T>> tasks)`**
   - Executes the given tasks, returning the result of one that has completed successfully (i.e., without throwing an exception).
   - Example:
     ```java
     List<CallableTask> tasks = Arrays.asList(new CallableTask(), new CallableTask());
     Integer result = executorService.invokeAny(tasks);
     ```

#### Lifecycle Management

1. **`void shutdown()`**
   - Initiates an orderly shutdown in which previously submitted tasks are executed, but no new tasks will be accepted.
   - Example:
     ```java
     executorService.shutdown();
     ```

2. **`List<Runnable> shutdownNow()`**
   - Attempts to stop all actively executing tasks, halts the processing of waiting tasks, and returns a list of the tasks that were waiting to be executed.
   - Example:
     ```java
     List<Runnable> pendingTasks = executorService.shutdownNow();
     ```

3. **`boolean isShutdown()`**
   - Returns `true` if this executor has been shut down.
   - Example:
     ```java
     boolean isShutdown = executorService.isShutdown();
     ```

4. **`boolean isTerminated()`**
   - Returns `true` if all tasks have completed following shutdown.
   - Example:
     ```java
     boolean isTerminated = executorService.isTerminated();
     ```

5. **`boolean awaitTermination(long timeout, TimeUnit unit)`**
   - Blocks until all tasks have completed execution after a shutdown request, or the timeout occurs, or the current thread is interrupted, whichever happens first.
   - Example:
     ```java
     try {
         boolean terminated = executorService.awaitTermination(5, TimeUnit.MINUTES);
     } catch (InterruptedException e) {
         e.printStackTrace();
     }
     ```

### Example Usage

#### Basic Usage

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class ExecutorServiceExample {
    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(5);

        for (int i = 0; i < 10; i++) {
            executorService.execute(new RunnableTask());
        }

        executorService.shutdown();
    }
}

class RunnableTask implements Runnable {
    @Override
    public void run() {
        System.out.println("Executing task by " + Thread.currentThread().getName());
    }
}
```

#### Callable Example

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class CallableExample {
    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        Future<Integer> future = executorService.submit(new CallableTask());

        try {
            Integer result = future.get();
            System.out.println("Result: " + result);
        } catch (Exception e) {
            e.printStackTrace();
        }

        executorService.shutdown();
    }
}

class CallableTask implements Callable<Integer> {
    @Override
    public Integer call() throws Exception {
        return 42;
    }
}
```

### Benefits

- **Concurrency**: Simplifies the development of concurrent applications by abstracting low-level thread management.
- **Resource Management**: Optimizes resource usage through reusable thread pools.
- **Error Handling**: Provides mechanisms for handling exceptions in asynchronous tasks.
- **Scalability**: Makes it easier to scale applications by managing a pool of threads.

### Conclusion

`ExecutorService` is a versatile and powerful tool in Java for managing the execution of asynchronous tasks. By providing a high-level API for submitting tasks and managing their execution, it allows developers to focus on the logic of their applications rather than the complexities of thread management.

# List all the methods of Executor Service

The `ExecutorService` interface in Java provides various methods to manage and control the execution of tasks. Here's a comprehensive list of the methods available in the `ExecutorService` interface:

### Task Submission Methods

1. **`void execute(Runnable command)`**
   - Executes the given task at some time in the future.

2. **`Future<?> submit(Runnable task)`**
   - Submits a `Runnable` task for execution and returns a `Future` representing that task.

3. **`<T> Future<T> submit(Callable<T> task)`**
   - Submits a `Callable` task for execution and returns a `Future` representing the pending result of the task.

4. **`<T> Future<T> submit(Runnable task, T result)`**
   - Submits a `Runnable` task for execution and returns a `Future` representing that task, with a specified result upon completion.

5. **`<T> List<Future<T>> invokeAll(Collection<? extends Callable<T>> tasks)`**
   - Executes the given tasks, returning a list of `Future` objects representing the tasks.

6. **`<T> List<Future<T>> invokeAll(Collection<? extends Callable<T>> tasks, long timeout, TimeUnit unit)`**
   - Executes the given tasks, returning a list of `Future` objects representing the tasks, within the given timeout.

7. **`<T> T invokeAny(Collection<? extends Callable<T>> tasks)`**
   - Executes the given tasks, returning the result of one that has completed successfully (i.e., without throwing an exception).

8. **`<T> T invokeAny(Collection<? extends Callable<T>> tasks, long timeout, TimeUnit unit)`**
   - Executes the given tasks, returning the result of one that has completed successfully (i.e., without throwing an exception), within the given timeout.

### Lifecycle Management Methods

1. **`void shutdown()`**
   - Initiates an orderly shutdown in which previously submitted tasks are executed, but no new tasks will be accepted.

2. **`List<Runnable> shutdownNow()`**
   - Attempts to stop all actively executing tasks, halts the processing of waiting tasks, and returns a list of the tasks that were waiting to be executed.

3. **`boolean isShutdown()`**
   - Returns `true` if this executor has been shut down.

4. **`boolean isTerminated()`**
   - Returns `true` if all tasks have completed following shut down.

5. **`boolean awaitTermination(long timeout, TimeUnit unit)`**
   - Blocks until all tasks have completed execution after a shutdown request, or the timeout occurs, or the current thread is interrupted, whichever happens first.

### Example Usage

Here’s an example that demonstrates some of these methods:

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import java.util.concurrent.TimeUnit;

public class ExecutorServiceExample {
    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // Using submit(Runnable task)
        Future<?> future1 = executorService.submit(new RunnableTask());

        // Using submit(Callable task)
        Future<Integer> future2 = executorService.submit(new CallableTask());

        // Using invokeAll
        List<Callable<Integer>> tasks = Arrays.asList(new CallableTask(), new CallableTask());
        try {
            List<Future<Integer>> futures = executorService.invokeAll(tasks);
        } catch (InterruptedException e) {
            e.printStackTrace();
        }

        // Using invokeAny
        try {
            Integer result = executorService.invokeAny(tasks);
        } catch (Exception e) {
            e.printStackTrace();
        }

        // Shutting down the executor service
        executorService.shutdown();
        try {
            if (!executorService.awaitTermination(5, TimeUnit.SECONDS)) {
                executorService.shutdownNow();
            }
        } catch (InterruptedException e) {
            executorService.shutdownNow();
        }
    }
}

class RunnableTask implements Runnable {
    @Override
    public void run() {
        System.out.println("Executing task by " + Thread.currentThread().getName());
    }
}

class CallableTask implements Callable<Integer> {
    @Override
    public Integer call() throws Exception {
        return 42;
    }
}
```

### Conclusion

The `ExecutorService` interface provides a rich set of methods for task submission, lifecycle management, and controlling the execution of asynchronous tasks. This makes it a powerful tool for building concurrent applications in Java.

# How many we can create a thread.

In Java, there are several ways to create and manage threads. Here are the main methods:

### 1. Extending the `Thread` Class

You can create a new thread by extending the `Thread` class and overriding its `run` method.

```java
public class MyThread extends Thread {
    public void run() {
        System.out.println("Thread is running...");
    }

    public static void main(String[] args) {
        MyThread thread = new MyThread();
        thread.start();  // Start the new thread
    }
}
```

### 2. Implementing the `Runnable` Interface

You can create a thread by implementing the `Runnable` interface and passing an instance of the implementing class to a `Thread` object.

```java
public class MyRunnable implements Runnable {
    public void run() {
        System.out.println("Thread is running...");
    }

    public static void main(String[] args) {
        MyRunnable myRunnable = new MyRunnable();
        Thread thread = new Thread(myRunnable);
        thread.start();  // Start the new thread
    }
}
```

### 3. Implementing the `Callable` Interface

The `Callable` interface is similar to `Runnable`, but it can return a result and throw a checked exception. You can submit a `Callable` task to an `ExecutorService`.

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class MyCallable implements Callable<Integer> {
    public Integer call() throws Exception {
        return 42;  // Return a result
    }

    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(1);
        MyCallable myCallable = new MyCallable();
        Future<Integer> future = executorService.submit(myCallable);

        try {
            Integer result = future.get();  // Get the result
            System.out.println("Result: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }

        executorService.shutdown();  // Shut down the executor service
    }
}
```

### 4. Using `ExecutorService`

The `ExecutorService` provides a higher-level API for managing threads. You can create different types of thread pools and submit tasks to them.

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class ExecutorServiceExample {
    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(5);

        for (int i = 0; i < 10; i++) {
            executorService.execute(() -> System.out.println("Thread is running..."));
        }

        executorService.shutdown();
    }
}
```

### 5. Using `ForkJoinPool`

The `ForkJoinPool` is designed for work that can be broken into smaller pieces recursively. It is useful for parallel processing.

```java
import java.util.concurrent.RecursiveTask;
import java.util.concurrent.ForkJoinPool;

public class ForkJoinExample extends RecursiveTask<Integer> {
    private static final int THRESHOLD = 10;
    private int[] array;
    private int start, end;

    public ForkJoinExample(int[] array, int start, int end) {
        this.array = array;
        this.start = start;
        this.end = end;
    }

    protected Integer compute() {
        if (end - start <= THRESHOLD) {
            int sum = 0;
            for (int i = start; i < end; i++) {
                sum += array[i];
            }
            return sum;
        } else {
            int middle = (start + end) / 2;
            ForkJoinExample leftTask = new ForkJoinExample(array, start, middle);
            ForkJoinExample rightTask = new ForkJoinExample(array, middle, end);

            leftTask.fork();
            int rightResult = rightTask.compute();
            int leftResult = leftTask.join();

            return leftResult + rightResult;
        }
    }

    public static void main(String[] args) {
        int[] array = new int[100];
        for (int i = 0; i < array.length; i++) {
            array[i] = i + 1;
        }

        ForkJoinPool forkJoinPool = new ForkJoinPool();
        ForkJoinExample task = new ForkJoinExample(array, 0, array.length);

        int result = forkJoinPool.invoke(task);
        System.out.println("Sum: " + result);
    }
}
```

### Summary

You can create and manage threads in Java using various methods, including extending the `Thread` class, implementing the `Runnable` or `Callable` interfaces, using `ExecutorService` for thread pool management, and employing `ForkJoinPool` for parallel processing tasks. Each method has its advantages and use cases depending on the complexity and requirements of your concurrent application.

# All the examples where as ExecutorService is used to write a logic for multithreading or asynchronous calling

Certainly! Here are examples of using `ExecutorService` for different multithreading and asynchronous calling scenarios:

### Example 1: Simple Task Execution with ExecutorService

This example demonstrates how to submit tasks to an `ExecutorService` for execution.

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class SimpleTaskExecution {
    public static void main(String[] args) {
        // Create a fixed thread pool with 3 threads
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // Submit 5 tasks to the executor service
        for (int i = 0; i < 5; i++) {
            executorService.execute(new RunnableTask());
        }

        // Shut down the executor service
        executorService.shutdown();
    }
}

class RunnableTask implements Runnable {
    @Override
    public void run() {
        System.out.println("Executing task by " + Thread.currentThread().getName());
    }
}
```

### Example 2: Callable and Future Example

This example shows how to use `Callable` to submit tasks that return results.

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class CallableExample {
    public static void main(String[] args) {
        // Create a fixed thread pool with 3 threads
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // Submit a Callable task
        Future<Integer> future = executorService.submit(new CallableTask());

        try {
            // Get the result of the Callable task
            Integer result = future.get();
            System.out.println("Result: " + result);
        } catch (Exception e) {
            e.printStackTrace();
        }

        // Shut down the executor service
        executorService.shutdown();
    }
}

class CallableTask implements Callable<Integer> {
    @Override
    public Integer call() throws Exception {
        return 42;  // Return a result
    }
}
```

### Example 3: Scheduled Executor Service

This example demonstrates how to schedule tasks to run at fixed intervals.

```java
import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class ScheduledExecutorExample {
    public static void main(String[] args) {
        // Create a scheduled thread pool with 2 threads
        ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(2);

        // Schedule a task to run at a fixed rate
        scheduler.scheduleAtFixedRate(new RunnableTask(), 0, 1, TimeUnit.SECONDS);
    }
}

class RunnableTask implements Runnable {
    @Override
    public void run() {
        System.out.println("Executing task at " + System.currentTimeMillis() + " by " + Thread.currentThread().getName());
    }
}
```

### Example 4: Using invokeAll to Execute Multiple Callables

This example shows how to execute multiple `Callable` tasks and wait for all of them to complete.

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class InvokeAllExample {
    public static void main(String[] args) {
        // Create a fixed thread pool with 3 threads
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // Create a list of Callable tasks
        List<Callable<Integer>> tasks = Arrays.asList(
            new CallableTask(),
            new CallableTask(),
            new CallableTask()
        );

        try {
            // Submit all tasks to the executor service
            List<Future<Integer>> futures = executorService.invokeAll(tasks);

            // Get the results of the tasks
            for (Future<Integer> future : futures) {
                System.out.println("Result: " + future.get());
            }
        } catch (Exception e) {
            e.printStackTrace();
        }

        // Shut down the executor service
        executorService.shutdown();
    }
}

class CallableTask implements Callable<Integer> {
    @Override
    public Integer call() throws Exception {
        return 42;  // Return a result
    }
}
```

### Example 5: Using invokeAny to Execute Multiple Callables

This example demonstrates how to execute multiple `Callable` tasks and get the result of the first one that completes successfully.

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class InvokeAnyExample {
    public static void main(String[] args) {
        // Create a fixed thread pool with 3 threads
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // Create a list of Callable tasks
        List<Callable<Integer>> tasks = Arrays.asList(
            new CallableTask(),
            new CallableTask(),
            new CallableTask()
        );

        try {
            // Submit all tasks to the executor service and get the result of the first one that completes
            Integer result = executorService.invokeAny(tasks);
            System.out.println("Result: " + result);
        } catch (Exception e) {
            e.printStackTrace();
        }

        // Shut down the executor service
        executorService.shutdown();
    }
}

class CallableTask implements Callable<Integer> {
    @Override
    public Integer call() throws Exception {
        return 42;  // Return a result
    }
}
```

### Example 6: Using shutdown and shutdownNow

This example demonstrates how to properly shut down an `ExecutorService`.

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class ShutdownExample {
    public static void main(String[] args) {
        // Create a fixed thread pool with 3 threads
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        // Submit tasks to the executor service
        for (int i = 0; i < 5; i++) {
            executorService.execute(new RunnableTask());
        }

        // Initiate an orderly shutdown
        executorService.shutdown();

        try {
            // Wait for existing tasks to complete
            if (!executorService.awaitTermination(60, TimeUnit.SECONDS)) {
                // Force shutdown if tasks don't complete in time
                executorService.shutdownNow();
            }
        } catch (InterruptedException e) {
            executorService.shutdownNow();
        }
    }
}

class RunnableTask implements Runnable {
    @Override
    public void run() {
        try {
            // Simulate long-running task
            Thread.sleep(2000);
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
        System.out.println("Executing task by " + Thread.currentThread().getName());
    }
}
```

### Example 7: Parallel Processing with ForkJoinPool

This example shows how to use `ForkJoinPool` for parallel processing tasks.

```java
import java.util.concurrent.RecursiveTask;
import java.util.concurrent.ForkJoinPool;

public class ForkJoinExample extends RecursiveTask<Integer> {
    private static final int THRESHOLD = 10;
    private int[] array;
    private int start, end;

    public ForkJoinExample(int[] array, int start, int end) {
        this.array = array;
        this.start = start;
        this.end = end;
    }

    @Override
    protected Integer compute() {
        if (end - start <= THRESHOLD) {
            int sum = 0;
            for (int i = start; i < end; i++) {
                sum += array[i];
            }
            return sum;
        } else {
            int middle = (start + end) / 2;
            ForkJoinExample leftTask = new ForkJoinExample(array, start, middle);
            ForkJoinExample rightTask = new ForkJoinExample(array, middle, end);

            leftTask.fork();
            int rightResult = rightTask.compute();
            int leftResult = leftTask.join();

            return leftResult + rightResult;
        }
    }

    public static void main(String[] args) {
        int[] array = new int[100];
        for (int i = 0; i < array.length; i++) {
            array[i] = i + 1;
        }

        ForkJoinPool forkJoinPool = new ForkJoinPool();
        ForkJoinExample task = new ForkJoinExample(array, 0, array.length);

        int result = forkJoinPool.invoke(task);
        System.out.println("Sum: " + result);
    }
}
```

### Conclusion

The `ExecutorService` interface provides a powerful and flexible way to manage and control thread execution in Java. By using various methods such as `submit`, `invokeAll`, `invokeAny`, and scheduled tasks, you can easily implement multithreading and asynchronous calling in your applications. Proper shutdown and resource management are also crucial to ensure your application runs smoothly.

# ExecutorService used in RestAPI Example

Sure! Below is an example of how to use `ExecutorService` in a REST API to handle asynchronous processing. This example uses Spring Boot to create a simple REST API.

### Setting Up the Project

First, you need to set up a Spring Boot project. You can do this by using Spring Initializr (https://start.spring.io/) or by manually setting up the project with the necessary dependencies.

For this example, we'll need the following dependencies:
- Spring Web
- Spring Boot Starter

### Creating the REST API

#### 1. Create a Spring Boot Application

Create a main application class to start the Spring Boot application.

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

#### 2. Create a Controller

Create a REST controller to handle the HTTP requests.

```java
package com.example.demo.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import com.example.demo.service.AsyncService;

import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

@RestController
@RequestMapping("/api")
public class ApiController {

    @Autowired
    private AsyncService asyncService;

    @GetMapping("/process")
    public ResponseEntity<String> process() {
        CompletableFuture<String> future = asyncService.processAsync();

        try {
            // Wait for the result and return the response
            String result = future.get();
            return ResponseEntity.ok(result);
        } catch (InterruptedException | ExecutionException e) {
            return ResponseEntity.status(500).body("Error processing request");
        }
    }
}
```

#### 3. Create a Service for Asynchronous Processing

Create a service class to handle the asynchronous task. This service will use `ExecutorService` to run the task asynchronously.

```java
package com.example.demo.service;

import org.springframework.stereotype.Service;

import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

@Service
public class AsyncService {

    private final ExecutorService executorService = Executors.newFixedThreadPool(3);

    public CompletableFuture<String> processAsync() {
        return CompletableFuture.supplyAsync(() -> {
            // Simulate a long-running task
            try {
                Thread.sleep(2000);  // Simulate delay
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
                return "Task interrupted";
            }
            return "Task completed";
        }, executorService);
    }
}
```

### Explanation

- **Controller (`ApiController`)**: This class handles the incoming HTTP GET request to `/api/process`. It calls the `processAsync` method of the `AsyncService` class to process the task asynchronously. The result of the asynchronous task is returned in the HTTP response.

- **Service (`AsyncService`)**: This class defines the `processAsync` method, which submits a task to the `ExecutorService`. The task simulates a long-running operation using `Thread.sleep(2000)`. The `CompletableFuture.supplyAsync` method is used to run the task asynchronously.

### Running the Application

To run the application, use the following command:

```bash
mvn spring-boot:run
```

Or run the `DemoApplication` class from your IDE.

### Testing the API

You can test the API using a tool like `curl` or Postman.

```bash
curl http://localhost:8080/api/process
```

The response should be:

```json
"Task completed"
```

And if you refresh quickly, you might see:

```json
"Task interrupted"
```

### Conclusion

This example demonstrates how to use `ExecutorService` to handle asynchronous processing in a Spring Boot REST API. By offloading the task processing to an executor service, you can keep your API responsive and handle long-running tasks efficiently.

# SpringBoot rest api example to use ExecutorService not a CompletableFuture

Sure! Below is an example of how to use `ExecutorService` directly in a Spring Boot REST API for asynchronous processing without using `CompletableFuture`.

### Setting Up the Project

First, set up a Spring Boot project using Spring Initializr (https://start.spring.io/) with the following dependencies:
- Spring Web
- Spring Boot Starter

### Creating the REST API

#### 1. Create the Spring Boot Application

Create the main application class to start the Spring Boot application.

```java
package com.example.demo;

import org.springframework.boot.SpringApplication;
import org.springframework.boot.autoconfigure.SpringBootApplication;

@SpringBootApplication
public class DemoApplication {
    public static void main(String[] args) {
        SpringApplication.run(DemoApplication.class, args);
    }
}
```

#### 2. Create a Controller

Create a REST controller to handle the HTTP requests.

```java
package com.example.demo.controller;

import org.springframework.beans.factory.annotation.Autowired;
import org.springframework.http.ResponseEntity;
import org.springframework.web.bind.annotation.GetMapping;
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import com.example.demo.service.AsyncService;

import java.util.concurrent.ExecutionException;
import java.util.concurrent.Future;

@RestController
@RequestMapping("/api")
public class ApiController {

    @Autowired
    private AsyncService asyncService;

    @GetMapping("/process")
    public ResponseEntity<String> process() {
        Future<String> future = asyncService.processAsync();

        try {
            // Wait for the result and return the response
            String result = future.get();
            return ResponseEntity.ok(result);
        } catch (InterruptedException | ExecutionException e) {
            return ResponseEntity.status(500).body("Error processing request");
        }
    }
}
```

#### 3. Create a Service for Asynchronous Processing

Create a service class to handle the asynchronous task. This service will use `ExecutorService` to run the task asynchronously.

```java
package com.example.demo.service;

import org.springframework.stereotype.Service;

import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

@Service
public class AsyncService {

    private final ExecutorService executorService = Executors.newFixedThreadPool(3);

    public Future<String> processAsync() {
        return executorService.submit(new Callable<String>() {
            @Override
            public String call() throws Exception {
                // Simulate a long-running task
                try {
                    Thread.sleep(2000);  // Simulate delay
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                    return "Task interrupted";
                }
                return "Task completed";
            }
        });
    }
}
```

### Explanation

- **Controller (`ApiController`)**: This class handles the incoming HTTP GET request to `/api/process`. It calls the `processAsync` method of the `AsyncService` class to process the task asynchronously. The result of the asynchronous task is returned in the HTTP response.

- **Service (`AsyncService`)**: This class defines the `processAsync` method, which submits a task to the `ExecutorService` using `submit`. The task simulates a long-running operation using `Thread.sleep(2000)`. The `submit` method returns a `Future` object which can be used to get the result of the asynchronous task.

### Running the Application

To run the application, use the following command:

```bash
mvn spring-boot:run
```

Or run the `DemoApplication` class from your IDE.

### Testing the API

You can test the API using a tool like `curl` or Postman.

```bash
curl http://localhost:8080/api/process
```

The response should be:

```json
"Task completed"
```

### Conclusion

This example demonstrates how to use `ExecutorService` to handle asynchronous processing in a Spring Boot REST API without using `CompletableFuture`. By offloading the task processing to an executor service, you can keep your API responsive and handle long-running tasks efficiently.

# ExecutorService used in stream api

Using `ExecutorService` with Java Streams API can be useful for parallel processing of tasks. Below, I'll show you how to integrate `ExecutorService` with Java Streams to perform parallel operations.

### Example: Using ExecutorService with Streams

In this example, we'll create a scenario where we use `ExecutorService` to process a list of items in parallel using Java Streams. We'll simulate a task that processes each item in the list asynchronously.

#### 1. Setup

Make sure you have the necessary Java setup. This example does not depend on any external libraries.

#### 2. Create the Main Application

Here's how you can use `ExecutorService` to parallelize tasks using Java Streams:

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import java.util.stream.Collectors;

public class ExecutorServiceWithStreams {

    public static void main(String[] args) {
        // Create a list of items to process
        List<Integer> items = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        // Create an ExecutorService
        ExecutorService executorService = Executors.newFixedThreadPool(4);

        try {
            // Use streams to process items asynchronously
            List<Future<String>> futures = items.stream()
                .map(item -> executorService.submit(new ProcessingTask(item)))
                .collect(Collectors.toList());

            // Retrieve and print the results
            for (Future<String> future : futures) {
                try {
                    String result = future.get();
                    System.out.println(result);
                } catch (InterruptedException | ExecutionException e) {
                    e.printStackTrace();
                }
            }
        } finally {
            // Shutdown the ExecutorService
            executorService.shutdown();
        }
    }
}

class ProcessingTask implements Callable<String> {
    private final int item;

    public ProcessingTask(int item) {
        this.item = item;
    }

    @Override
    public String call() throws Exception {
        // Simulate a processing task with delay
        Thread.sleep(1000);
        return "Processed item: " + item + " by " + Thread.currentThread().getName();
    }
}
```

### Explanation

1. **ExecutorService Creation**:
   - We create an `ExecutorService` with a fixed thread pool of size 4. This allows us to process up to 4 tasks concurrently.

2. **Processing Task Submission**:
   - We use the `Stream` API to map each item to a `Callable` task (`ProcessingTask`) and submit it to the `ExecutorService`.
   - `executorService.submit(new ProcessingTask(item))` returns a `Future` object which represents the result of the asynchronous computation.

3. **Collecting Results**:
   - We collect the `Future` objects into a `List` using `Collectors.toList()`.
   - We then iterate over the list of `Future` objects and call `future.get()` to retrieve the results. This will block until the result is available.

4. **Shutting Down ExecutorService**:
   - Finally, we call `executorService.shutdown()` to gracefully shut down the executor service after all tasks are completed.

### Benefits

- **Parallelism**: Using `ExecutorService` allows you to process tasks in parallel, improving performance for I/O-bound or CPU-bound operations.
- **Separation of Concerns**: The `Callable` tasks encapsulate the processing logic, making the code more modular and easier to maintain.

### Conclusion

This example demonstrates how to integrate `ExecutorService` with Java Streams API for parallel processing. By submitting tasks to the executor service and using streams to handle them, you can efficiently process large amounts of data asynchronously.

# ExecutorService in Kafka Stream API

Using `ExecutorService` with Kafka Streams API can help manage parallel processing and improve performance, especially when dealing with tasks that need to be executed concurrently.

Here's an example of how to integrate `ExecutorService` with Kafka Streams API. This example demonstrates how to use `ExecutorService` to process records from a Kafka topic asynchronously.

### Setup

Ensure you have Kafka Streams and Kafka dependencies in your Maven or Gradle configuration. For Maven, you would include:

```xml
<dependency>
    <groupId>org.apache.kafka</groupId>
    <artifactId>kafka-streams</artifactId>
    <version>3.4.0</version>
</dependency>
```

### Example: Using ExecutorService with Kafka Streams

#### 1. Create a Kafka Streams Application

Let's create a simple Kafka Streams application that processes records asynchronously using `ExecutorService`.

```java
import org.apache.kafka.common.serialization.Serdes;
import org.apache.kafka.streams.KafkaStreams;
import org.apache.kafka.streams.StreamsBuilder;
import org.apache.kafka.streams.StreamsConfig;
import org.apache.kafka.streams.kstream.KStream;
import org.apache.kafka.streams.kstream.Produced;
import org.apache.kafka.streams.kstream.ValueMapper;
import org.apache.kafka.streams.kstream.Materialized;
import org.apache.kafka.streams.kstream.Consumed;
import org.apache.kafka.streams.state.Stores;
import org.apache.kafka.streams.processor.ProcessorContext;
import org.apache.kafka.streams.processor.ProcessorSupplier;
import org.apache.kafka.streams.processor.Processor;
import org.apache.kafka.streams.processor.PunctuationType;
import org.apache.kafka.streams.processor.Punctuator;

import java.util.Properties;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class KafkaStreamsWithExecutorService {

    public static void main(String[] args) {
        // Define Kafka Streams configuration
        Properties props = new Properties();
        props.put(StreamsConfig.APPLICATION_ID_CONFIG, "kafka-streams-example");
        props.put(StreamsConfig.BOOTSTRAP_SERVERS_CONFIG, "localhost:9092");
        props.put(StreamsConfig.DEFAULT_KEY_SERDE_CLASS_CONFIG, Serdes.String().getClass().getName());
        props.put(StreamsConfig.DEFAULT_VALUE_SERDE_CLASS_CONFIG, Serdes.String().getClass().getName());

        // Create a Kafka Streams builder
        StreamsBuilder builder = new StreamsBuilder();

        // Define the input topic
        KStream<String, String> inputStream = builder.stream("input-topic");

        // Create an ExecutorService
        ExecutorService executorService = Executors.newFixedThreadPool(4);

        // Process records asynchronously using ExecutorService
        inputStream.foreach((key, value) -> {
            executorService.submit(() -> processRecord(key, value));
        });

        // Create a Kafka Streams instance and start processing
        KafkaStreams streams = new KafkaStreams(builder.build(), props);
        streams.start();

        // Add a shutdown hook to stop the streams and executor service
        Runtime.getRuntime().addShutdownHook(new Thread(() -> {
            streams.close(Duration.ofSeconds(10));
            executorService.shutdown();
            try {
                if (!executorService.awaitTermination(60, TimeUnit.SECONDS)) {
                    executorService.shutdownNow();
                }
            } catch (InterruptedException e) {
                executorService.shutdownNow();
            }
        }));
    }

    private static void processRecord(String key, String value) {
        // Simulate record processing
        System.out.printf("Processing record with key: %s, value: %s by %s%n", key, value, Thread.currentThread().getName());
        try {
            Thread.sleep(1000);  // Simulate delay
        } catch (InterruptedException e) {
            Thread.currentThread().interrupt();
        }
    }
}
```

### Explanation

1. **Kafka Streams Configuration**:
   - Define Kafka Streams properties including application ID and bootstrap servers.

2. **Create a StreamsBuilder**:
   - Create a `StreamsBuilder` to define the stream processing topology.

3. **Define the Input Topic**:
   - Create a `KStream` from the input topic.

4. **Create an ExecutorService**:
   - Instantiate an `ExecutorService` with a fixed thread pool to handle asynchronous processing.

5. **Process Records Asynchronously**:
   - Use the `foreach` method to submit each record processing task to the executor service.

6. **Start Kafka Streams**:
   - Create a `KafkaStreams` instance with the builder and properties, and start processing.

7. **Shutdown Hook**:
   - Add a shutdown hook to close the Kafka Streams instance and shutdown the executor service gracefully.

### Benefits

- **Parallel Processing**: By using `ExecutorService`, you can handle record processing in parallel, which can improve throughput and reduce latency.
- **Separation of Concerns**: Keeps the Kafka Streams processing logic separate from the record processing logic, making the code more modular and maintainable.

### Conclusion

This example demonstrates how to integrate `ExecutorService` with Kafka Streams API to perform asynchronous processing of records. This setup allows for efficient parallel processing of Kafka records, leveraging the power of multi-threading to handle large volumes of data more effectively.

# multithreading coding interview questions using ExecutorService

When preparing for coding interviews on multithreading, particularly with `ExecutorService`, it's useful to focus on various types of questions that test your understanding of concurrency, resource management, and task scheduling. Here are some common interview questions that involve `ExecutorService`:

### 1. **Basic ExecutorService Usage**

**Question:**
Write a program using `ExecutorService` to submit 10 tasks to a thread pool where each task prints a message with its thread name. Ensure that the thread pool uses a fixed number of threads.

**Answer:**
```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class ExecutorServiceExample {
    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(4);

        for (int i = 0; i < 10; i++) {
            int taskId = i;
            executorService.submit(() -> {
                System.out.println("Task " + taskId + " executed by " + Thread.currentThread().getName());
            });
        }

        executorService.shutdown();
    }
}
```

### 2. **Task Scheduling**

**Question:**
Write a program that schedules a task to run after an initial delay of 2 seconds and then repeats every 5 seconds.

**Answer:**
```java
import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class ScheduledExecutorServiceExample {
    public static void main(String[] args) {
        ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(1);

        scheduler.scheduleAtFixedRate(() -> {
            System.out.println("Scheduled task executed by " + Thread.currentThread().getName());
        }, 2, 5, TimeUnit.SECONDS);

        // Schedule shutdown after some time
        scheduler.schedule(() -> {
            scheduler.shutdown();
        }, 20, TimeUnit.SECONDS);
    }
}
```

### 3. **Handling Exceptions**

**Question:**
Write a program that submits multiple tasks to an `ExecutorService`. One of the tasks should throw an exception. Demonstrate how you handle exceptions thrown by tasks.

**Answer:**
```java
import java.util.ArrayList;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class ExceptionHandlingExample {
    public static void main(String[] args) {
        ExecutorService executorService = Executors.newFixedThreadPool(3);
        List<Future<String>> futures = new ArrayList<>();

        futures.add(executorService.submit(() -> {
            throw new RuntimeException("Task failed");
        }));
        futures.add(executorService.submit(() -> "Task succeeded"));

        for (Future<String> future : futures) {
            try {
                System.out.println(future.get());
            } catch (InterruptedException | ExecutionException e) {
                System.err.println("Error: " + e.getCause().getMessage());
            }
        }

        executorService.shutdown();
    }
}
```

### 4. **Custom Task Executors**

**Question:**
Create a custom `ExecutorService` that limits the number of concurrent tasks and implements a custom rejection policy.

**Answer:**
```java
import java.util.concurrent.*;

public class CustomExecutorServiceExample {
    public static void main(String[] args) {
        ThreadPoolExecutor executorService = new ThreadPoolExecutor(
            2, // corePoolSize
            4, // maximumPoolSize
            60, // keepAliveTime
            TimeUnit.SECONDS,
            new LinkedBlockingQueue<>(2), // workQueue
            new ThreadPoolExecutor.CallerRunsPolicy() // rejection policy
        );

        for (int i = 0; i < 10; i++) {
            final int taskId = i;
            executorService.submit(() -> {
                try {
                    Thread.sleep(1000);
                    System.out.println("Task " + taskId + " executed by " + Thread.currentThread().getName());
                } catch (InterruptedException e) {
                    Thread.currentThread().interrupt();
                }
            });
        }

        executorService.shutdown();
    }
}
```

### 5. **Shutdown Behavior**

**Question:**
Explain and demonstrate the difference between `shutdown()` and `shutdownNow()` methods in `ExecutorService`.

**Answer:**
```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.TimeUnit;

public class ShutdownBehaviorExample {
    public static void main(String[] args) throws InterruptedException {
        ExecutorService executorService = Executors.newFixedThreadPool(3);

        executorService.submit(() -> {
            try {
                Thread.sleep(5000);
                System.out.println("Task 1 completed");
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        });

        executorService.submit(() -> {
            try {
                Thread.sleep(5000);
                System.out.println("Task 2 completed");
            } catch (InterruptedException e) {
                Thread.currentThread().interrupt();
            }
        });

        // Uncomment one of the following lines to test behavior

        // executorService.shutdown(); // Graceful shutdown
        executorService.shutdownNow(); // Immediate shutdown

        executorService.awaitTermination(10, TimeUnit.SECONDS);
        System.out.println("Executor service terminated");
    }
}
```

### 6. **Complex Task Scheduling**

**Question:**
Write a program that schedules a task to run periodically and performs cleanup after the tasks are complete.

**Answer:**
```java
import java.util.concurrent.Executors;
import java.util.concurrent.ScheduledExecutorService;
import java.util.concurrent.TimeUnit;

public class ComplexSchedulingExample {
    public static void main(String[] args) {
        ScheduledExecutorService scheduler = Executors.newScheduledThreadPool(2);

        Runnable periodicTask = () -> {
            System.out.println("Periodic task executed by " + Thread.currentThread().getName());
        };

        scheduler.scheduleAtFixedRate(periodicTask, 1, 3, TimeUnit.SECONDS);

        Runnable cleanupTask = () -> {
            System.out.println("Cleanup task executed by " + Thread.currentThread().getName());
            scheduler.shutdown();
        };

        scheduler.schedule(cleanupTask, 15, TimeUnit.SECONDS);
    }
}
```

### Summary

- **Basic Usage**: Submitting simple tasks for execution.
- **Task Scheduling**: Scheduling tasks with delays and periodic execution.
- **Handling Exceptions**: Dealing with exceptions thrown by tasks.
- **Custom Executors**: Creating custom executor services with custom rejection policies.
- **Shutdown Behavior**: Understanding and demonstrating different shutdown methods.
- **Complex Scheduling**: Combining periodic tasks and cleanup tasks.

These questions cover a range of scenarios you might encounter when working with `ExecutorService` and can help you prepare for coding interviews focused on multithreading and concurrency.

# even or odd number print separately from a list using multithreading

To print even and odd numbers separately from a list using multithreading, you can use `ExecutorService` to handle the tasks concurrently. Here’s a detailed example of how you can achieve this:

### Problem Statement
You need to separate even and odd numbers from a list and print them using different threads.

### Solution

1. **Create a `Runnable` class** for processing even and odd numbers.
2. **Submit tasks to `ExecutorService`** to process the list concurrently.
3. **Print results from each thread**.

### Implementation

Here's how you can implement it:

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.atomic.AtomicInteger;

public class EvenOddPrinter {

    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
        
        // Create an ExecutorService with a fixed thread pool
        ExecutorService executorService = Executors.newFixedThreadPool(2);

        // Create and submit tasks for processing even and odd numbers
        executorService.submit(new NumberProcessor(numbers, true)); // Process even numbers
        executorService.submit(new NumberProcessor(numbers, false)); // Process odd numbers

        // Shutdown the ExecutorService
        executorService.shutdown();
    }
}

class NumberProcessor implements Runnable {
    private final List<Integer> numbers;
    private final boolean isEven;

    public NumberProcessor(List<Integer> numbers, boolean isEven) {
        this.numbers = numbers;
        this.isEven = isEven;
    }

    @Override
    public void run() {
        if (isEven) {
            System.out.println("Even numbers:");
            numbers.stream()
                   .filter(num -> num % 2 == 0)
                   .forEach(num -> System.out.println(num + " processed by " + Thread.currentThread().getName()));
        } else {
            System.out.println("Odd numbers:");
            numbers.stream()
                   .filter(num -> num % 2 != 0)
                   .forEach(num -> System.out.println(num + " processed by " + Thread.currentThread().getName()));
        }
    }
}
```

### Explanation

1. **ExecutorService Setup**:
   - We use `Executors.newFixedThreadPool(2)` to create a thread pool with 2 threads.

2. **NumberProcessor Class**:
   - Implements `Runnable` and takes a list of numbers and a boolean `isEven` to determine if it should process even or odd numbers.
   - Uses Java Streams to filter and print numbers.

3. **Task Submission**:
   - Two tasks are submitted to the executor service: one for even numbers and one for odd numbers.

4. **Shutdown**:
   - After submitting tasks, we call `executorService.shutdown()` to gracefully shut down the executor service.

### Running the Code

When you run this code, you will see that even and odd numbers are processed and printed by different threads, thanks to the `ExecutorService`.

### Output Example

```
Even numbers:
2 processed by pool-1-thread-1
4 processed by pool-1-thread-1
6 processed by pool-1-thread-1
8 processed by pool-1-thread-1
10 processed by pool-1-thread-1
Odd numbers:
1 processed by pool-1-thread-2
3 processed by pool-1-thread-2
5 processed by pool-1-thread-2
7 processed by pool-1-thread-2
9 processed by pool-1-thread-2
```

This example demonstrates how to use multithreading to process and print even and odd numbers from a list separately, improving efficiency and separating concerns.

# even or odd number print using executorservice in multithreading

To print even and odd numbers separately using `ExecutorService` in multithreading, you can break down the problem into the following steps:

1. **Create a list of numbers.**
2. **Use `ExecutorService` to manage and execute tasks concurrently.**
3. **Define tasks that process even and odd numbers separately.**
4. **Submit these tasks to the executor service.**
5. **Shut down the executor service gracefully.**

Here’s a step-by-step implementation in Java:

### 1. Setup the Project

Ensure you have Java set up and create a Java file (e.g., `EvenOddPrinter.java`).

### 2. Implement the Code

Here’s the complete code that demonstrates how to use `ExecutorService` to print even and odd numbers using multithreading:

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class EvenOddPrinter {

    public static void main(String[] args) {
        // List of numbers to process
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        // Create an ExecutorService with a fixed thread pool
        ExecutorService executorService = Executors.newFixedThreadPool(2);

        // Submit tasks to process even and odd numbers
        executorService.submit(new NumberPrinter(numbers, true)); // Process even numbers
        executorService.submit(new NumberPrinter(numbers, false)); // Process odd numbers

        // Shutdown the ExecutorService
        executorService.shutdown();
    }
}

class NumberPrinter implements Runnable {
    private final List<Integer> numbers;
    private final boolean printEven;

    public NumberPrinter(List<Integer> numbers, boolean printEven) {
        this.numbers = numbers;
        this.printEven = printEven;
    }

    @Override
    public void run() {
        if (printEven) {
            System.out.println("Even numbers:");
            numbers.stream()
                   .filter(num -> num % 2 == 0)
                   .forEach(num -> System.out.println(num + " processed by " + Thread.currentThread().getName()));
        } else {
            System.out.println("Odd numbers:");
            numbers.stream()
                   .filter(num -> num % 2 != 0)
                   .forEach(num -> System.out.println(num + " processed by " + Thread.currentThread().getName()));
        }
    }
}
```

### Explanation

1. **ExecutorService Creation**:
   - `Executors.newFixedThreadPool(2)` creates a thread pool with two threads. This allows the even and odd number processing to run concurrently.

2. **NumberPrinter Class**:
   - Implements `Runnable` and is used to define the task. It takes a list of numbers and a boolean flag (`printEven`) to determine if it should process even or odd numbers.
   - The `run()` method processes numbers using Java Streams and prints the results, including the thread name that processed the numbers.

3. **Task Submission**:
   - Two `NumberPrinter` tasks are submitted: one for even numbers and one for odd numbers. Each task is handled by a separate thread from the pool.

4. **Shutdown**:
   - `executorService.shutdown()` initiates an orderly shutdown where previously submitted tasks are executed, but no new tasks will be accepted.

### Running the Code

When you run this program, you will see that even and odd numbers are processed by separate threads, thanks to the `ExecutorService`. The output might look like this:

```
Even numbers:
2 processed by pool-1-thread-1
4 processed by pool-1-thread-1
6 processed by pool-1-thread-1
8 processed by pool-1-thread-1
10 processed by pool-1-thread-1
Odd numbers:
1 processed by pool-1-thread-2
3 processed by pool-1-thread-2
5 processed by pool-1-thread-2
7 processed by pool-1-thread-2
9 processed by pool-1-thread-2
```

This code demonstrates how to use `ExecutorService` to handle tasks concurrently in a multithreaded environment, with separate tasks for even and odd numbers.

# even or odd number using completableFuture

Using `CompletableFuture` to process and print even and odd numbers concurrently is a modern approach that leverages Java’s asynchronous programming capabilities. Here’s how you can achieve this:

### Example: Printing Even and Odd Numbers Using `CompletableFuture`

In this example, we'll create two `CompletableFuture` tasks to process even and odd numbers from a list concurrently.

#### 1. Setup the Project

Ensure you have Java set up and create a Java file (e.g., `EvenOddPrinterCompletableFuture.java`).

#### 2. Implement the Code

Here’s the complete code that demonstrates how to use `CompletableFuture` to print even and odd numbers:

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class EvenOddPrinterCompletableFuture {

    public static void main(String[] args) {
        // List of numbers to process
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        // Create CompletableFuture tasks to process even and odd numbers
        CompletableFuture<Void> evenFuture = CompletableFuture.runAsync(() -> processEvenNumbers(numbers));
        CompletableFuture<Void> oddFuture = CompletableFuture.runAsync(() -> processOddNumbers(numbers));

        // Wait for both tasks to complete
        CompletableFuture<Void> allOf = CompletableFuture.allOf(evenFuture, oddFuture);

        try {
            allOf.get(); // Block until all futures are completed
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }

    private static void processEvenNumbers(List<Integer> numbers) {
        System.out.println("Even numbers:");
        numbers.stream()
               .filter(num -> num % 2 == 0)
               .forEach(num -> System.out.println(num + " processed by " + Thread.currentThread().getName()));
    }

    private static void processOddNumbers(List<Integer> numbers) {
        System.out.println("Odd numbers:");
        numbers.stream()
               .filter(num -> num % 2 != 0)
               .forEach(num -> System.out.println(num + " processed by " + Thread.currentThread().getName()));
    }
}
```

### Explanation

1. **CompletableFuture Creation**:
   - `CompletableFuture.runAsync(Runnable)` creates a `CompletableFuture` that executes the given `Runnable` asynchronously. We use this to run tasks that process even and odd numbers.

2. **Processing Methods**:
   - `processEvenNumbers(List<Integer> numbers)` and `processOddNumbers(List<Integer> numbers)` filter and print even and odd numbers respectively.

3. **Combining Futures**:
   - `CompletableFuture.allOf(CompletableFuture<?>... cfs)` creates a new `CompletableFuture` that is completed when all of the given futures complete. This allows us to wait for both tasks to complete.

4. **Waiting for Completion**:
   - `allOf.get()` blocks until both `CompletableFuture` tasks are finished. This ensures that the main thread waits for the processing to complete.

### Running the Code

When you run this program, it will print even and odd numbers concurrently using `CompletableFuture`. The output might look like this:

```
Even numbers:
2 processed by ForkJoinPool.commonPool-worker-1
4 processed by ForkJoinPool.commonPool-worker-1
6 processed by ForkJoinPool.commonPool-worker-1
8 processed by ForkJoinPool.commonPool-worker-1
10 processed by ForkJoinPool.commonPool-worker-1
Odd numbers:
1 processed by ForkJoinPool.commonPool-worker-2
3 processed by ForkJoinPool.commonPool-worker-2
5 processed by ForkJoinPool.commonPool-worker-2
7 processed by ForkJoinPool.commonPool-worker-2
9 processed by ForkJoinPool.commonPool-worker-2
```

### Benefits

- **Asynchronous Execution**: Tasks are executed concurrently, improving performance for I/O-bound or CPU-bound operations.
- **Non-blocking**: `CompletableFuture` provides a non-blocking way to handle asynchronous tasks.
- **Composability**: You can easily chain and compose multiple asynchronous operations using `CompletableFuture`.

This approach demonstrates how to leverage `CompletableFuture` for concurrent processing and provides a modern alternative to traditional multithreading techniques.

# Completable Future Synchronous and Asynchronous programing example

`CompletableFuture` in Java provides a powerful way to handle asynchronous programming while also supporting synchronous operations. Here's an overview of both synchronous and asynchronous programming using `CompletableFuture`, along with examples for each.

### 1. **Asynchronous Programming with CompletableFuture**

Asynchronous programming allows tasks to run concurrently without blocking the main thread. This is useful for I/O operations, network calls, or any tasks that can be performed in parallel.

#### Example: Asynchronous Programming with CompletableFuture

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class AsyncExample {
    public static void main(String[] args) {
        // Asynchronous task to calculate the square of a number
        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
            try {
                // Simulate a long-running task
                Thread.sleep(2000);
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            return 10 * 10; // Calculate square of 10
        });

        // Asynchronously process the result
        CompletableFuture<Void> resultFuture = future.thenAccept(result -> {
            System.out.println("The result is: " + result);
        });

        // Wait for the result to be processed
        try {
            resultFuture.get(); // Block until the result is processed
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

### Explanation

1. **`supplyAsync`**: Starts a new asynchronous task that calculates the square of a number. This task runs in a separate thread.
2. **`thenAccept`**: Takes the result of the asynchronous task and processes it (e.g., printing it).
3. **`get`**: Blocks the main thread until the asynchronous operation is complete. This ensures the program waits for the result.

### 2. **Synchronous Programming with CompletableFuture**

Synchronous programming involves executing tasks in a sequential manner. However, `CompletableFuture` can also be used in a synchronous manner by blocking until the result is available.

#### Example: Synchronous Programming with CompletableFuture

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class SyncExample {
    public static void main(String[] args) {
        // Create a CompletableFuture for a simple synchronous task
        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> 5 * 5);

        // Synchronously block to get the result
        try {
            Integer result = future.get(); // Block until the result is available
            System.out.println("The result is: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

### Explanation

1. **`supplyAsync`**: Starts a new asynchronous task that calculates the square of a number. The task runs in a separate thread.
2. **`get`**: Blocks the main thread until the result is available. This is a synchronous wait for the result.

### Combining Asynchronous and Synchronous Operations

You can mix synchronous and asynchronous operations depending on your needs. For example, you might start with asynchronous operations but need to wait for results synchronously before proceeding.

#### Example: Combined Asynchronous and Synchronous

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CombinedExample {
    public static void main(String[] args) {
        // Start an asynchronous task
        CompletableFuture<Integer> future = CompletableFuture.supplyAsync(() -> {
            try {
                Thread.sleep(2000); // Simulate delay
            } catch (InterruptedException e) {
                e.printStackTrace();
            }
            return 20 * 20; // Calculate square of 20
        });

        // Chain another asynchronous task
        CompletableFuture<Integer> squaredFuture = future.thenApply(result -> result * result);

        // Wait synchronously for the final result
        try {
            Integer finalResult = squaredFuture.get(); // Block until the final result is available
            System.out.println("The final result is: " + finalResult);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

### Explanation

1. **`supplyAsync`**: Starts an asynchronous task.
2. **`thenApply`**: Chains another asynchronous task to process the result of the previous task.
3. **`get`**: Synchronously waits for the final result of the chained tasks.

### Summary

- **Asynchronous Programming**: `CompletableFuture` allows you to run tasks concurrently and handle their results asynchronously.
- **Synchronous Programming**: You can block the main thread using methods like `get()` to wait for the result of an asynchronous task.
- **Combining Both**: `CompletableFuture` supports chaining and combining tasks, allowing you to mix synchronous and asynchronous operations as needed.

This combination of synchronous and asynchronous programming can help you handle complex workflows and improve the efficiency of your applications.

# Future Asynchronous and Synchronous programing example.

Using `Future` in Java, you can handle both asynchronous and synchronous programming scenarios. `Future` represents the result of an asynchronous computation, allowing you to retrieve the result once it is available or handle the task when it's done.

Here’s a guide on how to use `Future` for both asynchronous and synchronous programming:

### 1. **Asynchronous Programming with Future**

In asynchronous programming with `Future`, you submit a task to an `ExecutorService` and continue executing other code. Later, you can retrieve the result when it’s ready.

#### Example: Asynchronous Programming with Future

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class AsyncFutureExample {
    public static void main(String[] args) {
        // Create an ExecutorService
        ExecutorService executor = Executors.newFixedThreadPool(1);

        // Submit a Callable task to the executor
        Future<Integer> future = executor.submit(new Callable<Integer>() {
            @Override
            public Integer call() throws Exception {
                // Simulate a long-running task
                Thread.sleep(2000);
                return 5 * 5; // Return the square of 5
            }
        });

        // Continue with other tasks while the computation is in progress
        System.out.println("Performing other tasks...");

        // Retrieve the result of the computation (blocking call)
        try {
            Integer result = future.get(); // This will block until the result is available
            System.out.println("The result is: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }

        // Shutdown the executor
        executor.shutdown();
    }
}
```

### Explanation

1. **ExecutorService Creation**:
   - `Executors.newFixedThreadPool(1)` creates a thread pool with one thread for executing tasks.

2. **Callable Task Submission**:
   - `executor.submit(new Callable<Integer>() {...})` submits a task that returns an integer result. The task simulates a delay to represent a long-running computation.

3. **Continue Execution**:
   - The main thread can continue executing other code while the computation is in progress.

4. **Retrieve Result**:
   - `future.get()` blocks until the result is available. This is a synchronous operation to retrieve the result of the asynchronous computation.

5. **Shutdown Executor**:
   - `executor.shutdown()` gracefully shuts down the executor after tasks are completed.

### 2. **Synchronous Programming with Future**

In synchronous programming with `Future`, you wait for the task to complete before proceeding with further code. This approach blocks the main thread until the computation is done.

#### Example: Synchronous Programming with Future

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class SyncFutureExample {
    public static void main(String[] args) {
        // Create an ExecutorService
        ExecutorService executor = Executors.newFixedThreadPool(1);

        // Submit a Callable task to the executor
        Future<Integer> future = executor.submit(new Callable<Integer>() {
            @Override
            public Integer call() throws Exception {
                // Simulate a long-running task
                Thread.sleep(2000);
                return 10 * 10; // Return the square of 10
            }
        });

        // Wait for the result (blocking call)
        try {
            Integer result = future.get(); // Block until the result is available
            System.out.println("The result is: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }

        // Shutdown the executor
        executor.shutdown();
    }
}
```

### Explanation

1. **ExecutorService Creation**:
   - Same as in the asynchronous example.

2. **Callable Task Submission**:
   - Same as in the asynchronous example.

3. **Blocking Call for Result**:
   - `future.get()` blocks the main thread until the result is available, making it a synchronous operation.

4. **Shutdown Executor**:
   - Same as in the asynchronous example.

### Summary

- **Asynchronous Programming with Future**:
  - Use `ExecutorService` and `Future` to submit tasks that run in the background.
  - Retrieve results using `future.get()` when needed, allowing other tasks to proceed concurrently.

- **Synchronous Programming with Future**:
  - Submit tasks and wait for the result using `future.get()`, blocking the main thread until the result is available.

Using `Future` for both asynchronous and synchronous operations allows you to manage tasks efficiently and handle results when they are ready.

# Odd or Even number using Future in multithreading

To use `Future` for separating odd and even numbers in multithreading, you can follow these steps:

1. **Create an `ExecutorService`** to manage threads.
2. **Define tasks** to filter and print even and odd numbers.
3. **Submit these tasks** to the executor service.
4. **Retrieve results using `Future`** and block if necessary.

Here's how you can implement this:

### Example: Odd and Even Number Processing Using `Future`

#### Step-by-Step Implementation

1. **Create a Callable Task** for processing even and odd numbers.
2. **Submit these tasks to an `ExecutorService`.**
3. **Retrieve and print results** from the `Future` objects.

#### Code

```java
import java.util.Arrays;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class OddEvenWithFuture {

    public static void main(String[] args) {
        // List of numbers to process
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);

        // Create an ExecutorService with a fixed thread pool
        ExecutorService executor = Executors.newFixedThreadPool(2);

        // Submit tasks for even and odd number processing
        Future<Void> evenFuture = executor.submit(new NumberProcessor(numbers, true)); // Process even numbers
        Future<Void> oddFuture = executor.submit(new NumberProcessor(numbers, false)); // Process odd numbers

        // Wait for both tasks to complete
        try {
            evenFuture.get(); // Block until the even numbers processing is complete
            oddFuture.get();  // Block until the odd numbers processing is complete
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }

        // Shutdown the executor
        executor.shutdown();
    }
}

class NumberProcessor implements Callable<Void> {
    private final List<Integer> numbers;
    private final boolean processEven;

    public NumberProcessor(List<Integer> numbers, boolean processEven) {
        this.numbers = numbers;
        this.processEven = processEven;
    }

    @Override
    public Void call() {
        if (processEven) {
            System.out.println("Even numbers:");
            numbers.stream()
                   .filter(num -> num % 2 == 0)
                   .forEach(num -> System.out.println(num + " processed by " + Thread.currentThread().getName()));
        } else {
            System.out.println("Odd numbers:");
            numbers.stream()
                   .filter(num -> num % 2 != 0)
                   .forEach(num -> System.out.println(num + " processed by " + Thread.currentThread().getName()));
        }
        return null;
    }
}
```

### Explanation

1. **ExecutorService Creation**:
   - `Executors.newFixedThreadPool(2)` creates a thread pool with two threads for processing tasks concurrently.

2. **Callable Task Definition**:
   - `NumberProcessor` implements `Callable<Void>` and processes either even or odd numbers based on the `processEven` flag.
   - `call()` method filters and prints the numbers, using `Thread.currentThread().getName()` to identify which thread processed the numbers.

3. **Task Submission**:
   - Two `NumberProcessor` tasks are submitted: one for even numbers and one for odd numbers.

4. **Retrieve Results**:
   - `future.get()` blocks until the respective task is complete. This ensures the main thread waits for both tasks to finish.

5. **Shutdown Executor**:
   - `executor.shutdown()` gracefully shuts down the executor service after all tasks are completed.

### Summary

- **Asynchronous Execution**: Tasks for processing even and odd numbers are run concurrently in separate threads.
- **Blocking**: `Future.get()` is used to block the main thread until each task is completed, ensuring both tasks finish before the program exits.

This approach efficiently handles parallel processing of even and odd numbers, leveraging the multithreading capabilities of Java’s `ExecutorService` and `Future`.

# ThreadPoolExecutor Example

The `ThreadPoolExecutor` class in Java is a powerful tool for managing a pool of threads and executing tasks concurrently. It provides fine-grained control over thread management and task execution.

Here's an example of how to use `ThreadPoolExecutor` to handle tasks concurrently:

### Example: Using `ThreadPoolExecutor` to Execute Tasks

In this example, we will:
1. Create a `ThreadPoolExecutor` instance.
2. Submit tasks to the executor for execution.
3. Manage the thread pool by adjusting its size and handling task execution.

#### Code

```java
import java.util.concurrent.Executors;
import java.util.concurrent.ThreadPoolExecutor;
import java.util.concurrent.TimeUnit;

public class ThreadPoolExecutorExample {

    public static void main(String[] args) {
        // Create a ThreadPoolExecutor with core pool size of 2, maximum pool size of 4, and a 60-second keep-alive time
        ThreadPoolExecutor executor = new ThreadPoolExecutor(
            2, // Core pool size
            4, // Maximum pool size
            60, // Time to keep idle threads alive
            TimeUnit.SECONDS, // Time unit for keep-alive time
            new java.util.concurrent.LinkedBlockingQueue<>()
        );

        // Submit tasks to the executor
        for (int i = 0; i < 10; i++) {
            final int taskId = i;
            executor.submit(() -> {
                System.out.println("Task " + taskId + " is being executed by " + Thread.currentThread().getName());
                try {
                    // Simulate a long-running task
                    Thread.sleep(2000);
                } catch (InterruptedException e) {
                    e.printStackTrace();
                }
                System.out.println("Task " + taskId + " completed by " + Thread.currentThread().getName());
            });
        }

        // Shutdown the executor gracefully
        executor.shutdown();
        try {
            // Wait for all tasks to complete or timeout after 5 minutes
            if (!executor.awaitTermination(5, TimeUnit.MINUTES)) {
                executor.shutdownNow(); // Force shutdown if not terminated
            }
        } catch (InterruptedException e) {
            executor.shutdownNow(); // Force shutdown if interrupted
        }
    }
}
```

### Explanation

1. **ThreadPoolExecutor Creation**:
   - `ThreadPoolExecutor(int corePoolSize, int maximumPoolSize, long keepAliveTime, TimeUnit unit, BlockingQueue<Runnable> workQueue)`
     - **Core Pool Size**: The minimum number of threads to keep alive.
     - **Maximum Pool Size**: The maximum number of threads allowed in the pool.
     - **Keep Alive Time**: Time to keep idle threads alive.
     - **Time Unit**: Unit for the keep-alive time.
     - **Work Queue**: Queue to hold tasks before they are executed. `LinkedBlockingQueue` is used here.

2. **Submitting Tasks**:
   - Tasks are submitted to the executor using `executor.submit()`. Each task prints its ID and the thread name executing it.

3. **Shutdown and Termination**:
   - `executor.shutdown()` initiates a graceful shutdown, allowing previously submitted tasks to complete.
   - `executor.awaitTermination(long timeout, TimeUnit unit)` waits for the termination of all tasks or until the timeout expires.
   - `executor.shutdownNow()` forces shutdown if tasks do not complete within the specified time.

### Key Points

- **Core and Maximum Pool Size**: Determines the number of threads that are used and how many additional threads can be created if needed.
- **Keep-Alive Time**: Defines how long idle threads are kept alive before being terminated.
- **Work Queue**: Holds tasks that are waiting to be executed. A `BlockingQueue` ensures that tasks are handled in a thread-safe manner.

This example demonstrates how to use `ThreadPoolExecutor` to manage and execute tasks concurrently, providing flexibility and control over thread management in a Java application.

