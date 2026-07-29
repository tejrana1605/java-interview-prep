# Some Interesting Observations About Generics In Java

In this post, I have tried to list down some interesting observations about generics in java. You may get questions about these points in the interview or any java certification exams.

- Java allows generic classes to use without type parameters i.e as a raw type. This is because to provide the compatibility of generic code with non-generic code. That means, non-generic code must be able to work with generic code and generic code must be able to work with non-generic code.

```java
class GenericClass<T>
{
    //Generic class
}
 
public class GenericsInJava
{
    public static void main(String[] args)
    {
        GenericClass rawType = new GenericClass();     //Using generic class as a raw type
    }
}
```

- You can’t create an instance to the type parameters. This is because, the type parameters does not exist at run time. They are erased during compilation.

```java
class GenericClass<T>
{
    T t = new T();     //Compile Time error
 
    <V> void genericMethod()
    {
        V v = new V();     //Compile Time error
    }
}
```

- In generic class with type parameter ‘T’, you can’t declare static fields of type ‘T’ and you can’t use ‘T’ in a static method. However, you can declare static generic methods with their own type parameters.

```java
class GenericClass<T>
{
    static T t;        //Compile time error
 
    static void staticMethod()
    {
        System.out.println(t);    //Compile time error
    }
 
    static <V> void genericMethod()
    {
        //Static generic method
    }
}
```

- You can’t instantiate an array whose type is a type parameter.

```java
class GenericClass<T>
{
    T[] t;        
 
    public GenericClass(T[] t)
    {
        t = new T[5];   //Compile time error
 
        this.t = t;     //But, This is OK
    }
}
```

- You can’t create an array of generic type containing specific type of data. But, you can create an array of generic type containing unknown type of data.

```java
class GenericClass<T>
{
        //Generic type
}
 
public class GenericsInJava
{
    public static void main(String[] args)
    {
        GenericClass<Number> gen[] = new GenericClass<Number>[10];   //Compile time error
 
        GenericClass<?> gen1[] = new GenericClass<?>[10];    //But, this is fine
    }
}
```

- You can not create generic exceptions i.e A generic class can not extend Throwable or any of it’s sub classes.

```java
class GenericClass<T> extends Throwable
{
    //Compile time error
}
```