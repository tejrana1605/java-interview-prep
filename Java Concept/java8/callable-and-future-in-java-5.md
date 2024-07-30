# Callable and Future in java

To create a thread in java we have two ways, one is the **Runnable interface**, and another is **Thread class**. The **Runnable interface** has some limitations in a multithreading environment. So, Java introduced **Callable** and **Future** interfaces to remove the limitations. In this topic, we will learn these advanced topics of **concurrency in java** and show how these are useful. We believe all of you have a basic understanding of threads. If you haven’t the basic idea, then read **multithreading in java**.

1. The need for Callable interface?
2. Callable interface in java?
3. Java Callable Interface Definition?
4. Implementing Callable and java callable example?
5. Difference between callable and runnable?
6. Future interface in java?
7. Java future example?

## The need for Callable interface

We can understand the use of the **Callable interface** when we will understand the problem without Callable. As we know, Java provides two ways to create thread- one by extending the Thread class and others by creating a thread with a Runnable. The Runnable interface has limitations because it can’t return the object after termination. But sometimes we wish that a thread could return some value that we can use.  To support this feature, Java introduced the Callable interface.

## 2. Callable interface in java

The **java.util.concurrent** package was introduced in java 5. The **callable interface** was introduced in the currency package and supports an asynchronous task which can be executed by a separate thread. The **callable interface** is similar to the **Runnable interface**, except it can return an object and it can **throw a checked Exception**.

**Note**: We can’t create a thread with a Callable, it can only be created with a Runnable.

## 3. Java Callable Interface Definition
The Callable interface is a functional interface because it has only one method named call(). You can see the JDK code below:

```java
*/
@FunctionalInterface
public interface Callable<V> {
    /**
     * Computes a result, or throws an exception if unable to do so.
     *
     * @return computed result
     * @throws Exception if unable to compute a result
     */
    V call() throws Exception;
}
```

The Callable interface uses the Generics concept of java, so we can return any type of Object. The **call () method** will be implemented by a class that will implement the Callable interface. The **call() method** works exactly same as the **run () method** of the **Runnable interface**, except it returns an object and it can throw a checked exception.

## 4. Implementing Callable and java callable example

In the above section, we have read about the **callable interface in java**. Let’s see an example of a **callable interface**.

**Step1**: We will place the task(code) in call() method that we want to perform.


**Step2**: We will use the **Executor Framework** to execute the Callable implementation.  The **Executor Framework** provides a **submit() method** that accepts the implementation of Callable and passes to the thread pool. When we pass a Callable to a thread pool, it chooses one thread and executes the Callable. The Java Executor Framework works based on WorkerThread patterns and we can initiate threads from the thread pool by use of the **Executors.newFixedThreadPool(5);** method.


**Step3**:  It will return the object of the Future that holds the result of computation once done. We can get the result by use of **get() method** of Future, which will return the result of the computation.

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
public class CallableImplementation 
{
   public static void main(String[] args) throws InterruptedException, ExecutionException 
   {
      ExecutorService service = Executors.newSingleThreadExecutor();
      CallableFactorialTask task = new CallableFactorialTask(5);
      Future<Integer> f = service.submit(task);
      Integer val = f.get();
      System.out.println(val);
      service.shutdown();
   }
}
class CallableFactorialTask implements Callable<Integer> 
{
   private int num = 0;
   public CallableFactorialTask(int num)
   {
      this.num = num;
   }
   @Override
   public Integer call() throws Exception 
   {
      int prod = 1;
      for (int i = 2; i <= num; i++)
         prod *= i;
      return prod;
   }
}
```

```java
Output:120
```

## Difference between callable and runnable
The callable and runnable interfaces have similarities and dissimilarities. Let’s see how callable vs runnable.

1. The **Runnable interface** provides, the **run() method** so we need to be implemented it and it doesn’t return anything. But a **Callable**, has **call() method** so we need to be implemented it and that returns an object.

2. A **run() method** can’t throw the exception because run() method runs independently and terminate itself. But doesn’t return anything or inform the parent thread. But a call method can throw checked exceptions.

3. Runnable interface was introduced in java 1.0 where Callable interface introduce in java 5.

4. Java Runnable interface is not generic, so it doesn’t take any parameter. But the Callable interface is generic.

<a href="#" target="_blank"><img src="https://javagoal.com/wp-content/uploads/2020/10/3.png" alt="Callable Interface"/></a>

## Future interface in java

The **Future interface** was introduced in java 5 and used to store the result returned by **call() method** of Callable. The **call() method** returns an object after completion of execution, so the answer must be stored in an object and get the response in the main thread.

**Callable and Future in java** works together but both are different things.  Callable performs tasks and returns the object stored in the Future. The Future can store the result obtained from a different thread. It has some method that are used to perform different operations:

1. **public boolean cancel(boolean mayInterrupt)**: This method is used to stop the task if it has not started. If the task already has started and mayInterrupt is true, then it interrupts the task.

2. **public Object get() throws InterruptedException, ExecutionException**: This method is used to get the result of the task. It returns a specific type of object. It returns the result immediately, if the task has completed otherwise it waits till the task is complete.

3. **public boolean isDone()**: This method returns a boolean value. It returns true if the task is complete and false otherwise.

Let’s see the code in JDK:

```java
public interface Future<V> 
{
   boolean cancel(boolean mayInterruptIfRunning);
   boolean isCancelled();
   boolean isDone();
}
```

### Java future example

```java
import java.util.ArrayList;
import java.util.Date;
import java.util.List;
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class CallableImplementation implements Callable<String> {

    @Override
    public String call() throws Exception 
    {
        Thread.sleep(1000);
        //return the thread name executing this callable task
        return Thread.currentThread().getName();
    }
    
    public static void main(String args[])
    {
        //Get ExecutorService from Executors utility class, thread pool size is 5
        ExecutorService executor = Executors.newFixedThreadPool(5);
        //create a list to hold the Future object associated with Callable
        List<Future<String>> list = new ArrayList<Future<String>>();
        //Create MyCallable instance
        Callable<String> callable = new CallableImplementation();
        for(int i=0; i< 10; i++)
        {
            //submit Callable tasks to be executed by thread pool
            Future<String> future = executor.submit(callable);
            //add Future to the list, we can get return value using Future
            list.add(future);
        }
        for(Future<String> future : list)
        {
            try 
            {
                //print the return value of Future, notice the output delay in console
                // because Future.get() waits for task to get completed
                System.out.println(new Date()+ "::"+future.get());
            } 
            catch (InterruptedException | ExecutionException e) 
            {
                e.printStackTrace();
            }
        }
        //shut down the executor service now
        executor.shutdown();
    }

}
```

```java
Output: Sat Oct 10 14:21:25 IST 2020::pool-1-thread-1
Sat Oct 10 14:21:26 IST 2020::pool-1-thread-2
Sat Oct 10 14:21:26 IST 2020::pool-1-thread-3
Sat Oct 10 14:21:26 IST 2020::pool-1-thread-4
Sat Oct 10 14:21:26 IST 2020::pool-1-thread-5
Sat Oct 10 14:21:26 IST 2020::pool-1-thread-4
Sat Oct 10 14:21:27 IST 2020::pool-1-thread-3
Sat Oct 10 14:21:27 IST 2020::pool-1-thread-1
Sat Oct 10 14:21:27 IST 2020::pool-1-thread-5
Sat Oct 10 14:21:27 IST 2020::pool-1-thread-2
```

<a href="#" target="_blank"><img src="https://javagoal.com/wp-content/uploads/2020/10/2.png" alt="future example"/></a>

# Callable and Future in Java

In Java, Callable and Future are the two most important concepts that are used with thread. In this section, we will understand how we can use Callable and Future in our code.

Future is used for storing a result received from a different thread, whereas Callable is the same as Runnable in that it encapsulates a task that is meant to be run on another thread.

<a href="#" target="_blank"><img src="https://static.javatpoint.com/core/images/callable-and-future-in-java.png" alt="future example"/></a>

## Callable Interface

Java offers two ways for creating a thread, i.e., by extending the Thread class and by creating a thread with a Runnable. There is a drawback of creating a thread with the Runnable interface, i.e., we cannot make a thread return result when it terminates, i.e., when the run() completes. In order to overcome this drawback, Java provides the Callable interface.

These are the two main differences between the Callable and Runnable methods:

1. The run() method is used for implementing the Runnable, whereas the call() method is used for implementing the Callable. The run() method doesn't return anything, whereas the call() method returns a result of completion.

2. The call() method can throw an exception, whereas the run() method cannot.

The syntax of the call() method is as follows:

public Object call() throws Exception;

Let's take an example to understand how we can use Callable interface:

**CallableInterfaceExample.java**

```java
// import required classes and package if any   
import java.util.concurrent.Callable;     
import java.util.Random;     
   
