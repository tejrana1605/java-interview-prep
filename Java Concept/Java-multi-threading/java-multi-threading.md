# Introduction To Threads In Java

## Application :

Application is a program which is designed to perform a specific task. For example, MS Word, Google Chrome, a video or audio player etc.

## Process :

Process is an executing instance of an application. For example, when you double click MS Word icon in your computer, you start a process that will run this MS word application. Processes are heavy weight operations that they require their own separate memory address in operating system. Because of the processes are stored in separate memory, communication between processes (Inter Process Communication) takes time. Context switching from one process to another process is also expensive.

## Thread :

Thread is a smallest executable unit of a process. Thread has it’s own path of execution in a process. For example, when you start MS word, operating system creates a process and start the execution of a primary thread of that process. A process can have multiple threads. Threads of the same process share the memory address of that process. i.e threads are stored inside the memory of a process. As the threads are stored in the same memory space, communication between threads (Inter Thread Communication) is fast. Context switching from one thread to another thread is also less expensive.

Processes and threads can be diagrammatically represented as below,

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2014/11/ThreadsAndProcesses.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

## Multitasking :
Multitasking is an operation in which multiple tasks are performed simultaneously. Multitasking is used to utilize CPU’s idle time. Multitasking can be of two types. One is process-based and another one is thread-based.

1) Process-based multitasking Or Multiprocessing :
In process-based multitasking or multiprocessing, Multiple processes are executed simultaneously. You are all familiar with process-based multitasking. Because of this feature only, your computer runs two or more programs simultaneously. For example, You can play a video file and print a text file simultaneously in your computer.

2) Thread-based Multitasking  Or Multithreading:
In thread-based multitasking or multithreading, multiple threads in a process are executed simultaneously. For example, MS word can print a document using background thread, at the same another thread can accept the user input so that user can create a new document.

Now come to Threads in java. Consider this example.

```java
public class ThreadsInJava
{
    //Main Thread
    public static void main(String[] args)
    {
        for (int i = 0; i <= 100; i++)
        {
            System.out.println("From Main Thread");
        }
    }
}
```


When you run this program, java command creates a primary thread or main thread which is responsible for executing main method. That’s why, execution of all java programs start with main() method.

This is an example of single thread execution. Java supports multi thread execution. i.e Java program can have more than one threads that can run simultaneously. This is called multithreaded programming.

For example, in the below program, main thread creates two threads. The task of first thread is to print the numbers from 0 to 1000. The task of second thread is to print the numbers from 1001 to 2000. These two threads perform their task simulataneously not one after the other.

```java
//Defining first thread with task
//The task of this thread is to print the numbers from 0 to 1000 times
class Thread1 extends Thread
{
    @Override
    public void run()
    {
        for(int i = 0; i <= 1000; i++)
        {
            System.out.println(i);
        }
    }
}
 
//Defining second thread with task
//The task of this thread is to print the numbers from 1001 to 2000
class Thread2 extends Thread
{
    @Override
    public void run()
    {
        for(int i = 1001; i<= 2000; i++)
        {
            System.out.println(i);
        }
    }
}
 
public class ThreadsInJava
{
    //Main Thread
    public static void main(String[] args)
    {
        //Creating first thread
        Thread1 t1 = new Thread1();
        t1.start();
 
        //Creating second thread
        Thread2 t2 = new Thread2();
        t2.start();
    }
}
```

# Creating Threads In Java

There are two ways to create threads in java language.

1) By extending java.lang.Thread class.

2) By implementing java.lang.Runnable interface.

## 1) By Extending java.lang.Thread Class

You can create your own thread by extending Thread class of java.lang package. You have to override run() method of Thread class and keep the task which you want your thread to perform in this run() method. Here is the syntax of creating a thread by extending Thread class.

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

After defining your thread, create an object of your thread and call start() method where ever you want this task to be performed. Like this,

```java
MyThread myThread = new MyThread();
myThread.start();
```

The following example shows how to create a thread by extending Thread class and how to start it.

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        //Task of this thread is to print multiplication of successive numbers up to 1000 numbers
        for(int i = 0; i < 1000; i++)
        {
            System.out.println(i+" * "+(i+1)+" = " + i * (i+1));
        }
    }
}
 
public class ThreadsInJava
{
    //Main Thread
    public static void main(String[] args)
    {
        //Creating and starting MyThread.
        MyThread myThread = new MyThread();
        myThread.start();
    }
}
```

## 2) By Implementing java.lang.Runnable Interface.
Another method of creating a thread is to implement Runnable interface of java.lang package. Runnable interface has only one abstract method i.e run(). You have to implement this method and keep the task to be performed in this method. Here is the syntax for creating a thread by implementing Runnable interface.

```java
class MyThread implements Runnable
{
    @Override
    public void run()
    {
        //Keep the task to be performed here
    }
}
```

After defining the thread, create an object to java.lang.Thread class through a constructor which takes Runnable type as an argument and pass the object of your thread that implements Runnable interface as an argument to it and call the start() method.Like this,

```java
MyThread myThread = new MyThread();    //Creating object of your thread that implements Runnable interface
Thread t = new Thread(myThread);       //passing your thread object to the constructor of Thread class
t.start();   
```

The following example shows how to create a thread by implementing Runnable interface and how to start it.

```java
class MyThread implements Runnable
{
    @Override
    public void run()
    {
        //Task of this thread is to print multiplication of successive numbers up to 1000 numbers
        for(int i = 0; i < 1000; i++)
        {
            System.out.println(i+" * "+(i+1)+" = " + i * (i+1));
        }
    }
}
 
public class ThreadsInJava
{
    //Main Thread
    public static void main(String[] args)
    {
        MyThread myThread = new MyThread();    //instantiating your thread class that implements Runnable interface
 
        Thread t = new Thread(myThread);       //Creating an object to Thread class by passing your thread as an argument
 
        t.start();                            //Starting the thread
    }
}
```

# Different Ways Of Defining Threads In Java

In the previous concept, we have seen two ways of creating thread class. It can be created by extending java.lang.Thread class or it can be created by implementing java.lang.Runnable interface. Such created thread class can be a separate concrete class or it can be an inner class of the usage class or it can be a local inner class of the method of usage class or it can be an anonymous inner class. Let’s discuss different ways of defining threads in java.

Note : Usage class is a class where you use the thread and it’s task.

## 1) Thread As A Separate Concrete Class

Threads class can be defined as a separate concrete class. This method of defining thread class is useful when more than one classes need that task to be performed.

```java
//Thread as a separate concrete class
class MyThread extends Thread
{
    @Override
    public void run()
    {
        System.out.println("Keep Some task here......");
    }
}
 
//Usage Class
class UsageClassOne
{
    void method()
    {
        //Using the thread and it's task
 
        MyThread t = new MyThread();
        t.start();
    }
}
 
//Usage Class
class UsageClassTwo
{
    void method()
    {
        //Using the thread and it's task
 
        MyThread t = new MyThread();
        t.start();
    }
}
```

## 2) Thread As A Nested Class or Static Inner Class

Thread class can be defined as a nested class or static inner class of the usage class. This method is useful when only one class uses the thread and it’s task more oftenly.

```java
public class UsageClass
{
    //Thread class as a nested class or Static Inner Class of the usage class
    static class MyThread1 extends Thread
    {
        @Override
        public void run()
        {
            System.out.println("Keep some task here.....");
        }
    }
 
    //Another thread class as a nested class or Static Inner Class of the usage class
    static class MyThread2 implements Runnable
    {
        @Override
        public void run()
        {
            System.out.println("Keep some task here......");
        }
    }
 
    public static void main(String[] args)
    {
        //Using the MyThread1 and it's task
 
        MyThread1 thread1 = new MyThread1();
        thread1.start();
 
        //Using MyThread2 and it's task
 
        MyThread2 thread2 = new MyThread2();
        Thread t = new Thread(thread2);
        t.start();
    }
}
```

## 3) Thread As A Member Inner Class or Non-static Inner Class

This method is also useful when one class uses thread and it’s task more excessively.

```java
public class UsageClass
{
    //Thread class as a member inner class or Non-static Inner Class of the usage class
    class MyThread1 extends Thread
    {
        @Override
        public void run()
        {
            System.out.println("Keep Some task here.....");
        }
    }
 
    //Another thread class as a member inner class or Non-Static Inner Class of the usage class
    class MyThread2 implements Runnable
    {
        @Override
        public void run()
        {
            System.out.println("Keep some task here.....");
        }
    }
 
    public static void main(String[] args)
    {
        //Using MyThread1 and it's task
 
        MyThread1 thread1 = new UsageClass().new MyThread1();
        thread1.start();
 
        //Using MyThread2 and it's task
 
        MyThread2 thread2 = new UsageClass().new MyThread2();
        Thread t = new Thread(thread2);
        t.start();
    }
}
```

## 4) Thread As A Local Inner Class

The thread class can be defined as a local inner class of the method of the usage class. If declared so, only that method can use the functionality of that thread.

```java
public class UsageClass
{
    public static void main(String[] args)
    {
        //Thread as a Local Inner Class
        class MyThread1 extends Thread
        {
            @Override
            public void run()
            {
                System.out.println("Keep some task here.....");
            }
        }
 
        //Another thread as a Local Inner Class
        class MyThread2 implements Runnable
        {
            @Override
            public void run()
            {
                System.out.println("Keep some task here.....");
            }
        }
 
        //Using MyThread1 and it's task
 
        MyThread1 thread1 = new MyThread1();
        thread1.start();
 
        //Using MyThread2 and it's task
 
        MyThread2 thread2 = new MyThread2();
        Thread t = new Thread(thread2);
        t.start();
    }
}
```

## 5) Thread As An Anonymous Inner Class

Threads can be declared as anonymous inner class. This method is useful when some task is needed only once. You can’t use the thread which is declared as anonymous inner class multiple times. You can use it only once.

```java
public class UsageClass
{
    public static void main(String[] args)
    {
        //Thread as an anonymous inner class
        new Thread()
        {
            @Override
            public void run()
            {
                System.out.println("Keep some task here.....");
            }
        }.start();
 
        //Thread as an anonymous inner class
        new Thread(new Runnable() {
 
            @Override
            public void run()
            {
                System.out.println("Keep some task here.....");
 
            }
        }).start();
    }
}
```

## 6) Usage class itself as a thread class.

You can declare usage class itself as a thread class. If declared so, other classes can also use the thread and it’s task.

```java
class UsageClass extends Thread
{
    @Override
    public void run()
    {
        System.out.println("Keep some task here.....");
    }
 
    public static void main(String[] args)
    {
        //Using thread and it's task
 
        UsageClass t = new UsageClass();
        t.start();
    }
}
 
//Another Usage Class
class AnotherUsageClass
{
    void method()
    {
        //Using the thread and it's task
 
        UsageClass t = new UsageClass();
        t.start();
    }
}
```

# Types Of Threads In Java

There are two types of Threads in java.

1) User Thread

2) Daemon Thread

## 1) User Thread :

User threads are threads which are created by the application or user. They are high priority threads. JVM (Java Virtual Machine) will not exit until all user threads finish their execution. JVM wait for these threads to finish their task. These threads are foreground threads.

## 2) Daemon Thread :

Daemon threads are threads which are mostly created by the JVM. These threads always run in background. These threads are used to perform some background tasks like garbage collection and house-keeping tasks. These threads are less priority threads. JVM will not wait for these threads to finish their execution. JVM will exit as soon as all user threads finish their execution. JVM doesn’t wait for daemon threads to finish their task.

## Some Things-To-Remember about user threads and daemon threads In Java :

* You can convert user thread into daemon thread explicitly by calling setDaemon() method of the thread.

```java
class UserThread extends Thread
{
    @Override
    public void run()
    {
        for(int i = 0; i < 1000; i++)
        {
            System.out.println("This is an user thread....");
        }
    }
}
 
