# What Are Bounded Types And Why They Are Used?

In the earlier posts, We have seen that while creating objects to generic classes we can pass any derived type as type parameters. Many times it will be useful to limit the types that can be passed to type parameters. For that purpose, bounded types or bounded type parameters are introduced in generics. Using bounded types, you can make the objects of generic class to have data of specific derived types.

For example, If you want a generic class that works only with numbers (like int, double, float, long …..) then declare type parameter of that class as a bounded type to java.lang.Number class. Then while creating objects to that class you have to pass only Number types or it’s subclass types as type parameters.

Here is the syntax for declaring Bounded type parameters.

```java
<T extends SuperClass>
```

This specifies that ‘T’ can only be replaced by ‘SuperClass’ or it’s sub classes. Remember that extends clause is an inclusive bound. That means bound includes ‘SuperClass’ also.

Here is an example which demonstrates the bounded type parameters.

```java
class GenericClass<T extends Number>    //Declaring Number class as upper bound of T
{
    T t;
 
    public GenericClass(T t)
    {
        this.t = t;
    }
 
    public T getT()
    {
        return t;
    }
}
```

In this example, T has been declared as bounded type to Number class. So while creating objects to this class, you have to pass either Number type or it’s subclass types (Integer, Double, Float, Byte… ) as a type parameter. It wouldn’t allow other than these types to pass as a type parameter. If you try to pass, compiler will throw compile time error.

```java
public class GenericsInJava
{
    public static void main(String[] args)
    {
        //Creating object by passing Number as a type parameter
 
        GenericClass<Number> gen1 = new GenericClass<Number>(123);
 
        //Creating object by passing Integer as a type parameter
 
        GenericClass<Integer> gen2 = new GenericClass<Integer>(new Integer(456));
 
        //Creating object by passing Double as a type parameter
 
        GenericClass<Double> gen3 = new GenericClass<Double>(new Double(23.589));
 
        //Creating object by passing Long as a type parameter
 
        GenericClass<Long> gen4 = new GenericClass<Long>(new Long(12));
 
        //While Creating object by passing String as a type parameter, it gives compile time error
 
        GenericClass<String> gen5 = new GenericClass<String>("I am string");   //Compile time error
    }
}
```

## Bounded Type Parameters In Generic Methods :

You can use bounded types while defining generic methods also. Here is an example.

```java
class GenericClass
{
    //Declaring T as bounded type to Number class
 
    public static <T extends Number> void printNumbers(T[] t)
    {
        for (int i = 0; i < t.length; i++)
        {
            System.out.println(t[i]);
        }
    }
}
 
public class GenericsInJava
{
    public static void main(String[] args)
    {
        //Passing Integer[] array while calling printNumbers()
 
        GenericClass.printNumbers(new Integer[] {new Integer(10), new Integer(20), new Integer(30), new Integer(40)} );
 
        //Passing Double[] array while calling printNumbers()
 
        GenericClass.printNumbers(new Double[] {new Double(21.45), new Double(20.45), new Double(34.87), new Double(48.36)} );
 
        //Passing String[] array while calling printNumbers(), it gives compile time error
 
        GenericClass.printNumbers(new String[] {"one", "Two", "Three", "Four"});    //Compile time error
    }
}
```

## Using Interface As An Upper Bound :

You can also use interface type along with class type as an upper bound to type parameters. As in java, any class can extend only one class and can implement multiple interfaces, this also applies while declaring the bound to type parameters. That means a bounded parameter can extend only one class and one or more interfaces. While specifying bounded parameters that has a class and an interface or multiple interfaces, use & operator as a delimiter.

```java
class GenericClass <T extends AnyClass & FirstInterface & SecondInterface>
{   
 
}
```