//create class CallableInterfaceExample that implements Callable interface   
class CallableInterfaceExample implements Callable<Object> {     
      
    // override the call() method      
    @Override     
      
    public Object call() throws Exception {     
          
        //create an instance of the  Random class      
        Random obj = new Random();     
          
        //generate a random number between 0-100   
        Integer number = obj.nextInt(100);     
          
        //delay thread for some random time     
        Thread.sleep(number * 1000);     
          
        //return the object having the generated random number     
        return number;     
    }      
}    
```

## Future

In the main() method, the returned value of the call() method(after completion) should be stored in an object to know about the result that the thread returns. In order to store the returned data in the main() method, we use a Future object.

The future is one of the ways through which we can keep track of the progress and result from other threads. We need to override the five methods for implementing the Future interface. The **cancel()**, **get()** and **isDone()** methods are the most important methods from the Future interface.

```java
public boolean cancel(boolean mayInterrupt)
```

The **cancel()** method is used to stop the task if it has not started. If the task has started and **the mayInterrupt** boolean value is true, it will interrupt that task too.

```java
public Object get() throws InterruptedException
```

The method returns the result of the task. It returns the result immediately if the task is completed; else, it will wait for its completion and then returns the result.

```java
public boolean isDone() throws InterruptedException
```

It returns a boolean value based on the completion of the task.

Note: For creating a thread, a Runnable is necessary.

Note: For obtaining the result, a Future is necessary.

Let's take an example to understand how we can use Future to store the returned result of call() in the main() method:

**CallableFutureExample.java**

```java
//import required classes and package if any   
import java.util.concurrent.Callable;   
import java.util.concurrent.ExecutionException;   
import java.util.concurrent.FutureTask;   
import java.util.Random;     
   
//create class CallableInterface that implements Callable interface   
class CallableInterface implements Callable<Object> {     
      
    // override the call() method      
    @Override     
      
    public Object call() throws Exception {     
          
        //create an instance of the  Random class      
        Random obj = new Random();     
          
        //generate a random number between 0-10   
        Integer number = obj.nextInt(10);     
          
        //delay thread for some random time     
        Thread.sleep(number * 1000);     
          
        //return the object having the generated random number     
        return number;     
    }     
}     
   
// create CallableFutureExample class   
public class CallableFutureExample{   
      
    //main() method start   
    @SuppressWarnings({ "unchecked", "rawtypes" })   
      
    public static void main(String args[]) throws InterruptedException, ExecutionException {   
          
        //create an array of FutureTask   
        //A concrete class having implementation of both Runnable and Future is called FutureTask   
        FutureTask[] returnedTask = new FutureTask[5];   
          
        //use for loop   
        for(int i = 0; i < 5; i++) {   
            //create an instance of Callable   
            Callable callableObj = new CallableInterface();   
              
            //create an instance of FutureTask with Callable   
            returnedTask[i] = new FutureTask(callableObj);   
              
            // create a Thread with FutureTask   
            Thread thread = new Thread(returnedTask[i]);   
              
            thread.start();   
        }   
          
        //use for loop for printing returned value of each callable   
        for(int j = 0; j < 5; j++) {   
            // use get() method of FutureTask to print the returned value   
            System.out.println("Callable["+j+"] ===> "+returnedTask[j].get());   
        }   
    }   
}  
```

Let's take another example in which we will use only the Runnable interface.

**RunnableExample.java**

```java
//import required classes and package if any   
import java.util.Random;     
   
//create class RunnableInterface that implements Runnable interface   
class RunnableInterface implements Runnable {   
      
    // create a shared Object for storing result   
    private Object result = null;   
      
    @Override   
    public void run() {   
          
        //create an instance of Random class for generating random number   
        Random obj = new Random();   
          
        // generate random number using Random class   
        Integer number = obj.nextInt(10);   
          
        // use try-catch because Runnable doesn't throw any Exception   
        try {   
            Thread.sleep(number * 10);   
        }catch(InterruptedException exception) {   
            exception.printStackTrace();   
        }   
          
        // store the returned value in result after completion   
        result = number;   
          
        // wake up threads blocked on the get() method    
        synchronized(this) {   
            notifyAll();   
        }   
    }   
      
    // get() method for returning the result   
    public synchronized Object get() throws InterruptedException{   
          
        while(result == null) {   
            wait();   
        }   
        return result;   
    }   
}     
   
//create RunnableExample class   
public class RunnableExample {   
      
    //main() method start   
    public static void main(String args[]) throws InterruptedException {   
          
        //create an array of RunnableInterface   
        RunnableInterface[] tasks = new RunnableInterface[5];   
          
        //use for loop   
        for(int i = 0; i < 5; i++) {   
            //create an instance of RunnableInterface   
            tasks[i] = new RunnableInterface();   
              
            // create a Thread with RunnableInterface   
            Thread thread = new Thread(tasks[i]);   
              
            thread.start();   
        }   
          
        //use for loop for printing returned value of each Runnable   
        for(int j = 0; j < 5; j++) {   
            // use get() method to print the returned value   
            System.out.println("Runnable["+j+"] ===> "+tasks[j].get());   
        }   
    }   
}  
```

# What is the difference between Callable and Runnable interface explain with an example.

In Java, both the `Callable` and `Runnable` interfaces are designed to represent tasks that can be executed by multiple threads. However, there are key differences between the two:

1. **Return Value**:
   - `Runnable`: This interface does not return a result. Its `run` method is void and does not throw any checked exceptions.
   - `Callable`: This interface can return a result and can throw a checked exception. It has a `call` method that returns a generic type `V`.

2. **Method Signature**:
   - `Runnable`:
     ```java
     public interface Runnable {
         void run();
     }
     ```
   - `Callable`:
     ```java
     public interface Callable<V> {
         V call() throws Exception;
     }
     ```

3. **Usage in Thread Pool**:
   - Both can be used to represent tasks that can be executed by a thread pool, but `Callable` is typically used when the task needs to return a result.

### Example

**Using Runnable**:

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class RunnableExample {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(2);

        Runnable task = new Runnable() {
            @Override
            public void run() {
                System.out.println("Runnable Task executed");
            }
        };

        executor.submit(task);
        executor.shutdown();
    }
}
```

**Using Callable**:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class CallableExample {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newFixedThreadPool(2);

        Callable<String> task = new Callable<String>() {
            @Override
            public String call() throws Exception {
                return "Callable Task executed";
            }
        };

        Future<String> future = executor.submit(task);
        
        try {
            // Retrieve the result of the task
            String result = future.get();
            System.out.println(result);
        } catch (Exception e) {
            e.printStackTrace();
        }

        executor.shutdown();
    }
}
```

### Key Points

- **Runnable**: Use this when you don't need to return a result or throw a checked exception.
- **Callable**: Use this when you need to return a result or handle a checked exception.

### Summary

- **Runnable** is simpler and used for tasks that don't return a result.
- **Callable** is more flexible and is used for tasks that need to return a result or throw exceptions.

# difference between implementation of Runnable and Callable interface in java explain with an example.

### Implementation of `Runnable` and `Callable` Interface in Java

#### Runnable Implementation

The `Runnable` interface is simple and straightforward. It defines a single method, `run()`, that does not return any result and does not throw any checked exceptions. Here is an example of how to implement and use the `Runnable` interface:

```java
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;

public class RunnableExample {
    public static void main(String[] args) {
        // Create a fixed thread pool with 2 threads
        ExecutorService executor = Executors.newFixedThreadPool(2);

        // Create a Runnable task
        Runnable task = new Runnable() {
            @Override
            public void run() {
                System.out.println("Runnable Task executed");
            }
        };

        // Submit the task to the executor
        executor.submit(task);

        // Shutdown the executor
        executor.shutdown();
    }
}
```

In this example:
- A `Runnable` task is created by implementing the `run` method.
- The task is submitted to an `ExecutorService` for execution.

#### Callable Implementation

The `Callable` interface is more flexible. It defines a single method, `call()`, that can return a result and throw a checked exception. Here is an example of how to implement and use the `Callable` interface:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class CallableExample {
    public static void main(String[] args) {
        // Create a fixed thread pool with 2 threads
        ExecutorService executor = Executors.newFixedThreadPool(2);

        // Create a Callable task
        Callable<String> task = new Callable<String>() {
            @Override
            public String call() throws Exception {
                return "Callable Task executed";
            }
        };

        // Submit the task to the executor and get a Future object
        Future<String> future = executor.submit(task);

        try {
            // Retrieve the result of the task
            String result = future.get();
            System.out.println(result);
        } catch (Exception e) {
            e.printStackTrace();
        }

        // Shutdown the executor
        executor.shutdown();
    }
}
```