public class ThreadsInJava
{
    //Main Thread
    public static void main(String[] args)
    {
        UserThread userThread = new UserThread();   //Creating the UserThread
 
        userThread.setDaemon(true);        //Changing the thread as Daemon
 
        userThread.start();               //Starting the thread
    }
}
```

* You can’t set a daemon property after starting the thread. If you try to set the daemon property when the thread is active, It will throw a IllegalThreadStateException at run time.

```java
class UserThread extends Thread
{
    @Override
    public void run()
    {
        for(int i = 0; i < 1000; i++)
        {
            System.out.println("This is an user thread....");
        }
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        UserThread userThread = new UserThread();   //Creating the UserThread
 
        userThread.start();               //Starting the thread
 
        userThread.setDaemon(true);        //This statement will throw IllegalThreadStateException
    }
}
```

* You can check whether the thread is user thread or a daemon thread by using isDaemon() method of Thread class. This method returns “true” for a daemon thread and “false” for a user thread.

```java
{
    @Override
    public void run()
    {
        for(int i = 0; i < 1000; i++)
        {
            System.out.println("This is an user thread....");
        }
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        UserThread userThread = new UserThread();   //Creating the UserThread
 
        System.out.println(userThread.isDaemon());    //Output : false
 
        userThread.setDaemon(true);         //changing the thread as Daemon
 
        userThread.start();                 //Starting the thread
 
        System.out.println(userThread.isDaemon());      //Output : true
    }
}
```

* Daemon property of a thread is inherited from it’s parent thread. i.e The thread created by user thread will be user thread and the thread created by daemon thread will be a daemon thread.


```java
class Thread1 extends Thread
{
    @Override
    public void run()
    {
        Thread t = new Thread();      //Creating a child thread
 
        System.out.println(t.isDaemon());   //Checking the Daemon property of a child thread
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread1 t1 = new Thread1();   //Creating the Thread1
 
        t1.start();                 //Starting the thread
 
        Thread1 t2 = new Thread1();   //Creating the Thread1
 
        t2.setDaemon(true);         //changing the thread as Daemon
 
        t2.start();          //Starting the thread
    }
}
```

* The main thread or primary thread created by JVM is an user thread.

* **Demonstration of User thread and daemon thread**  :  In the below program, The task of daemon thread will not be completed. Program terminates as soon as user thread finishes it’s task. It will not wait for daemon thread to finish it’s task.


```java
class UserThread extends Thread
{
    @Override
    public void run()
    {
        System.out.println("This is a user thread.....");
    }
}
 
class DaemonThread extends Thread
{
    public DaemonThread()
    {
        setDaemon(true);
    }
 
    @Override
    public void run()
    {
        for(int i = 0; i < 1000; i++)
        {
            System.out.println("This is daemon thread....."+i);
        }
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        DaemonThread daemon = new DaemonThread();   //Creating the DaemonThread
 
        daemon.start();                 //Starting the daemon thread
 
        UserThread userThread = new UserThread();   //Creating the UserThread
 
        userThread.start();          //Starting the user thread
    }
}
```

# Difference Between User Threads Vs Daemon Threads In Java

There are two types of threads in java. One is User Thread and another one is Daemon Thread. User threads are high priority threads which always run in foreground. Where as Daemon threads are low priority threads which always run in background. User threads are designed to do some specific task where as daemon threads are used to perform some supporting tasks. In this post, we will discuss some of the differences between user thread vs daemon thread and see how they differ from each other.

1) User threads are created by the application (user) to perform some specific task. Where as daemon threads are mostly created by the JVM to perform some background tasks like garbage collection.

2) JVM will wait for user threads to finish their tasks. JVM will not exit until all user threads finish their tasks. On the other side, JVM will not wait for daemon threads to finish their tasks. It will exit as soon as all user threads finish their tasks.

3) User threads are high priority threads, They are designed mainly to execute some important task in an application. Where as daemon threads are less priority threads. They are designed to serve the user threads.

4) User threads are foreground threads. They always run in foreground and perform some specific task assigned to them. Where as daemon threads are background threads. They always run in background and act in a supporting role to user threads.

5) JVM will not force the user threads to terminate. It will wait for user threads to terminate themselves. On the other hand, JVM will force the daemon threads to terminate if all the user threads have finished their task.

6) User threads are chosen to do the core work of an application. The application is very much dependent on the user threads for it’s smooth execution. Where as daemon threads are chosen to do some supporting tasks. The application is less dependent on the daemon threads for it’s smooth running.

## User Threads Vs Daemon Threads In Java :

Below is the quick recap of the above points.

| User Threads        | Daemon Threads    |
| ------------- |-------------|
|JVM waits for user threads to finish their work. It will not exit until all user threads finish their work.| JVM will not wait for daemon threads to finish their work. It will exit as soon as all user threads finish their work.|
|User threads are foreground threads.|	Daemon threads are background threads.|
|User threads are high priority threads.|	Daemon threads are low priority threads.|
|User threads are created by the application.|	Daemon threads, in most of time, are created by the JVM.|
|User threads are mainly designed to do some specific task.|	Daemon threads are designed to support the user threads.|
|JVM will not force the user threads to terminate. It will wait for user threads to terminate themselves.|	JVM will force the daemon threads to terminate if all user threads have finished their work.|

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2015/06/UserVsDaemon.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

# Naming A Thread In Java

You can give a name to a thread by using setName() method of Thread class. You can also retrieve the name of a thread using getName() method of a Thread class. These two methods are public and final. Below is the method signatures of these methods.

1)  **public final void setName(String name)**   —-> It changes the name of the thread to “name”.

2)  **public final String getName()**   —-> Returns the name of the thread.

Below example shows how to use setName() and getName() methods.

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        System.out.println("Keep some task here....");
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        MyThread thread = new MyThread();     //Creating a thread
 
        thread.start();                     //Starting a thread
 
        thread.setName("My Thread");        //Giving a name to the thread
 
        String name = thread.getName();    //Retreiveing the name of the thread
 
        System.out.println(name);   //Output : My Thread
    }
}
```

## Some Things-To-Remember about Naming a thread in java :

* setName() method may throw a SecurityException at run time if the current thread can not modify the name of the specified thread.

* You can change the name of a thread at any state of the thread.

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        for(int i = 0; i < 1000; i++)
        {
            System.out.println(i);
        }
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        MyThread thread = new MyThread();     
 
        thread.setName("My Thread");        //Changing the name of the thread before starting the thread
 
        thread.start();                     
 
        thread.setName("My Thread");        //changing the name of the thread when thread is active
 
        try
        {
            thread.sleep(5000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        thread.setName("My Thread");     //Changing the name of the thread when thread is sleeping
    }
}
```

* **Default Name Of The Thread** :

In Java, All threads have names. If you are not providing the name to a thread, thread will get default name. Default name of the thread will be consist of a word “Thread”, followed by hyphen (-) and followed by an integer number starting with 0.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread();
 
        System.out.println(t.getName());    //Output : Thread-0
    }
}
```


* **How to retrieve a name of the primary thread or main thread?**

First, get the reference of the main thread by using currentThread() method of Thread class. currentThread() method returns the reference of currently executing thread. After, getting the reference of the main thread, use the getName() method to retrieve the name of the thread.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName());    //Output : main
    }
}
```

* **Can we change the name of the main thread ?**

Yes, we can change the name of the main thread. It can be done by first getting the reference of the main thread by using currentThread() method and then calling setName() method on it.


```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = Thread.currentThread();
 
        t.setName("main-thread-name-modified");
 
        System.out.println(t.getName());    //Output : main-thread-name-modified
    }
}
```

* **Another method of naming a thread in java** :

You can pass name of the thread while creating the object to thread. There is a constructor in Thread class which takes name of the thread as an argument.

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
        System.out.println(getName());      //Output : My Thread
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        MyThread t = new MyThread("My Thread");    //passing the name while creating the thread
 
        t.start();
    }
}
```

Naming a thread is very useful in identifying a thread and also in debugging a code.

# How to identify a thread in java?

In a multithreaded application, It is very important to know which thread is currently executing it’s task. But the question is, How to identify a thread?. The answer which effortlessly comes to our mind is “through it’s name”. Of course, you can identify a thread by it’s name.  But, more than one threads can have the same name. This makes identifying a thread more difficult. There is a solution for this problem from JDK 1.5 onward. JVM assigns one unique long number for every thread created. This remains unchanged for the whole life term of a thread. This number can be used to identify a thread.

From JDK 1.5 onward, One more method added to java.lang.Thread class. That is getID() method. This method returns the unique long number associated with a thread. That can be used as an identifier of a thread. Below is the method signature of getID() method.

```java
public long getID()
```

The following example shows how to retrieve the ID of a thread using getID() method.

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        System.out.println(getId()+" is running");   //Output : 8 is running
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        MyThread t = new MyThread();    
 
        t.start();      
 
        System.out.println(t.getId());     //Output : 8
    }
}
```

## Some Things-To-Remember about Identifying a Thread In Java :

1) Thread ID is a **unique positive long number**. It remains the same for a thread during its whole life term. Thread ID may be reused when the thread is terminated.

2) **Can we use the thread ID before a thread is started?** Thread ID is generated as soon as the thread is created. So, you can use the thread ID before starting the thread.

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        System.out.println(getId()+" is running");   //Output : 8 is running
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        MyThread t = new MyThread();     //Creating the thread
 
        System.out.println(t.getId());     //Using the thread ID before starting the thread
 
        t.start();           //starting the thread
    }
}
```

3) **Does thread ID changes when the thread name is changed?.**

Thread ID doesn’t change when the name of a thread is changed. Therefore, if the thread name is changed, still thread can be identified by it’s ID.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread("Name-Of-A-Thread");
 
        System.out.println(t.getName());     //Output : Name-Of-A-Thread
 
        System.out.println(t.getId());       //Output : 8
 
        t.setName("Name-Of-A-Thread-Changed");
 
        System.out.println(t.getName());    //Output : Name-Of-A-Thread-Changed
 
        System.out.println(t.getId());      //Output : 8
    }
}
```

4) **How to get ID of the main thread?**

First, get the reference of main thread using currentThread() method of Thread class. After getting the reference of main thread, call the getId() method on it.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = Thread.currentThread();
 
        long ID = t.getId();
 
        System.out.println(ID);
    }
}
```java

5) **Can we give our own ID to the thread?**

No, we can’t assign our own ID to the thread. But, we can change the way getID() returns the thread ID as it is not a final method.

```java
class MyThread extends Thread
{
    @Override
    public long getId()
    {
        long l = super.getId() + 1;    // It increases the thread ID by 1
 
        return l;
 
    }
 
    @Override
    public void run()
    {
        System.out.println(getId());    //Output : 9
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        MyThread thread = new MyThread();
 
        thread.start();
    }
}
```

# Priority Of A Thread In Java

As we know, Java allows multithreaded programming. i.e Java application can have more than one threads running simultaneously. When an application has multiple threads they are choosen to execute on priority basis. A thread with highest priority is choosen first for execution than the thread with lowest priority.

There are two methods in java.lang.Thread class related to priority of a thread. They are setPriority() and getPriority methods. setPriority() method is used to set the priority of a thread and getPriority() method is used to retrieve the priority of a thread. Below is the method signatures of these methods.

**public final void setPriority(int newPriority)**  —> Changes the priority of a thread to newPriority.

**public final int getPriority()**  —>  Returns the priority of a thread.

Below example shows how to use setPriority() and getPriority() methods.

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
        for(int i = 0; i < 1000; i++)
        {
            System.out.println("from "+getName());
        }
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        MyThread t1 = new MyThread("Thread 1");
 
        t1.setPriority(5);         //Setting the priority of Thread 1
 
        t1.start();
 
        MyThread t2 = new MyThread("Thread 2");
 
        t1.setPriority(7);         //Setting the priority of Thread 2
 
        t2.start();
 
        System.out.println(t1.getPriority());      //Output : 5
 
        System.out.println(t2.getPriority());      //Output : 7
    }
}
```

## Some Things-To-Remember about priority of a thread in java :

* There are three constant fields in java.lang.Thread class related to priority of a thread. They are,

**MIN_PRIORITY**   —> It defines the lowest priority that a thread can have and It’s value is 1.

**NORM_PRIORITY**  —> It defines the normal priority that a thread can have and it’s value is 5.

**MAX_PRIORITY**  —> It defines the highest priority that a thread can have and it’s value is 10.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        System.out.println(Thread.MIN_PRIORITY);     //Output : 1
 
        System.out.println(Thread.NORM_PRIORITY);    //Output : 5
 
        System.out.println(Thread.MAX_PRIORITY);     //Output : 10
    }
}
```

* setPriority() method may throw two exceptions. One is IllegelArgumentException if supplied priority is not in the range of MIN_PRIORITY and MAX_PRIORITY and another one is SecurityException if current thread can not modify the priority of a specified thread.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread();
 
        t.setPriority(12);    //This statement throws IllegalArgumentException at run time
 
        t.start();
    }
}
```

* **How to retrieve the priority of a main thread?**

First, get the reference to a main thread using currentThread() method of Thread class. After getting the reference of main thread, call getPriority() method on it.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getPriority());    //Output : 5
    }
}
```

* **Can we change the priority of a main thread?.**

