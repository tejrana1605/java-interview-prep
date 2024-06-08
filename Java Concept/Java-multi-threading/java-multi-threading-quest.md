# 50+ Java Threads Interview Questions And Answers

## 1) What is multithreaded programming? Does Java supports multithreaded programming? Explain with an example?

In a program or in an application, when two or more threads execute their task simultaneously then it is called multi threaded programming.

Yes, Java supports multithreaded programming.

For example, in the below code, main thread which is responsible for executing the main() method, creates two threads – t1 and t2. t1 prints numbers from 1 to 1000 and t2 prints numbers from 1001 to 2000. These two threads execute their task simultaneously not one after the other. This is called multi threaded programming.

```java
//Thread1 : The task of this thread is to print numbers from 1 to 1000
 
class Thread1 extends Thread
{
    @Override
    public void run() 
    {
        for (int i = 1; i <= 1000; i++) 
        {
            System.out.println(i);
        }
    }
}
 
//Thread2 : The task of this thread is to print numbers from 1001 to 2000
 
class Thread2 extends Thread
{
    @Override
    public void run() 
    {
        for (int i = 1001; i <= 2000; i++) 
        {
            System.out.println(i);
        }
    }
}
 
public class JavaThreadsInterviewQuestions 
{
    //Main Thread : The task of this thread is to execute main() method
     
    public static void main(String[] args) 
    {
        //Creating and starting first thread
         
        Thread1 t1 = new Thread1();
        t1.start();
         
        //Creating and starting second thread
         
        Thread2 t2 = new Thread2();
        t2.start();
         
        //Both these two threads will be executed simultaneously
    }
}
```

## 2) In how many ways, you can create threads in Java? What are those? Explain with examples?

There are two ways two create threads in Java.

1. By extending java.lang.Thread class

2.  By implementing java.lang.Runnable interface

### 1) Creating thread by extending java.lang.Thread class :

Your thread must extend Thread class and override run() method. Whatever the task which you want to be performed by this thread, keep that task in the overridden run() method.

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        //Keep the task to be performed here
    }
}
```

Where ever you want this task to be performed, create an object to your thread class and call start() method.

```java
MyThread myThread = new MyThread();
myThread.start();
```

## 2) By implementing java.lang.Runnable interface

Runnable interface has only one methode i.e run() method. Your thread class must implement Runnable interface and override run() method and keep the task to be performed in this run() method.

```java
class MyRunnable implements Runnable
{
    @Override
    public void run()
    {
        //Keep the task to be performed here
    }
}
```

Whenever you want this task to be performed, create an object to java.lang.Thread class by passing an object of your thread class which implements Runnable interface and call start() method.

```java
Thread t = new Thread(new MyRunnable());      
t.start();
```

## 3) How many types of threads are there in Java? Explain?

There are two types of threads in Java. They are,

1. User Threads

2. Daemon Threads

User threads are threads which are created by the application or user. They are high priority threads. JVM will not exit until all user threads finish their execution. JVM wait for user threads to finish their task. These threads are foreground threads.

Daemon threads are threads which are mostly created by the JVM. These threads always run in background. These threads are used to perform some background tasks like garbage collection. These threads are less priority threads. JVM will not wait for these threads to finish their execution. JVM will exit as soon as all user threads finish their execution.

## 4) What is the default daemon status of a thread? How do you check it?

Default daemon status of a thread is inherited from it’s parent thread i.e a thread created by user thread will be a user thread and a thread created by a daemon thread will be a daemon thread.

isDaemon() method is used to check whether a thread is daemon thread or not.

## 5) Can you convert user tread into daemon thread and vice-versa? Explain with example?

Yes, you can convert user thread into daemon thread and vice-versa using setDaemon() method. But, it has to be done before starting the thread. If you call this method after starting the thread, you will get java.lang.IllegalThreadStateException.

```java
class UserThread extends Thread
{
    @Override
    public void run() 
    {
        System.out.println("Keep user thread task here...");
    }
}
 
public class JavaThreadsInterviewQuestions 
{
    public static void main(String[] args) 
    {
        UserThread userThread = new UserThread();
         
        userThread.setDaemon(true);
         
        userThread.start();
    }
}
```

## 6) Is it possible to give a name to a thread? If yes, how do you do that? What will be the default name of a thread if you don’t name a thread?

Yes, it is possible to give a name to a thread. It can be done via setName() method or else you can pass the name while creating the thread itself.

```java
class MyThread extends Thread
{
    public MyThread(String name)
    {
        super(name);
    }
     
    @Override
    public void run() 
    {
        System.out.println("Keep the task to be performed here...");
    }
}
 
public class JavaThreadsInterviewQuestions 
{
    public static void main(String[] args) 
    {
        MyThread myThread = new MyThread("My_Thread");
         
        myThread.start();
         
        System.out.println(myThread.getName());   //Output : My_Thread
         
        myThread.setName("My_Thread_2.0");
         
        System.out.println(myThread.getName());   //Output : My_Thread_2.0
    }
}
```

If you don’t name a thread, thread will get default name. Default name of the thread will consist of a word “Thread”, followed by hyphen (-) and followed by an integer number starting from 0 like Thread-0, Thread-1, Thread-2.

## 7) Can we change the name of the main thread? If yes, How?

Yes, we can change the name of the main thread. Below code shows how to do it.

```java
public class JavaThreadsInterviewQuestions 
{
    public static void main(String[] args) 
    {
        Thread t = Thread.currentThread();
         
        System.out.println(t.getName());       //Output : main
         
        t.setName("My_Main_Thread");
         
        System.out.println(t.getName());      //Output : My_Main_Thread
    }
}
```

## 8) Do two threads can have same name? If yes then how do you identify the threads having the same name?

Yes, two threads can have same name. In such scenarios, Thread ID can be used to identify the threads. Thread ID is a unique long number which remains unchanged through out the life of a thread. Thread ID can be retrieved using getID() method.

## 9) What are MIN_PRIORITY, NORM_PRIORITY and MAX_PRIORITY?

MIN_PRIORITY, NORM_PRIORITY and MAX_PRIORITY are three constant fields in java.lang.Thread class which define lowest, normal and highest priority of a thread respectively.

**MIN_PRIORITY** : It defines the lowest priority that a thread can have and it’s value is 1.

**NORM_PRIORITY** : It defines the normal priority that a thread can have and it’s value is 5.

**MAX_PRIORITY** : It defines the highest priority that a thread can have and it’s value is 10.

## 10) What is the default priority of a thread? Can we change it? If yes, how?

The default priority of a thread is same as that of it’s parent. We can change the priority of a thread at any time using setPriority() method.

## 11) What is the priority of main thread? Can we change it?

The priority of a main thread, if explicitly not set, is always NORM_PRIORITY i.e 5.

Yes, we can change the priority of a main thread using setPriority() method.

```java
public class JavaThreadsInterviewQuestions 
{
    public static void main(String[] args) 
    {
        Thread t = Thread.currentThread();
         
        System.out.println(t.getPriority());       //Output : 5
         
        t.setPriority(8);
         
        System.out.println(t.getPriority());      //Output : 8
    }
}
```

## 12) What is the purpose of Thread.sleep() method?

Thread.sleep() is used to pause the execution of current thread for a specified period of time.

## 13) Can you tell which thread is going to sleep after calling myThread.sleep(5000) in the below program? is it main thread or myThread?

```java
class MyThread extends Thread
{
    @Override
    public void run() 
    {
        for (int i = 0; i <= 10000; i++) 
        {
            System.out.println(i);
        }
    }
}
 
public class JavaThreadsInterviewQuestions 
{
    public static void main(String[] args) 
    {
        MyThread myThread = new MyThread();
         
        myThread.start();
         
        try
        {
            myThread.sleep(5000);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
    }
}
```

It is the main thread which is going to sleep not myThread. Because, when you call sleep() method, it is currently executing thread which is going to sleep, not on which you have called it.

To sleep myThread in the above program, call Thread.sleep() inside the run() method of MyThread class.

## 14) Does the thread releases the lock it holds when it is going for sleep?

No. When the thread is going for sleep, it does not release the synchronized locks it holds.

## 15) What is the purpose of join() method? Explain with an example?

join() method can be used to apply the order of execution on threads. Using join() method, you can make the currently executing thread to wait for the some other threads to finish their task. For example, let’s us assume that there are two threads – thread1 and thread2. You can make thread1 to hold it’s execution for some time so that thread2 can finish it’s task. After thread2 finishes it’s task, thread1 resumes it’s execution. For this to happen, you should call join() method on thread2 within thread1.

## 16) What do you mean by synchronization? Explain with an example?

Through synchronization, we can make the threads to execute particular method or block in sync not simultaneously. When a method or block is declared as synchronized, only one thread can enter into that method or block. When one thread is executing synchronized method or block, the other threads which wants to execute that method or block have to wait until first thread executes that method or block. Thus avoiding the thread interference and achieving the thread safeness.

```java
class Shared
{
    int i;
  
    synchronized void SharedMethod()
    {
        Thread t = Thread.currentThread();
  
        for(i = 0; i <= 1000; i++)
        {
            System.out.println(t.getName()+" : "+i);
        }
    }
}
  
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        final Shared s1 = new Shared();
  
        Thread t1 = new Thread("Thread - 1")
        {
            @Override
            public void run()
            {
                s1.SharedMethod();
            }
        };
  
        Thread t2 = new Thread("Thread - 2")
        {
            @Override
            public void run()
            {
                s1.SharedMethod();
            }
        };
  
        t1.start();
  