In this example:
- A `Callable` task is created by implementing the `call` method.
- The task is submitted to an `ExecutorService`, which returns a `Future` object.
- The result of the task is retrieved using the `Future.get()` method.

### Key Differences in Implementation

1. **Method Definition**:
   - `Runnable`: 
     ```java
     @Override
     public void run() {
         // Task implementation
     }
     ```
   - `Callable`: 
     ```java
     @Override
     public V call() throws Exception {
         // Task implementation
         return result;
     }
     ```

2. **Return Type**:
   - `Runnable` does not return any value (void).
   - `Callable` returns a value of type `V`.

3. **Exception Handling**:
   - `Runnable` does not throw any checked exceptions.
   - `Callable` can throw checked exceptions.

4. **Usage**:
   - `Runnable` is used when you do not need to return a result or handle checked exceptions.
   - `Callable` is used when you need to return a result or handle checked exceptions.

### Summary

- **Runnable**: Implement the `run` method, do not return a result, do not throw checked exceptions. Suitable for simple tasks where the outcome is not needed.
- **Callable**: Implement the `call` method, return a result, can throw checked exceptions. Suitable for tasks where you need a result or need to handle exceptions.

# How we can create a single thread using Runnable and Callable interface explain with an example.

To create a single thread using the `Runnable` and `Callable` interfaces, you can use the `Thread` class for `Runnable` and the `ExecutorService` for `Callable`. Here are examples for both:

### Using Runnable

1. **Create a Runnable Implementation**:
2. **Create a Thread and Start It**:

```java
public class SingleThreadRunnableExample {
    public static void main(String[] args) {
        // Create a Runnable task
        Runnable task = new Runnable() {
            @Override
            public void run() {
                System.out.println("Runnable Task executed by thread: " + Thread.currentThread().getName());
            }
        };

        // Create a Thread with the Runnable task
        Thread thread = new Thread(task);

        // Start the Thread
        thread.start();

        // Optionally, wait for the thread to complete
        try {
            thread.join();
        } catch (InterruptedException e) {
            e.printStackTrace();
        }
    }
}
```

### Using Callable

1. **Create a Callable Implementation**:
2. **Use ExecutorService to Submit the Task and Retrieve the Result**:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class SingleThreadCallableExample {
    public static void main(String[] args) {
        // Create a Callable task
        Callable<String> task = new Callable<String>() {
            @Override
            public String call() throws Exception {
                return "Callable Task executed by thread: " + Thread.currentThread().getName();
            }
        };

        // Create a single-thread executor
        ExecutorService executor = Executors.newSingleThreadExecutor();

        // Submit the Callable task and get a Future object
        Future<String> future = executor.submit(task);

        try {
            // Retrieve the result of the task
            String result = future.get();
            System.out.println(result);
        } catch (Exception e) {
            e.printStackTrace();
        } finally {
            // Shutdown the executor
            executor.shutdown();
        }
    }
}
```

### Key Points

- **Runnable Example**:
  - A `Runnable` task is created by implementing the `run` method.
  - A `Thread` object is created with the `Runnable` task.
  - The thread is started using the `start` method.

- **Callable Example**:
  - A `Callable` task is created by implementing the `call` method.
  - An `ExecutorService` with a single thread is created using `Executors.newSingleThreadExecutor()`.
  - The `Callable` task is submitted to the executor, which returns a `Future` object.
  - The result of the task is retrieved using the `Future.get()` method.
  - The executor is shut down after the task is complete.

Both examples demonstrate how to execute a task in a single thread using the `Runnable` and `Callable` interfaces in Java.

# Is this possible to use Callable interface with Thread class to create a thread?

The `Thread` class in Java does not directly support the `Callable` interface. The `Thread` class is designed to work with the `Runnable` interface. However, you can still use the `Callable` interface to create a thread by wrapping the `Callable` task in a `Runnable`. This can be done by using a `FutureTask`, which implements both `Runnable` and `Future`.

Here's an example of how to use the `Callable` interface with the `Thread` class:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

public class CallableWithThreadExample {
    public static void main(String[] args) {
        // Create a Callable task
        Callable<String> callableTask = new Callable<String>() {
            @Override
            public String call() throws Exception {
                return "Callable Task executed by thread: " + Thread.currentThread().getName();
            }
        };

        // Wrap the Callable task in a FutureTask
        FutureTask<String> futureTask = new FutureTask<>(callableTask);

        // Create a Thread with the FutureTask
        Thread thread = new Thread(futureTask);

        // Start the Thread
        thread.start();

        try {
            // Retrieve the result of the task
            String result = futureTask.get();
            System.out.println(result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

### Explanation

1. **Create a Callable Task**:
   - Implement the `Callable` interface by overriding the `call` method.

2. **Wrap the Callable in a FutureTask**:
   - Create a `FutureTask` object, passing the `Callable` task to its constructor. `FutureTask` implements both `Runnable` and `Future`.

3. **Create and Start a Thread**:
   - Create a `Thread` object, passing the `FutureTask` to the `Thread` constructor.
   - Start the thread using the `start` method.

4. **Retrieve the Result**:
   - Use the `get` method of the `FutureTask` to retrieve the result of the `Callable` task. This method blocks until the task is complete.

### Key Points

- `Callable` cannot be directly used with the `Thread` class.
- `FutureTask` is a bridge between `Runnable` and `Callable`.
- `FutureTask` can be used to wrap a `Callable` and then be executed by a `Thread`.

This approach allows you to take advantage of the `Callable` interface's ability to return results and throw exceptions, while still using the `Thread` class to execute the task.

# What is future, futureTask explain with an example how they are used?

### Future and FutureTask in Java

#### Future

The `Future` interface represents the result of an asynchronous computation. It provides methods to check if the computation is complete, to wait for its completion, and to retrieve the result of the computation. If necessary, the computation can be canceled.

Key methods in the `Future` interface:
- `boolean cancel(boolean mayInterruptIfRunning)`: Attempts to cancel the execution.
- `boolean isCancelled()`: Returns `true` if the execution was canceled.
- `boolean isDone()`: Returns `true` if the execution is complete.
- `V get()`: Waits if necessary for the computation to complete and then retrieves the result.
- `V get(long timeout, TimeUnit unit)`: Waits for the computation to complete within the specified timeout.

#### FutureTask

`FutureTask` is a concrete implementation of the `Future` interface and also implements the `Runnable` interface. This allows it to be used as a `Runnable` and be submitted to an executor. It wraps a `Callable` or `Runnable` and can be used to obtain the result of the asynchronous computation.

### Example: Using Future and FutureTask

Here's an example that demonstrates how to use `Future` and `FutureTask`:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import java.util.concurrent.FutureTask;

public class FutureAndFutureTaskExample {
    public static void main(String[] args) {
        // Create an ExecutorService with a single thread
        ExecutorService executor = Executors.newSingleThreadExecutor();

        // Create a Callable task
        Callable<String> callableTask = new Callable<String>() {
            @Override
            public String call() throws Exception {
                Thread.sleep(2000); // Simulate long-running task
                return "Callable Task executed by thread: " + Thread.currentThread().getName();
            }
        };

        // Use FutureTask to wrap the Callable
        FutureTask<String> futureTask = new FutureTask<>(callableTask);

        // Submit the FutureTask to the executor
        executor.submit(futureTask);

        // Alternatively, you can use Future directly
        // Future<String> future = executor.submit(callableTask);

        try {
            // Check if the task is done
            if (!futureTask.isDone()) {
                System.out.println("Task is not completed yet...");
            }

            // Retrieve the result of the task
            String result = futureTask.get(); // This will block until the task is complete
            System.out.println(result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            // Shutdown the executor
            executor.shutdown();
        }
    }
}
```

### Explanation