Yes, we can change the priority of a main thread. First, get the reference of main thread using CurrentThread() method. Then call setPriority() method on it.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = Thread.currentThread();
 
        t.setPriority(8);
 
        System.out.println(t.getPriority());    //Output : 8
    }
}
```

* The priority of a main thread, if explicitly not set, is always 5 i.e NORM_PRIORITY.

* The default priority of a thread is same as that of it’s parent.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = Thread.currentThread();
 
        t.setPriority(8);
 
        Thread t1 = new Thread("Child Thread");      //Creating the child thread
 
        System.out.println(t1.getPriority());       //Output : 8
    }
}
```

# Thread.sleep() Method In Java

Thread.sleep() method makes the currently executing thread to pause it’s execution for a specified period of time. There are two overloaded forms of sleep() method available in java.lang.Thread class. They are,

1) **public static void sleep(long millis) throws InterruptedException**

—> It causes the currently executing thread to sleep for specified number of milliseconds.

2) **public static void sleep(long millis, int nanos) throws InterruptedException**

—> It makes the currently executing thread to sleep for specified number of milliseconds plus specified number of nanoseconds.

Thread.sleep() method throws InterruptedException if a thread in sleep is interrupted by other threads. InterruptedException is a checked type of exception. That means, “Thread.sleep()” statement must be enclosed within try-catch blocks or it must be specified with throws clause.

The following example shows how to use Thread.sleep() method.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        System.out.println("Before Sleeping");
 
        try
        {
            Thread.sleep(5000);
        }
        catch (InterruptedException e)
        {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
 
        System.out.println("After Sleeping");
    }
}
```

In the above example, the main thread first prints “Before Sleeping”. After that it pauses for 5000 milisseconds(5 seconds) and prints “After Sleeping”. Notice that the statement “Thread.sleep(5000)” is enclosed within try-catch blocks.

## Some Things-To-Remember About Thread.sleep() Method In Java :

* It is always current thread that is going to sleep. For example, In the below example, main thread is going to sleep not “My Thread” even though you are calling sleep() method on “My Thread”.

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
        for(int i = 0; i <= 1000; i++)
        {
            System.out.println(i);
        }
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        MyThread thread = new MyThread("My Thread");
 
        thread.start(); 
 
        System.out.println("Before Sleeping");
 
        try
        {
            thread.sleep(5000);       //main thread is going for sleep not My Thread
        }
        catch (InterruptedException e)
        {
            // TODO Auto-generated catch block
            e.printStackTrace();
        }
 
        System.out.println("After Sleeping");
    }
}
```

* It is a bad practice to call sleep() method with an instance of Thread class as in the above example. If you want a particular thread to sleep for a while, then call sleep() method inside the run() method of that thread.

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        for(int i = 0; i <= 10; i++)
        {
            System.out.println(i);
 
            try
            {
                sleep(1000);            //this thread sleeps for 1 second
            }
            catch (InterruptedException e)
            {
                e.printStackTrace();
            }
        }
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        MyThread thread = new MyThread();
 
        thread.start();
    }
}
```

* An example for using second form of sleep() method.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        System.out.println("Before Sleeping");
 
        try
        {
            Thread.sleep(5000, 500000);       //thread sleeps for about 5.5 seconds
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        System.out.println("After Sleeping");
    }
}
```

* Thread.sleep() method may also throws IllegalArgumentException if miilis value is negative or nanos value is not in the range 0 – 999999.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        System.out.println("Before Sleeping");
 
        try
        {
            Thread.sleep(-5000);          //This statement throws IllegalArgumentException
        }
        catch (Exception e)
        {
            e.printStackTrace();
        }
 
        System.out.println("In between sleep");
 
        try
        {
            Thread.sleep(1000, 50000000);       //This statement throws IllegalArgumentException
        }
        catch (Exception e)
        {
            e.printStackTrace();
        }
 
        System.out.println("After Sleeping");
    }
}
```

* When the thread is going for sleep, it does not release the synchronized locks it holds.

# Joining The Threads In Java

join() method of java.lang.Thread class is used to mantain the order of execution of threads. Using join() method, you can make the currently executing thread to wait for the some other threads to finish their task. For example, Let’s us assume that there are two threads namely, thread1 and thread2. You can make thread1 to hold it’s execution for some time so that thread2 can finish it’s task. After, thread2 finishes it’s task, thread1 resumes it’s execution.For this to happen, you should call join() method on thread2 within thread1.

Like sleep() method, join() method is also overloaded in Thread class. There are three forms of join() method available in Thread class.

1) **public final void join() throws InterruptedException**

—> Currently executing thread waits for a thread to finish it’s task on which it is called.

2) **public final void join(long millis) throws InterruptedException**

—> currently executing thread waits at most millis milliseconds for a thread to finish it’s task on which it is called.

3) **public final void join(long millis, int nanos) throws InterruptedException**

—> Currently executing thread waits at most millis milliseconds plus nanos nanoseconds for a thread to finish it’s task on which it is called.

Like sleep() method, join() method also throws InterruptedException. Therefore, you have to keep calling statement to join() method in try-catch blocks or else propagate the exception with throws clause.

The below example shows usage of all these three forms of join() method.

```java
public class ThreadsInJava
{
    public static void main(String[] args) throws InterruptedException
    {
        System.out.println("main thread started : Task is to print numbers from 0 to 3000");
 
        final Thread t1 = new Thread()
        {
            @Override
            public void run()
            {
                //Thread t1 started : Task is to print numbers from 0 to 1000"
 
                for(int i = 0; i <= 1000; i++)
                {
                    System.out.println(i);
                }
 
                System.out.println("Numbers from 0 to 1000 are printed");
            }
        };
 
        final Thread t2 = new Thread()
        {
            @Override
            public void run()
            {
                //Thread t2 started : Task is to print numbers from 1001 to 2000
 
                try
                {
                    t1.join(5000, 500000);   //waits at most 5.5 seconds for thread t1 to finish it's task
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
 
                for(int i = 1001; i <= 2000; i++)
                {
                    System.out.println(i);
                }
 
                System.out.println("Numbers from 1001 to 2000 are printed");
            }
        };
 
        Thread t3 = new Thread()
        {
            @Override
            public void run()
            {
                //Thread t3 started : Task is to print numbers from 2001 to 3000
 
                try
                {
                    t2.join(5000);   //waits at most 5 seconds for thread t2 to finish it's task
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
 
                for(int i = 2001; i <= 3000; i++)
                {
                    System.out.println(i);
                }
 
                System.out.println("Numbers from 2001 to 3000 are printed");
            }
        };
 
        t3.start();
 
        t2.start();
 
        t1.start();
 
        t3.join();     //Waits for t3 thread to finish it's task
 
        //No need enclose this join statement in try-catch blocks as we have already specified the exception with throws clause.
 
        System.out.println("Task is finished");
    }
}
```

The main task of above example is to print the numbers from 0 to 3000. This task is devided into three parts and each part is assigned to one thread. i.e The task of printing the numbers from 0 to 1000 is assigned to thread t1, printing the numbers from 1001 to 2000 is assigned to thread t2 and printing the numbers from 2001 to 3000 is assigned to thread t3.The main thread creates and starts these three threads. main thread also calls join method on thread t3 (Line 79). So main thread waits until thread t3 finishes it’s task. Before starting it’s task, thread t3 calls join method on thread t2 (Line 57). So, thread t3 waits at most 5 seconds for thread t2 to finish it’s task. Thread t2 also calls join method on thread t1 (Line 32). So, thread t2 waits at most 5.5 seconds for thread t1 to finish it’s task. So, first t1 finishes it’s task and then t2 finishes it’s task and after that t3 finishes it’s task. After all these three threads finish their task, main threads completes the task.

# Thread Interference In Java

Multithreading has it’s own pros and cons. The main advantage of multithreading is that we can perform multiple tasks simultaneously. At the same time it is a challenge for software developers to protect the memory into which thread are reading or writing. There is no problem when multiple threads have their own memory. Each thread will be reading or writing into their own memory. There is a challenge when multiple threads share same memory. Every thread will be reading or writing into same memory. This creates inconsistent data in the memory. For example,

If a thread reads a memory while another thread writes into it, what value will be the first thread end up reading? is it the old value or value written by the second thread? If two threads are writing into same memory, then what value will be stored in that memory? is it value written by the first thread or the value written by the second thread? Questions like these will arise when multiple threads share same memory. Thread interference is also one of them.

Thread interference in java is a condition which occurs when more than one threads, executing simultaneously, access same piece of data. When more than one threads have access to same data, it is possible that data may get corrupted or one may not get the desired output. Thread interference occurs when code written is not thread safe.

Consider the below program. This program is not thread safe.

```java
class Shared
{
    int i;
 
    void SharedMethod()
    {
        i = 10;
        System.out.println(i);
        i = 20;
        System.out.println(i);
        i = 30;
        System.out.println(i);
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        final Shared s1 = new Shared();
 
        Thread t1 = new Thread()
        {
            @Override
            public void run()
            {
                s1.SharedMethod();
            }
        };
 
        Thread t2 = new Thread()
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

In the above example, There are two threads namely t1 and t2, and they are using same Shared class object s1. Both t1 and t2 are calling sharedMethod() of s1 object from their run() method. As we are starting thread t1 first, let’s assume that thread t1 is executing the last statement of sharedMethod() (Line 12) and thread t2 has finished executing the first statement of sharedMethod() (Line 7). While executing last statement, thread t1 will be expecting value of “i” as 30 as it has assigned 30 to it in the previous statement (Line 11), but t2 has changed value of “i” to 10 while executing the first statement. So, t1 will read value of “i” as 10 not 30 as it is expecting.

This is an example of Thread Interference. Thread interference occurs when sequence of steps of more than one threads overlap. You can follow the Oracle documentation of thread interference here. The above example can be described by the diagram as below.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2014/11/ThreadInterference.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

## How To Avoid Thread Interference or How To Acheive Thread Safeness?
Following are some methods which are used to avoid thread interference in java.(These methods will be discussed in detail in subsequent articles).

* By declaring the method as synchronized.

* By declaring the variables as final.

* By declaring the variable as volatile.

* By creating the immutable objects.

* By using Atomic operations.

* By restricting the access to same object by multiple threads.

# 10 Points-To-Remember About Synchronization In Java

Synchronization in java is a strategy or a method to avoid thread interference and hence protecting the data from inconsistency. synchronization is also one of the way to make code thread safe. Through synchronization, we can make the threads to execute particular method or block in sync not simultaneously.

Synchronization in java is implemented using synchronized keyword. synchronized keyword can be used with methods or blocks but not with the variables.

When a method or block is declared as synchronized, only one thread can enter into that method or block. When one thread is executing synchronized method or block, the other threads which wants to execute that method or block wait or suspend their execution until first thread is done with that method or block. Thus avoiding the thread interference and achieving thread safeness. This can be explained well with the help of an example.

Consider this example,

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

In the above example, both threads t1 and t2 wants to execute sharedMethod() of s1 object. But, sharedMethod() is declared as synchronized. So, whichever thread enters first into sharedMethod(), it continues to execute that method. The other thread waits for first thread to finish it’s execution of sharedMethod(). It never enters into sharedMethod() until first thread is done with that method. That means, both threads are executing sharedMethod() one by one not simultaneously. This protects the value of “i” in the memory for a particular thread.

## The Logic Behind The Synchronization In Java :

The synchronization in java is built around an entity called object lock or monitor. Here is the brief description about lock or monitor.

* Whenever an object is created to any class, an object lock is created and is stored inside the object.

* One object will have only one object lock associated with it.

* Any thread wants to enter into synchronized methods or blocks of any object, they must acquire object lock associated with that object and release the lock after they are done with the execution.

* The other threads which wants to enter into synchronized methods of that object have to wait until the currently executing thread releases the object lock.

* To enter into static synchronized methods or blocks, threads have to acquire class lock associated with that class as static members are stored inside the class memory.

## Synchronized Blocks :
Some times, you need only some part of the method to be synchronized not the whole method. This can be achieved with synchronized blocks. Synchronized blocks must be defined inside a definition blocks like methods, constructors, static initializer or instance initializer.

synchronized block takes one argument and it is called mutex. if synchronized block is defined inside non-static definition blocks like non-static methods, instance initializer or constructors, then this mutex must be an instance of that class. If synchronized block is defined inside static definition blocks like static methods or static initializer, then this mutex must be like ClassName.class.

Here is an example of static and non-static synchronized blocks.

```java
class Shared
{
    static void staticMethod()
    {
        synchronized (Shared.class)
        {
            //static synchronized block
        }
    }
 
    void NonStaticMethod()
    {
        synchronized (this)
        {
            //Non-static synchronized block
        }
    }
 
    void anotherNonStaticMethod()
    {
        synchronized (new Shared())
        {
            //Non-static synchronized block
        }
    }
}
```

## 10 Points-To-Remember About Synchronization In Java :

1) You can use synchronized keyword only with methods but not with variables, constructors, static initializer and instance initializers.

```java
class Shared
{
    synchronized int i;    //compile time error, can't use synchronized keyword with variables
 
    synchronized public Shared()
    {
        //compile time error, constructors can not be synchronized
    }
 
    synchronized static
    {
        //Compile time error, Static initializer can not be synchronized
    }
 
    synchronized
    {
        //Compile time error, Instance initializer can not be synchronized
    }
}
```

2) Constructors, Static initializer and instance initializer can’t be declared with synchronized keyword, but they can contain synchronized blocks.

```java
class Shared
{
    public Shared()
    {
        synchronized (this)
        {
            //synchronized block inside a constructor
        }
    }
 
    static
    {
        synchronized (Shared.class)
        {
            //synchronized block inside a static initializer
        }
    }
 
    {
        synchronized (this)
        {
            //synchronized block inside a instance initializer
        }
    }
}
```

3) Both static and non-static methods can use synchronized keyword. For static methods, thread need class level lock and for non-static methods, thread need object level lock.

```java
class Shared
{
    synchronized static void staticMethod()
    {
        //static synchronized method
    }
 
    synchronized void NonStaticMethod()
    {
        //Non-static Synchronized method
    }
}
```

4) It is possible that both static synchronized and non-static synchronized methods can run simultaneously. Because, static methods need class level lock and non-static methods need object level lock.

