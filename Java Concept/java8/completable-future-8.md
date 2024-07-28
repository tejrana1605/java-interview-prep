# CompletableFuture in java 8

The **CompletableFuture in Java** was also introduced in Java 8 to support asynchronous programming. **CompletableFuture** is an extension of **Future’s** API. Here we will discuss why we needed CompletableFuture when we have Future’s API.

## Need of CompletableFuture in Java 8?
As we know **Future interface** was introduced in Java 5  and used represents the result of an asynchronous computation. But Future interface has some limitations like there is no provision for a callback method which can be called once the task completes. The Future interface has **isDone()** and **isCancelled() method** to check whether the task has completed or canceled. To get the result we use the **get() method**.

### 1. It can’t be manually completed

Suppose you have written a function to get the address of employee (Updated address) from a remote API. You will run it in sperate thread by use of Callable and it will return a Future object. But API is taking time due to down service. Then you want to complete Future manually which is not possible by Future interface.

### 2. Notify the completion

You can get the result by using get() method, but the Future doesn’t notify the main thread after its completion. The get() method blocks until the result is available. Java doesn’t provide any mechanism of the call back method so that the main thread can get a notification after completion of the task.

### 3. Doesn’t support chained task

There may be a situation when you want to execute a long long-running computation and send the result to the next long-running computation. In this case, the next computation starts when it gets results from the previous computation. But we can’t create such a chained task in the future.

### 4. No Exception Handling

It doesn’t provide any exception handling construct.

The **CompletableFuture class in Java** was introduced to remove the existing problems. It implements **Future interface** and CompletionStage interface and provides methods like **runAsync()** and **supplyAsync()** that run a task asynchronously.


It has all the capability of the **Future interface** and the ability to run a task as a series of stages due to the **CompletionStage interface**.  Here each stage can run asynchronously. **CompletableFuture** can have a chain of stages of **CompletionStage** and each stage runs when another CompletionStage completes. In the next section, we will read all the things in detail.


**CompletableFuture class in Java** A **CompletableFuture class** introduced in **java 8** and belongs to **java.util.cocurrent** package. It implements the **Future** and **CompletionStage interface**. A **CompltableFuture** is used for Asynchronous programming that means we can write non-blocking code. It creates a sperate thread from the main thread and works independently. But it notifies the main thread about its progress, completion, or failure. So that the main thread can work parallelly and the main thread does not block or wait for the completion of the task.

```java
public class CompletableFuture<T> implements Future<T>, CompletionStage<T>
{
      //Code 
}
```

The Future interface is used to hold the result from the Callable interface. We can check whether task is completed or not?

**CompletionStage interface** is used to represent the asynchronous operation in a pipeline of computations. You can assume some tasks chained together and the computation of the next task depends on the previous task.

The CompletionStage interface provides some methods to achieve end result like **thenAccept()**, **thenApply()**, **thenCombine()**, **thenRun()**, whenComplete.

## Creating a CompletableFuture
You can create an object of CompletableFuture by use of default constructor.

```java
CompletableFuture<String> objEompletableFuture = new CompletableFuture<String>();
```

By use of this constructor we can create the **CompletableFuture**. We can get the result from CompletableFuture by use of **get() method**. The **get() method** blocks until the Future is complete.

```java
String result = completableFuture.get()
```

If we want to complete it manually you can use complete method. In above it will block forever. So we will complete by complete() method.

```java
completableFuture.complete("By use of complete")
```

The **thenApply() method** is used to transform the result of **CompletableFuture**. It takes a parameter of **Function<T,R>** type. This method is useful when we take input from the previous stage and apply transform on it.

```java
import java.util.concurrent.CompletableFuture;
import java.util.concurrent.ExecutionException;

public class CompletableFutureExample1   
{  
    public static void main(String[] args) throws InterruptedException, ExecutionException   
    {
        // Create a CompletableFuture
        CompletableFuture<String> whatsYourNameFuture = CompletableFuture.supplyAsync(() -> ("JavaGoal"));

        // Attach a callback to the Future using thenApply()
        CompletableFuture<String> greetingFuture = whatsYourNameFuture.thenApply(name -> "Website " + name );

        // Block and get the result of the future.
        System.out.println(greetingFuture.get()); 
    }
}
```