1. **Create an ExecutorService**:
   - An `ExecutorService` with a single thread is created using `Executors.newSingleThreadExecutor()`.

2. **Create a Callable Task**:
   - A `Callable` task is created by implementing the `call` method.

3. **Wrap the Callable in a FutureTask**:
   - A `FutureTask` object is created, passing the `Callable` task to its constructor. `FutureTask` implements both `Runnable` and `Future`.

4. **Submit the FutureTask to the Executor**:
   - The `FutureTask` is submitted to the executor using the `submit` method.

5. **Retrieve the Result**:
   - The `get` method of the `FutureTask` is called to retrieve the result of the `Callable` task. This method blocks until the task is complete.

6. **Shutdown the Executor**:
   - The executor is shut down using the `shutdown` method.

### Key Points

- `Future` represents the result of an asynchronous computation.
- `FutureTask` is a concrete implementation of `Future` and `Runnable`, used to wrap a `Callable` or `Runnable`.
- `FutureTask` can be used with an `ExecutorService` to execute a `Callable` or `Runnable` task and retrieve the result asynchronously.

This example demonstrates how `Future` and `FutureTask` can be used to manage and retrieve the results of asynchronous tasks in Java.

# All Methods of Future

The `Future` interface in Java provides several methods to manage the result of an asynchronous computation. Here is a list of all the methods in the `Future` interface along with their explanations:

1. **`boolean cancel(boolean mayInterruptIfRunning)`**:
   - Attempts to cancel the execution of the task.
   - If the task has already completed or has been canceled, this method returns `false`.
   - If the task is currently running and `mayInterruptIfRunning` is `true`, the thread executing the task is interrupted.

2. **`boolean isCancelled()`**:
   - Returns `true` if the task was canceled before it completed normally.

3. **`boolean isDone()`**:
   - Returns `true` if the task completed, either normally or via cancellation.

4. **`V get()` throws InterruptedException, ExecutionException**:
   - Waits if necessary for the task to complete, and then retrieves its result.
   - Throws `InterruptedException` if the current thread was interrupted while waiting.
   - Throws `ExecutionException` if the computation threw an exception.

5. **`V get(long timeout, TimeUnit unit)` throws InterruptedException, ExecutionException, TimeoutException**:
   - Waits if necessary for at most the given time for the task to complete, and then retrieves its result if available.
   - Throws `InterruptedException` if the current thread was interrupted while waiting.
   - Throws `ExecutionException` if the computation threw an exception.
   - Throws `TimeoutException` if the wait timed out before the task completed.

### Example Usage of Future Methods

Here's an example that demonstrates the use of all the `Future` methods:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.TimeoutException;

public class FutureMethodsExample {
    public static void main(String[] args) {
        // Create an ExecutorService
        ExecutorService executor = Executors.newSingleThreadExecutor();

        // Create a Callable task
        Callable<String> callableTask = new Callable<String>() {
            @Override
            public String call() throws Exception {
                Thread.sleep(2000); // Simulate long-running task
                return "Callable Task executed by thread: " + Thread.currentThread().getName();
            }
        };

        // Submit the Callable task to the executor
        Future<String> future = executor.submit(callableTask);

        try {
            // Check if the task is done
            System.out.println("Is task done? " + future.isDone());

            // Attempt to cancel the task (will not cancel because it is already running)
            boolean cancelResult = future.cancel(true);
            System.out.println("Cancellation result: " + cancelResult);

            // Check if the task was cancelled
            System.out.println("Is task cancelled? " + future.isCancelled());

            // Retrieve the result of the task (blocking)
            String result = future.get();
            System.out.println("Result: " + result);

            // Retrieve the result of the task with a timeout (this will not block because the task is already complete)
            String resultWithTimeout = future.get(1, TimeUnit.SECONDS);
            System.out.println("Result with timeout: " + resultWithTimeout);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } catch (TimeoutException e) {
            System.out.println("Task timed out");
        } finally {
            // Shutdown the executor
            executor.shutdown();
        }
    }
}
```

### Explanation

1. **Submit the Callable Task**:
   - The `Callable` task is submitted to the `ExecutorService`, which returns a `Future` object.

2. **Check if the Task is Done**:
   - The `isDone` method checks if the task is complete.

3. **Attempt to Cancel the Task**:
   - The `cancel` method attempts to cancel the task. In this case, it will return `false` because the task is already running.

4. **Check if the Task was Cancelled**:
   - The `isCancelled` method checks if the task was canceled.

5. **Retrieve the Result**:
   - The `get` method blocks until the task is complete and then retrieves the result.

6. **Retrieve the Result with a Timeout**:
   - The `get` method with a timeout waits for the specified time for the task to complete and then retrieves the result if available.

7. **Shutdown the Executor**:
   - The executor is shut down using the `shutdown` method.

This example demonstrates how to use all the methods of the `Future` interface to manage and retrieve the result of an asynchronous task in Java.

# All type of constructor of FutureTask

`FutureTask` in Java provides multiple constructors to create instances. These constructors allow you to create a `FutureTask` that can wrap either a `Callable` or a `Runnable` task.

Here are the constructors of `FutureTask`:

1. **Constructor with Callable**:
   ```java
   public FutureTask(Callable<V> callable)
   ```
   - Creates a `FutureTask` that will run the given `Callable` task.
   - The result of the `Callable` will be the result of the `FutureTask`.

2. **Constructor with Runnable and Result**:
   ```java
   public FutureTask(Runnable runnable, V result)
   ```
   - Creates a `FutureTask` that will run the given `Runnable` task.
   - The `result` is the result that the `FutureTask` returns upon completion of the `Runnable` task.

### Example Usage of FutureTask Constructors

Here's an example that demonstrates how to use both constructors of `FutureTask`:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

public class FutureTaskConstructorsExample {
    public static void main(String[] args) {
        // Using the constructor with Callable
        Callable<String> callableTask = new Callable<String>() {
            @Override
            public String call() throws Exception {
                Thread.sleep(2000); // Simulate long-running task
                return "Callable Task executed by thread: " + Thread.currentThread().getName();
            }
        };
        
        FutureTask<String> futureTaskWithCallable = new FutureTask<>(callableTask);
        Thread threadWithCallable = new Thread(futureTaskWithCallable);
        threadWithCallable.start();

        // Using the constructor with Runnable and Result
        Runnable runnableTask = new Runnable() {
            @Override
            public void run() {
                System.out.println("Runnable Task executed by thread: " + Thread.currentThread().getName());
            }
        };
        
        FutureTask<String> futureTaskWithRunnable = new FutureTask<>(runnableTask, "Runnable Task Result");
        Thread threadWithRunnable = new Thread(futureTaskWithRunnable);
        threadWithRunnable.start();

        try {
            // Retrieve and print the result of the Callable task
            String callableResult = futureTaskWithCallable.get();
            System.out.println("Result from Callable task: " + callableResult);

            // Retrieve and print the result of the Runnable task
            String runnableResult = futureTaskWithRunnable.get();
            System.out.println("Result from Runnable task: " + runnableResult);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

### Explanation

1. **Using the Constructor with Callable**:
   - A `Callable` task is created and passed to the `FutureTask` constructor.
   - A `Thread` is created with the `FutureTask` and started.
   - The result of the `Callable` task is retrieved using the `get` method of `FutureTask`.

2. **Using the Constructor with Runnable and Result**:
   - A `Runnable` task is created and passed to the `FutureTask` constructor along with a result.
   - A `Thread` is created with the `FutureTask` and started.
   - The result specified during the creation of the `FutureTask` is retrieved using the `get` method.

### Key Points

- **Constructor with Callable**: Useful when you need the task to return a result upon completion.
- **Constructor with Runnable and Result**: Useful when you have a `Runnable` task that doesn't inherently produce a result, but you want to provide a predefined result upon its completion.

By using these constructors, you can create `FutureTask` instances to manage asynchronous tasks that return results or simply execute `Runnable` tasks with a predefined result.

# Why FutureTask is introduce in java

`FutureTask` was introduced in Java as part of the `java.util.concurrent` package to provide a flexible and powerful mechanism for handling asynchronous computations. It combines the functionalities of both the `Runnable` and `Future` interfaces, allowing for more versatile task management and result handling. Here are some key reasons why `FutureTask` was introduced:

### Key Reasons for the Introduction of `FutureTask`

1. **Combining `Runnable` and `Future`**:
   - `FutureTask` implements both `Runnable` and `Future` interfaces, allowing it to be used as a `Runnable` for task execution and as a `Future` for result handling. This dual capability simplifies the process of running tasks and obtaining their results.

2. **Result Handling**:
   - With `FutureTask`, you can run a task asynchronously and retrieve its result once it completes. It provides methods to check if the task is done, wait for its completion, and retrieve the result, or handle exceptions if any occurred during execution.

3. **Task Cancellation**:
   - `FutureTask` supports task cancellation. You can attempt to cancel the execution of a task if it has not yet completed, providing better control over long-running or unnecessary tasks.

4. **Flexible Task Submission**:
   - `FutureTask` can wrap both `Callable` and `Runnable` tasks. This allows for greater flexibility in task definitions, whether they need to return a result or simply perform an action.

5. **Synchronization and Concurrency**:
   - `FutureTask` provides built-in synchronization, ensuring that the task's result is accessed in a thread-safe manner. It is particularly useful in concurrent programming, where multiple threads may be involved in executing tasks and accessing results.

### Example Usage of `FutureTask`

Here's an example demonstrating the use of `FutureTask` to handle an asynchronous computation:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.FutureTask;

public class FutureTaskExample {
    public static void main(String[] args) {
        // Create a Callable task
        Callable<String> callableTask = new Callable<String>() {
            @Override
            public String call() throws Exception {
                Thread.sleep(2000); // Simulate long-running task
                return "Callable Task executed by thread: " + Thread.currentThread().getName();
            }
        };

        // Wrap the Callable in a FutureTask
        FutureTask<String> futureTask = new FutureTask<>(callableTask);

        // Create an ExecutorService to run the task
        ExecutorService executor = Executors.newSingleThreadExecutor();
        executor.submit(futureTask);

        try {
            // Check if the task is done
            if (!futureTask.isDone()) {
                System.out.println("Task is not completed yet...");
            }

            // Retrieve the result of the task (blocking)
            String result = futureTask.get();
            System.out.println("Result: " + result);

        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            // Shutdown the executor
            executor.shutdown();
        }
    }
}
```