5) A method can contain any number of synchronized blocks. This is like synchronizing multiple parts of a method.

```java
class Shared
{
    static void staticMethod()
    {
        synchronized (Shared.class)
        {
            //static synchronized block - 1
        }
 
        synchronized (Shared.class)
        {
            //static synchronized block - 2
        }
    }
 
    void NonStaticMethod()
    {
        synchronized (this)
        {
            //Non-static Synchronized block - 1
        }
 
        synchronized (this)
        {
            //Non-static Synchronized block - 2
        }
    }
}
```

6) Synchronization blocks can be nested.

```java
synchronized (this)
{
    synchronized (this)
    {
        //Nested synchronized blocks
    }
}
```

7) Lock acquired by the thread before executing a synchronized method or block must be released after the completion of execution, no matter whether execution is completed normally or abnormally (due to exceptions).

8) Synchronization in java is Re-entrant in nature. A thread can not acquire a lock that is owned by another thread. But, a thread can acquire a lock that it already owns. That means if a synchronized method gives a call to another synchronized method which needs same lock, then currently executing thread can directly enter into that method or block without acquiring the lock.

9) synchronized method or block is very slow. They decrease the performance of an application. So, special care need to be taken while using synchronization. Use synchronization only when you needed it the most.

10) Use synchronized blocks instead of synchronized methods. Because, synchronizing some part of a method improves the performance than synchronizing the whole method.

# Deadlock In Java

## What Is Deadlock In Java?

Deadlock in java is a condition which occurs when two or more threads get blocked waiting for each other for an infinite period of time to release the resources(Locks) they hold. Deadlock is the common problem in multi threaded programming which can completely stops the execution of an application. So, extra care need to be taken while writing the multi threaded programs so that deadlock never occurs.

Let’s look at one simple example of deadlock condition.

```java
class Shared
{
    synchronized void methodOne(Shared s)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName()+"is executing methodOne...");
 
        System.out.println(t.getName()+"is calling methodTwo...");
 
        s.methodTwo(this);
 
        System.out.println(t.getName()+"is finished executing methodOne...");
    }
 
    synchronized void methodTwo(Shared s)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName()+"is executing methodTwo...");
 
        System.out.println(t.getName()+"is calling methodOne...");
 
        s.methodOne(this);
 
        System.out.println(t.getName()+"is finished executing methodTwo...");
    }
}
 
public class DeadLockInJava
{
    public static void main(String[] args)
    {
        final Shared s1 = new Shared();
 
        final Shared s2 = new Shared();
 
        Thread t1 = new Thread()
        {
            public void run()
            {
                s1.methodOne(s2);
            }
        };
 
        Thread t2 = new Thread()
        {
            @Override
            public void run()
            {
                s2.methodTwo(s1);
            }
        };
 
        t1.start();
 
        t2.start();
    }
}
```

In the above multithreaded program, thread t1 and t2 are concurrent threads i.e they are executing their task simultaneously. There are two Shared class objects, s1 and s2, which are shared by both the threads. Shared class has two synchronized methods, methodOne() and methodTwo(). That means, only one thread can execute these methods at a given time.

First, thread t1 enters the methodOne() of s1 object by acquiring the object lock of s1. At the same time, thread t2 also enters the methodTwo() of s2 object by acquiring the object lock of s2. methodOne() of s1 object, currently executing by thread t1, calls methodTwo() of s2 object from it’s body. So, thead t1 tries to acquire the object lock of s2 object. But object lock of s2 object is already acquired by thread t2. So, thread t1 waits for thread t2 to release the object lock of s2 object.

At the same time, thread t2 is also executing methodTwo() of s2 object. methodTwo() of s2 object also makes a call to methodOne() of s1 object. So, thread t2 tries to acquire the object lock of s1 object. But, it is already acquired by thread t1. So, thread t2 also waits for thread t1 to release the object lock of s1 object.

Thus, both the threads wait for each other to release the object locks they own. They wait for infinite period of time to get the object locks owned by opposite threads. This condition of threads waiting forever is called Deadlock.

If you still confused, see the below diagram.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2014/11/Deadlock.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

# How To Detect The Deadlocked Threads In Java

In the previous article, we have seen what is the deadlock and why it occurs. Deadlock is the condition which occurs when two or more threads wait for each other forever.

Programmatically, You can detect the threads which have entered into deadlock condition and also you can retrieve the details about them. This can be done using ThreadMXBean interface of java.lang.Management package. You can go through the oracle docs of ThreadMXBean interface here.

First, you have to get an instance of ThreadMXBean using getThreadMXBean() method of ManagementFactory, like this.

```java
ThreadMXBean bean = ManagementFactory.getThreadMXBean();
```

After getting an instance of ThreadMXBean, call findMonitorDeadlockedThreads() method on it. It returns an array of type long containing ids of all currently deadlocked threads.

```java
long ids[] = bean.findMonitorDeadlockedThreads();
```

After getting the ids of deadlocked threads, pass these ids to getThreadInfo() method of ThreadMXBean. It will return an array of ThreadInfo objects, where one ThreadInfo object contains the details of one deadlocked thread.

```java
ThreadInfo threadInfo[] = bean.getThreadInfo(ids);
```

Iterate the ThreadInfo array to get the details of individual deadlocked thread.

```java
for (ThreadInfo threadInfo1 : threadInfo)
{
    System.out.println(threadInfo1.getThreadName());    //Prints the name of deadlocked thread
}
```

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2014/07/DeadlockedThreads11.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

Here are the some methods of ThreadInfo class which are useful to retrieve the details of deadlocked threads.

**getThreadId()**               —>    Returns the ID of a deadlocked thread.

**getThreadName()**         —>     Returns the name of a deadlocked thread.

**getBlockedTime()**          —>    Returns the elapsed time in milli seconds that a thread is in deadlock condition.

**getLockName()**             —>    Returns string representation of an object for which thread has been waiting.

**getLockOwnerId()**         —>    Returns ID of a thread that currently owns the object lock.

**getLockOwnerName()**    —>    Returns the name of a thread that currently owns the object lock.

Here is yesterday’s example that has been modified to get the details of deadlocked threads.

```java
import java.lang.management.ManagementFactory;
import java.lang.management.ThreadInfo;
import java.lang.management.ThreadMXBean;
 
class Shared
{
    synchronized void methodOne(Shared s)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName()+"is executing methodOne...");
 
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        System.out.println(t.getName()+"is calling methodTwo...");
 
        s.methodTwo(this);
 
        System.out.println(t.getName()+"is finished executing methodOne...");
    }
 
    synchronized void methodTwo(Shared s)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName()+"is executing methodTwo...");
 
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        System.out.println(t.getName()+"is calling methodOne...");
 
        s.methodOne(this);
 
        System.out.println(t.getName()+"is finished executing methodTwo...");
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        final Shared s1 = new Shared();
 
        final Shared s2 = new Shared();
 
        Thread t1 = new Thread()
        {
            public void run()
            {
                s1.methodOne(s2);
            }
        };
 
        Thread t2 = new Thread()
        {
            @Override
            public void run()
            {
                s2.methodTwo(s1);
            }
        };
 
        t1.start();
 
        t2.start();
 
        try
        {
            Thread.sleep(5000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
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
        else
        {
            System.out.println("No Deadlocked Threads");
        }
    }
}
```

# How To Avoid The Deadlock In Java

Deadlock is a dangerous condition, if it happens , it will bring the whole application to complete halt. So, extra care need to be taken to avoid the deadlock. Followings are some tips that can be used to avoid the deadlock in java.

* Try to avoid nested synchronized blocks. Nested synchronized blocks makes a thread to acquire another lock while it is already holding one lock. This may create the deadlock if another thread wants the same lock which is currently held by this thread.

```java
synchronized (Lock A)
{
    //Some statements
 
    synchronized (Lock B)
    {
        //Try to avoid this block
    }
}
```

* **Lock Ordering** :

If you needed nested synchronized blocks at any cost, then make sure that threads acquire the needed locks in some predefined order. For example, If there are three threads t1, t2 and t3 running concurrently and they needed locks A, B and C in the following manner,

```java
Thread t1 :
        Lock A
        Lock B
Thread t2 :
        Lock A
        Lock C
Thread t3 :
        Lock A
        Lock B
        Lock C
```

In the above scenario, t1 needs A and B locks, t2 needs A and C locks and t3 needs A, B and C locks. If you define an order to acquire the locks like, Lock A must be acquired before Lock B and Lock B must be acquired before Lock c, then deadlock never occurs in the above case.

If you define such lock ordering, then thread t2 never acquire lock C and t3 never acquire lock B and lock C until they got lock A. They will wait for lock A until it is released by t1. After lock A is released by t1, any one of these threads will acquire lock A on the priority basis and finishes their task. Other thread which is waiting for lock A, will never try to acquire remaining locks.

By defining such lock ordering, you can avoid the deadlock.

* **Lock Timeout** :

Another deadlock preventive tip is to specify the time for a thread to acquire the lock. If it fails to acquire the specified lock in the given time, then it should give up trying for a lock and retry after some time. Such method of specifying time to acquire the lock is called lock timeout.

* Lock the code where it is actually needed. For example,If you want only some part of the method to be thread safety, then lock only that part not the whole method.

```java
void method()
{
    //Some statements
 
    synchronized (this)
    {
        //Locking only some part of the method
    }
 
    //Some statements
}
```

# Interthread Communication Using wait(), notify() and notifyAll()

Threads can communicate with each other using wait(), notify() and notifyAll() methods. These methods are final methods of java.lang.Object class. That means every class in java will have these methods. Below is the method signatures of these methods.

1) **public final void wait() throws InterruptedException**

This method tells the currently executing thread to release the lock of this object and wait until some other thread acquires the same lock and notify it using either notify() or notifyAll() methods. This method throws InterruptedException if waiting thread is interrupted.

2) **public final void notify()**

This method wakes up one thread randomly that called wait() method on this object.

3) **public final void notifyAll()**

This method wakes up all the threads that called wait() method on this object. But, only one thread will acquire lock of this object depending upon the priority.

**Important Note : These three methods must be called within synchronized method or block. Any thread which calls these methods must have lock of that object.**

Below is an example for using wait() and notify() methods.

```java
class Shared
{
    synchronized void methodOne()
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getName()+" is relasing the lock and going to wait");
 
        try
        {
            wait();        //releases the lock of this object and waits
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        System.out.println(t.getName()+" got the object lock back and can continue with it's execution");
    }
 
    synchronized void methodTwo()
    {
        Thread t = Thread.currentThread();
 
        try
        {
            Thread.sleep(5000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        notify();     //wakes up one thread randomly which is waiting for lock of this object
 
        System.out.println("A thread which is waiting for lock of this object is notified by "+t.getName());
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        final Shared s = new Shared();
 
        Thread t1 = new Thread()
        {
            public void run()
            {
                s.methodOne();   //t1 calling methodOne() of 's' object
            }
        };
 
        Thread t2 = new Thread()
        {
            @Override
            public void run()
            {
                s.methodTwo();   //t2 calling methodTwo() of 's' object
            }
        };
 
        t1.start();
 
        t2.start();
    }
}
```