        t2.start();
    }
}
```
In the above example, both threads t1 and t2 wants to execute sharedMethod() of s1 object. But, sharedMethod() is declared as synchronized. So, whichever thread enters first into sharedMethod(), it continues to execute that method. The other thread waits for first thread to finish it’s execution of sharedMethod(). It never enters into sharedMethod() until first thread is done with that method. That means, both threads are executing sharedMethod() one by one not simultaneously. 

## 17) What is object lock or monitor?

The synchronization in Java is built around an entity called object lock or monitor. Below is the brief description about lock or monitor.

* Whenever an object is created to any class, an object lock is created and is stored inside the object.
* One object will have only one object lock associated with it.
* Any thread wants to enter into synchronized methods or blocks of any object, they must acquire object lock associated with that object and release the lock after they are done with the execution.
* The other threads which wants to enter into synchronized methods of that object have to wait until the currently executing thread releases the object lock.
* To enter into static synchronized methods or blocks, threads have to acquire class lock associated with that class as static members are stored inside the class memory.

## 18) I want only some part of the method to be synchronized, not the whole method? How do you achieve that?

This can be done using synchronized blocks.

## 19) What is the use of synchronized blocks?

Synchronization slows down the application. Because, at any given time, only one thread can enter into synchronized method. Other threads have to wait until first thread finishes it’s execution of that method. This slows down the execution of whole application.

Instead of synchronizing the whole method, synchronizing the only that part which is to be monitored for thread safe saves the time. This can be done using synchronized blocks.

## 20) What is mutex?

synchronized block takes one argument and it is called mutex. If synchronized block is defined inside non-static definition blocks like non-static methods, instance initializer or constructors, then this mutex must be an instance of that class. If synchronized block is defined inside static definition blocks like static methods or static initializer, then this mutex must be like ClassName.class.

## 21) Is it possible to make constructors synchronized?

Not possible. Synchronized keyword can not be used with constructors. But, constructors can have synchronized blocks.

## 22) Can we use synchronized keyword with variables?

No, you can’t use synchronized keyword with variables. You can use synchronized keyword only with methods but not with variables, constructors, static initializers and instance initializers.

## 23) As you know that synchronized static methods need class level lock and synchronized non-static methods need object level lock. Is it possible to run these two methods simultaneously?

Yes. It is possible.

## 24) If a particular thread caught with exceptions while executing a synchronized method, does executing thread releases lock or not?

Thread must release the lock whether the execution is completed normally or caught with exceptions.

## 25) Synchronized methods or synchronized blocks – which one do you prefer?

Synchronized blocks are better than synchronized methods. Because, synchronizing some part of a method improves the performance than synchronizing the whole method.

## 26) What is deadlock in Java?

Deadlock in Java is a condition which occurs when two or more threads get blocked waiting for each other for an infinite period of time to release the resources(Locks) they hold.

## 27) How do you programatically detect the deadlocked threads in Java?

```java
import java.lang.management.ManagementFactory;
import java.lang.management.ThreadInfo;
import java.lang.management.ThreadMXBean;
 
public class JavaThreadsInterviewQuestions 
{
    public static void main(String[] args) 
    {
        ThreadMXBean bean = ManagementFactory.getThreadMXBean();
          
        long ids[] = bean.findMonitorDeadlockedThreads();
  
        if(ids != null)
        {
            ThreadInfo threadInfo[] = bean.getThreadInfo(ids);
  
            for (ThreadInfo threadInfo1 : threadInfo)
            {
                System.out.println(threadInfo1.getThreadId());    //Prints the ID of deadlocked thread
  
                System.out.println(threadInfo1.getThreadName());  //Prints the name of deadlocked thread
  
                System.out.println(threadInfo1.getLockName());    //Prints the string representation of an object for which thread has entered into deadlock.
  
                System.out.println(threadInfo1.getLockOwnerId());  //Prints the ID of thread which currently owns the object lock
  
                System.out.println(threadInfo1.getLockOwnerName());  //Prints name of the thread which currently owns the object lock.
            }
        }
    }
}
```

## 28) What do you know about lock ordering and lock timeout?

Lock ordering and lock timeout are two methods which are used to avoid the deadlock in Java.

**Lock Ordering** : In this method of avoiding the deadlock, some predefined order is applied for threads to acquire the locks they need. For example, If there are three threads t1, t2 and t3 running concurrently and they needed locks A, B and C. t1 needs A and B locks, t2 needs A and C locks and t3 needs A, B and C locks. If you define an order to acquire the locks like, Lock A must be acquired before Lock B and Lock B must be acquired before Lock c, then deadlock never occurs.

**Lock Timeout** : It is another deadlock preventive method in which we specify the time for a thread to acquire the lock. If it fails to acquire the specified lock in the given time, then it should give up trying for a lock and retry after some time. 

29) How do you avoid the deadlock? Tell some tips?

Below are some tips that can be used to avoid the deadlock in Java.

* Try to avoid nested synchronized blocks. Nested synchronized blocks makes a thread to acquire another lock while it is already holding one lock. This may create the deadlock if another thread wants the same lock which is currently held by this thread.

* If you needed nested synchronized blocks at any cost, then make sure that threads acquire the needed locks in some predefined order. It is called lock ordering.

* Another deadlock preventive tip is to specify the time for a thread to acquire the lock. If it fails to acquire the specified lock in the given time, then it should give up trying for a lock and retry after some time. Such method of specifying time to acquire the lock is called lock timeout.

* Lock the code where it is actually needed. For example, if you want only some part of the method to be thread safety, then lock only that part not the whole method.

## 30) How threads communicate with each other in Java?

Threads in Java communicate with each other using wait(), notify() and notifyAll() methods.

**wait()** : This method tells the currently executing thread to release the lock of this object and wait until some other thread acquires the same lock and notify it using either notify() or notifyAll() methods.

**notify()** : This method wakes up one thread randomly that called wait() method on this object.

**notifyAll()** : This method wakes up all the threads that called wait() method on this object. But, only one thread will acquire lock of this object depending upon the priority.

## 31) What is the difference between wait() and sleep() methods in Java?

| wait()      | sleep()   |
| ------------- |-------------|
|The thread which calls wait() method releases the lock it holds.| The thread which calls sleep() method doesn’t release the lock it holds.|
|The thread regains the lock after other threads call either notify() or notifyAll() methods on the same lock.|	No question of regaining the lock as thread doesn’t release the lock.|
|wait() method must be called within the synchronized block.| sleep() method can be called within or outside the synchronized block.|
|wait() method is a member of java.lang.Object class.| sleep() method is a member of java.lang.Thread class.|
|wait() method is always called on objects.|	sleep() method is always called on threads.|
|wait() is a non-static method of Object class.| sleep() is a static method of Thread class.|
|Waiting threads can be woken up by other threads by calling notify() or notifyAll() methods.|	Sleeping threads can not be woken up by other threads. If done so, thread will throw InterruptedException.|
| To call wait() method, thread must have object lock.|	 To call sleep() method, thread need not to have object lock.|

## 32) What is the difference between notify() and notifyAll() in Java?

**notify()** : When a thread calls notify() method on a particular object, only one thread will be notified which is waiting for the lock or monitor of that object. The thread chosen to notify is random i.e randomly one thread will be selected for notification. Notified thread doesn’t get the lock of the object immediately. It gets once the calling thread releases the lock of that object.

**notifyAll()** : When a thread calls notifyAll() method on a particular object, all threads which are waiting for the lock of that object are notified. All notified threads will move from WAITING state to BLOCKED state. All these threads will get the lock of the object on a priority basis. The thread which gets the lock of the object moves to RUNNING state. The remaining threads will remain in BLOCKED state until they get the object lock.

## 33) Though they are used for inter thread communication, why wait(), notify() and notifyAll() methods are included in java.lang.Object class not in java.lang.Thread class?

See this post to know why wait(), notify() and notifyAll() methods are included in java.lang.Object class not in java.lang.Thread class

## 34) What do you know about interrupt() method? Why it is used?

interrupt() method is used to interrupt sleeping or waiting thread. The whole thread interruption mechanism depends on an internal flag called interrupt status. The initial value of this flag for any thread is false. When you call interrupt() method on a thread, interrupt status of that thread will be set to true. When a thread throws InterruptedException, this status will be set to false again.

## 35) How do you check whether a thread is interrupted or not?

isInterrupted() or interrupted() method is used to check whether a particular thread is interrupted or not.

## 36) What is the difference between isInterrupted() and interrupted() methods?

Both, isInterrupted() and interrupted() methods are used to check whether a particular thread is interrupted or not. Both these methods return current interrupt status of a thread. isInterrupted() is a non-static method where as interrupted() is a static method of java.lang.Thread class. The main difference between these two methods is that isInterrupted() doesn’t clear the interrupt status where as interrupted() clears the interrupt status of a thread.

## 37) Can a thread interrupt itself? Is it allowed in Java?

Yes, a thread can interrupt itself. It is very much legal in Java.

## 38) Explain thread life cycle? OR Explain thread states in Java?

There are six thread states. They are NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING and TERMINATED. At any point of time, thread will be in any one of these states.

1. NEW : A thread will be in this state before calling start() method.

2. RUNNABLE : A thread will be in this state after calling the start() method.

3. BLOCKED : A thread will be in this state when a thread is waiting for object lock to enter into synchronized method/block or a thread will be in this state if deadlock occurs.

4. WAITING : A thread will be in this state when wait() or join() method is called.

5. TIMED_WAITING : A thread will be in this state when sleep() or wait() with timeOut or join() with timeOut is called.

6. TERMINATED : A thread will be in this state once it finishes it’s execution.

## 39) In what state deadlocked threads will be?

Deadlocked threads will be in BLOCKED state.

## 40) What is the difference between BLOCKED and WAITING states?

a thread will be in WAITING state if it is waiting for notification from other threads. A thread will be in BLOCKED state if it is waiting for other thread to release the lock it wants.

A thread enters into WAITING state when it calls wait() or join() method on an object. Before entering into WAITING state, thread releases the lock of the object it holds. It will remain in WAITING state until any other thread calls either notify() or notifyAll() on the same object.

Once the other thread calls notify() or notifyAll() on the same object, one or all the threads which are WAITING for lock of that object will be notified. All the notified threads will not get the object lock immediately. They will get the object lock on a priority basis once the current thread releases the lock. Until that they will be in BLOCKED state.

## 41) What is the difference between WAITING and TIMED_WAITING states?

A thread enters into WAITING state when it calls wait() or join() method on an object. Before entering into WAITING state, thread releases the lock of the object it holds. It will remain in WAITING state until any other thread calls either notify() or notifyAll() on the same object.

A thread will be in TIMED_WAITING state when sleep() or wait() with timeOut or join() with timeOut is called. Thread doesn’t release the lock it holds before entering into this state. It will remain in this state till specified time is over.

## 42) Can we call start() method twice?

No, start() method must be called only once. If you call start() method second time, it will throw IllegalThreadStateException as thread is already started.

## 43) What is the difference between calling start() method and calling run() method directly as anyhow start() method internally calls run() method?

When you call start() method, a new thread is created and that newly created thread executes the task kept in the run() method. If you call run() method directly, no new thread is created. Any task kept in run() method is executed by the calling thread itself.

If you are calling run() method directly, then you are not making use of the multi-threaded programming concept. Because, when you call run() method directly, no new thread is created. run() method is executed by the calling thread itself. It just acts as normal method invocation. You are not using the concept of multi-threading.

## 44) How do you stop a thread?

As stop() method has been deprecated, there are two ways through which you can stop a thread in Java. One is using boolean variable and second one is using interrupt() method.

## 45) Suppose there are two threads T1 and T2 executing their task concurrently. If an exception occurred in T1, will it effect execution of T2 or it will execute normally?

T2 will execute normally. Exception is thread wise not execution wise. i.e exception effects the thread in which it occurs. Other threads will execute normally.

## 46) Which one is the better way to implement threads in Java? Is it using Thread class or using Runnable interface?

when multiple threads need to execute same task, then use Runnable interface. If multiple threads need to execute different tasks, then go for Thread class.

## 47) What is the difference between program, process and thread?

Program is an executable file containing the set of instructions written to perform a specific job on your computer. For example, chrome.exe, notepad.exe…

Process is an executing instance of a program. For example, When you double click on the Google Chrome icon on your computer, you start a process which will run the Google Chrome program. When you double click on a notepad icon on your computer, a process is started that will run the notepad program.

Thread is the smallest executable unit of a process. For example, when you run a notepad program, operating system creates a process and starts the execution of main thread of that process.

## 48) What are the differences between user threads and daemon threads?

| User Threads   | Daemon Threads   |
| ------------- |-------------|	
|JVM waits for user threads to finish their work. It will not exit until all user threads finish their work.| JVM will not wait for daemon threads to finish their work. It will exit as soon as all user threads finish their work.|
|User threads are foreground threads.| Daemon threads are background threads.|
|User threads are high priority threads.|	Daemon threads are low priority threads.|
|User threads are created by the application.|	Daemon threads, in most of time, are created by the JVM.|
|User threads are mainly designed to do some specific task.| Daemon threads are designed to support the user threads.|
|JVM will not force the user threads to terminate. It will wait for user threads to terminate themselves.| JVM will force the daemon threads to terminate if all user threads have finished their work.|

## 49) What is the use of thread groups in Java?

Thread groups in Java are used to group similar threads into one unit. A thread group can contain a set of threads or other thread groups. The main use of thread groups is that you can handle multiple threads simultaneously.

## 50) What is the thread group of a main thread?

main thread belongs to main thread group.

## 51) What activeCount() and activeGroupCount() methods do?

activeCount() returns the number of active threads in a specified group and it’s subgroups. activeGroupCount() returns the numbers of active thread groups in a specified group and it’s subgroups.

## What is Multithreading in Java? Why is it important?

Multithreading in Java is a programming concept that refers to small tasks running simultaneously. Let's take an example of multithreading as our computer or mobile phones, which allows us to run various tasks at once. Its main purpose is to enable multiple threads to run simultaneously, maximizing CPU usage and improving program execution speed. This Java feature allows a program to be divided into multiple threads for faster and easier execution.

## What is a thread in Java?
Threads are referred to as the smallest parts of a process that simply let a program execute efficiently with other parts or threads of the process at the same time. They share a common address space and are independent of each other. In Java, there are two ways of creating threads:

1. Via Thread class

2. Via Runnable interface

## 3. What is multitasking in an operating system?
Multitasking is a feature in an operating system that divides system resources among tasks/processes and switches between the tasks/processes while they are executing over and over again. This gives the perception of 2 or more tasks running concurrently. Multitasking is of two types:

→ Process-based multitasking

→ Thread-based multitasking

## 4.  What are the benefits of using Multithreading?
Multithreading possesses various benefits described below:

It increases the use of CPU resources.
Does not get blocked easily if some parts of it are blocked
It allows the programs to utilize maximum CPU time
Improves the responsiveness of the program.
It allows parallelism.

## 6. What is the difference between a thread and a process?

A program in execution is called a process, while the smallest independent units in a process are called a thread.

| Thread      | Process   |
| ------------- |-------------|
|It is the smallest unit in a process.| Program in execution is called a process.|
|It requires less time for creation, termination and switching.| It requires mor etime for creation, termination and switching.|
|Inter-thread communication is faster.| Inter-process communication is slower and expensive.|
|Threads are units of the same process so they are dependent.| Processes are independent of each other.|
|They share data with each other.| They do not share data with each other.|

## 7. What is the task of the main thread?

The main Thread is a thread contained in every program created by the JVM at the start of the program when the main() function is invoked with the main Thread as depicted from the output perceived from pseudo-code illustration.

```java
System.out.println("coding ninjas");
Output: coding ninjas
System.out.println(Thread.getname().currentthread()); 
Output: main
```

## 9. What is the start() and run() method of Thread class?

**Start()**: The start() method is used to start or begin the execution of a newly created thread. When the start() method is called, a new thread is created, and this newly created Thread executes the task that is kept in the run() method. One can call the start() method only once.

**run()**:  The run() method is used to start or begin the execution of the same Thread. When the run() method is called, no new thread is created, as in the case of the start() method. This method is executed by the current Thread. One can call the run() method multiple times. 

## 10. How to set the name of the thread?

A method named as setName() is there which is used to change or set the names of the threads.

```java
thread_class_object.setName("Name_thread_here");
```

## 1. What do you mean by garbage collection?

Garbage collection is a process of managing memory automatically. A garbage collector finds objects that are no longer required by the program and then deletes or removes these unused objects to free up memory space. It uses several GC algorithms. One popular name of the algorithm is  Mark and Sweep.

## 12. What is thread Starvation?

When low-priority threads do not get CPU for their execution because high-priority threads occupy the CPU for long periods of time, this phenomenon is called thread starvation. This makes the Thread unable to progress.

## 13. What is thread priority?

In Java, every Thread has a priority which is represented by the numbers from 1 to 10. The default priority is set to 5, the minimum priority is set to one, and the maximum priority is set to 10. Here, three constants are defined as NORM_PRIORITY, MIN_PRIORITY, and MAX_PRIORITY.

## 14. What is context switching

Context Switching is referred to as switching the CPU from one Thread or process to another one. In context switching, the state of the Thread is stored so that the next time the execution of the Thread is required, it can be resumed from the same point.

## 15. What do you mean by inter-thread communication?

It is a mechanism using which multiple threads can communicate with each other. It is especially used to avoid thread polling in Java and can be obtained using wait(), notify(), and notifyAll() methods.

## 16. What do you mean by finalize() method?

The finalize() method in Java was defined in the Object class before Java version 9. It was supposed to be used for performing cleanup operations on an object before it was garbage collected. After the release of Java 9, this method has been deprecated and it is no longer recommended for managing memory.

## 17. What is the purpose of the finalize() method?

The finalize method in Java is used for performing cleanup operations on objects about to be garbage collected by the JVM. When an object becomes eligible for garbage collection, the JVM checks for a finalize() method and calls it before cleaning the memory. This method can be overridden to define custom cleanup logic. Let's look at the basic syntax of this overriding this method.

```java
class MyClass {
   // Constructor and other methods
   