### Explanation

1. **Callable Task**:
   - A `Callable` task is created to simulate a long-running computation that returns a result.

2. **FutureTask**:
   - The `Callable` task is wrapped in a `FutureTask`.

3. **ExecutorService**:
   - An `ExecutorService` is created to execute the `FutureTask`.

4. **Task Execution**:
   - The `FutureTask` is submitted to the executor for execution.

5. **Result Retrieval**:
   - The `get` method of `FutureTask` is used to retrieve the result of the computation, blocking until the task is complete.

### Key Points

- `FutureTask` simplifies asynchronous programming by combining task execution and result handling.
- It provides methods for task cancellation, synchronization, and flexible task submission.
- By implementing both `Runnable` and `Future`, `FutureTask` can be used in various concurrency scenarios, enhancing the Java concurrency utilities.

Overall, `FutureTask` was introduced to provide a more efficient and versatile way to handle asynchronous tasks and their results in Java's concurrent programming environment.

# list all the methods of FutureTask

The `FutureTask` class in Java provides several methods that allow you to control and retrieve the results of asynchronous tasks. Below are all the methods of the `FutureTask` class, along with a brief explanation of each:

### FutureTask Methods

1. **Constructors:**
   - `FutureTask(Callable<V> callable)`: Creates a `FutureTask` that will execute the given `Callable` task.
   - `FutureTask(Runnable runnable, V result)`: Creates a `FutureTask` that will execute the given `Runnable` task and return the given result upon completion.

2. **cancel(boolean mayInterruptIfRunning)**:
   - Attempts to cancel the execution of this task.
   - If the task has already completed, has already been canceled, or could not be canceled for some other reason, this attempt will fail.
   - Parameters: `mayInterruptIfRunning` - `true` if the thread executing this task should be interrupted; otherwise, in-progress tasks are allowed to complete.
   - Returns: `true` if the task was canceled successfully.

3. **get()**:
   - Waits if necessary for the computation to complete, and then retrieves its result.
   - Returns: The computed result.
   - Throws: `InterruptedException`, `ExecutionException`.

4. **get(long timeout, TimeUnit unit)**:
   - Waits if necessary for at most the given time for the computation to complete, and then retrieves its result, if available.
   - Parameters: `timeout` - the maximum time to wait, `unit` - the time unit of the `timeout` argument.
   - Returns: The computed result.
   - Throws: `InterruptedException`, `ExecutionException`, `TimeoutException`.

5. **isCancelled()**:
   - Returns `true` if this task was canceled before it completed normally.
   - Returns: `true` if this task was canceled before it completed.

6. **isDone()**:
   - Returns `true` if this task completed.
   - Completion may be due to normal termination, an exception, or cancellation.
   - Returns: `true` if this task completed.

7. **run()**:
   - Sets this `FutureTask` as the task to be executed by the thread.
   - This method is invoked when the thread starts executing.

8. **runAndReset()**:
   - Runs this task to completion if not canceled, and then resets this task to its initial state if canceling is still possible.
   - Returns `true` if the task was run and reset successfully.

### Example Usage

Here's an example demonstrating the usage of some of the `FutureTask` methods:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.FutureTask;
import java.util.concurrent.TimeUnit;
import java.util.concurrent.TimeoutException;

public class FutureTaskExample {
    public static void main(String[] args) {
        // Create a Callable task
        Callable<String> callableTask = new Callable<String>() {
            @Override
            public String call() throws Exception {
                Thread.sleep(2000); // Simulate long-running task
                return "Callable Task executed by thread: " + Thread.currentThread().getName();
            }
        };

        // Wrap the Callable in a FutureTask
        FutureTask<String> futureTask = new FutureTask<>(callableTask);

        // Create an ExecutorService to run the task
        ExecutorService executor = Executors.newSingleThreadExecutor();
        executor.submit(futureTask);

        try {
            // Check if the task is done
            System.out.println("Is task done? " + futureTask.isDone());

            // Attempt to cancel the task (will not cancel because it is already running)
            boolean cancelResult = futureTask.cancel(true);
            System.out.println("Cancellation result: " + cancelResult);

            // Check if the task was cancelled
            System.out.println("Is task cancelled? " + futureTask.isCancelled());

            // Retrieve the result of the task (blocking)
            String result = futureTask.get();
            System.out.println("Result: " + result);

            // Retrieve the result of the task with a timeout (this will not block because the task is already complete)
            String resultWithTimeout = futureTask.get(1, TimeUnit.SECONDS);
            System.out.println("Result with timeout: " + resultWithTimeout);
        } catch (InterruptedException | ExecutionException | TimeoutException e) {
            e.printStackTrace();
        } finally {
            // Shutdown the executor
            executor.shutdown();
        }
    }
}
```

### Explanation

1. **Creating a Callable Task**:
   - A `Callable` task is created to simulate a long-running computation.

2. **Wrapping in FutureTask**:
   - The `Callable` task is wrapped in a `FutureTask`.

3. **Submitting to ExecutorService**:
   - The `FutureTask` is submitted to an `ExecutorService`.

4. **Checking Task Status**:
   - Methods like `isDone` and `isCancelled` are used to check the status of the task.

5. **Cancelling the Task**:
   - The `cancel` method is used to attempt task cancellation.

6. **Retrieving the Result**:
   - The `get` method is used to retrieve the result of the task, either blocking or with a timeout.

This example demonstrates how to use the various methods provided by `FutureTask` to manage and retrieve the results of asynchronous tasks in Java.

# Real Time Business Example of FutureTask?

Sure, let's consider a real-time business scenario where `FutureTask` can be particularly useful. In this example, we'll look at an e-commerce application that needs to process multiple tasks asynchronously, such as fetching product details, calculating shipping costs, and checking inventory status. These tasks can be executed in parallel to optimize performance and reduce response time for the user.

### Scenario: E-Commerce Order Processing

Imagine an e-commerce platform where a customer places an order, and the system needs to perform several tasks concurrently:

1. Fetch product details from a database.
2. Calculate shipping costs based on the delivery address.
3. Check the inventory status of the ordered items.

By using `FutureTask`, we can execute these tasks in parallel, improving the overall efficiency and user experience.

### Implementation

Here's how you might implement this using `FutureTask`:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.FutureTask;

class ProductDetails {
    // Assume some properties and methods for product details
}

class ShippingCost {
    // Assume some properties and methods for shipping cost calculation
}

class InventoryStatus {
    // Assume some properties and methods for inventory status
}

public class ECommerceOrderProcessing {
    public static void main(String[] args) {
        // Create a thread pool
        ExecutorService executor = Executors.newFixedThreadPool(3);

        // Task to fetch product details
        Callable<ProductDetails> fetchProductDetailsTask = new Callable<ProductDetails>() {
            @Override
            public ProductDetails call() throws Exception {
                // Simulate fetching product details from the database
                Thread.sleep(1000);
                System.out.println("Fetched product details");
                return new ProductDetails();
            }
        };

        // Task to calculate shipping cost
        Callable<ShippingCost> calculateShippingCostTask = new Callable<ShippingCost>() {
            @Override
            public ShippingCost call() throws Exception {
                // Simulate calculating shipping cost
                Thread.sleep(2000);
                System.out.println("Calculated shipping cost");
                return new ShippingCost();
            }
        };

        // Task to check inventory status
        Callable<InventoryStatus> checkInventoryStatusTask = new Callable<InventoryStatus>() {
            @Override
            public InventoryStatus call() throws Exception {
                // Simulate checking inventory status
                Thread.sleep(1500);
                System.out.println("Checked inventory status");
                return new InventoryStatus();
            }
        };

        // Wrap the tasks in FutureTask
        FutureTask<ProductDetails> futureProductDetails = new FutureTask<>(fetchProductDetailsTask);
        FutureTask<ShippingCost> futureShippingCost = new FutureTask<>(calculateShippingCostTask);
        FutureTask<InventoryStatus> futureInventoryStatus = new FutureTask<>(checkInventoryStatusTask);

        // Submit tasks to the executor
        executor.submit(futureProductDetails);
        executor.submit(futureShippingCost);
        executor.submit(futureInventoryStatus);

        try {
            // Wait for all tasks to complete and retrieve the results
            ProductDetails productDetails = futureProductDetails.get();
            ShippingCost shippingCost = futureShippingCost.get();
            InventoryStatus inventoryStatus = futureInventoryStatus.get();

            // Combine the results and proceed with order processing
            System.out.println("Order processing completed with product details, shipping cost, and inventory status.");

        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            // Shutdown the executor
            executor.shutdown();
        }
    }
}
```

