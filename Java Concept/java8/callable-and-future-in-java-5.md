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
