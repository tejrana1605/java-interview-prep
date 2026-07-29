# Defining Generic Class

In the previous post, we have seen why we need to use generics. Generics are used to check the type compatibility at the compile time and hence removing the chances of occuring ClassCastException at run time. In this particular post, we will see how to define our own generic class.

## Generic Class :
The syntax for defining generic class is as follows,

```java
class Class_Name<T1, T2, T3 ... Tn>
{
    //Generic Type or Parameterized type
}
```

Where T1, T2, T3 … Tn (T stands for Type) enclosed within angle brackets (<>) are called type parameters and class ‘Class_Name‘ is called generic type or parameterized type.

Now, let’s try to define one generic class based on the above format.

```java
class GenericClass<T>
{
    T t;
 
    public GenericClass(T t)
    {
        this.t = t;
    }
 
    public void setT(T t)
    {
        this.t = t;
    }
 
    public T getT()
    {
        return t;
    }
}
```

While creating an instance to the above generic class, you can pass any class type as a type parameter and that class type replaces generic ‘T’ for that object. For example, if you pass String type as a type parameter then String will be the type of variable ‘t’. If you pass Integer as type parameter than Integer will be the type of variable ‘t’.

In the other words, when you pass a type while creating an object to the generic class, that object works only with that type. For example, If you pass String type while creating an object to the above generic class then that object works only with String type. That means setT() method takes String type as an argument and getT() method returns String type. If you pass any other type to setT() method, it gives compile time error. Hence, strictly checking type casting during compilation.

```java
public class GenericsInJava
{
    public static void main(String[] args)
    {
        GenericClass<String> gen1 = new GenericClass<String>("It must be string");
 
        gen1.setT("Value Changed");        //Passing String to setT() method
 
        String s = gen1.getT();              //getT() method returning string
 
        gen1.setT(new Integer(123));      //Compile time error. You can't pass Integer type to setT() method now
 
        gen1.setT(new Double(23.56));    //Compile time error. You can't pass Double type to setT() method now
    }
}
```

If you create an object by using Integer type as a type parameter then that object works only with Integer type.

```java
public class GenericsInJava
{
    public static void main(String[] args)
    {
        GenericClass<Integer> gen1 = new GenericClass<Integer>(new Integer(123));
 
        gen1.setT(456);             //Passing Integer type to setT() method
 
        Integer I = gen1.getT();      //getT() method returning Integer type
 
        gen1.setT(new String("123"));      //Compile time error. You can't pass String type to setT() method now
 
        gen1.setT(new Double(23.56));    //Compile time error. You can't pass Double type to setT() method now
    }
}
```

## Generics Work Only With Derived Types :

While creating an instance of generic class, you must pass only derived types. You can’t pass primitive types. If you pass primitive type, it gives compile time error. i.e generics works only with derived type.

```java
public class GenericsInJava
{
    public static void main(String[] args)
    {
        GenericClass<int> gen1 = new GenericClass<int>(123);   //Error, can't use primitive type
 
        GenericClass<float> gen2 = new GenericClass<float>(23.56);  //Error, can't use primitive type
    }
}
```

## Objects Of Same Generic Class Differ Based On Their Type Parameters :

Objects of same generic class differ depending upon their type parameters. For example, object of above generic class created using String type is not compatible with an object of same class created using Integer type.

```java
public class GenericsInJava
{
    public static void main(String[] args)
    {
        GenericClass<String> gen1 = new GenericClass<String>("Value Of t");
 
        GenericClass<Integer> gen2 = new GenericClass<Integer>(new Integer(20));
 
        gen1 = gen2;        //Error : Type mismatch
 
        gen2 = gen1;        //Error : Type mismatch
    }
}
```

## Generic Class With Two Type Parameters :
Below is an example of a generic class with two type parameters.

```java
class GenericClass<T1, T2>
{
    T1 t1;
 
    T2 t2;
 
    public GenericClass(T1 t1, T2 t2)
    {
        this.t1 = t1;
 
        this.t2 = t2;
    }
 
    public void setT1(T1 t1)
    {
        this.t1 = t1;
    }
 
    public T1 getT1()
    {
        return t1;
    }
 
    public void setT2(T2 t2)
    {
        this.t2 = t2;
    }
 
    public T2 getT2()
    {
        return t2;
    }
}
 
public class GenericsInJava
{
    public static void main(String[] args)
    {
        GenericClass<String, Integer> gen1 = new GenericClass<String, Integer>("Value of t1", new Integer(123));
 
        GenericClass<Integer, String> gen2 = new GenericClass<Integer, String>(new Integer(123), "Value of t2");
 
        System.out.println(gen1.getT1());       //Output : Value of t1
 
        System.out.println(gen1.getT2());       //Output : 123
 
        System.out.println(gen2.getT1());       //Output : 123
 
        System.out.println(gen2.getT2());       //Output : Value of t2
    }
}
```

You can pass your own type while creating an instance to the generic class. Here is an example for that.

```java
class GenericClass<T>
{
    T t;
 
    public GenericClass(T t)
    {
        this.t = t;
    }
 
    public void setT(T t)
    {
        this.t = t;
    }
 
    public T getT()
    {
        return t;
    }
}
 
class A
{
    int i;
 
    public A(int i)
    {
        this.i = i;
    }
}
 
public class GenericsInJava
{
    public static void main(String[] args)
    {
        GenericClass<A> gen1 = new GenericClass<A>(new A(10));     //Passing A-type as type parameter
 
        GenericClass<A> gen2 = new GenericClass<A>(new A(20));     //Passing A-type as type parameter
 
        System.out.println(gen1.getT().i);    //Output : 10 
 
        System.out.println(gen2.getT().i);    //Output : 20
    }
}
```