### Explanation

1. **Task Definitions**:
   - We define three `Callable` tasks for fetching product details, calculating shipping costs, and checking inventory status.

2. **Wrapping in FutureTask**:
   - Each `Callable` task is wrapped in a `FutureTask`.

3. **Submitting Tasks**:
   - The `FutureTask` instances are submitted to an `ExecutorService` for execution.

4. **Retrieving Results**:
   - The `get` method of each `FutureTask` is called to retrieve the results once the tasks are complete. This method blocks until the task is finished.

5. **Order Processing**:
   - After retrieving the results, we can proceed with order processing, using the fetched product details, calculated shipping cost, and inventory status.

6. **Executor Shutdown**:
   - Finally, we shut down the `ExecutorService`.

### Benefits

- **Parallel Execution**: By executing tasks in parallel, the overall response time is reduced, enhancing user experience.
- **Efficient Resource Utilization**: Using a thread pool allows for efficient utilization of system resources.
- **Simplified Asynchronous Programming**: `FutureTask` provides a straightforward way to handle asynchronous computations and retrieve results.

This example demonstrates how `FutureTask` can be effectively used in a real-time business scenario to improve the performance and responsiveness of an e-commerce application.

# Real Time Example of Future

Let's consider a real-time business scenario where `Future` can be used effectively. We'll look at a scenario in a financial application where multiple independent calculations or data fetches need to be performed in parallel to generate a consolidated report. 

### Scenario: Financial Data Processing

Imagine a financial application that generates a report based on multiple independent data sources. These data sources might include fetching stock prices, retrieving exchange rates, and getting market news. These tasks can be performed in parallel, and once all the data is retrieved, it can be processed to generate the final report.

### Implementation

Here's how you might implement this using `Future`:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

class StockPrice {
    // Assume some properties and methods for stock price details
}

class ExchangeRate {
    // Assume some properties and methods for exchange rate details
}

class MarketNews {
    // Assume some properties and methods for market news
}

public class FinancialDataProcessing {
    public static void main(String[] args) {
        // Create a thread pool
        ExecutorService executor = Executors.newFixedThreadPool(3);

        // Task to fetch stock prices
        Callable<StockPrice> fetchStockPriceTask = new Callable<StockPrice>() {
            @Override
            public StockPrice call() throws Exception {
                // Simulate fetching stock prices from a data source
                Thread.sleep(2000);
                System.out.println("Fetched stock prices");
                return new StockPrice();
            }
        };

        // Task to fetch exchange rates
        Callable<ExchangeRate> fetchExchangeRateTask = new Callable<ExchangeRate>() {
            @Override
            public ExchangeRate call() throws Exception {
                // Simulate fetching exchange rates from a data source
                Thread.sleep(1500);
                System.out.println("Fetched exchange rates");
                return new ExchangeRate();
            }
        };

        // Task to fetch market news
        Callable<MarketNews> fetchMarketNewsTask = new Callable<MarketNews>() {
            @Override
            public MarketNews call() throws Exception {
                // Simulate fetching market news from a data source
                Thread.sleep(1000);
                System.out.println("Fetched market news");
                return new MarketNews();
            }
        };

        // Submit tasks to the executor and get Futures
        Future<StockPrice> futureStockPrice = executor.submit(fetchStockPriceTask);
        Future<ExchangeRate> futureExchangeRate = executor.submit(fetchExchangeRateTask);
        Future<MarketNews> futureMarketNews = executor.submit(fetchMarketNewsTask);

        try {
            // Retrieve the results of the tasks
            StockPrice stockPrice = futureStockPrice.get();
            ExchangeRate exchangeRate = futureExchangeRate.get();
            MarketNews marketNews = futureMarketNews.get();

            // Process the results to generate the final report
            System.out.println("Generating financial report with fetched data.");

        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            // Shutdown the executor
            executor.shutdown();
        }
    }
}
```

### Explanation

1. **Task Definitions**:
   - Three `Callable` tasks are defined for fetching stock prices, exchange rates, and market news.

2. **Submitting Tasks**:
   - Each `Callable` task is submitted to an `ExecutorService`, and a `Future` object is obtained for each task.

3. **Retrieving Results**:
   - The `get` method of each `Future` is called to retrieve the results once the tasks are complete. This method blocks until the task is finished.

4. **Processing Results**:
   - After retrieving the results, we can process the data to generate the final financial report.

5. **Executor Shutdown**:
   - Finally, the `ExecutorService` is shut down to free up resources.

### Benefits

- **Parallel Execution**: By executing tasks in parallel, the overall time to generate the report is reduced.
- **Efficient Resource Utilization**: Using a thread pool allows for efficient utilization of system resources.
- **Simplified Asynchronous Programming**: `Future` provides a straightforward way to handle asynchronous computations and retrieve results.

This example demonstrates how `Future` can be effectively used in a real-time business scenario to improve the performance and responsiveness of a financial data processing application.

# Real Time Complete Example of Future.

Sure, let's dive into a complete real-time example using `Future` in Java. We'll expand on the financial data processing scenario where an application needs to fetch data from multiple sources to generate a comprehensive financial report. This example will demonstrate how `Future` can be used to manage asynchronous tasks effectively.

### Scenario: Comprehensive Financial Report Generation

In this scenario, we need to:
1. Fetch stock prices from a financial API.
2. Retrieve exchange rates from a currency exchange service.
3. Get market news from a news service.

Once all data is retrieved, it will be processed to generate a financial report.

### Implementation

Here's the complete implementation using `Future`:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

class StockPrice {
    private double price;

    public StockPrice(double price) {
        this.price = price;
    }

    public double getPrice() {
        return price;
    }

    @Override
    public String toString() {
        return "StockPrice{price=" + price + '}';
    }
}

class ExchangeRate {
    private double rate;

    public ExchangeRate(double rate) {
        this.rate = rate;
    }

    public double getRate() {
        return rate;
    }

    @Override
    public String toString() {
        return "ExchangeRate{rate=" + rate + '}';
    }
}

class MarketNews {
    private String news;

    public MarketNews(String news) {
        this.news = news;
    }

    public String getNews() {
        return news;
    }

    @Override
    public String toString() {
        return "MarketNews{news='" + news + "'}";
    }
}

public class FinancialDataProcessing {
    public static void main(String[] args) {
        // Create a thread pool
        ExecutorService executor = Executors.newFixedThreadPool(3);

        // Task to fetch stock prices
        Callable<StockPrice> fetchStockPriceTask = new Callable<StockPrice>() {
            @Override
            public StockPrice call() throws Exception {
                // Simulate fetching stock prices from a data source
                Thread.sleep(2000);
                System.out.println("Fetched stock prices");
                return new StockPrice(150.75);
            }
        };

        // Task to fetch exchange rates
        Callable<ExchangeRate> fetchExchangeRateTask = new Callable<ExchangeRate>() {
            @Override
            public ExchangeRate call() throws Exception {
                // Simulate fetching exchange rates from a data source
                Thread.sleep(1500);
                System.out.println("Fetched exchange rates");
                return new ExchangeRate(1.13);
            }
        };

        // Task to fetch market news
        Callable<MarketNews> fetchMarketNewsTask = new Callable<MarketNews>() {
            @Override
            public MarketNews call() throws Exception {
                // Simulate fetching market news from a data source
                Thread.sleep(1000);
                System.out.println("Fetched market news");
                return new MarketNews("Market is bullish today.");
            }
        };

        // Submit tasks to the executor and get Futures
        Future<StockPrice> futureStockPrice = executor.submit(fetchStockPriceTask);
        Future<ExchangeRate> futureExchangeRate = executor.submit(fetchExchangeRateTask);
        Future<MarketNews> futureMarketNews = executor.submit(fetchMarketNewsTask);

        try {
            // Retrieve the results of the tasks
            StockPrice stockPrice = futureStockPrice.get();
            ExchangeRate exchangeRate = futureExchangeRate.get();
            MarketNews marketNews = futureMarketNews.get();

            // Process the results to generate the final report
            System.out.println("Generating financial report with fetched data.");
            System.out.println("Stock Price: " + stockPrice);
            System.out.println("Exchange Rate: " + exchangeRate);
            System.out.println("Market News: " + marketNews);

        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            // Shutdown the executor
            executor.shutdown();
        }
    }
}
```

