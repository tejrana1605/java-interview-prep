# Can We Define Methods And Constructors As Generic?

Generics are very useful and flexible feature of Java. Generics provide safe type casting to your coding. Along with safe type casting, they also give flexibility to your coding. For example, Once you write a class or interface using generics, you can use any type to create objects to them. In simple words, You can make objects to work with any type using generics.

One more addition to generics is Generic Methods. If you don’t want whole class or interface to be generic, you want only some part of class as generic, then generic methods will be solution for this.

The syntax for defining generic methods is as follows,

```java
<type-Parameters> return_type method_name(parameter list)
{
 
}
```

You can observe that type parameters are mentioned just before the return type. It is a rule you must follow while defining generic methods. The remaining parts are same as in normal method.

Generic methods can be static or non-static. There is no restriction for that. Generic class as well as non-generic class can have generic methods.

Here is an example which contains static generic method defined inside a non-generic class.

```java
class NonGenericClass
{   
    static <T> void genericMethod(T t1)
    {
        T t2 = t1;
         
        System.out.println(t2);
    }
}
```

In this example, ‘genericMethod()’ is a static generic method with ‘T’ as type parameter. Notice that type parameter is mentioned just before the return type.

While calling above generic method, you can pass any type as an argument. This is the best example for generics providing the flexibility. Look at the below code, I have called the above method by passing three different types as an argument.

```java
public class GenericsInJava
{
    public static void main(String[] args)
    {
        NonGenericClass.genericMethod(new Integer(123));     //Passing Integer type as an argument 
         
        NonGenericClass.genericMethod("I am string");        //Passing String type as an argument
         
        NonGenericClass.genericMethod(new Double(25.89));    //Passing Double type as an argument
    }
}
```

## Constructors As Generics :
As we all know that constructors are like methods but without return types. Like methods, constructors also can be generic. Even non-generic class can have generic constructors. Here is an example in which constructor of a non-generic class is defined as generic.

```java
class NonGenericClass
{   
    public <T> NonGenericClass(T t1)
    {
        T t2 = t1;
         
        System.out.println(t2);
    }
}
 
public class GenericsInJava
{
    public static void main(String[] args)
    {
        //Creating object by passing Integer as an argument
         
        NonGenericClass nonGen1 = new NonGenericClass(123);
         
        //Creating object by passing String as an argument
         
        NonGenericClass nonGen2 = new NonGenericClass("abc");
         
        //Creating object by passing Double as an argument
         
        NonGenericClass nonGen3 = new NonGenericClass(25.69);
    }
}
```