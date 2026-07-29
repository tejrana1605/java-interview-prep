# What Are Wildcard Arguments In Java?

Wildcard arguments means unknown type arguments. They just act as placeholder for real arguments to be passed while calling method. They are denoted by question mark (?). One important thing is that the types which are used to declare wildcard arguments must be generic types. Wildcard arguments are declared in three ways.

1) Wildcard Arguments With An Unknown Type

2) Wildcard Arguments with An Upper Bound

3) Wildcard Arguments with Lower Bound

## 1) Wildcard Arguments With An Unknown Type :

The syntax for declaring this type of wildcard arguments is,

```java
GenericType<?>
```

The arguments which are declared like this can hold any type of objects. For example, Collection<?> or ArrayList<?> can hold any type of objects like String, Integer, Double etc.

Look at the below code. The same processElements() method is used to process the ArrayList containing strings as well as integers.

```java
public class GenericsInJava
{
    static void processElements(ArrayList<?> a)
    {
        for (Object element : a)
        {
            System.out.println(element);
        }
    }
 
    public static void main(String[] args)
    {
        //ArrayList Containing Integers
 
        ArrayList<Integer> a1 = new ArrayList<>();
 
        a1.add(10);
 
        a1.add(20);
 
        a1.add(30);
 
        processElements(a1);
 
        //Arraylist containing strings
 
        ArrayList<String> a2 = new ArrayList<>();
 
        a2.add("One");
 
        a2.add("Two");
 
        a2.add("Three");
 
        processElements(a2);
    }
}

```

## 2)Wildcard Arguments With An Upper Bound :

In the above example, if you want the processElements() method to work with only numbers, then you can specify an upper bound for wildcard argument. To specify an upper bound for wildcards, use this syntax,

```java
GenericType<? extends SuperClass>
```

This specifies that a wildcard argument can contain ‘SuperClass’ type or it’s sub classes. Remember that extends clause is an inclusive bound. i.e ‘SuperClass’ also lies in the bound.

The above processElements() method can be modified to process only numbers like below,

```java
public class GenericsInJava
{
    static void processElements(ArrayList<? extends Number> a)
    {
        for (Object element : a)
        {
            System.out.println(element);
        }
    }
 
    public static void main(String[] args)
    {
        //ArrayList Containing Integers
 
        ArrayList<Integer> a1 = new ArrayList<>();
 
        a1.add(10);
 
        a1.add(20);
 
        a1.add(30);
 
        processElements(a1);
 
        //Arraylist containing Doubles
 
        ArrayList<Double> a2 = new ArrayList<>();
 
        a2.add(21.35);
 
        a2.add(56.47);
 
        a2.add(78.12);
 
        processElements(a2);
 
        //Arraylist containing Strings
 
        ArrayList<String> a3 = new ArrayList<>();
 
        a3.add("One");
 
        a3.add("Two");
 
        a3.add("Three");
 
        //This will not work
 
        processElements(a3);     //Compile time error
    }
}
```

3) Wildcard Arguments With Lower Bound :
You can also specify a lower bound for wildcard argument using super clause. Here is the syntax,

```java
GenericType<? super SubClass>
```
This means that a wildcard argument can contain ‘SubClass’ type or it’s super classes.

```java
public class GenericsInJava
{
    static void processElements(ArrayList<? super Integer> a)
    {
        for (Object element : a)
        {
            System.out.println(element);
        }
    }
 
    public static void main(String[] args)
    {
        //ArrayList Containing Integers
 
        ArrayList<Integer> a1 = new ArrayList<>();
 
        a1.add(10);
 
        a1.add(20);
 
        a1.add(30);
 
        processElements(a1);
 
        //Arraylist containing Doubles
 
        ArrayList<Double> a2 = new ArrayList<>();
 
        a2.add(21.35);
 
        a2.add(56.47);
 
        a2.add(78.12);
 
        //This will not work
 
        processElements(a2);     //Compile time error
    }
}
```

### Note : ‘super’ clause is used to specify the lower bound for only wildcard arguments. It does not work with bounded types.