### Explanation

1. **Task Definitions**:
   - Three `Callable` tasks are defined to simulate fetching stock prices, exchange rates, and market news. Each task simulates a delay using `Thread.sleep` to mimic the time taken to fetch data from an external source.

2. **Submitting Tasks**:
   - Each `Callable` task is submitted to an `ExecutorService`, and a `Future` object is obtained for each task. This allows us to manage the asynchronous execution of the tasks.

3. **Retrieving Results**:
   - The `get` method of each `Future` is called to retrieve the results once the tasks are complete. This method blocks until the task is finished, ensuring that we wait for all tasks to complete before proceeding.

4. **Processing Results**:
   - After retrieving the results, we process the data to generate the final financial report. In this example, we simply print the results to the console.

5. **Executor Shutdown**:
   - Finally, we shut down the `ExecutorService` to free up resources. This is important to prevent resource leaks and to ensure that the application terminates cleanly.

### Benefits

- **Parallel Execution**: Tasks are executed in parallel, reducing the overall time to fetch all the required data.
- **Efficient Resource Utilization**: Using a thread pool allows for efficient utilization of system resources.
- **Simplified Asynchronous Programming**: `Future` provides a straightforward way to manage asynchronous computations and retrieve results, simplifying the code and making it more maintainable.

This complete example demonstrates how `Future` can be effectively used in a real-time business scenario to improve the performance and responsiveness of a financial data processing application.

# How many ways we can create a thread using Callable Interface

Creating threads using the `Callable` interface in Java can be done in a few different ways. Here are the main approaches:

1. **Using `ExecutorService` and `Future`**:
   - The most common way is to use an `ExecutorService` to submit a `Callable` task and retrieve the result using a `Future`.

2. **Using `ExecutorService` and `FutureTask`**:
   - You can also wrap the `Callable` in a `FutureTask` and submit the `FutureTask` to an `ExecutorService`.

3. **Using `Thread` with `FutureTask`**:
   - Although not typical, you can create a thread by wrapping the `Callable` in a `FutureTask` and then using a `Thread` to execute the `FutureTask`.

### 1. Using `ExecutorService` and `Future`

This is the standard approach where you submit a `Callable` to an `ExecutorService` and get back a `Future` representing the result of the computation.

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.Future;

public class CallableExample {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newSingleThreadExecutor();

        Callable<String> callableTask = () -> {
            Thread.sleep(2000);
            return "Task's execution";
        };

        Future<String> future = executor.submit(callableTask);

        try {
            String result = future.get();
            System.out.println("Result: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            executor.shutdown();
        }
    }
}
```

### 2. Using `ExecutorService` and `FutureTask`

`FutureTask` is a concrete class that implements `Runnable` and `Future`. You can use it to wrap a `Callable` and then submit it to an `ExecutorService`.

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.FutureTask;

public class CallableExample {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newSingleThreadExecutor();

        Callable<String> callableTask = () -> {
            Thread.sleep(2000);
            return "Task's execution";
        };

        FutureTask<String> futureTask = new FutureTask<>(callableTask);
        executor.submit(futureTask);

        try {
            String result = futureTask.get();
            System.out.println("Result: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            executor.shutdown();
        }
    }
}
```

### 3. Using `Thread` with `FutureTask`

Although not as common, you can use a `Thread` to execute a `FutureTask` directly. This method doesn't use an `ExecutorService`.

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.FutureTask;