   // Custom finalize() method for cleanup
   protected void finalize() {
       // Perform resource cleanup here
   }
}
```

## 18. What is a semaphore?

Semaphore is regarded as a thread synchronization system that is usually required to control and manage the access to the shared resource using counters. The semaphore class is defined within the package java.util.concurrent and can be used to send signals between threads to avoid missed signals or to guard critical sections.

## 19. How to make a user thread to daemon thread?

There are two methods in the thread class that is used to make a user thread into a daemon thread. First, the setDaemon() method converts the user thread to the daemon thread and vice-versa. After this, the isDaemon() method is used, which returns a boolean true if the Thread is daemon. Else returns false if it is a non-daemon thread. 

## 20. Can you start a thread twice?

No, it's not at all possible to restart a thread once a thread gets started and completes its execution. Thread only runs once, and if you try to run it for a second time, then it will throw a runtime exception, i.e., Java. lang.IllegalThreadStateException. 

## 21. What are the tasks of the start() method?

The main task of the start() method is to register the Thread with the thread scheduler, so one can tell what child thread should perform, when, and how it will be scheduled that is handled by the thread scheduler. The second task is to call the corresponding run() method.

## 22. Explain the difference between class lock and object lock?

A class lock is present within the class and prevents simultaneous access to a concurrent static method or block. While object lock is related to the instance of a class that allows simultaneous access to concurrent methods or blocks in different objects.

## 23. Explain the difference between User thread and Daemon thread?

A user thread is also known as high priority thread. The Java virtual machine completes all the user threads before terminating. While the daemon thread is also known as low priority thread, and they are mainly used as background tasks and provide services to the user thread. 

## 24. What are the wait() and sleep() methods?

The wait() and sleep() methods are used to stop any running thread and convert them into a non-runnable state. The wait method is mostly used for thread sync, and the sleep() method is used to pause the running threads.

## 25. Explain the  difference between notify() and notifyAll()?

The notify() method is used to alert only one waiting thread among many waiting threads, while the notifyAll() method is used to send notifications to all the waiting threads. notify() method uses less memory and CPU in comparison to the notifyAll() method.

## 26. What do you mean by thread pool?

A thread pool can be considered a collection of all the threads that are ready to perform the tasks. It also increases the reusability of the threads as it does not create and destroy the threads each time.

## 27. Can two threads execute two methods (static and non-static concurrently)?

Yes, two threads can run two different methods (one static and one non-static) of the same class. However, it is important to note that unexpected behavior can occur because the locking mechanism will lock two different things: the object and the class itself, which means both methods will execute simultaneously, and a shared state can be mutated.

## 28. What is meant by volatile variables in Java?

In Java, the volatile keyword is used to declare a variable as volatile, which means changes made to it by one thread will be immediately visible to other threads. You can use this keyword to define simple flags or status indicators frequently checked by many threads.

## 29. What’s the purpose of the join() method?

The join() method in Java is provided by the Thread class and used for thread synchronization and coordination. This method allows you to make a thread wait for the completion of another thread. 

For example, there are two threads, A and B. If thread A calls the join() method on thread B, thread A will pause its execution and wait for thread B to complete.

## 30. How do synchronized methods and synchronized blocks differ, and which one is the preferred choice?

Synchronized methods and blocks in Java are used to achieve thread synchronization and prevent multiple threads from concurrently accessing critical code sections. The choice between synchronized methods and synchronized blocks depends on your specific requirements:

**Synchronized Methods**: Use synchronized methods when you want to synchronize the entire method and there's no need to synchronize different parts of the method separately.
 
**Synchronized Blocks**: Use synchronized blocks when you need more control over synchronization, and you want to synchronize specific sections of code. Synchronized blocks are more flexible and allow for finer-grained synchronization.

## 31. What is meant by deadlock and how it can occur?

A deadlock is a situation in which two or more threads are blocked for an infinite time, and they all wait for each other to release their resources. Deadlock can occur due to mutual exclusion, holding and waiting of threads or when a circular chain of two or more threads exists.

## Is it possible to call the run() method directly to start a new thread?

No, it's not possible at all. You need to call the start method to create a new thread otherwise it will execute in the current thread.

## Can we Overload run() method?

Yes, it is possible to overload run() by passing parameters to it and also keeping a check over to comment down @override from the run() method. 

## Why is multithreading required?

Multithreading is required in order to enhance the performance and to improve the responsiveness of the process.

## 2. What is Thread in Java?

Threads are basically the lightweight and smallest unit of processing that can be managed independently by a scheduler. Threads are referred to as parts of a process that simply let a program execute efficiently with other parts or threads of the process at the same time. Using threads, one can perform complicated tasks in the easiest way. It is considered the simplest way to take advantage of multiple CPUs available in a machine. They share the common address space and are independent of each other.

## 1. What are the benefits of using Multithreading?

There are various benefits of multithreading as given below:

* Allow the program to run continuously even if a part of it is blocked.

* Improve performance as compared to traditional parallel programs that use multiple processes. 

* Allows to write effective programs that utilize maximum CPU time

* Improves the responsiveness of complex applications or programs. 

* Increase use of CPU resources and reduce costs of maintenance. 

* Saves time and parallelism tasks. 

* If an exception occurs in a single thread, it will not affect other threads as threads are independent. 

* Less resource-intensive than executing multiple processes at the same time. 

## 5. What’s the difference between class lock and object lock?

**Class Lock**: In java, each and every class has a unique lock usually referred to as a class level lock. These locks are achieved using the keyword ‘static synchronized’ and can be used to make static data thread-safe. It is generally used when one wants to prevent multiple threads from entering a synchronized block. 

Example:  

```java
public class ClassLevelLockExample  
{    
  public void classLevelLockMethod()  
 {       
     synchronized (ClassLevelLockExample.class)  
       {         
            //DO your stuff here       
       }    
 } 
} 
```

**Object Lock**: In java, each and every object has a unique lock usually referred to as an object-level lock. These locks are achieved using the keyword ‘synchronized’ and can be used to protect non-static data. It is generally used when one wants to synchronize a non-static method or block so that only the thread will be able to execute the code block on a given instance of the class.  

Example:  

```java
public class ObjectLevelLockExample  
{    
  public void objectLevelLockMethod()  
 {   
     synchronized (this)  
       {     
            //DO your stuff here   
       } 
 }
} 
```

## 7. How can we create daemon threads?

We can create daemon threads in java using the thread class setDaemon(true). It is used to mark the current thread as daemon thread or user thread. isDaemon() method is generally used to check whether the current thread is daemon or not. If the thread is a daemon, it will return true otherwise it returns false.  

Example:   
**Program to illustrate the use of setDaemon() and isDaemon() method.** 

```java
public class DaemonThread extends Thread 
{ 
   public DaemonThread(String name){ 
       super(name); 
   } 
   public void run() 
   {  
       // Checking whether the thread is Daemon or not 
       if(Thread.currentThread().isDaemon()) 
       {  
           System.out.println(getName() + " is Daemon thread");  
       }    
       else 
       {  
           System.out.println(getName() + " is User thread");  
       }  
   }   
   public static void main(String[] args) 
   {  
       DaemonThread t1 = new DaemonThread("t1"); 
       DaemonThread t2 = new DaemonThread("t2"); 
       DaemonThread t3 = new DaemonThread("t3");  
       // Setting user thread t1 to Daemon 
       t1.setDaemon(true);       
       // starting first 2 threads  
       t1.start();  
       t2.start();   
       // Setting user thread t3 to Daemon 
       t3.setDaemon(true);  
       t3.start();         
   }  
} 
```

Output:  

```java
t1 is Daemon thread 
t3 is Daemon thread 
t2 is User thread 
```

But one can only call the setDaemon() method before start() method otherwise it will definitely throw IllegalThreadStateException as shown below:   

```java
public class DaemonThread extends Thread 
{ 
   public void run() 
   { 
       System.out.println("Thread name: " + Thread.currentThread().getName()); 
       System.out.println("Check if its DaemonThread: "  
                       + Thread.currentThread().isDaemon()); 
   } 
   public static void main(String[] args) 
   { 
       DaemonThread t1 = new DaemonThread(); 
       DaemonThread t2 = new DaemonThread(); 
       t1.start();         
       // Exception as the thread is already started 
       t1.setDaemon(true); 
       t2.start(); 
   } 
} 
```

Output:  

```java
Thread name: Thread-0 
Check if its DaemonThread: false 
```

## 8. What are the wait() and sleep() methods?

wait(): As the name suggests, it is a non-static method that causes the current thread to wait and go to sleep until some other threads call the notify () or notifyAll() method for the object’s monitor (lock). It simply releases the lock and is mostly used for inter-thread communication. It is defined in the object class, and should only be called from a synchronized context. 

Example:  

```java
synchronized(monitor) 
{ 
monitor.wait();       Here Lock Is Released by Current Thread  
} 
```

sleep(): As the name suggests, it is a static method that pauses or stops the execution of the current thread for some specified period. It doesn’t release the lock while waiting and is mostly used to introduce pause on execution. It is defined in thread class, and no need to call from a synchronized context.  

Example:  

```java
synchronized(monitor) 
{ 
Thread.sleep(1000);     Here Lock Is Held by The Current Thread 
//after 1000 milliseconds, the current thread will wake up, or after we call that is interrupt() method 
} 
```

## 9. What’s the difference between notify() and notifyAll()?

notify(): It sends a notification and wakes up only a single thread instead of multiple threads that are waiting on the object’s monitor.

<a href="#" target="_blank"><img src="https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/475/original/notify%28%29.png?1623226111"/></a>

notifyAll(): It sends notifications and wakes up all threads and allows them to compete for the object's monitor instead of a single thread. 

## 10. Why wait(), notify(), and notifyAll() methods are present in Object class?

We know that every object has a monitor that allows the thread to hold a lock on the object. But the thread class doesn't contain any monitors. Thread usually waits for the object’s monitor (lock) by calling the wait() method on an object, and notify other threads that are waiting for the same lock using notify() or notifyAll() method.  Therefore, these three methods are called on objects only and allow all threads to communicate with each that are created on that object.

## 11. What is Runnable and Callable Interface? Write the difference between them.
Both the interfaces are generally used to encapsulate tasks that are needed to be executed by another thread. But there are some differences between them as given below: 

**Running Interface**: This interface is basically available in Java right from the beginning. It is simply used to execute code on a concurrent thread.  

**Callable Interface**: This interface is basically a new one that was introduced as a part of the concurrency package. It addresses the limitation of runnable interfaces along with some major changes like generics, enum, static imports, variable argument method, etc. It uses generics to define the return type of object.   

```java
public interface Runnable  
{   
  public abstract void run(); 
}  
public interface Callable<V>  
{    
V call() throws Exception;  
} 
```
Runnable Interface vs Callable Interface

| Runnable Interface      | Callable Interface    |
| ------------- |-------------|
|It does not return any result and therefore, cannot throw a checked exception.| It returns a result and therefore, can throw an exception.|
|It cannot be passed to invokeAll method.| It can be passed to invokeAll method.|
|It was introduced in JDK 1.0.|	It was introduced in JDK 5.0, so one cannot use it before Java 5.| 
|It simply belongs to Java.lang.| It simply belongs to java.util.concurrent.| 
|It uses the run() method to define a task.| It uses the call() method to define a task.|
|To use this interface, one needs to override the run() method.|  To use this interface, one needs to override the call() method.|

## 13. Explain thread pool?

A Thread pool is simply a collection of pre-initialized or worker threads at the start-up that can be used to execute tasks and put back in the pool when completed. It is referred to as pool threads in which a group of fixed-size threads is created.  By reducing the number of application threads and managing their lifecycle, one can mitigate the issue of performance using a thread pool. Using threads, performance can be enhanced and better system stability can occur. To create the thread pools, java.util.concurrent.Executors class usually provides factory methods.

## 14. What’s the purpose of the join() method?

join() method is generally used to pause the execution of a current thread unless and until the specified thread on which join is called is dead or completed. To stop a thread from running until another thread gets ended, this method can be used. It joins the start of a thread execution to the end of another thread’s execution. It is considered the final method of a thread class.

## 16. Explain the meaning of the deadlock and when it can occur?

Deadlock, as the name suggests, is a situation where multiple threads are blocked forever. It generally occurs when multiple threads hold locks on different resources and are waiting for other resources to complete their task.

<a href="#" target="_blank"><img src="https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/477/original/Deadlock_example.png?1623231654"/></a>

The above diagram shows a deadlock situation where two threads are blocked forever.  Thread 1 is holding Object 1 but needs object 2 to complete processing whereas Thread 2 is holding Object 2 but needs object 1 first. In such conditions, both of them will hold lock forever and will never complete tasks.

## 17. Explain volatile variables in Java?

A volatile variable is basically a keyword that is used to ensure and address the visibility of changes to variables in multithreaded programming. This keyword cannot be used with classes and methods, instead can be used with variables. It is simply used to achieve thread-safety. If you mark any variable as volatile, then all the threads can read its value directly from the main memory rather than CPU cache, so that each thread can get an updated value of the variable.

## 18. How do threads communicate with each other?

Threads can communicate using three methods i.e., wait(), notify(), and notifyAll().

## 19. Can two threads execute two methods (static and non-static concurrently)?

Yes, it is possible. If both the threads acquire locks on different objects, then they can execute concurrently without any problem.

## 1. What is the synchronization process? Why use it?

Synchronization is basically a process in java that enables a simple strategy for avoiding thread interference and memory consistency errors. This process makes sure that resource will be only used one thread at a time when one thread tries to access a shared resource. It can be achieved in three different ways as given below: 

1. By the synchronized method

2. By synchronized block

3. By static synchronization

Syntax:  

```java
synchronized (object) 
{        
   //statement to be synchronized 
} 
```

## 2. What is synchronized method and synchronized block? Which one should be preferred?

**Synchronized Method**: In this method, the thread acquires a lock on the object when they enter the synchronized method and releases the lock either normally or by throwing an exception when they leave the method.  No other thread can use the whole method unless and until the current thread finishes its execution and release the lock. It can be used when one wants to lock on the entire functionality of a particular method. 

**Synchronized Block**: In this method, the thread acquires a lock on the object between parentheses after the synchronized keyword, and releases the lock when they leave the block. No other thread can acquire a lock on the locked object unless and until the synchronized block exists. It can be used when one wants to keep other parts of the programs accessible to other threads.
 
Synchronized blocks should be preferred more as it boosts the performance of a particular program. It only locks a certain part of the program (critical section) rather than the entire method and therefore leads to less contention.

## 3. What is thread starvation?

Thread starvation is basically a situation or condition where a thread won’t be able to have regular access to shared resources and therefore is unable to proceed or make progress. This is because other threads have high priority and occupy the resources for too long. This usually happens with low-priority threads that do not get CPU for its execution to carry on. 

<a href="#" target="_blank"><img src="https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/478/original/starvation_in_Java.png?1623234594"/></a>

## 4. What is Livelock? What happens when it occurs?

Similar to deadlock, livelock is also another concurrency problem. In this case, the state of threads changes between one another without making any progress. Threads are not blocked but their execution is stopped due to the unavailability of resources.

## 5. What is BlockingQueue?

BlockingQueue basically represents a queue that is thread-safe. Producer thread inserts resource/element into the queue using put() method unless it gets full and consumer thread takes resources from the queue using take() method until it gets empty. But if a thread tries to dequeue from an empty queue, then a particular thread will be blocked until some other thread inserts an item into the queue, or if a thread tries to insert an item into a queue that is already full, then a particular thread will be blocked until some threads take away an item from the queue. 

<a href="#" target="_blank"><img src="https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/479/original/blockingqueue.png?1623234868"/></a>

Example: 

```java
package org.arpit.java2blog; 
 
