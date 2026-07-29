# Garbage Collection And finalize() method In Java

You all know that an object is created in the memory using new operator. Constructor is used to initialize the properties of that object. When an object is no more required, it must be removed from the memory so that that memory can be reused for other objects. Removing unwanted objects or abandoned objects from the memory is called garbage collection (GC). In the languages like C++, GC is performed manually using destructors.

But, there is no destructors in java. In java, there exist better mechanism to handle the garbage collection. You need not to delete unwanted objects explicitly. JVM does this for you. JVM implicitly sweeps out abandoned objects from the memory.

Before moving on to Garbage Collection in java, let’s have a look at the finalize() method of Object class.

## finalize() method In Java:
finalize() method is a protected and non-static method of java.lang.Object class. This method will be available in all objects you create in java. This method is used to perform some final operations or clean up operations on an object before it is removed from the memory.  you can override the finalize() method to keep those operations you want to perform before an object is destroyed. Here is the general form of finalize() method.

```java
protected void finalize() throws Throwable
{
    //Keep some resource closing operations here
}
```

## Garbage Collection In Java :

Whenever you run a java program, JVM creates three threads. 1) main thread   2) Thread Scheduler   3) Garbage Collector Thread. In these three threads, main thread is a user thread and remaining two are daemon threads which run in background.

The task of main thread is to execute the main() method. The task of thread scheduler is to schedule the threads. The task of garbage collector thread is to sweep out abandoned objects from the heap memory. Abandoned objects or dead objects are those objects which does not have live references. Garbage collector thread before sweeping out an abandoned object, it calls finalize() method of that object. After finalize() method is executed, object is destroyed from the memory. That means clean up operations which you have kept in the finalize() method are executed before an object is destroyed from the memory.

Garbage collector thread does not come to heap memory whenever an object becomes abandoned. It comes once in a while to the heap memory and at that time if it sees any abandoned objects, it sweeps out those objects after calling finalize() method on them. Garbage collector thread calls finalize() method only once for one object.

Let’s discuss some interesting points about garbage collection and finalize() method.

## Some Interesting Points About Garbage Collection And finalize() method In Java :

1) In some scenarios, finalize() method is not at all called by the garbage collector thread. For example, When I executed the below program in my system, finalize() method of Class A is not at all executed.

```java
class A
{
    int i = 50;
 
    @Override
    protected void finalize() throws Throwable
    {
        System.out.println("From Finalize Method");
    }
}
 
public class Test
{
   public static void main(String[] args)
   {
      //Creating two instances of class A
 
      A a1 = new A();
 
      A a2 = new A();
 
      //Assigning a2 to a1
 
      a1 = a2;
 
      //Now both a1 and a2 will be pointing to same object 
 
      //An object earlier referred by a1 will become abandoned
 
      System.out.println("done");
   }
}
```

2) You can make finalize() method to be executed forcefully using either Runtime.getRuntime().runFinalization() OR Runtime.runFinalizersOnExit(true). But, both the methods have disadvantages. Runtime.getRuntime().runFinalization() makes the just best effort to execute finalize() method. It is not gauranteed that it will execute finalize() method. Runtime.runFinalizersOnExit(true) is deprecated in JDK because some times it runs finalize() method on live objects also.

```java
class A
{
    int i = 50;
 
    @Override
    protected void finalize() throws Throwable
    {
        System.out.println("From Finalize Method");
    }
}
 
public class Test
{
   public static void main(String[] args)
   {
      //Creating two instances of class A
 
      A a1 = new A();
 
      A a2 = new A();
 
      //Assigning a2 to a1
 
      a1 = a2;
 
      //Making finalize() method to execute forcefully
       
      Runtime.getRuntime().runFinalization();
 
      System.out.println("done");
   }
}
```

3) you can call garbage collector explicitly using System.gc() or RunTime.getRunTime().gc(). Again it is just a request to garbage collector not a command. It is up to garbage collector to honour this request.

```java
class A
{
    int i;
 
    public A(int i)
    {
        this.i = i;
    }
 
    @Override
    protected void finalize() throws Throwable
    {
        System.out.println("From Finalize Method, i = "+i);
    }
}
 
public class Test
{
   public static void main(String[] args)
   {
       //Creating two instances of class A
 
       A a1 = new A(10);
 
       A a2 = new A(20);      
 
       //Assigning a2 to a1
 
       a1 = a2;
 
       //Now both a1 and a2 will be pointing same object 
 
       //An object earlier referred by a1 will become abandoned
 
           //Calling garbage collector thread explicitly
 
       System.gc();              //OR call Runtime.getRuntime().gc();
 
       System.out.println("done");
   }
}
```

4) finalize() methods are not chained like constructors.i.e there is no calling statement to super class finalize() method inside the finalize() method of sub class. You need to explicitly call super class finalize() method.

```java
protected void finalize() throws Throwable
{
    System.out.println("From Finalize Method");
 
    //Calling super class finalize() method explicitly
 
    super.finalize();
}
```

5) Exceptions occurred in finalize() method are not propagated. They are ignored by the garbage collector.

6) You can call finalize() method explicitly on an object before it is abandoned. When you call, only operations kept in finalize() method are performed on an object. Object will not be destroyed from the memory.

```java
class A
{
    int i;
 
    public A(int i)
    {
        this.i = i;
    }
 
    @Override
    protected void finalize() throws Throwable
    {
        System.out.println("From Finalize Method, i = "+i);
 
        //Calling super class finalize() method explicitly
 
        super.finalize();
    }
}
 
public class Test
{
   public static void main(String[] args)
   {
       //Creating two instances of class A
 
       A a1 = new A(10);
 
       A a2 = new A(20);      
 
       //Calling finalize() method of a1 before it is abandoned
       try
       {
           a1.finalize();
       }
       catch (Throwable e)
       {
           e.printStackTrace();
       }
 
       //Assigning a2 to a1
 
       a1 = a2;
 
       //Now both a1 and a2 will be pointing same object 
 
       //An object earlier referred by a1 will become abandoned
 
       System.out.println("done");
   }
}
```

7) finalize() method on an abandoned object is called only once by the garbage collector thread. GC ignores finalize() method called on an object by the developer.

## What do you mean by cleanup operations on the object?

These are the operations which are carried out by garbage collector before an object is destroyed. These operations are kept in finalize() method as garbage collector calls finalize() method before an object is destroyed from the memory. The operations like releasing the resources held by an object or closing a database connection or closing a file are some examples for cleanup operations.

## Can you explain the difference between finalize() and finally block.Because Both are Used for Clean Up Operations. Among Both Of Them Which One Is Preferred.

finalize() is used to release the external resources of object…
finally is used to release the external resources of try block…

finally is used to close any Connection stream , Open files, after try block no matter whether an exception has occured on or not, always finally block statements will be executed after try block if there is.
finalize is used to clean up memeory from unwanted or non-useable objects for garbage Collection

## I don’t understand ur 7 point i.e. “GC ignores finalize() method called on an object by the developer. ” If it ignores by GC, then what the mean or the requirement of Override finalize() method, as it will be ignored by GC Thread, when it will be run.

It means that GC has nothing to do with our calling of finalize(explicitly) on an object. It doesn’t see it as same as calling of finalize on the object by its own.
You know that GC calls finalize method on an object only once in its lifetime.
Now suppose, We as developer calls finalize on an object explicitly even before GC calls, and then we call System.GC command. Now, GC will not take into consideration our calling of finalize on the object and instead calls finalize on that object again (as a part of Garbage collection mechanism).