In this example, Thread t1 and t2 are sharing shared class object ‘s’. Thread t1 is calling methodOne() and thread t2 is calling methodTwo() of ‘s’ object. Both the methods are synchronized. That means, for any thread to enter these methods, they must acquire lock of ‘s’ object.

First, thread t1 acquires the object lock and enters methodOne(). Thread t2 waits for thread t1 to release the object lock. Thread t1 calls wait() method within methodOne(). As soon as, it calls wait() method, It releases the lock of ‘s’ object and goes for wait. Thread t2 acquires this lock and enters methodTwo(). After entering methodTwo(), thread t2 sleeps for 5 seconds and calls notify() method on this object. It wakes up thread t1 which is waiting for this object lock. As soon as, thread t2 releases the object lock after finishing it’s execution of methodTwo(), thread t1 acquires this lock and executes remaining statements of methodOne(). In this manner, both threads t1 and t2 communicate with each other and share the lock.

For more clarification, see the below picture.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2014/11/InterThreadCommunication.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

## Some Things-To-Remember About wait(), notify() and notifyAll() :

* If a thread calls notify() method and more than one threads are waiting for the object lock, then only one thread will be notified randomly.

* When a thread calls notifyAll() method on an object, it notifies all the threads which are waiting for this object lock. But, only one thread will acquire this object lock depending upon priority.

* When you call sleep() method on a thread, thread goes to sleep with holding the object lock with it. But, if you call wait() method, thread releases the object lock and goes for sleep. This is the main difference between wait() and sleep() methods.

* wait(), notify() and notifyAll() are final methods of java.lang.Object class not java.lang.Thread class.

* wait(), notify() and notifyAll() – all these three methods throw IllegalMonitorStateException if the calling thread does not owns the object lock.

* wait() method is overloaded in Object class. There are two more wait() methods available in Object class. They are,

**public final void wait(long timeOut)**  —>  This makes current thread to wait until any other thread calls notify() or notifyAll() on this object or specified time(milli seconds) has elapsed.


**public final void wait(long timeOut, int nanos)**  —>  This makes current thread to wait until any other thread calls notify() or notifyAll() on this object or specified time(milli seconds + nano seconds) has elapsed.

# Thread Interruption In Java

Thread interruption in java is a mechanism in which a thread which is either sleeping or waiting can be made to stop sleeping or waiting. Thread interruption is like telling the thread that it should stop waiting or sleeping and return to running status. Thread interruption is programmatically implemented using interrupt() method of java.lang.Thread class. interrupt() method is a non-static public method of Thread class. Here is the method signature of interrupt() method.

```java
public void interrupt()
```

The whole thread interruption mechanism depends on an internal flag called interrupt status. The initial value of this flag for any thread is false. When you call interrupt() method on a thread, interrupt status of that thread will be set to true. When a thread throws InterruptedException, this status will be set to false again. Remember, InterruptedException is thrown when a thread is interrupted while it is sleeping or waiting. Many methods of Thread class like sleep(), wait(), join() throw InterruptedException.

Here is an example for interrupting a sleeping thread using interrupt() method.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                try
                {
                    Thread.sleep(10000);        //Thread is sleeping for 10 seconds
                }
                catch (InterruptedException e)
                {
                    System.out.println("Thread is interrupted");
                }
            }
        };
 
        t.start();
 
        try
        {
            Thread.sleep(3000);      //Main thread is sleeping for 3 seconds
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        t.interrupt();         //main thread is interrupting thread t
    }
}
```

In the above example, main thread is creating and starting thread t. Thread t is going to sleep for 10 seconds as soon as it started. main thread, after starting thread t, is also going to sleep for 3 seconds. After sleeping for 3 seconds, main thread calls interrupt() method on thread t. It interrupts sleeping thread t. It causes the InterruptedException.

# Some Things-To-Remember About Thread Interruption In Java :

* You can check whether a particular thread is interrupted or not using isInterrupted() method of Thread class. This method returns current interrupt status of a thread.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                System.out.println(isInterrupted());         //Output : true
 
                try
                {
                    Thread.sleep(10000);        //Thread is going to sleep for 10 seconds
                }
                catch (InterruptedException e)
                {
                    System.out.println("Thread is interrupted");
                }
 
                System.out.println(isInterrupted());       //Output : false
            }
        };
 
        t.start();
 
        t.interrupt();         //main thread is interrupting thread t
    }
}
```

* Interrupted thread will not be eligible to go for sleep. i.e If you call interrupt() method on a thread which is not yet slept but running, such thread will throw InterruptedException while going to sleep. Look at the below example. In this example, thread t is interrupted by main thread as soon as it is started. But thread t will not throw InterruptedException as soon as it is interrupted. Instead it will continue to print 1000 numbers. While going to sleep after printing the numbers it will raise InterruptedException.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                for(int i = 0; i <= 1000; i++)
                {
                    System.out.println(i);
                }
 
                try
                {
                    Thread.sleep(10000);        //Thread is going to sleep for 10 seconds
                }
                catch (InterruptedException e)
                {
                    System.out.println("Thread is interrupted");
                }
            }
        };
 
        t.start();
 
        t.interrupt();         //main thread is interrupting thread t
    }
}
```

* A thread can interrupt itself. i.e a thread can call interrupt() method on it’s own.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                System.out.println(isInterrupted());         //Output : false
 
                interrupt();              //Thread interrupting itself
 
                System.out.println(isInterrupted());        //Output : true
 
                try
                {
                    Thread.sleep(1000);
                }
                catch (InterruptedException e)
                {
                    System.out.println("Thread interrupted");
                }
 
                System.out.println(isInterrupted());       //Output : false
            }
        };
 
        t.start();
    }
}
```

* There is one more method to check interrupt status of a thread, called interrupted() method. It is a static method of Thread class. It also returns the current interrupt status of a thread like isInterrupted() method. But, it clears interrupt status of a thread. i.e if interrupt status of a thread is true, then it will set the status to false.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                System.out.println(interrupted());         //Output : false
 
                interrupt();
 
                System.out.println(interrupted());        //Output : true
 
                System.out.println(interrupted());       //Output : false
            }
        };
 
        t.start();
    }
}
```

* interrupt() method will throw SecurityException if current thread can not interrupt a calling thread.

# Thread Life Cycle OR Thread States In Java

There are six thread states. They are NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING and TERMINATED. At any point of time, thread will be in any one of these states.

java.lang.Thread class has one member of enum type called State. All states of a thread are stored in this enum as constants. Let’s extract these thread states programmatically. Execute the below program, it prints all states of a thread.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread.State[] states = Thread.State.values();
 
        for (Thread.State state : states)
        {
            System.out.println(state);
        }
    }
}
```

The output of this program will be,

```java
NEW
RUNNABLE
BLOCKED
WAITING
TIMED_WAITING
TERMINATED
```

These are the states of a thread in Java . let’s discuss these thread states one by one.

## 1) NEW
A thread will be in this state before calling start() method.

```java
public class JavaThreadLifeCycle
{
    public static void main(String[] args)
    {
        Thread t = new Thread();
 
        //Checking the state before starting the thread
 
        System.out.println(t.getState());     //Output : NEW
    }
}
```

## 2) RUNNABLE

A thread will be in this state after calling the start() method.

```java
public class JavaThreadLifeCycle
{
    public static void main(String[] args)
    {
        Thread t = new Thread();
 
        t.start();
 
        //Checking the state after starting the thread
 
        System.out.println(t.getState());     //Output : RUNNABLE
    }
}
```

3) BLOCKED

A thread will be in this state when a thread is waiting for object lock to enter into synchronized method/block or a thread will be in this state if deadlock occurs. Below example shows the states of two threads when deadlock occurs.

```java
class Shared
{
    synchronized void methodOne(Shared s)
    {
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        s.methodTwo(this);
    }
 
    synchronized void methodTwo(Shared s)
    {
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        s.methodOne(this);
    }
}
 
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        final Shared s1 = new Shared();
 
        final Shared s2 = new Shared();
 
        Thread t1 = new Thread()
        {
            public void run()
            {
                s1.methodOne(s2);
            }
        };
 
        Thread t2 = new Thread()
        {
            @Override
            public void run()
            {
                s2.methodTwo(s1);
            }
        };
 
        t1.start();
 
        t2.start();
 
        try
        {
            Thread.sleep(3000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        //Checking states of both the threads
 
        System.out.println(t1.getState());     //Output : BLOCKED
 
        System.out.println(t2.getState());     //Output : BLOCKED
    }
}
```

## 4)  WAITING

