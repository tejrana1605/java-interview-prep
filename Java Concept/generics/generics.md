# Why We Need Generics In Java?

Errors are integral part of coding. Some errors occur at compile time and some errors occur at run time. Errors which occur at compile time can be easily identified and can be removed. But, run time errors occur when an application is running in real time. If they happen, they cause abrupt termination of an application.

ClassCastException is also such an exception which happens only at run time. It occurs when data of one type can not be casted to another type. You will never get a single clue about this exception during compilation. Look at the below code which throws ClassCastException at run time. But, you will never be get notified about this exception at compile time.

```java
public class GenericsInJava
{
    public static void main(String[] args)
    {
        ArrayList list = new ArrayList();
 
        list.add("JAVA");
 
        list.add(123);
 
        for (Object object : list)
        {
            //Below statement throws ClassCastException at run time
 
            String str = (String) object;       //Type casting
 
            System.out.println(str);
        }
    }
}
```

In this example, ‘list’ contains elements of String type as well as int type. When you try to cast it’s elements to string type in the for loop, element of string type is casted without throwing errors but element of int type throws ClassCastException.

You can avoid ClassCastException by using generics in your code. The above example can be re-written using generics like below.

```java
public class GenericsInJava
{
    public static void main(String[] args)
    {
        ArrayList<String> list = new ArrayList<String>();
 
        list.add("JAVA");
 
    //  list.add(123);       Compile time error
 
        for (String str : list)
        {
            //No type casting needed. ClasscastException Never occurs
 
            System.out.println(str);
        }
    }
}
```

Now, ‘list’ is declared so that it can hold only string type. If you try to add elements of different type, it gives compile time error. Therefore, ClassCastException never occurs while executing the for loop.

**Definition**

Generics are introduced in Java 5 to provide the type checking at compile time. If you use generics, you need not to perform the type casting explicitly. Java compiler applies strong type checking if you use generics in your code and shows errors if the code violates the type safety. Thus removing the risk of ClassCastException.

Therefore, To write the type safety code and to remove the risk of ClassCastException at run time, we need generics.