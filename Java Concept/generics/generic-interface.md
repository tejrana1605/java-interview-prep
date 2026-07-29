# Rules To Follow While Implementing Generic Interfaces

Like generic classes, you can also define generic interfaces. The same syntax used to define generic classes is also used to define generic interfaces. Here is an example of generic interface.

```java
interface GenericInterface<T>
{
    void setT(T t);    
 
    T getT();
}
```

While implementing generic interfaces you have to follow some rules. Below is the discussion of those rules.

## Rules To Follow While Implementing Generic Interfaces :

- Only generic classes can implement generic interfaces. Normal classes can’t implement generic interfaces. For example, above generic interface can be implemented as,

```java
class GenericClass<T> implements GenericInterface<T>
{
 
}
```

Not like below. It gives compile time error.

```java
class NormalClass implements GenericInterface<T>
{
     //Compile time error
}
```

Here is the full implementation of above generic interface.

```java
class GenericClass<T> implements GenericInterface<T>
{
    T t;
 
    //Implementing setT() method
 
    @Override
    public void setT(T t)
    {
        this.t = t;
    }
 
    //Implementing getT() method
 
    @Override
    public T getT()
    {
        return t;
    }
}
```

- A normal class can implement a generic interface if type parameter of generic interface is a wrapper class. For example, below implementation of GenericInterface is legal.

```java
interface GenericInterface<Integer>
{
       //Generic interface with Integer as type parameter
}
 
class NormalClass implements GenericInterface<Integer>
{
       //Normal class implementing generic interface
}
```

- Class implementing generic interface at least must have same number and same type of parameters and at most can have any number and any type of parameters.

```java
interface GenericInterface<T>
{
    //Generic interface with one type parameter
}
 
class GenericClass1<T> implements GenericInterface<T>
{
    //Class with same type parameter
}
 
class GenericClass2<T, V> implements GenericInterface<T>
{
    //Class with two type parameters
}
 
class GenericClass<T1, T2> implements GenericInterface<T>
{
    //Compile time error, class having different type of parameters
}
```

- You can change the type of parameter passed to generic interface while implementing it. When changed, the class which is implementing should have new type as parameter and also, you have to change old type with new type while implementing the methods.

```java
interface GenericInterface<T>
{
    void setT(T t);
 
    T getT();
}
 
//Changing the type of parameter passed to GenericInterface while implementing
 
class GenericClass<V> implements GenericInterface<V>
{
    V t;
 
    @Override
    public void setT(V t)    //Changing the type of parameter
    {
        this.t = t;
    }
 
    @Override
    public V getT()          //Changing the return type
    {
        return t;
    }
}
```

- Generic interface can have any number of type parameters. Class implementing generic interface at least must have  same type of parameters and at most can have any number of parameters

```java
interface GenericInterface<T1, T2, T3, T4>
{
    //Generic interface with 4 type parameters
}
 
class GenericClass1<T1, T2, T3, T4, T5> implements GenericInterface<T1, T2, T3, T4>
{
    //Generic class with 5 type parameters implementing generic interface with 4 type parameters
}
 
class GenericClass2<T1, T2, T3> implements GenericInterface<T1, T2, T3, T4>
{
    //Compile time error, must have same number of type parameters
}
 
class GenericClass3<T1, T2, T5, T6> implements GenericInterface<T1, T2, T3, T4>
{
    //Compile time error. must have same type of parameters
}
```

- Class can implement more than one generic interfaces. If implemented, class should have type parameters of both the interfaces.

```java
interface GenericInterface1<T1>
{
    //Generic interface with one type parameter
}
 
interface GenericInterface2<T2, T3>
{
    //Generic interface with two type parameters
}
 
class GenericClass<T1,T2, T3> implements GenericInterface1<T1>, GenericInterface2<T2, T3>
{
    //Class having parameters of both the interfaces
}
```

# Generics And Their Inheritance

You have to follow some rules while making a generic class as a super class or a sub class. Some of those rules we have already discussed while implementing generic interfaces as above. This post is an extend of that post.

In this post, We will discuss some very interesting points about generic classes and their inheritance.

- A generic class can extend a non-generic class.

```java
class NonGenericClass
{
     //Non Generic Class
}
 
class GenericClass<T> extends NonGenericClass
{
    //Generic class extending non-generic class
}
```