public class CallableExample {
    public static void main(String[] args) {
        Callable<String> callableTask = () -> {
            Thread.sleep(2000);
            return "Task's execution";
        };

        FutureTask<String> futureTask = new FutureTask<>(callableTask);
        Thread thread = new Thread(futureTask);
        thread.start();

        try {
            String result = futureTask.get();
            System.out.println("Result: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        }
    }
}
```

### Summary

To summarize, the three main ways to create a thread using the `Callable` interface in Java are:

1. Submitting the `Callable` to an `ExecutorService` and retrieving the result with a `Future`.
2. Wrapping the `Callable` in a `FutureTask` and submitting it to an `ExecutorService`.
3. Wrapping the `Callable` in a `FutureTask` and executing it directly with a `Thread`.

Each approach has its use cases, with the first two being more common and flexible due to their integration with the `ExecutorService` framework, which provides better thread management capabilities.

# Give all the name of all implementation class of Future

The `Future` interface in Java is part of the `java.util.concurrent` package and has several known implementing classes, primarily designed to handle asynchronous task results. Here are the main implementation classes of the `Future` interface:

1. **FutureTask**
   - A general-purpose implementation of `Future` that can be used to wrap a `Callable` or `Runnable` task. It can be used directly or as a base class for custom implementations.
   - **Class Name**: `java.util.concurrent.FutureTask`

2. **ForkJoinTask**
   - The base class for tasks submitted to a `ForkJoinPool`. Implements `Future` and provides methods for managing and controlling tasks.
   - **Class Name**: `java.util.concurrent.ForkJoinTask`

3. **RecursiveAction**
   - A `ForkJoinTask` for tasks that don't return a result.
   - **Class Name**: `java.util.concurrent.RecursiveAction`

4. **RecursiveTask<V>**
   - A `ForkJoinTask` that returns a result.
   - **Class Name**: `java.util.concurrent.RecursiveTask`

5. **RunnableFuture<V>**
   - An interface that extends `Runnable` and `Future`. `FutureTask` implements this interface.
   - **Class Name**: `java.util.concurrent.RunnableFuture`

6. **SwingWorker<T, V>**
   - Used in Swing applications to perform background tasks and publish intermediate results. It implements `Future` and `Runnable`.
   - **Class Name**: `javax.swing.SwingWorker`

These are the primary classes in the standard Java library that implement the `Future` interface. In addition, many frameworks and libraries provide their custom implementations of `Future` for specific use cases, such as Spring's `ListenableFuture` and others. 

Here's a brief code example demonstrating the use of `FutureTask`:

```java
import java.util.concurrent.Callable;
import java.util.concurrent.ExecutionException;
import java.util.concurrent.ExecutorService;
import java.util.concurrent.Executors;
import java.util.concurrent.FutureTask;

public class FutureTaskExample {
    public static void main(String[] args) {
        ExecutorService executor = Executors.newSingleThreadExecutor();

        Callable<String> callableTask = () -> {
            Thread.sleep(2000);
            return "Task's execution result";
        };

        FutureTask<String> futureTask = new FutureTask<>(callableTask);
        executor.submit(futureTask);

        try {
            String result = futureTask.get();
            System.out.println("Result: " + result);
        } catch (InterruptedException | ExecutionException e) {
            e.printStackTrace();
        } finally {
            executor.shutdown();
        }
    }
}
```

This example demonstrates how to use `FutureTask` to execute a `Callable` task and retrieve the result.

# Explain with an example of ForkJoinTask.

Sure, let's look at how `ForkJoinTask` works in Java, particularly through its subclasses `RecursiveTask` and `RecursiveAction`. The `ForkJoinTask` framework is part of the `java.util.concurrent` package and is designed for parallel execution of tasks that can be broken down into smaller sub-tasks.

### Example: ForkJoinTask Using RecursiveTask

In this example, we'll demonstrate how to use `RecursiveTask` to perform a parallel sum of an array of integers. `RecursiveTask` is used when you expect the task to return a result.

```java
import java.util.concurrent.RecursiveTask;
import java.util.concurrent.ForkJoinPool;

public class ForkJoinSum extends RecursiveTask<Long> {
    private static final int THRESHOLD = 10_000;
    private long[] numbers;
    private int start;
    private int end;

    public ForkJoinSum(long[] numbers, int start, int end) {
        this.numbers = numbers;
        this.start = start;
        this.end = end;
    }

    @Override
    protected Long compute() {
        int length = end - start;
        if (length <= THRESHOLD) {
            return computeDirectly();
        } else {
            int split = length / 2;
            ForkJoinSum leftTask = new ForkJoinSum(numbers, start, start + split);
            ForkJoinSum rightTask = new ForkJoinSum(numbers, start + split, end);
            
            leftTask.fork(); // asynchronously execute the left task
            long rightResult = rightTask.compute(); // compute the right task directly
            long leftResult = leftTask.join(); // wait for the left task to complete and get the result
            
            return leftResult + rightResult;
        }
    }

    private long computeDirectly() {
        long sum = 0;
        for (int i = start; i < end; i++) {
            sum += numbers[i];
        }
        return sum;
    }

    public static void main(String[] args) {
        long[] numbers = new long[100_000];
        for (int i = 0; i < numbers.length; i++) {
            numbers[i] = i + 1;
        }

        ForkJoinPool forkJoinPool = new ForkJoinPool();
        ForkJoinSum task = new ForkJoinSum(numbers, 0, numbers.length);
        long result = forkJoinPool.invoke(task);
        
        System.out.println("Sum: " + result);
    }
}
```

### Explanation

1. **ForkJoinSum Class**:
   - This class extends `RecursiveTask<Long>` and represents the task of summing a portion of an array.
   - It takes a portion of an array (from `start` to `end`) and sums the elements.

2. **compute Method**:
   - This method is overridden from `RecursiveTask` and contains the logic for splitting the task.
   - If the portion size is less than or equal to the threshold, it computes the sum directly.
   - Otherwise, it splits the task into two subtasks (left and right), forks the left task, computes the right task directly, and then joins the left task.

3. **computeDirectly Method**:
   - This method performs the direct computation of the sum for the given portion of the array.

4. **main Method**:
   - The `main` method initializes an array of `100,000` integers.
   - It creates a `ForkJoinPool` to manage the tasks.
   - It creates an instance of `ForkJoinSum` for the entire array and invokes it using the `ForkJoinPool`.
   - Finally, it prints the result.

### Benefits

- **Parallel Processing**: The task is divided into smaller sub-tasks, which can be processed in parallel, leading to better performance on multi-core processors.
- **Simplified Code**: The `ForkJoinTask` framework provides a simple way to parallelize recursive algorithms.
- **Efficiency**: By splitting tasks into manageable chunks and processing them in parallel, the framework can handle large datasets more efficiently.

This example demonstrates the power of the `ForkJoinTask` framework in handling parallelizable tasks, particularly those that can be broken down into smaller, independent sub-tasks.

# list of methods of ForkJoinTask

The `ForkJoinTask` class in Java is a part of the `java.util.concurrent` package and serves as a base class for tasks that run within a `ForkJoinPool`. Here is a list of important methods provided by `ForkJoinTask`:

### Main Methods

1. **fork()**
   - Arranges to asynchronously execute this task in the pool.
   ```java
   ForkJoinTask<V> fork()
   ```

2. **join()**
   - Returns the result of the computation when it is done.
   ```java
   V join()
   ```

3. **invoke()**
   - Forks and awaits completion of the task, returning its result upon completion.
   ```java
   V invoke()
   ```

4. **compute()**
   - The main computation performed by this task. This method must be implemented in subclasses.
   ```java
   protected abstract V compute()
   ```

5. **complete(V value)**
   - Completes this task normally, and return the given result.
   ```java
   void complete(V value)
   ```

6. **completeExceptionally(Throwable ex)**
   - Completes this task exceptionally, and if it has not already started, causes it to throw the given exception.
   ```java
   void completeExceptionally(Throwable ex)
   ```

7. **isCompletedAbnormally()**
   - Returns true if this task threw an exception or was cancelled.
   ```java
   boolean isCompletedAbnormally()
   ```

8. **isCompletedNormally()**
   - Returns true if this task completed without cancellation or exception.
   ```java
   boolean isCompletedNormally()
   ```

9. **isDone()**
   - Returns true if this task completed.
   ```java
   boolean isDone()
   ```

10. **isCancelled()**
    - Returns true if this task was cancelled before it completed normally.
    ```java
    boolean isCancelled()
    ```

11. **cancel(boolean mayInterruptIfRunning)**
    - Attempts to cancel execution of this task.
    ```java
    boolean cancel(boolean mayInterruptIfRunning)
    ```

12. **get()**
    - Waits if necessary for the computation to complete, and then retrieves its result.
    ```java
    V get() throws InterruptedException, ExecutionException
    ```

13. **get(long timeout, TimeUnit unit)**
    - Waits if necessary for at most the given time for the computation to complete, and then retrieves its result, if available.
    ```java
    V get(long timeout, TimeUnit unit) throws InterruptedException, ExecutionException, TimeoutException
    ```

14. **reinitialize()**
    - Resets the internal bookkeeping state of this task, allowing a subsequent invocation of `fork()` or `invoke()` to proceed as if this task had never been started.
    ```java
    void reinitialize()
    ```

15. **tryUnfork()**
    - Tries to unschedule this task for execution.
    ```java
    boolean tryUnfork()
    ```

16. **quietlyJoin()**
    - Returns the result of the computation when it is done, without throwing any exceptions.
    ```java
    void quietlyJoin()
    ```

17. **quietlyInvoke()**
    - Forks and awaits completion of the task, without throwing any exceptions.
    ```java
    void quietlyInvoke()
    ```

18. **getRawResult()**
    - Returns the result of the computation without waiting for it to complete.
    ```java
    protected abstract V getRawResult()
    ```

19. **setRawResult(V value)**
    - Sets the result of the computation without marking it as completed.
    ```java
    protected abstract void setRawResult(V value)
    ```

### Example Usage

Here is a simple example demonstrating some of these methods:

```java
import java.util.concurrent.RecursiveTask;
import java.util.concurrent.ForkJoinPool;

class FibonacciTask extends RecursiveTask<Integer> {
    private final int n;

    FibonacciTask(int n) {
        this.n = n;
    }

    @Override
    protected Integer compute() {
        if (n <= 1) {
            return n;
        }
        FibonacciTask f1 = new FibonacciTask(n - 1);
        f1.fork(); // fork a new subtask
        FibonacciTask f2 = new FibonacciTask(n - 2);
        return f2.compute() + f1.join(); // join the result of the forked subtask
    }
}

public class ForkJoinExample {
    public static void main(String[] args) {
        ForkJoinPool pool = new ForkJoinPool();
        FibonacciTask task = new FibonacciTask(10);
        int result = pool.invoke(task); // invokes the task and waits for the result
        System.out.println("Fibonacci(10) = " + result);
    }
}
```

In this example:
- The `FibonacciTask` class extends `RecursiveTask<Integer>` to compute the Fibonacci sequence.
- The `compute` method is overridden to define the task's computation logic, which forks new subtasks and joins their results.
- The main method creates a `ForkJoinPool`, submits the `FibonacciTask`, and invokes it to get the result.

These methods and this example demonstrate the flexibility and power of the `ForkJoinTask` framework for parallel task execution.

# 