A thread will be in this state when wait() or join() method is called. Below example shows the thread state when join() method is called.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        final Thread t1 = new Thread()
        {
            public void run()
            {
                try
                {
                    Thread.sleep(2000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        Thread t2 = new Thread()
        {
            public void run()
            {
                try
                {
                    t1.join();
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t2.start();
 
        t1.start();
 
        try
        {
            Thread.sleep(100);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        //Checking the state of t2 after it calls join() on t1
 
        System.out.println(t2.getState());     //Output : WAITING
    }
}
```

## 5) TIMED_WAITING

A thread will be in this state when thread is sleeping. i.e A thread will be in this state when sleep() or wait() with timeOut or join() with timeOut is called.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t.start();
 
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        //Checking the state when thread is sleeping
 
        System.out.println(t.getState());     //Output : TIMED_WAITING
    }
}
```

# 6) TERMINATED

A thread will be in this state once it finishes it’s execution.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                for(int i = 0; i <= 25; i++)
                {
                    System.out.println(i);
                }
            }
        };
 
        t.start();
 
        try
        {
            Thread.sleep(2000);      //Main thread is sleeping for 2 sec
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        //Checking the state when thread t is finished it's execution
 
        System.out.println(t.getState());     //Output : TERMINATED
    }
}
```

Below picture shows all 6 states of a thread.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2014/11/JavaThreadLifeCycle.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

Note : In the above picture, RUNNING is not a state. For understanding purpose we have mentioned it. This is when the thread is actually executing it’s task.

# Thread Group In Java

Thread group in java is used to group similar threads into one unit. A thread group can also contain other thread groups. Thread groups are constructed using java.lang.ThreadGroup class. The main use of thread groups is that you can handle multiple threads simultaneously.

## How To Add Threads To Thread Group :

While creating the threads itself, you can specify it’s group using constructor which takes ThreadGroup and name of a thread as arguments. Below example shows how to add threads and child thread group to a parent thread group.

```java
public class ThreadGroupInJava
{
    public static void main(String[] args)
    {
        //Creating Parent Thread Group 
 
        ThreadGroup parentGroup = new ThreadGroup("Parent Thread Group");
 
        //Adding threads to ThreadGroup while creating threads itself
 
        Thread t1 = new Thread(parentGroup, "Thread 1");
 
        Thread t2 = new Thread(parentGroup, "Thread 2");
 
        //Creating child thread group
 
        ThreadGroup childGroup = new ThreadGroup(parentGroup, "Child Thread Group");
 
        //Adding a thread to child thread group
 
        Thread t3 = new Thread(childGroup, "Thread 3");
    }
}
```

## Some Useful Methods Of ThreadGroup :

1) **getParent() Method** :

It returns the parent of the thread group in the form ClassName[name=name of the parent, maxpri=Maximum priority].

```java
public class ThreadGroupsInJava
{
    public static void main(String[] args)
    {
        //Creating Parent Thread Group 
 
        ThreadGroup parentGroup = new ThreadGroup("Parent Thread Group ");
 
        //Creating Child Thread Group
 
        ThreadGroup childGroup = new ThreadGroup(parentGroup, "Child Thread Group");
 
        //Printing parent of Child Thread Group
 
        System.out.println(childGroup.getParent());   //Output : java.lang.ThreadGroup[name=Parent Thread Group ,maxpri=10]
    }
}
```

2) **setDaemon() And isDaemon() Methods** :

setDaemon() method is used to set the daemon property of a thread group. isDaemon() is used to check whether a thread group is daemon or not.

```java
public class ThreadGroupsInJava
{
    public static void main(String[] args)
    {
        //Creating Thread Group 
 
        ThreadGroup threadGroup = new ThreadGroup("Thread Group ");
 
        //Setting the daemon property of thread group
 
        threadGroup.setDaemon(true);
 
        //Checking the daemon property of thread group
 
        System.out.println(threadGroup.isDaemon());   //Output : true
    }
}
```

3) **setMaxPriority() And getMaxPriority() Methods** :

setMaxPriority() is used to set the maximum priority of a thread group. getMaxPriority() method is used to retrieve the maximum priority of a thread group.

```java
public class ThreadGroupsInJava
{
    public static void main(String[] args)
    {
        //Creating Thread Group 
 
        ThreadGroup threadGroup = new ThreadGroup("Parent Thread Group ");
 
        //Setting the maximum priority of thread group
 
        threadGroup.setMaxPriority(8);
 
        //getting the maximum priority of thread group
 
        System.out.println(threadGroup.getMaxPriority());   //Output : 8
    }
}
```

4) **activeCount() and activeGroupCount() Methods**

activeCount() returns the number of active threads in a specified group and it’s subgroups. activeGroupCount() returns the numbers of active thread groups in a specified group and it’s subgroups.

```java
public class ThreadGroupsInJava
{
    public static void main(String[] args)
    {
        //Creating parent Thread Group 
 
        ThreadGroup parentGroup = new ThreadGroup("Parent Thread Group ");
 
        Thread t1 = new Thread(parentGroup, "Thread 1")
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t1.start();
 
        Thread t2 = new Thread(parentGroup, "Thread 2")
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t2.start();
 
        //Creating Child Thread Group
 
        ThreadGroup childGroup = new ThreadGroup(parentGroup, "Child Group");
 
        Thread t3 = new Thread(childGroup, "Thread 3")
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t3.start();
 
        //Checking Active thread count
 
        System.out.println(parentGroup.activeCount());     //Output : 3
 
        //Checking Active thread group count
 
        System.out.println(parentGroup.activeGroupCount());   //Output : 1
    }
}
```

5) **interrupt() Method** :

This method is used to interrupt all threads in a group.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        //Creating Thread Group 
 
        ThreadGroup parentGroup = new ThreadGroup("Parent Group ");
 
        Thread t1 = new Thread(parentGroup, "Thread 1")
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    System.out.println("Thread interrupted");
                }
            }
        };
 
        t1.start();
 
        Thread t2 = new Thread(parentGroup, "Thread 2")
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    System.out.println("Thread interrupted");
                }
            }
        };
 
        t2.start();
 
        ThreadGroup childGroup = new ThreadGroup(parentGroup, "Child Group");
 
        Thread t3 = new Thread(childGroup, "Thread 3")
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    System.out.println("Thread interrupted");
                }
            }
        };
 
        t3.start();
 
        //Interrupting whole group
 
        parentGroup.interrupt();
    }
}
```

6) **destroy() Method** :

This method is used to destroy the whole thread group and it’s subgroups. Before calling this method, thread group must be empty i.e all threads in a group must be exited. Otherwise this method will throw IllegalThreadStateException.

```java
public class ThreadGroupsInJava
{
    public static void main(String[] args)
    {
        //Creating Thread Group 
 
        ThreadGroup parentGroup = new ThreadGroup("Parent Group ");
 
        Thread t1 = new Thread(parentGroup, "Thread 1");
 
        t1.start();
 
        Thread t2 = new Thread(parentGroup, "Thread 2");
 
        t2.start();
 
        ThreadGroup childGroup = new ThreadGroup(parentGroup, "Child Group");
 
        Thread t3 = new Thread(childGroup, "Thread 3");
 
        t3.start();
 
        try
        {
            Thread.sleep(2000);
        }
        catch (InterruptedException e)
        {
            e.printStackTrace();
        }
 
        //Destroying the whole group
 
        parentGroup.destroy();
    }
}
```

7) **enumerate() Method** :

There exist four versions of enumerate() method in ThreadGroup class. They are,

**public int enumerate(Thread[] list)** —> It copies all active threads of a group into specified array of threads.

**public int enumerate(Thread[] list, boolean recurse)** —> It copies all active threads of a group into specified array of threads. If recurse is true, subgroups are also enumerated.

**public int enumerate(ThreadGroup[] list)** —> It copies all active subgroups of a thread group into specified array of ThreadGroup.

**public int enumerate(ThreadGroup[] list, boolean recurse)** —> It copies all active subgroups of a thread group into specified array of ThreadGroup. If recurse is true, subgroups of subgroups are also enumerated.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        //Creating Thread Group 
 
        ThreadGroup parentGroup = new ThreadGroup("Parent Group ");
 
        Thread t1 = new Thread(parentGroup, "Thread 1")
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t1.start();
 
        Thread t2 = new Thread(parentGroup, "Thread 2")
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t2.start();
 
        ThreadGroup childGroup = new ThreadGroup(parentGroup, "Child Group");
 
        Thread t3 = new Thread(childGroup, "Thread 3")
        {
            public void run()
            {
                try
                {
                    Thread.sleep(5000);
                }
                catch (InterruptedException e)
                {
                    e.printStackTrace();
                }
            }
        };
 
        t3.start();
 
        //Enumerating all active threads
 
        Thread[] threads = new Thread[parentGroup.activeCount()];
 
        int No_Of_Active_Threads = parentGroup.enumerate(threads);
 
        System.out.println(No_Of_Active_Threads);
 
        for (Thread thread : threads)
        {
            System.out.println(thread.getName());
        }
    }
}
```

# 7 Things Every Java Programmer Should Know About Threads In Java

Here, I have tried to make a list of some observations about threads in java. You may be asked about these points in the interviews. I hope you guys will find it useful.

1) If you start a thread that is already started, you will get java.lang.IllegalThreadStateException at run time. There will be no compilation errors.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread();
 
        t.start();
 
        t.start();    //This statement will throw java.lang.IllegalThreadStateException
    }
}
```

2) Exception is thread wise not execution wise. i.e exception effects the thread in which it occurs. Other threads will execute normally. In the below example, exception occurs in thread t1. only this thread will be terminated abruptly. Thread t2 will continue to execute it’s task.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t1 = new Thread()
        {
            public void run()
            {
                String s = null;
 
                System.out.println(s.length());  //This statement will throw NullPointerException
 
                System.out.println("This statement will not be executed");
            }
        };
 
        Thread t2 = new Thread()
        {
            public void run()
            {
                for(int i = 0; i <= 1000; i++)
                {
                    System.out.println(i);
                }
            }
        };
 
        t1.start();
 
        t2.start();
    }
}
```

3) As we all know that start() method internally calls run() method. What happens when you call run() method directly?. When you call run() method of a thread directly, calling thread will execute the task defined in the run() method. For example, in the below program main thread is calling run() method of thread t. In this case, main thread will execute run() method not thread t.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = new Thread()
        {
            public void run()
            {
                System.out.println(Thread.currentThread().getName());    //Output : main
            }
        };
 
        t.run();
    }
}
```

4) Which one is better way to implement threads in java. Is it using Thread class or using Runnable interface?. It is the most confusing question for a java developer. I am of opinion that when multiple threads need to execute same task, then use Runnable interface. If multiple threads need to execute different tasks, then go for Thread class.

5) Setting the priority to a thread is not effective as we thought. Setting Priority of a thread is just an advice to OS not an instruction. It is up to OS to consider this advice.

6) Every thread in java is a member of a thread group. When a java application first starts up, Java runtime system creates a thread group called main. main thread is also member of this group.

```java
public class ThreadsInJava
{
    public static void main(String[] args)
    {
        Thread t = Thread.currentThread();
 
        System.out.println(t.getThreadGroup());    
 
        //Output : java.lang.ThreadGroup[name=main,maxpri=10]
    }
}
```

7) A thread is a permanent member of a thread group to which it joins during creation. You can’t move a thread to a new group after creating it.

# Difference Between wait() and sleep() Methods In Java

wait() and sleep() methods in Java, are used to pause the execution of a particular thread in a multi threaded environment. Whenever a thread calls wait() method, it releases the lock or monitor it holds and when it calls sleep() method, it doesn’t release the lock or monitor it holds. This is the main difference between wait() and sleep() methods. In this post, we discuss all the differences between wait() and sleep() methods in Java.

## Differences Between wait() And sleep() Methods In Java :

1) Both wait() and sleep() methods are used to pause the execution of current thread for some period of time. Whenever a thread calls wait() method, it goes into WAITING state after releasing the lock it holds. Whenever a thread calls sleep() method, it goes into TIMED_WAITING state without releasing the lock it holds.

2) A thread which is in WAITING state (state after calling wait() method) can be woken up by other threads by calling notify() or notifyAll() methods on the same lock. But, a thread which is in TIMED_WAITING state (state after calling sleep() method) can not be woken up. If any threads interrupt sleeping thread, InterruptedException will be raised.

3) wait() method along with notify() and notifyAll() are used for inter thread communication where as sleep() method is used to pause the execution of current thread for specific period of time.

4) wait() method is an instance method of java.lang.Object class. That means, this method is available in all objects you create in Java. Where as sleep() method is a static method of java.lang.Thread class. That means, it is available only in threads.

5) wait() method is called on objects. Whenever it is called by a thread on a particular object, thread releases the lock of that object and waits until other threads call either notify() or notifyAll() methods on the same object. Where as sleep() method is called on threads.

6) Whenever sleep() method is called, only current thread is going for sleep. For example, if main thread calls sleep() method on a thread t, i.e t.sleep(), main thread itself is going to sleep not thread t.

7) To call wait() method, calling thread must hold the lock of the object on which it is calling wait() method. That means, wait() method must be called within the synchronized block. Where as to call sleep() method, thread need not to hold the object lock. That means, sleep() method can be called outside the synchronized block also.

## wait() Vs sleep() Methods In Java :

| wait()        | sleep()      |
| ------------- |-------------|
| The thread which calls wait() method releases the lock it holds.	 |The thread which calls sleep() method doesn’t release the lock it holds.|
| The thread regains the lock after other threads call either notify() or notifyAll() methods on the same lock. |No question of regaining the lock as thread doesn’t release the lock.|
| wait() method must be called within the synchronized block. |sleep() method can be called within or outside the synchronized block.|
| wait() method is a member of java.lang.Object class. |sleep() method is a member of java.lang.Thread class.|
| wait() method is always called on objects. |sleep() method is always called on threads.|
| wait() is a non-static method of Object class. |sleep() is a static method of Thread class.|
| Waiting threads can be woken up by other threads by calling notify() or notifyAll() methods. |Sleeping threads can not be woken up by other threads. If done so, thread will throw InterruptedException.|
|  To call wait() method, thread must have object lock. |To call sleep() method, thread need not to have object lock.|


<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2015/02/WaitAndSleep.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

# Differences Between Program Vs Process vs Threads

Program, Process and Threads are three basic concepts of the operating systems about which every computer science engineer must be familiar with. That’s why most of the freshers will get a question or two about these concepts in their interview. Interviewer ask the questions about these concepts to check whether the candidate is familiar with the basics of operating systems or not. In this post, I have tried to explain what is a program, a process and a thread and how they differ from each other in a very simple manner. I hope you guys will find it useful.

## What Is A Program?

Program is an executable file containing the set of instructions written to perform a specific job on your computer. For example, chrome.exe is an executable file containing the set of instructions written so that we can view web pages. notepad.exe is an executable file containing the set of instructions which help us to edit and print the text files.

Programs are not stored on the primary memory in your computer. They are stored on a disk or a secondary memory on your computer. They are read into the primary memory and executed by the kernel. A program is sometimes referred as passive entity as it resides on a secondary memory.

## What Is A Process?

Process is an executing instance of a program. For example, When you double click on the Google Chrome icon on your computer, you start a process which will run the Google Chrome program. When you double click on a notepad icon on your computer, a process is started that will run the notepad program.

A process is sometimes referred as active entity as it resides on the primary memory and leaves the memory if the system is rebooted. Several processes may related to same program. For example, you can run multiple instances of a notepad program. Each instance is referred as a process.

## What Is A Thread?

Thread is the smallest executable unit of a process. For example, when you run a notepad program, operating system creates a process and starts the execution of main thread of that process.

A process can have multiple threads. Each thread will have their own task and own path of execution in a process. For example, in a notepad program, one thread will be taking user inputs and another thread will be printing a document.

All threads of the same process share memory of that process. As threads of the same process share the same memory, communication between the threads is fast.

Processes and threads can be represented like below,

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2014/11/ThreadsAndProcesses.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

## Process Vs Thread :

Below is the list of differences between Process Vs Thread.

| Process        | Thread    |
| ------------- |-------------|
|Processes are heavy weight operations.|	Threads are light weight operations.|
|Every process has its own memory space.|	Threads use the memory of the process they belong to.|
|Inter process communication is slow as processes have different memory address.	|Inter thread communication is fast as threads of the same process share the same memory address of the process they belong to.|
|Context switching between the process is more expensive.|	Context switching between threads of the same process is less expensive.|
|Processes don’t share the memory with other processes.|	Threads share the memory with other threads of the same process.|

# Extends Thread Vs Implements Runnable In Java

There are two ways you can create the threads in java. One is by extending java.lang.Thread class and another one is by implementing java.lang.Runnable interface [more]. In this post, we will see the differences between “Extends Thread” and “Implements Runnable” and what is the best option between these two to create the threads in java.