- Generic class can also extend another generic class. When generic class extends another generic class, sub class should have at least same type and same number of type parameters and at most can have any number and any type of parameters.

```java
class GenericSuperClass<T>
{
    //Generic super class with one type parameter
}
 
class GenericSubClass1<T> extends GenericSuperClass<T>
{
    //sub class with same type parameter
}
 
class GenericSubClass2<T, V> extends GenericSuperClass<T>
{
    //sub class with two type parameters
}
 
class GenericSubClass3<T1, T2> extends GenericSuperClass<T>
{
    //Compile time error, sub class having different type of parameters
}
```

-  When generic class extends another generic class, the type parameters are passed from sub class to super class same as in the case of constructor chaining where super class constructor is called by sub class constructor by passing required arguments. For example, in the below program  ‘T’ in ‘GenericSuperClass’ will be replaced by String.

```java
class GenericSuperClass<T>
{
    T t;
 
    public GenericSuperClass(T t)
    {
        this.t = t;
    }
}
 
class GenericSubClass<T> extends GenericSuperClass<T>
{
    public GenericSubClass(T t)
    {
        super(t);
    }
}
 
public class GenericsInJava
{
    public static void main(String[] args)
    {
        GenericSubClass<String> gen = new GenericSubClass<String>("I am string");
 
        System.out.println(gen.t);       //Output : I am string
    }
}
```

- A generic class can extend only one generic class and one or more generic interfaces. Then it’s type parameters should be union of type parameters of generic class and generic interface(s).

```java
class GenericSuperClass<T1>
{
    //Generic class with one type parameter
}
 
interface GenericInterface1<T1, T2>
{
    //Generic interface with two type parameters
}
 
interface GenericInterface2<T2, T3>
{
    //Generic interface with two type parameters
}
 
class GenericClass<T1,T2, T3> extends GenericSuperClass<T1> implements GenericInterface1<T1, T2>, GenericInterface2<T2, T3>
{
    //Class having parameters of both the interfaces and super class
}
```

- Non-generic class can’t extend generic class except of those generic classes which have already pre defined types as their type parameters.

```java
class GenericSuperClass<T>
{
    //Generic class with one type parameter
}
 
class NonGenericClass extends GenericSuperClass<T>
{
    //Compile time error, non-generic class can't extend generic class
}
 
class A
{
    //Pre defined class
}
 
class GenericSuperClass1<A>
{
    //Generic class with pre defined type 'A' as type parameter
}
 
class NonGenericClass1 extends GenericSuperClass1<A>
{
    //No compile time error, It is legal
}
```

- Non-generic class can extend generic class by removing the type parameters. i.e as a raw type. But, it gives a warning.

```java
class GenericClass<T>
{
    T t;
 
    public GenericClass(T t)
    {
        this.t = t;
    }
}
 
class NonGenericClass extends GenericClass       //Warning
{
    public NonGenericClass(String s)
    {
        super(s);           //Warning
    }
}
 
public class GenericsInJava
{
    public static void main(String[] args)
    {
        NonGenericClass nonGen = new NonGenericClass("I am String");
 
        System.out.println(nonGen.t);    //Output : I am String
    }
}
```

- While extending a generic class having bounded type parameter, type parameter must be replaced by either upper bound or it’s sub classes.

```java
class GenericSuperClass<T extends Number>
{
    //Generic super class with bounded type parameter
}
 
class GenericSubClass1 extends GenericSuperClass<Number>
{
    //type parameter replaced by upper bound
}
 
class GenericSubClass2 extends GenericSuperClass<Integer>
{
    //type parameter replaced by sub class of upper bound
}
 
class GenericSubClass3 extends GenericSuperClass<T extends Number>
{
    //Compile time error
}
```

- Generic methods of super class can be overrided in the sub class like normal methods.

```java
class GenericClass
{
    <T> void genericMethod(T t)
    {
        System.out.println(1);
    }
}
 
class NonGenericClass extends GenericClass
{
    @Override
    <T> void genericMethod(T t)
    {
            System.out.println(2);
    }
}
 
public class GenericsInJava
{
    public static void main(String[] args)
    {
        new GenericClass().genericMethod("I am String");       //Output : 1
 
        new NonGenericClass().genericMethod("I am String");    //Output : 2
    }
}
```