import java.util.concurrent.ArrayBlockingQueue; 
import java.util.concurrent.BlockingQueue; 
 
public class BlockingQueuePCExample { 
 
   public static void main(String[] args) { 
 
       BlockingQueue<String> queue=new ArrayBlockingQueue<>(5); 
       Producer producer=new Producer(queue); 
       Consumer consumer=new Consumer(queue); 
       Thread producerThread = new Thread(producer); 
       Thread consumerThread = new Thread(consumer); 
 
       producerThread.start(); 
       consumerThread.start(); 
 
   } 
 
   static class Producer implements Runnable { 
 
       BlockingQueue<String> queue=null; 
 
       public Producer(BlockingQueue queue) { 
           super(); 
           this.queue = queue; 
       } 
 
       @Override 
       public void run() { 
 
               try { 
                   System.out.println("Producing element 1"); 
                   queue.put("Element 1"); 
                   Thread.sleep(1000); 
                   System.out.println("Producing element 2"); 
                   queue.put("Element 2"); 
                   Thread.sleep(1000); 
                   System.out.println("Producing element 3"); 
                   queue.put("Element 3"); 
               } catch (InterruptedException e) { 
 
                   e.printStackTrace(); 
               } 
       } 
   } 
 
   static class Consumer implements Runnable { 
 