## Differences Between Extends Thread And Implements Runnable In Java :

1) **Multiple Inheritance Limitation**

As you know, Java doesn’t support multiple inheritance. A class in java can extend only one class. If you extend Thread class, then your class will not be able to extend any other class. This will limit your class to thread behavior. If you implement Runnable interface, then you will have an option for your class to extend any other class and inherit behaviors from other class also.

2) **Overhead Of Additional Methods**

If you extend Thread class, all methods of Thread class will be inheriting to your class which you may not need. This will cause additional overhead. You can remove this overhead by implementing Runnable interface.

3) **Logical Separation Of Task From The Runner**

If you implement Runnable interface, it will separate actual task from the runner. Runnable interface represents only the task and you can pass this task to any type of runner, either a thread or any executors.

4) **Best Object Oriented Design Practice**

In object oriented programming, extending a class means modifying or improving the existing class. If you are not improving the class, then it is not a good practice to extend it. So, implementing Runnable will be the best object oriented design practice.

5) **Loosely Coupled Vs Tightly coupled**

“Implements Runnable” makes your code loosely coupled. Because it separates the task from the runner. “Extends Thread” will make your code tightly coupled. Because, single class will act as both task container as well as runner.

6) **Reusability**

Implementing Runnable improves the reusability of your code. Because, Runnable contains only the task and you can use it wherever and whenever you want.

7) **Specialization Vs Generalization**

“Extends Thread” gives more specialized code. Because, it defines the thread specific task. Where as “Implements Runnable” gives more generalized version of the task applicable to many threads.

8) **Maintenance**

“Implements Runnable” will make your code easily maintainable as it separates the task from the runner. If you want to modify the task at any time, you can do so easily without disturbing the runner.

9) **Example**

a) Extends Thread Class

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        //Keep the task to be performed here
    }
}
 
public class MainClass 
{   
    public static void main(String[] args) 
    {
        MyThread thread = new MyThread();
         
        thread.start();
    }   
}
```

b) Implements Runnable Interface

```java
class MyRunnable implements Runnable
{
    @Override
    public void run()
    {
        //Keep the task to be performed here
    }
}
 
public class MainClass 
{   
    public static void main(String[] args) 
    {
        MyRunnable runnable = new MyRunnable();
         
        Thread t = new Thread(runnable);
         
        t.start();
    }   
}
```

## Extends Thread Vs Implements Runnable In Java :
| Implements Runnable        | Extends Thread    |
| ------------- |-------------|
|You can extend any other class.|	You can’t extend any other class.|
|No overhead of additional methods .|	Overhead of additional methods from Thread class.|
|Separates the task from the runner.|	Doesn’t separate the task from the runner.|
|Best object oriented programming practice.|	Not a good object oriented programming practice.|
|Loosely coupled.|	Tightly coupled.|
|Improves the reusability of the code.|	Doesn’t improve the reusability of the code.|
|More generalized task.|	Thread specific task.|
|Maintenance  of the code will be easy.|	Maintenance of the code will be time consuming.|

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2015/12/RunnableVsThread.png?w=1300" alt="Collections Framework Class Hierarchy"/></a>

## Conclusion :

From the above all findings, it is clear that “Implements Runnable” is the preferred method to create the threads in java.

# How To Stop A Thread In Java?

How do you stop a thread in java? now-a-days, this has been the popular question in the java interviews. Because, stop() method has been deprecated for some safety reasons. As stop() method has been deprecated, interviewer will be interested in what logic you will be using to stop a thread. There are two ways through which you can stop a thread in java. One is using boolean variable and second one is using interrupt() method. In this post, we will discuss both of these methods.

## How To Stop A Thread In Java Using A boolean Variable?

In this method, we declare one boolean variable called flag in a thread. Initially we set this flag as true. Keep the task to be performed in while loop inside the run() method by passing this flag. This will make thread continue to run until flag becomes false. We have defined stopRunning() method. This method will set the flag as false and stops the thread. Whenever you want to stop the thread, just call this method. Also notice that we have declared flag as volatile. This will make thread to read its value from the main memory, thus making sure that thread always gets its updated value.

```java
class MyThread extends Thread
{
    //Initially setting the flag as true
     
    private volatile boolean flag = true;
     
    //This method will set flag as false
     
    public void stopRunning()
    {
        flag = false;
    }
     
    @Override
    public void run()
    {
        //Keep the task in while loop
         
        //This will make thread continue to run until flag becomes false
         
        while (flag)
        {
            System.out.println("I am running....");
        }
         
        System.out.println("Stopped Running....");
    }
}
 
public class MainClass 
{   
    public static void main(String[] args) 
    {
        MyThread thread = new MyThread();
         
        thread.start();
         
        try
        {
            Thread.sleep(100);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        //call stopRunning() method whenever you want to stop a thread
         
        thread.stopRunning();
    }   
}
```

Output :

```java
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
Stopped Running….
```

## How To Stop A Thread In Java Using interrupt() Method?
In this method, we use interrupt() method to stop a thread. Whenever you call interrupt() method on a thread, it sets the interrupted status of a thread. This status can be obtained by interrupted() method. This status is used in a while loop to stop a thread.

```java
class MyThread extends Thread
{   
    @Override
    public void run()
    {
        while (!Thread.interrupted())
        {
            System.out.println("I am running....");
        }
         
        System.out.println("Stopped Running.....");
    }
}
 
public class MainClass 
{   
    public static void main(String[] args) 
    {
        MyThread thread = new MyThread();
         
        thread.start();
         
        try
        {
            Thread.sleep(100);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        //interrupting the thread
         
        thread.interrupt();
    }   
}
```

Output :

```java
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
I am running….
Stopped Running…..
```

# Difference Between notify And notifyAll In Java

notify() and notifyAll() methods along with wait() method are used to establish a communication between the threads. A thread goes into WAITING mode by calling wait() method. This thread will be in WAITING state until any other thread calls either notify() or notifyAll() method on the same object. Look here how threads communicate with each other using wait(), notify() and notifyAll() in Java. Any thread calling wait(), notify() and notifyAll() must have lock of that object. In the other words, these methods must be called within synchronized method or synchronized block. In this post, we will see the differences between notify and notifyAll in Java with an example.

## notify() In Java :

When a thread calls notify() method on a particular object, only one thread will be notified which is waiting for the lock or monitor of that object. The thread chosen to notify is random i.e randomly one thread will be selected for notification. Notified thread doesn’t get the lock of the object immediately. It gets once the calling thread releases the lock of that object. Until that it will be in BLOCKED state. It will move from BLOCKED state to RUNNING state once it gets the lock.

**Note** : Before notification, the thread will be in WAITING state. Once it is notified, it will move to BLOCKED state. It remains in BLOCKED state until it gets the lock. Once it gets the lock, it moves from BLOCKED state to RUNNING state.

Let’s see notify() method with an example.

```java
class Shared
{
    synchronized void waitMethod()
    {
        Thread t = Thread.currentThread();
         
        System.out.println(t.getName()+" is releasing the lock and going to wait");
         
        try
        {
            wait();
        }
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        System.out.println(t.getName()+" has been notified and acquired the lock back");
    }
     
    synchronized void notifyOneThread()
    {
        Thread t = Thread.currentThread();
         
        notify();
         
        System.out.println(t.getName()+" has notified one thread waiting for this object lock");
    }
}
 
public class MainClass 
{   
    public static void main(String[] args) 
    {
        final Shared s = new Shared();
         
        //Thread t1 will be waiting for lock of object 's'
         
        Thread t1 = new Thread() 
        {
            @Override
            public void run()
            {
                s.waitMethod();
            }
        };
         
        t1.start();
         
        //Thread t2 will be waiting for lock of object 's'
         
        Thread t2 = new Thread() 
        {
            @Override
            public void run()
            {
                s.waitMethod();
            }
        };
 
        t2.start();
         
        //Thread t3 will be waiting for lock of object 's'
         
        Thread t3 = new Thread() 
        {
            @Override
            public void run()
            {
                s.waitMethod();
            }
        };
         
        t3.start();
         
        try
        {
            Thread.sleep(1000);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        //Thread t4 will notify only one thread which is waiting for lock of object 's'
         
        Thread t4 = new Thread() 
        {
            @Override
            public void run()
            {
                s.notifyOneThread();
            }
        };
         
        t4.start(); 
    }   
}
```

Output :

```java
Thread-1 is releasing the lock and going to wait
Thread-0 is releasing the lock and going to wait
Thread-2 is releasing the lock and going to wait
Thread-3 has notified one thread waiting for this object lock
Thread-1 has been notified and acquired the lock back
```

## notifyAll() In Java :

When a thread calls notifyAll() method on a particular object, all threads which are waiting for the lock of that object are notified. All notified threads will move from WAITING state to BLOCKED state. All these threads will get the lock of the object on a priority basis. The thread which gets the lock of the object moves to RUNNING state. The remaining threads will remain in BLOCKED state until they get the object lock.

Below is an example of notifyAll() method in Java.

```java
class Shared
{
    synchronized void waitMethod()
    {
        Thread t = Thread.currentThread();
         
        System.out.println(t.getName()+" is releasing the lock and going to wait");
         
        try
        {
            wait();
        }
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        System.out.println(t.getName()+" has been notified and acquired the lock back");
    }
     
