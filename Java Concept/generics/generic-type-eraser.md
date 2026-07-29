# Type Erasure

In the previous posts, we have seen how type safety can be achieved using generics. If you use generics in your code, you need not to perform explicit casting. Compiler performs strong type checking during compilation and hence removing the chances of occurring ClassCastException at run time.

One more interesting thing about generics is **type erasure**. When you compile your java code, compiler removes all generic information mentioned in your code. Compiler replaces all type parameters with their bounded type. The type parameters which don’t have bounds will be replaced with java.lang.Object class. That means all type parameters exist till compilation only. They are erased during compilation. They don’t exist at run time.

To understand how type erasure works, consider this example.

```java
class GenericClassOne<T>
{
    T t;    //T will be replaced by java.lang.Object when compiled
}
 
class GenericClassTwo<T extends Number>
{
    T t;    //T will be replaced by java.lang.Number when compiled
}
```

When you compile above two classes, compiler replaces type parameter ‘T’ of GenericClassOne with java.lang.Object class as it is not bounded and type parameter ‘T’ of GenericClassTwo is replaced by java.lang.Number class as it is bounded by Number class. This is how above two classes look after compilation.

```java
class GenericClassOne extends java.lang.Object
{
    java.lang.Object t;
}
 
class GenericClassTwo extends java.lang.Object
{
    java.lang.Number t;
}
```

You can notice that type parameters are erased after compilation. They don’t exist at run time. That’s why you can’t instantiate a type parameter. It gives compile time error.

```java
class GenericClass<T>
{
    T t = new T();      //Compile time error
 
    <V> void genericMethod()
    {
        V v = new V();   //Compile time error
    }
}
```