       BlockingQueue<String> queue=null; 
 
       public Consumer(BlockingQueue queue) { 
           super(); 
           this.queue = queue; 
       } 
 
       @Override 
       public void run() { 
 
           while(true) 
           { 
               try { 
                   System.out.println("Consumed "+queue.take()); 
               } catch (InterruptedException e) { 
                   e.printStackTrace(); 
               } 
           } 
       } 
 
   } 
} 
```

Output: 

```java
Producing element 1 
Consumed Element 1 
Producing element 2 
Consumed Element 2 
Producing element 3 
Consumed Element 3
```

## 6. Can you start a thread twice?
No, it's not at all possible to restart a thread once a thread gets started and completes its execution. Thread only runs once and if you try to run it for a second time, then it will throw a runtime exception i.e., java.lang.IllegalThreadStateException. 

Example: 

```java
public class TestThreadTwice1 extends Thread{   
public void run(){   
System.out.println(" thread is executing now........");   
}   
public static void main(String args[]){   
TestThreadTwice1 t1=new TestThreadTwice1();   
t1.start();   
t1.start();   
}   
}   
```

Output:

```java
thread is executing now........ 
Exception in thread "main" java.lang.IllegalThreadStateException
```

## 7. Explain context switching.

Context switching is basically an important feature of multithreading. It is referred to as switching of CPU from one thread or process to another one. It allows multiple processes to share the same CPU. In context switching, the state of thread or process is stored so that the execution of the thread can be resumed later if required. 

## 8. What is CyclicBarrier and CountDownLatch?

CyclicBarrier and CountDownLatch, both are required for managing multithreaded programming. But there is some difference between them as given below: 

**CyclicBarrier**: It is a tool to synchronize threads processing using some algorithm. It enables a set of threads to wait for each other till they reach a common execution point or common barrier points, and then let them further continue execution. One can reuse the same CyclicBarrier even if the barrier is broken by setting it. 

**CountDownLatch**: It is a tool that enables main threads to wait until mandatory operations are performed and completed by other threads. In simple words, it makes sure that a thread waits until the execution in another thread completes before it starts its execution. One cannot reuse the same CountDownLatch once the count reaches 0. 

<a href="#" target="_blank"><img src="https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/480/original/cyclicbarrier-and-countdownlatch.png?1623235287"/></a>

## 9. What do you mean by inter-thread communication?

Inter-thread communication, as the name suggests, is a process or mechanism using which multiple threads can communicate with each other. It is especially used to avoid thread polling in java and can be obtained using wait(), notify(), and notifyAll() methods. 

## 10. What is Thread Scheduler and Time Slicing?

**Thread Scheduler**: It is a component of JVM that is used to decide which thread will execute next if multiple threads are waiting to get the chance of execution. By looking at the priority assigned to each thread that is READY, the thread scheduler selects the next run to execute. To schedule the threads, it mainly uses two mechanisms: Preemptive Scheduling and Time slicing scheduling.  

**Time Slicing**: It is especially used to divide CPU time and allocate them to active threads. In this, each thread will get a predefined slice of time to execute. When the time expires, a particular thread has to wait till other threads get their chances to use their time in a round-robin fashion. Every running thread will get executed for a fixed time period. 

## 11. What is a shutdown hook?

A shutdown hook is simply a thread that is invoked implicitly before JVM shuts down. It is one of the most important features of JVM because it provides the capacity to do resource cleanup or save application state JVM shuts down.  By calling the halt(int) method of the Runtime class, the shutdown hook can be stopped. Using the following method, one can add a shutdown hook. 

```java
public void addShutdownHook(Thread hook){}     
Runtime r=Runtime.getRuntime();   
r.addShutdownHook(new MyThread());
```

## 12. What is busy spinning?

Busy Spinning, also known as Busy-waiting, is a technique in which one thread waits for some condition to happen, without calling wait or sleep methods and releasing the CPU. In this condition, one can pause a thread by making it run an empty loop for a certain time period, and it does not even give CPY control. Therefore, it is used to preserve CPU caches and avoid the cost of rebuilding cache.

## 13. What is ConcurrentHashMap and Hashtable? In java, why is ConcurrentHashMap considered faster than Hashtable?

ConcurrentHashMap: It was introduced in Java 1.5 to store data using multiple buckets. As the name suggests, it allows concurrent read and writes operations to the map. It only locks a certain portion of the map while doing iteration to provide thread safety so that other readers can still have access to the map without waiting for iteration to complete.  

**Hashtable**: It is a thread-safe legacy class that was introduced in old versions of java to store key or value pairs using a hash table.  It does not provide any lock-free read, unlike ConcurrentHashMap. It just locks the entire map while doing iteration. 

ConcurrentHashMap and Hashtable, both are thread-safe but ConcurrentHashMap generally avoids read locks and improves performance, unlike Hashtable. ConcurrentHashMap also provides lock-free reads, unlike Hashtable. Therefore, ConcurrentHashMap is considered faster than Hashtable especially when the number of readers is more as compared to the number of writers. 

## 14. Explain thread priority.

Thread priority simply means that threads with the highest priority will get a chance for execution prior to low-priority threads. One can specify the priority but it's not necessary that the highest priority thread will get executed before the lower-priority thread. Thread scheduler assigns processor to thread on the basis of thread priority. The range of priority changes between 1-10 from lowest priority to highest priority. 

## 15. What do you mean by the ThreadLocal variable in Java?

ThreadLocal variables are special kinds of variables created and provided by the Java ThreadLocal class. These variables are only allowed to be read and written by the same thread. Two threads cannot be able to see each other’s ThreadLocal variable, so even if they will execute the same code, then there won't be any race condition and the code will be thread-safe.  

Example:  

```java
public class ThreadLocalExp   
{   
     public static class MyRunnable implements Runnable    
   {   
       private ThreadLocal<Integer> threadLocal =   
              new ThreadLocal<Integer>();   
      @Override   
       public void run() {   
           threadLocal.set( (int) (Math.random() * 50D) );   
           try    
           {   
               Thread.sleep(1000);   
           } catch (InterruptedException e) {   
           }   
           System.out.println(threadLocal.get());   
       }   
   }   
   public static void main(String[] args)    
   {   
       MyRunnable runnableInstance = new MyRunnable();    
       Thread t1 = new Thread(runnableInstance);   
       Thread t2 = new Thread(runnableInstance);   
      // this will call run() method    
       t1.start();   
       t2.start();   
   }   
} 
```

Output: 

```java
10 
33 
10 33 
```

## 16. What is semaphore?

Semaphore is regarded as a thread synchronization construct that is usually required to control and manage the access to the shared resource using counters. It simply sets the limit of the thread. The semaphore class is defined within the package java.util.concurrent and can be used to send signals between threads to avoid missed signals or to guard critical sections. It can also be used to implement resource pools or bounded collection.

## 17. Explain Thread Group. Why should we not use it?

ThreadGroup is a class that is used to create multiple groups of threads in a single object. This group of threads is present in the form of three structures in which every thread group has a parent except the initial thread. Thread groups can contain other thread groups also. A thread is only allowed to have access to information about its own thread group, not other thread groups. 

Previously in the old version of Java, the only functionality that did not work without a thread group was uncaughtException( Thread t, Throwable e). But now in Java 5 versions, there is Thread.setUncaughtExceptionHandler(UncaughtExceptionHandler). So now even that works without thread groups and therefore, there is no need to use thread groups.  

```java
t1.setUncaughtExceptionHandler(new UncaughtExceptionHandler() 
{ 
@Override  
public void uncaughtException(Thread t, Throwable e)  
{  
System.out.println("exception occured:"+e.getMessage()); 
}  
}; 
```

## 18. What is the ExecutorService interface?

ExecutorService interface is basically a sub-interface of Executor interface with some additional methods or features that help in managing and controlling the execution of threads. It enables us to execute tasks asynchronously on threads.

<a href="#" target="_blank"><img src="https://s3.ap-south-1.amazonaws.com/myinterviewtrainer-domestic/public_assets/assets/000/000/482/original/executorservice_interface.png?1623236645"/></a>

Example: 

```java
import java.util.concurrent.ExecutorService;   
import java.util.concurrent.Executors;   
import java.util.concurrent.TimeUnit;   
  
public class TestThread {   
                                   public static void main(final String[] arguments) throws InterruptedException {   
ExecutorService e = Executors.newSingleThreadExecutor();   
 
     try {   
       e.submit(new Thread());   
        System.out.println("Shutdown executor");   
        e.shutdown();   
        e.awaitTermination(5, TimeUnit.SECONDS);   
  } catch (InterruptedException ex) {   
       System.err.println("tasks interrupted");   
  } finally {   
  
        if (!e.isTerminated()) {   
           System.err.println("cancel non-finished tasks");   
     }   
        e.shutdownNow();   
        System.out.println("shutdown finished");   
  }   
  }   
  
  static class Task implements Runnable {   
        
     public void run() {   
          
        try {   
        Long duration = (long) (Math.random() * 20);   
           System.out.println("Running Task!");   
           TimeUnit.SECONDS.sleep(duration);   
     } catch (InterruptedException ex) {   
           ex.printStackTrace();   
     }   
  }   
 }          
} 
```

Output:

```java
Shutdown executor 
shutdown finished
```

## 19. What will happen if we don’t override the thread class run() method?

Nothing will happen as such if we don’t override the run() method. The compiler will not show any error. It will execute the run() method of thread class and we will just don’t get any output because the run() method is with an empty implementation. 

Example:  

```java
class MyThread extends Thread { 
  //don't override run() method 
} 
public class DontOverrideRun { 
  public static void main(String[] args) { 
         System.out.println("Started Main."); 
         MyThread thread1=new MyThread(); 
      thread1.start(); 
         System.out.println("Ended Main."); 
  } 
} 
```

Output: 

```java
Started Main. 
Ended Main. 
```

## 20. What is the lock interface? Why is it better to use a lock interface rather than a synchronized block.?

Lock interface was introduced in Java 1.5 and is generally used as a synchronization mechanism to provide important operations for blocking.  

Advantages of using Lock interface over Synchronization block: 

* Methods of Lock interface i.e., Lock() and Unlock() can be called in different methods. It is the main advantage of a lock interface over a synchronized block because the synchronized block is fully contained in a single method.  

* Lock interface is more flexible and makes sure that the longest waiting thread gets a fair chance for execution, unlike the synchronization block.

## 21. Is it possible to call the run() method directly to start a new thread?

No, it's not possible at all. You need to call the start method to create a new thread otherwise run method won't create a new thread. Instead, it will execute in the current thread.

## 22. Is it possible that each thread can have its stack in multithreaded programming?

Of course, it is possible. In multithreaded programming, each thread maintains its own separate stack area in memory because of which every thread is independent of each other rather than dependent.

## Q-13 How deadlock plays a important role in multithreading?

## Q-14 Why output is not ordered? 

## Q-17 What are the tasks of the start() method?

## Q-19 Can we Overload run() method? What if we do not override the run() method? 

## Q-20 Can we Override the start() method?

## Q-13 How deadlock plays a important role in multithreading?

## Q-8 What is the task of the main thread?

## Q-6 What is a thread?

## Q-5 Which Kind of Multitasking is Better and Why?

## Q-4 What is Multithreading and How it is Different from Multitasking?

## Q-3 How do you see a thread?

## Q-2 How can you identify the process?

Any program which is in a working state is referred to as a process. These processes do have threads that are single dispatchable units.

## Q-1 What is multitasking?

## What are the benefits of multi-threaded programming?

In Multi-Threaded programming, multiple threads are executing concurrently that improves the performance because CPU is not idle incase some thread is waiting to get some resources. Multiple threads share the heap memory, so it’s good to create multiple threads to execute some task rather than creating multiple processes. For example, Servlets are better in performance than CGI because Servlet support multi-threading but CGI doesn’t.

## Can we call run() method of a Thread class?

Yes, we can call run() method of a Thread class but then it will behave like a normal method. To actually execute it in a Thread, we need to start it using **Thread.start()** method.

## How can we pause the execution of a Thread for specific time?

We can use Thread class sleep() method to pause the execution of Thread for certain time. Note that this will not stop the processing of thread for specific time, once the thread awake from sleep, it's state gets changed to runnable and based on thread scheduling, it gets executed.

## What do you understand about Thread Priority?

Every thread has a priority, usually higher priority thread gets precedence in execution but it depends on Thread Scheduler implementation that is OS dependent. We can specify the priority of thread but it doesn't guarantee that higher priority thread will get executed before lower priority thread. Thread priority is an _int_ whose value varies from 1 to 10 where 1 is the lowest priority thread and 10 is the highest priority thread.

## What is Thread Scheduler and Time Slicing?

Thread Scheduler is the Operating System service that allocates the CPU time to the available runnable threads. Once we create and start a thread, it's execution depends on the implementation of Thread Scheduler. Time Slicing is the process to divide the available CPU time to the available runnable threads. Allocation of CPU time to threads can be based on thread priority or the thread waiting for longer time will get more priority in getting CPU time. Thread scheduling can't be controlled by java, so it's always better to control it from application itself.

## What is context-switching in multi-threading?

Context Switching is the process of storing and restoring of CPU state so that Thread execution can be resumed from the same point at a later point of time. Context Switching is the essential feature for multitasking operating system and support for multi-threaded environment.

## How can we make sure main() is the last thread to finish in Java Program?

We can use Thread join() method to make sure all the threads created by the program is dead before finishing the main function. 

## How does thread communicate with each other?

When threads share resources, communication between Threads is important to coordinate their efforts. Object class wait(), notify() and notifyAll() methods allows threads to communicate about the lock status of a resource. 

## Why thread communication methods wait(), notify() and notifyAll() are in Object class?

In Java every Object has a monitor and wait, notify methods are used to wait for the Object monitor or to notify other threads that Object monitor is free now. There is no monitor on threads in java and synchronization can be used with any Object, that's why it's part of Object class so that every class in java has these essential methods for inter thread communication.

## Why wait(), notify() and notifyAll() methods have to be called from synchronized method or block?

When a Thread calls wait() on any Object, it must have the monitor on the Object that it will leave and goes in wait state until any other thread call notify() on this Object. Similarly when a thread calls notify() on any Object, it leaves the monitor on the Object and other waiting threads can get the monitor on the Object. Since all these methods require Thread to have the Object monitor, that can be achieved only by synchronization, they need to be called from synchronized method or block.

## Why Thread sleep() and yield() methods are static?

Thread sleep() and yield() methods work on the currently executing thread. So there is no point in invoking these methods on some other threads that are in wait state. That’s why these methods are made static so that when this method is called statically, it works on the current executing thread and avoid confusion to the programmers who might think that they can invoke these methods on some non-running threads.

## How can we achieve thread safety in Java?

There are several ways to achieve thread safety in java - synchronization, atomic concurrent classes, implementing concurrent Lock interface, using volatile keyword, using immutable classes and Thread safe classes. 

## What is volatile keyword in Java

When we use volatile keyword with a variable, all the threads read it's value directly from the memory and don't cache it. This makes sure that the value read is the same as in the memory.

## Which is more preferred - Synchronized method or Synchronized block?

Synchronized block is more preferred way because it doesn't lock the Object, synchronized methods lock the Object and if there are multiple synchronization blocks in the class, even though they are not related, it will stop them from execution and put them in wait state to get the lock on Object.

## What is Java Thread Dump, How can we get Java Thread dump of a Program?

A thread dump is a list of all the threads active in the JVM, thread dumps are very helpful in analyzing bottlenecks in the application and analyzing deadlock situations. There are many ways using which we can generate Thread dump - Using Profiler, Kill -3 command, jstack tool, etc. I prefer jstack tool to generate thread dump of a program because it's easy to use and comes with JDK installation. Since it's a terminal-based tool, we can create a script to generate thread dump at regular intervals to analyze it later on. 

## What is Deadlock? How to analyze and avoid deadlock situation?

Deadlock is a programming situation where two or more threads are blocked forever, this situation arises with at least two threads and two or more resources. To analyze a deadlock, we need to look at the java thread dump of the application, we need to look out for the threads with state as BLOCKED and then the resources it’s waiting to lock, every resource has a unique ID using which we can find which thread is already holding the lock on the object. Avoid Nested Locks, Lock Only What is Required and Avoid waiting indefinitely are common ways to avoid deadlock situation,

## What is Java Timer Class? How to schedule a task to run after the specified interval?

java.util.Timer is a utility class that can be used to schedule a thread to be executed at a certain time in future. Java Timer class can be used to schedule a task to be run one-time or to be run at regular intervals. java.util.TimerTask is an **[abstract class](/community/tutorials/abstract-class-in-java "Abstract Class in Java with Example")** that implements Runnable interface and we need to extend this class to create our own TimerTask that can be scheduled using java Timer class. Check this post for [java Timer example](/community/tutorials/java-timer-timertask-example).

##  What is Thread Pool? How can we create Thread Pool in Java?

A thread pool manages the pool of worker threads, it contains a queue that keeps tasks waiting to get executed. A thread pool manages the collection of Runnable threads and worker threads execute Runnable from the queue. java.util.concurrent.Executors provide implementation of java.util.concurrent.Executor interface to create the thread pool in java. [Thread Pool Example](/community/tutorials/threadpoolexecutor-java-thread-pool-example-executorservice) program shows how to create and use Thread Pool in java. Or read [ScheduledThreadPoolExecutor Example](/community/tutorials/java-scheduler-scheduledexecutorservice-scheduledthreadpoolexecutor-example) to know how to schedule tasks after certain delay.

# Java Concurrency Interview Questions and Answers

## What is atomic operation? What are atomic classes in Java Concurrency API?

## What is Lock interface in Java Concurrency API? What are its benefits over synchronization?

## What is Executors Framework?

## What is BlockingQueue? How can we implement Producer-Consumer problem using Blocking Queue?

## What is Callable and Future?

## What is FutureTask Class?

## What are Concurrent Collection Classes?

## What is Executors Class?

## What are some of the improvements in Concurrency API in Java 8?

## Some important concurrent API enhancements are:

-   ConcurrentHashMap compute(), forEach(), forEachEntry(), forEachKey(), forEachValue(), merge(), reduce() and search() methods.
-   CompletableFuture that may be explicitly completed (setting its value and status).
-   Executors newWorkStealingPool() method to create a work-stealing thread pool using all available processors as its target parallelism level.

**Recommended Read**: [Java 8 Features](/community/tutorials/java-8-features-with-examples "Java 8 Features for Developers – lambdas, Functional interface, Stream and Time API")

## 1) What is multithreading?

Multithreading is a process of executing multiple threads simultaneously. Multithreading is used to obtain the multitasking. It consumes less memory and gives the fast and efficient performance. Its main advantages are:

* Threads share the same address space.

* The thread is lightweight.

* The cost of communication between the processes is low.

## 2) What is the thread?

A thread is a lightweight subprocess. It is a separate path of execution because each thread runs in a different stack frame. A process may contain multiple threads. Threads share the process resources, but still, they execute independently.

## 4) What do you understand by inter-thread communication?

* The process of communication between synchronized threads is termed as inter-thread communication.
* Inter-thread communication is used to avoid thread polling in Java.

* The thread is paused running in its critical section, and another thread is allowed to enter (or lock) in the same critical section to be executed.

* It can be obtained by wait(), notify(), and notifyAll() methods.

## 6) Why must wait() method be called from the synchronized block?
We must call the wait method otherwise it will throw java.lang.IllegalMonitorStateException exception. Moreover, we need wait() method for inter-thread communication with notify() and notifyAll(). Therefore It must be present in the synchronized block for the proper and correct communication.

## 9) What is the difference between preemptive scheduling and time slicing?
 
Under preemptive scheduling, the highest priority task executes until it enters the waiting or dead states or a higher priority task comes into existence. Under time slicing, a task executes for a predefined slice of time and then reenters the pool of ready tasks. The scheduler then determines which task should execute next, based on priority and other factors.

## 10) What is context switching?

In Context switching the state of the process (or thread) is stored so that it can be restored and execution can be resumed from the same point later. Context switching enables the multiple processes to share the same CPU.

## 12) What does join() method?
The join() method waits for a thread to die. In other words, it causes the currently running threads to stop executing until the thread it joins with completes its task. Join method is overloaded in Thread class in the following ways.

* public void join()throws InterruptedException
* public void join(long milliseconds)throws InterruptedException

## 17) What about the daemon threads?

The daemon threads are the low priority threads that provide the background support and services to the user threads. Daemon thread gets automatically terminated by the JVM if the program remains with the daemon thread only, and all other user threads are ended/died. There are two methods for daemon thread available in the Thread class:

* **public void setDaemon(boolean status)**: It used to mark the thread daemon thread or a user thread.

* **public boolean isDaemon()**: It checks the thread is daemon or not.

## 18) Can we make the user thread as daemon thread if the thread is started?

No, if you do so, it will throw IllegalThreadStateException. Therefore, we can only create a daemon thread before starting the thread.

```java
class Testdaemon1 extends Thread{    
public void run(){  
          System.out.println("Running thread is daemon...");  
}  
public static void main (String[] args) {  
      Testdaemon1 td= new Testdaemon1();  
      td.start();  
      setDaemon(true);// It will throw the exception: td.   
   }  
}  
```

Output

```java
Running thread is daemon...
Exception in thread "main" java.lang.IllegalThreadStateException
at java.lang.Thread.setDaemon(Thread.java:1359)
at Testdaemon1.main(Testdaemon1.java:8)
```

## 19) What is shutdown hook?

The shutdown hook is a thread that is invoked implicitly before JVM shuts down. So we can use it to perform clean up the resource or save the state when JVM shuts down normally or abruptly. We can add shutdown hook by using the following method:

```java
public void addShutdownHook(Thread hook){}    
Runtime r=Runtime.getRuntime();  
r.addShutdownHook(new MyThread());
```

Some important points about shutdown hooks are :

* Shutdown hooks initialized but can only be started when JVM shutdown occurred.

* Shutdown hooks are more reliable than the finalizer() because there are very fewer chances that shutdown hooks not run.

* The shutdown hook can be stopped by calling the halt(int) method of Runtime class.

## 20)When should we interrupt a thread?

We should interrupt a thread when we want to break out the sleep or wait state of a thread. We can interrupt a thread by calling the interrupt() throwing the InterruptedException.

## 21) What is the synchronization?

Synchronization is the capability to control the access of multiple threads to any shared resource. It is used:

1. To prevent thread interference.

2. To prevent consistency problem.

When the multiple threads try to do the same task, there is a possibility of an erroneous result, hence to remove this issue, Java uses the process of synchronization which allows only one thread to be executed at a time. Synchronization can be achieved in three ways:

* by the synchronized method

* by synchronized block

* by static synchronization

Syntax for synchronized block

```java
synchronized(object reference expression)  
    {  
        //code block  
    }  
```

## 22) What is the purpose of the Synchronized block?

The Synchronized block can be used to perform synchronization on any specific resource of the method. Only one thread at a time can execute on a particular resource, and all other threads which attempt to enter the synchronized block are blocked.

* Synchronized block is used to lock an object for any shared resource.

* The scope of the synchronized block is limited to the block on which, it is applied. Its scope is smaller than a method.

## 23) Can Java object be locked down for exclusive use by a given thread?

Yes. You can lock an object by putting it in a "synchronized" block. The locked object is inaccessible to any thread other than the one that explicitly claimed it.


## 24) What is static synchronization?

If you make any static method as synchronized, the lock will be on the class not on the object. If we use the synchronized keyword before a method so it will lock the object (one thread can access an object at a time) but if we use static synchronized so it will lock a class (one thread can access a class at a time).

## 25)What is the difference between notify() and notifyAll()?

The notify() is used to unblock one waiting thread whereas notifyAll() method is used to unblock all the threads in waiting state.

##  26)What is the deadlock?

Deadlock is a situation in which every thread is waiting for a resource which is held by some other waiting thread. In this situation, Neither of the thread executes nor it gets the chance to be executed. Instead, there exists a universal waiting state among all the threads. Deadlock is a very complicated situation which can break our code at runtime.

## 27) How to detect a deadlock condition? How can it be avoided?

We can detect the deadlock condition by running the code on cmd and collecting the Thread Dump, and if any deadlock is present in the code, then a message will appear on cmd.

Ways to avoid the deadlock condition in Java:

* **Avoid Nested lock**: Nested lock is the common reason for deadlock as deadlock occurs when we provide locks to various threads so we should give one lock to only one thread at some particular time.

* **Avoid unnecessary locks**: we must avoid the locks which are not required.

* **Using thread join**: Thread join helps to wait for a thread until another thread doesn't finish its execution so we can avoid deadlock by maximum use of join method.

## 28) What is Thread Scheduler in java?

In Java, when we create the threads, they are supervised with the help of a Thread Scheduler, which is the part of JVM. Thread scheduler is only responsible for deciding which thread should be executed. Thread scheduler uses two mechanisms for scheduling the threads: Preemptive and Time Slicing.

Java thread scheduler also works for deciding the following for a thread:
* It selects the priority of the thread.

* It determines the waiting time for a thread

* It checks the Nature of thread

## 29) Does each thread have its stack in multithreaded programming?

Yes, in multithreaded programming every thread maintains its own or separate stack area in memory due to which every thread is independent of each other.

## 30) How is the safety of a thread achieved?

If a method or class object can be used by multiple threads at a time without any race condition, then the class is thread-safe. Thread safety is used to make a program safe to use in multithreaded programming. It can be achieved by the following ways:

* Synchronization
* Using Volatile keyword
* Using a lock based mechanism
* Use of atomic wrapper classes

## 31) What is race-condition?

A Race condition is a problem which occurs in the multithreaded programming when various threads execute simultaneously accessing a shared resource at the same time. The proper use of synchronization can avoid the Race condition.

## 32) What is the volatile keyword in java?

Volatile keyword is used in multithreaded programming to achieve the thread safety, as a change in one volatile variable is visible to all other threads so one variable can be used by one thread at a time.

## 33) What do you understand by thread pool?

* Java Thread pool represents a group of worker threads, which are waiting for the task to be allocated.

* Threads in the thread pool are supervised by the service provider which pulls one thread from the pool and assign a job to it.

* After completion of the given task, thread again came to the thread pool.

* The size of the thread pool depends on the total number of threads kept at reserve for execution.

The advantages of the thread pool are :

* Using a thread pool, performance can be enhanced.

* Using a thread pool, better system stability can occur.

## 34) What are the main components of concurrency API?

Concurrency API can be developed using the class and interfaces of java.util.Concurrent package. There are the following classes and interfaces in java.util.Concurrent package.

* Executor

* FarkJoinPool

* ExecutorService

* ScheduledExecutorService

* Future

* TimeUnit(Enum)

* CountDownLatch

* CyclicBarrier

* Semaphore

* ThreadFactory

* BlockingQueue

* DelayQueue

* Locks

* Phaser

## 35) What is the Executor interface in Concurrency API in Java?

The Executor Interface provided by the package java.util.concurrent is the simple interface used to execute the new task. The execute() method of Executor interface is used to execute some given command. The syntax of the execute() method is given below.

```java
void execute(Runnable command)
```

Consider the following example:

```java
import java.util.concurrent.Executor;  
import java.util.concurrent.Executors;  
import java.util.concurrent.ThreadPoolExecutor;  
import java.util.concurrent.TimeUnit;  
  
public class TestThread {  
   public static void main(final String[] arguments) throws InterruptedException {  
      Executor e = Executors.newCachedThreadPool();  
      e.execute(new Thread());  
      ThreadPoolExecutor pool = (ThreadPoolExecutor)e;  
      pool.shutdown();  
   }    
  
   static class Thread implements Runnable {  
      public void run() {  
         try {  
            Long duration = (long) (Math.random() * 5);  
            System.out.println("Running Thread!");  
            TimeUnit.SECONDS.sleep(duration);  
            System.out.println("Thread Completed");  
         } catch (InterruptedException ex) {  
            ex.printStackTrace();  
         }  
      }  
   }  
} 
```

Output

```java
Running Thread!
Thread Completed
```

## 36) What is BlockingQueue?

The java.util.concurrent.BlockingQueue is the subinterface of Queue that supports the operations such as waiting for the space availability before inserting a new value or waiting for the queue to become non-empty before retrieving an element from it. Consider the following example.

```java      
import java.util.Random;  
import java.util.concurrent.ArrayBlockingQueue;  
import java.util.concurrent.BlockingQueue;  
  
public class TestThread {  
  
   public static void main(final String[] arguments) throws InterruptedException {  
      BlockingQueue<Integer> queue = new ArrayBlockingQueue<Integer>(10);  
  
      Insert i = new Insert(queue);  
      Retrieve r = new Retrieve(queue);  
  
      new Thread(i).start();  
      new Thread(r).start();  
  
      Thread.sleep(2000);  
   }    
  
  
   static class Insert implements Runnable {  
      private BlockingQueue<Integer> queue;  
  
      public Insert(BlockingQueue queue) {  
         this.queue = queue;  
      }  
  
      @Override  
      public void run() {  
         Random random = new Random();  
  
         try {  
            int result = random.nextInt(200);  
            Thread.sleep(1000);  
            queue.put(result);  
            System.out.println("Added: " + result);  
              
            result = random.nextInt(10);  
            Thread.sleep(1000);  
            queue.put(result);  
            System.out.println("Added: " + result);  
              
            result = random.nextInt(50);  
            Thread.sleep(1000);  
            queue.put(result);  
            System.out.println("Added: " + result);  
         } catch (InterruptedException e) {  
            e.printStackTrace();  
         }  
      }      
   }  
  
   static class Retrieve implements Runnable {  
      private BlockingQueue<Integer> queue;  
  
      public Retrieve(BlockingQueue queue) {  
         this.queue = queue;  
      }  
        
      @Override  
      public void run() {  
           
         try {  
            System.out.println("Removed: " + queue.take());  
            System.out.println("Removed: " + queue.take());  
            System.out.println("Removed: " + queue.take());  
         } catch (InterruptedException e) {  
            e.printStackTrace();  
         }  
      }  
   }  
}  
```

Output

```java
Added: 96
Removed: 96
Added: 8
Removed: 8
Added: 5
Removed: 5
```

## 7) How to implement producer-consumer problem by using BlockingQueue?

The producer-consumer problem can be solved by using BlockingQueue in the following way.

```java      
import java.util.concurrent.BlockingQueue;  
import java.util.concurrent.LinkedBlockingQueue;  
import java.util.logging.Level;  
import java.util.logging.Logger;  
public class ProducerConsumerProblem {  
    public static void main(String args[]){  
     //Creating shared object  
     BlockingQueue sharedQueue = new LinkedBlockingQueue();  
  
     //Creating Producer and Consumer Thread  
     Thread prod = new Thread(new Producer(sharedQueue));  
     Thread cons = new Thread(new Consumer(sharedQueue));  
  
     //Starting producer and Consumer thread  
     prod.start();  
     cons.start();  
    }  
   
}  
  
//Producer Class in java  
class Producer implements Runnable {  
  
    private final BlockingQueue sharedQueue;  
  
    public Producer(BlockingQueue sharedQueue) {  
        this.sharedQueue = sharedQueue;  
    }  
  
    @Override  
    public void run() {  
        for(int i=0; i<10; i++){  
            try {  
                System.out.println("Produced: " + i);  
                sharedQueue.put(i);  
            } catch (InterruptedException ex) {  
                Logger.getLogger(Producer.class.getName()).log(Level.SEVERE, null, ex);  
            }  
        }  
    }  
  
}  
  
//Consumer Class in Java  
class Consumer implements Runnable{  
  
    private final BlockingQueue sharedQueue;  
  
    public Consumer (BlockingQueue sharedQueue) {  
        this.sharedQueue = sharedQueue;  
    }  
    
    @Override  
    public void run() {  
        while(true){  
            try {  
                System.out.println("Consumed: "+ sharedQueue.take());  
            } catch (InterruptedException ex) {  
                Logger.getLogger(Consumer.class.getName()).log(Level.SEVERE, null, ex);  
            }  
        }  
    }  
}  
```

Output

```java
Produced: 0
Produced: 1
Produced: 2
Produced: 3
Produced: 4
Produced: 5
Produced: 6
Produced: 7
Produced: 8
Produced: 9
Consumed: 0
Consumed: 1
Consumed: 2
Consumed: 3
Consumed: 4
Consumed: 5
Consumed: 6
Consumed: 7
Consumed: 8
Consumed: 9
```

## 38) What is the difference between Java Callable interface and Runnable interface?

The Callable interface and Runnable interface both are used by the classes which wanted to execute with multiple threads. However, there are two main differences between the both :

* A Callable <V> interface can return a result, whereas the Runnable interface cannot return any result.

* A Callable <V> interface can throw a checked exception, whereas the Runnable interface cannot throw checked exception.

* A Callable <V> interface cannot be used before the Java 5 whereas the Runnable interface can be used.

## 39) What is the Atomic action in Concurrency in Java?

* The Atomic action is the operation which can be performed in a single unit of a task without any interference of the other operations.

* The Atomic action cannot be stopped in between the task. Once started it fill stop after the completion of the task only.

* An increment operation such as a++ does not allow an atomic action.

* All reads and writes operation for the primitive variable (except long and double) are the atomic operation.

* All reads and writes operation for the volatile variable (including long and double) are the atomic operation.

* The Atomic methods are available in java.util.Concurrent package.

## 40) What is lock interface in Concurrency API in Java?

The java.util.concurrent.locks.Lock interface is used as the synchronization mechanism. It works similar to the synchronized block. There are a few differences between the lock and synchronized block that are given below.

* Lock interface provides the guarantee of sequence in which the waiting thread will be given the access, whereas the synchronized block doesn't guarantee it.

* Lock interface provides the option of timeout if the lock is not granted whereas the synchronized block doesn't provide that.

* The methods of Lock interface, i.e., Lock() and Unlock() can be called in different methods whereas single synchronized block must be fully contained in a single method.

## 41) Explain the ExecutorService Interface.

The ExecutorService Interface is the subinterface of Executor interface and adds the features to manage the lifecycle. Consider the following example.

```java
import java.util.concurrent.ExecutorService;  
import java.util.concurrent.Executors;  
import java.util.concurrent.TimeUnit;  
  
public class TestThread {  
   public static void main(final String[] arguments) throws InterruptedException {  
      ExecutorService e = Executors.newSingleThreadExecutor();  
  
      try {  
         e.submit(new Thread());  
         System.out.println("Shutdown executor");  
         e.shutdown();  
         e.awaitTermination(5, TimeUnit.SECONDS);  
      } catch (InterruptedException ex) {  
         System.err.println("tasks interrupted");  
      } finally {  
  
         if (!e.isTerminated()) {  
            System.err.println("cancel non-finished tasks");  
         }  
         e.shutdownNow();  
         System.out.println("shutdown finished");  
      }  
   }  
  
   static class Task implements Runnable {  
        
      public void run() {  
           
         try {  
            Long duration = (long) (Math.random() * 20);  
            System.out.println("Running Task!");  
            TimeUnit.SECONDS.sleep(duration);  
         } catch (InterruptedException ex) {  
            ex.printStackTrace();  
         }  
      }  
   }         
}  
```

Output

```java
Shutdown executor
shutdown finished
```

## 42) What is the difference between Synchronous programming and Asynchronous programming regarding a thread?

**Synchronous programming**: In Synchronous programming model, a thread is assigned to complete a task and hence thread started working on it, and it is only available for other tasks once it will end the assigned task.

**Asynchronous Programming**: In Asynchronous programming, one job can be completed by multiple threads and hence it provides maximum usability of the various threads.

## 43) What do you understand by Callable and Future in Java?

**Java Callable interface**: In Java5 callable interface was provided by the package java.util.concurrent. It is similar to the Runnable interface but it can return a result, and it can throw an Exception. It also provides a run() method for execution of a thread. Java Callable can return any object as it uses Generic.

Syntax:

```java
public interface Callable<V>
```
**Java Future interface**: Java Future interface gives the result of a concurrent process. The Callable interface returns the object of java.util.concurrent.Future.

Java Future provides following methods for implementation.

* **cancel(boolean mayInterruptIfRunning)**: It is used to cancel the execution of the assigned task.

* **get()**: It waits for the time if execution not completed and then retrieved the result.

* **isCancelled()**: It returns the Boolean value as it returns true if the task was canceled before the completion.

* **isDone()**: It returns true if the job is completed successfully else returns false.

## 44. What is the difference between ScheduledExecutorService and ExecutorService interface?

ExecutorServcie and ScheduledExecutorService both are the interfaces of java.util.Concurrent package but scheduledExecutorService provides some additional methods to execute the Runnable and Callable tasks with the delay or every fixed time period.

## 45) Define FutureTask class in Java?

Java FutureTask class provides a base implementation of the Future interface. The result can only be obtained if the execution of one task is completed, and if the computation is not achieved then get method will be blocked. If the execution is completed, then it cannot be re-started and can't be canceled.

Syntax

```java
public class FutureTask<V> extends Object implements RunnableFuture<V>
```