    synchronized void notifyAllThread()
    {
        Thread t = Thread.currentThread();
         
        notifyAll();
         
        System.out.println(t.getName()+" has notified all threads waiting for this object lock");
    }
}
 
public class MainClass 
{   
    public static void main(String[] args) 
    {
        final Shared s = new Shared();
         
        //Thread t1 will be waiting for lock of object 's'
         
        Thread t1 = new Thread() 
        {
            @Override
            public void run()
            {
                s.waitMethod();
            }
        };
         
        t1.start();
         
        //Thread t2 will be waiting for lock of object 's'
         
        Thread t2 = new Thread() 
        {
            @Override
            public void run()
            {
                s.waitMethod();
            }
        };
 
        t2.start();
         
        //Thread t3 will be waiting for lock of object 's'
         
        Thread t3 = new Thread() 
        {
            @Override
            public void run()
            {
                s.waitMethod();
            }
        };
         
        t3.start();
         
        try
        {
            Thread.sleep(1000);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        //Thread t4 will notify all threads which are waiting for lock of object 's'
         
        Thread t4 = new Thread() 
        {
            @Override
            public void run()
            {
                s.notifyAllThread();
            }
        };
         
        t4.start(); 
    }   
}
```

Output :

```java
Thread-0 is releasing the lock and going to wait
Thread-2 is releasing the lock and going to wait
Thread-1 is releasing the lock and going to wait
Thread-3 has notified all threads waiting for this object lock
Thread-1 has been notified and acquired the lock back
Thread-2 has been notified and acquired the lock back
Thread-0 has been notified and acquired the lock back
```

## Difference Between notify And notifyAll In Java :

Below diagram summarizes the difference between notify and notifyAll in java.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2016/03/NotifyVsNotifyAll.png?w=1300"/></a>

# Difference Between BLOCKED Vs WAITING States In Java

There are six thread states in Java. They are NEW, RUNNABLE, BLOCKED, WAITING, TIMED_WAITING and TERMINATED. At any point of time, a thread will be in any one of these six states. In these six states, BLOCKED and WAITING states are closely related. In this post, we will discuss the differences between BLOCKED Vs WAITING states in Java.

## BLOCKED And WAITING States In Java :

A thread enters into WAITING state when it calls wait() or join() method on an object. Before entering into WAITING state, thread releases the lock of the object it holds. It will remain in WAITING state until any other thread calls either notify() or notifyAll() on the same object.

Once the other thread calls notify() or notifyAll() on the same object, one or all the threads which are WAITING for lock of that object will be notified. All the notified threads will not get the object lock immediately. They will get the object lock on a priority basis once the current thread releases the lock. Until that they will be in BLOCKED state.

In simple terms, a thread will be in WAITING state if it is waiting for notification from other threads. A thread will be in BLOCKED state if it is waiting for other thread to release the lock it wants.

Look at the below diagram for more clarity.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2016/06/WaitingVsBlocked.png?w=1300"/></a>

## BLOCKED Vs WAITING States In Java :

| WAITING      | BLOCKED   |
| ------------- |-------------|	
|The thread will be in this state when it calls wait() or join() method.| The thread will remain in WAITING state until any other thread calls notify() or notifyAll().|
|The thread will be in this state when it is notified by other thread but has not got the object lock yet.| The WAITING thread is waiting for notification from other threads.|	
|The BLOCKED thread is waiting for other thread to release the lock.|The WAITING thread can be interrupted.	The BLOCKED thread can’t be interrupted.|

Note : Deadlocked threads will be in BLOCKED state.

# Differences between Start And Run Methods In Java Threads

As you know, thread execution starts when you call start() method. You may be also aware that start() method internally calls run() method. Then what is the use of calling start() method. Can’t we call run() method directly? What is the difference between calling start() method and calling run() method directly as anyhow start() method internally calls run() method? In this post, we will see the differences between start and run methods in Java threads. What is the best way? is it calling run() method directly or calling start() method?

## Differences Between Start And Run Methods In Java Threads :

1) **Thread Creation** :

When you call start() method, a new thread is created and that newly created thread executes the task kept in the run() method. If you call run() method directly, no new thread is created. Any task kept in run() method is executed by the calling thread itself.

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        System.out.println("I am executed by "+currentThread().getName());
    }
}
 
public class ThreadExample
{
    public static void main(String[] args)
    {
        MyThread myThread = new MyThread();
 
        //Calling run() method directly
         
        myThread.run();
 
        //Calling start() method. It creates a new thread which executes run() method
 
        myThread.start();
    }
}
```

Output :

```java
I am executed by main
I am executed by Thread-0
```

2) **Use Of Multi-threading Concept** :

If you are calling run() method directly, then you are not making use of the most superb feature of Java language – Multi-threaded programming. Because, when you call run() method directly, no new thread is created. run() method is executed by the calling thread itself. It just acts as normal method invocation. You are not using the concept of multi-threading.

3) **Thread.start() and Runnable.run()** :

start() method is the member of java.lang.Thread class. run() method is the member of java.lang.Runnable interface. As Thread class implements Runnable interface, run() method is inherited to Thread class also.

4) **Multiple Invocation** :

You can call run() method any number of times. You will never get any exceptions. But, start() method must be called only once. If you call start() method second time, it will throw IllegalThreadStateException as thread is already started.

```java
class MyThread extends Thread
{
    @Override
    public void run()
    {
        System.out.println("I am executed by "+currentThread().getName());
    }
}
 
public class ThreadExample
{
    public static void main(String[] args)
    {
        MyThread myThread = new MyThread();
 
        //Calling run() method multiple times
 
        myThread.run();
 
        myThread.run();
 
        myThread.run();
 
        //Calling start() method first time
 
        myThread.start();
 
        //Calling start() method second time. It will throw IllegalThreadStateException
 
        myThread.start();
    }
}
```

Output :

```java
I am executed by main
I am executed by main
I am executed by main
I am executed by Thread-0
Exception in thread "main" java.lang.IllegalThreadStateException
    at java.lang.Thread.start(Thread.java:708)
    at ThreadPrograms.ThreadExample.main(ThreadExample.java:32)
```

## start() Vs run() Methods In Java Threads :

| start()      | run()   |
| ------------- |-------------|
|New thread is created.| No new thread is created.|
|Newly created thread executes task kept in run() method.| Calling thread itself executes task kept in run() method.|
|It is a member of java.lang.Thread class.|	It is a member of java.lang.Runnable interface.|
|You can’t call start() method more than once.|	You can call run() method multiple times.|
|Use of multi-threaded programming concept.| No use of multi-threaded programming concept.|

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2018/12/StartVsRun.png?w=703&ssl=1"/></a>

# Print Odd And Even Numbers By Two Threads In Java

## Odd And Even Numbers By Two Threads Java Program :
Write a java program where two threads print odd and even numbers in sync. That means, one thread should print only the odd numbers and another thread should print only the even numbers. But, both threads should communicate with each other so that numbers should be printed in natural order.

**Sample Output** :

```java
Odd-Thread : 1
Even-Thread : 2
Odd-Thread : 3
Even-Thread : 4
Odd-Thread : 5
Even-Thread : 6
…………..
…………..
…………..
```

## How To Print Odd And Even Numbers By Two Threads In Java?

The task of printing odd and even numbers by two threads in sync can be divided in 4 steps. Let’s see those steps one by one.

**Step 1 : Odd Thread**

The task of this thread is to print only the odd numbers. OddThread internally calls printOdd() method of SharedPrinter class (We will see SharedPrinter class in step 3).

```java
//OddThread to print odd numbers
//Calls printOdd() method of SharedPrinter class until limit is exceeded.
 
class OddThread extends Thread
{
    int limit;
     
    sharedPrinter printer;
     
    public OddThread(int limit, sharedPrinter printer)
    {
        this.limit = limit;
         
        this.printer = printer;
    }
     
    @Override
    public void run() 
    {
        int oddNumber = 1;        //First odd number is 1
         
        while (oddNumber <= limit)
        {
            printer.printOdd(oddNumber);       //Calling printOdd() method of SharedPrinter class
             
            oddNumber = oddNumber + 2;         //Incrementing to next odd number
        }
    }
}
```

**Step 2 : Even Thread**

The task of this thread is to print only the even numbers. EvenThread internally calls printEven() method of SharedPrinter class (See SharedPrinter class in step 3)

```java
//EvenThread to print even numbers.
//Calls printEven() method of SharedPrinter class until limit is exceeded.
 
class EvenThread extends Thread
{
    int limit;
     
    sharedPrinter printer;
     
    public EvenThread(int limit, sharedPrinter printer)
    {
        this.limit = limit;
         
        this.printer = printer;
    }
     
    @Override
    public void run() 
    {
        int evenNumber = 2;           //First even number is 2
         
        while (evenNumber <= limit)
        {
            printer.printEven(evenNumber);          //Calling printEven() method of SharedPrinter class
             
            evenNumber = evenNumber + 2;           //Incrementing to next even number
        }
    }
}
```

**Step 3 : SharedPrinter Class.**

This class is at the core of the whole task. In this class, both threads – OddThread and EvenThread – communicate with each other using wait() and notify() to print odd and even numbers in sync. This class has three members.

1) A boolean variable, isOddPrinted : It stores the status whether odd number is printed or not.

2) printOdd() Method : This method is called by OddThread. First, it checks the status isOddPrinted. If isOddPrinted is true then it waits until next even number is printed by EvenThread. If isOddPrinted is false then it prints next odd number, sets isOddPrinted to true and notifies EvenThread.

3) printEven() Method : This method is called by EvenThread. First, it checks the status of isOddPrinted. If isOddPrinted is false then it waits until next odd number is printed by OddThread. If isOddPrinted is true then it prints next even number, sets isOddPrinted to false and notifies OddThread.

```java
class sharedPrinter
{
    //A boolean flag variable to check whether odd number is printed or not
    //Initially it is false.
     
    boolean isOddPrinted = false;
     
    //synchronized printOdd() method to print odd numbers. It is executed by OddThread.
    //First checks isOddPrinted, 
    //if isOddPrinted is true then it waits until next even number is printed by EvenThread
    //If isOddPrinted is false then prints next odd number, sets isOddPrinted to true
    //sleeps for 1 second before notifying EvenThread
     
    synchronized void printOdd(int number)
    {
        while (isOddPrinted)
        {
            try
            {
                wait();
            } 
            catch (InterruptedException e)
            {
                e.printStackTrace();
            }
        }
         
        System.out.println(Thread.currentThread().getName()+" : "+number);
         
        isOddPrinted = true;
         
        try
        {
            Thread.sleep(1000);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        notify();
    }
     
    //Synchronized printEven() method to print even numbers. It is executed by EvenThread
    //First checks isOddPrinted, 
    //if isOddPrinted is false then it waits until next odd number is printed by OddThread
    //If isOddPrinted is true then it prints next even number, sets isOddPrinted to false
    //sleeps for 1 second before notifying OddThread
     
    synchronized void printEven(int number)
    {
        while (! isOddPrinted)
        {
            try
            {
                wait();
            }
            catch (InterruptedException e) 
            {
                e.printStackTrace();
            }
        }
         
        System.out.println(Thread.currentThread().getName()+" : "+number);
         
        isOddPrinted = false;
         
        try
        {
            Thread.sleep(1000);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        notify();
    }
}
```

**Step 4 : Main Class**

In the MainClass, we instantiate OddThread and EvenThread by passing limit and SharedPrinter object, give them the name and start both the threads.

```java
public class MainClass 
{
    public static void main(String[] args) 
    {
        sharedPrinter printer = new sharedPrinter();
         
        OddThread oddThread = new OddThread(20, printer);
         
        oddThread.setName("Odd-Thread");
         
        EvenThread evenThread = new EvenThread(20, printer);
         
        evenThread.setName("Even-Thread");
         
        oddThread.start();
         
        evenThread.start();
    }
}
```
Above 4 steps can be represented pictorially as follows.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2019/03/OddEvenNumbersByTwoThreads.png?w=628&ssl=1"/></a>

## Full Java Program To Print Odd And Even Numbers By Two Threads :

```java
//OddThread to print odd numbers
//Calls printOdd() method of SharedPrinter class until limit is exceeded.
 
class OddThread extends Thread
{
    int limit;
     
    sharedPrinter printer;
     
    public OddThread(int limit, sharedPrinter printer)
    {
        this.limit = limit;
         
        this.printer = printer;
    }
     
    @Override
    public void run() 
    {
        int oddNumber = 1;        //First odd number is 1
         
        while (oddNumber <= limit)
        {
            printer.printOdd(oddNumber);       //Calling printOdd() method of SharedPrinter class
             
            oddNumber = oddNumber + 2;         //Incrementing to next odd number
        }
    }
}
 
//EvenThread to print even numbers.
//Calls printEven() method of SharedPrinter class until limit is exceeded.
 
class EvenThread extends Thread
{
    int limit;
     
    sharedPrinter printer;
     
    public EvenThread(int limit, sharedPrinter printer)
    {
        this.limit = limit;
         
        this.printer = printer;
    }
     
    @Override
    public void run() 
    {
        int evenNumber = 2;           //First even number is 2
         
        while (evenNumber <= limit)
        {
            printer.printEven(evenNumber);          //Calling printEven() method of SharedPrinter class
             
            evenNumber = evenNumber + 2;           //Incrementing to next even number
        }
    }
}
 
class sharedPrinter
{
    //A boolean flag variable to check whether odd number is printed or not
    //Initially it is false.
     
    boolean isOddPrinted = false;
     
    //synchronized printOdd() method to print odd numbers. It is executed by OddThread.
    //First checks isOddPrinted, 
    //if isOddPrinted is true then it waits until next even number is printed by EvenThread
    //If isOddPrinted is false then prints next odd number, sets isOddPrinted to true
    //sleeps for 1 second before notifying EvenThread
     
    synchronized void printOdd(int number)
    {
        while (isOddPrinted)
        {
            try
            {
                wait();
            } 
            catch (InterruptedException e)
            {
                e.printStackTrace();
            }
        }
         
        System.out.println(Thread.currentThread().getName()+" : "+number);
         
        isOddPrinted = true;
         
        try
        {
            Thread.sleep(1000);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        notify();
    }
     
    //Synchronized printEven() method to print even numbers. It is executed by EvenThread.
    //First checks isOddPrinted, 
    //if isOddPrinted is false then it waits until next odd number is printed by OddThread
    //If isOddPrinted is true then it prints next even number, sets isOddPrinted to false
    //sleeps for 1 second before notifying OddThread
     
    synchronized void printEven(int number)
    {
        while (! isOddPrinted)
        {
            try
            {
                wait();
            }
            catch (InterruptedException e) 
            {
                e.printStackTrace();
            }
        }
         
        System.out.println(Thread.currentThread().getName()+" : "+number);
         
        isOddPrinted = false;
         
        try
        {
            Thread.sleep(1000);
        } 
        catch (InterruptedException e) 
        {
            e.printStackTrace();
        }
         
        notify();
    }
}
 
//Main Class
 
public class MainClass 
{
    public static void main(String[] args) 
    {
        sharedPrinter printer = new sharedPrinter();
         
        OddThread oddThread = new OddThread(20, printer);
         
        oddThread.setName("Odd-Thread");
         
        EvenThread evenThread = new EvenThread(20, printer);
         
        evenThread.setName("Even-Thread");
         
        oddThread.start();
         
        evenThread.start();
    }
}
```

Output :

```java
Odd-Thread : 1
Even-Thread : 2
Odd-Thread : 3
Even-Thread : 4
Odd-Thread : 5
Even-Thread : 6
Odd-Thread : 7
Even-Thread : 8
Odd-Thread : 9
Even-Thread : 10
Odd-Thread : 11
Even-Thread : 12
Odd-Thread : 13
Even-Thread : 14
Odd-Thread : 15
Even-Thread : 16
Odd-Thread : 17
Even-Thread : 18
Odd-Thread : 19
Even-Thread : 20
```