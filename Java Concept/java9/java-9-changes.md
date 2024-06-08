# Java 9 Interface Private Methods

Before Java 8, interfaces in Java can have only constant variables and abstract methods. From Java 8 and onwards, interfaces are allowed to have two types of concrete methods – default and static methods. From Java 9, two more method types are introduced to interfaces. They are – private methods and private static methods. Let’s see the journey of Java interfaces from earlier versions of Java to Java 8 and Java 9.

## Interfaces : Before Java 8

Till Java 7, interfaces are allowed to have only constant variables and abstract methods. Concrete methods are not allowed in interfaces. The classes which implement interfaces need to provide implementations for the abstract methods of the interfaces.

```java
interface InterfaceBeforeJava8
{
    //Constant Variables
     
    int constantVariableOne = 10;
    int constantVariableTwo = 20;
     
    //Abstarct Methods
     
    void abstractMethodOne();
    void abstractMethodTwo();
}
```

By default, constant variables of interfaces are public, static and final and abstract methods are public and abstract.

## Interfaces : From Java 8 And Onwards

From Java 8, two types of concrete methods are allowed inside the interfaces. They are default and static methods.

```java
interface InterfaceFromJava8
{
    //Constant Variables
     
    int constantVariableOne = 10;
    int constantVariableTwo = 20;
         
    //Abstarct Methods
         
    void abstractMethodOne();
    void abstractMethodTwo();
     
    //Default Method
     
    default void defaultMethod()
    {
        System.out.println("I am default method");
    }
     
    //Static Method
     
    static void staticMethod()
    {
        System.out.println("I am static method");
    }
}
```

## Why default methods?

Default methods are introduced to add extra features to existing interfaces without disrupting their existing implementations. If there were no default methods, even if you are adding a single abstract method to an existing interface, all its existing implementations have to be updated with implementation of that method. This will be a headache if there are hundreds or thousands of implementing classes.

To overcome such overhead, default methods are introduced in interfaces from Java 8. Default methods provide default implementation for a particular method.

## Why static methods?

Java API developers have followed a pattern of supplying an extra utility class along with an interface. This utility class contains only static methods to perform some basic operations on given interface type objects.

For example, Collection and Collections. Collection is an interface and Collections is an utility class which contains only static methods which perform some basic operations on Collection types.

From Java 8, they have break this pattern by introducing static methods in interface itself. From Java 8, interface itself will have static methods to perform some basic operations on its types.

## Interfaces : From Java 9 And Onwards

From Java 9, two more type of concrete methods are allowed inside the interfaces. They are – private methods and private static methods.

```java
interface InterfaceFromJava9
{
    //Constant Variables
     
    int constantVariableOne = 10;
    int constantVariableTwo = 20;
         
    //Abstarct Methods
         
    void abstractMethodOne();
    void abstractMethodTwo();
     
    //Default Method
     
    default void defaultMethod()
    {
        System.out.println("I am default method!!!");
    }
     
    //Static Method
     
    static void staticMethod()
    {
        System.out.println("I am static method!!!");
    }
     
    //Private Method
     
    private void privatemethod()
    {
        System.out.println("I am private method!!!");
    }
     
    //Private Static Method
     
    private static void privateStaticMethod()
    {
        System.out.println("I am private static method!!!");
    }
}
```

Hence, from Java 9 onwards, interfaces can have 6 type of members. They are,

1. Constant Variables
2. Abstract Methods
3. Default Methods
4. Static Methods
5. Private Methods
6. Private Static Methods

## Why Private Methods?

1. Private methods enhance the code re-usability inside the interfaces. For example, if two or more methods have the common code to execute then put that code block in a private method and call it whenever you require.

2. Using private methods, you can have control over what to hide and what to expose to outside the interface. If you have a sensitive data and want to use inside the interface only, then private methods will be of great use.
The following table shows the differences between abstract class and interface after Java 9.

The following table shows the differences between abstract class and interface after Java 9.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2021/07/InterfaceVsAbstractClassJava9.png?ssl=1" alt="Collections Framework Class Hierarchy"/></a>

# Java 9 Immutable Collections : List.of(), Set.of() And Map.of()

Immutable collections are the collections which can not be modified once they are created. Java 9 has introduced some static factory methods to easily create immutable collections like List, Set and Map. Before Java 9, wrapper methods of Collections class are used to create, not immutable, but unmodifiable collections. In this post, we will see how unmodifiable collections are used to created before Java 9? how to create Java 9 immutable collections? difference between immutable vs unmodifiable collections and characteristics of Java 9 immutable collections.

## Before Java 9 : Creating Unmodifiable Collections

Before Java 9, Collections.unmodifiableXXX() methods are used to create unmodifiable collections. These methods just behave like wrapper methods which return unmodifiable view or read-only view of the original collection. i.e you can’t perform modifying operations like add, remove, replace, clear etc through the references returned by these wrapper methods. But, you can modify original collection if you have other references to it and those modifications will be reflected in the view returned by these methods.

For example, in the below program, unModifiableSportList is created from sportList through Collections.unmodifiableList(). unModifiableSportList just acts as a read-only view of the original sportList. You can’t add elements to unModifiableSportList. If you try to add, it will give UnsupportedOperationException. But, you can add elements to original sportList and those elements will be reflected in unModifiableSportList.

```java
import java.util.ArrayList;
import java.util.Collections;
import java.util.List;
 
public class Java9ImmutableCollections 
{
    public static void main(String[] args) 
    {
        List<String> sportList = new ArrayList<String>();
         
        sportList.add("Hockey");
        sportList.add("Cricket");
        sportList.add("Tennis");
         
        List<String> unModifiableSportList = Collections.unmodifiableList(sportList);
 
        System.out.println(sportList);    //Output : [Hockey, Cricket, Tennis]
         
        System.out.println(unModifiableSportList);    //Output : [Hockey, Cricket, Tennis]
         
        unModifiableSportList.add("Wrestling");     //It gives run-time error
         
        sportList.add("Kabaddi");      //It gives no error and will be reflected in unModifiableSportList
         
        System.out.println(sportList);    //Output : [Hockey, Cricket, Tennis, Kabaddi]
         
        System.out.println(unModifiableSportList);    //Output : [Hockey, Cricket, Tennis, Kabaddi]
         
    }
}
```

There are other wrapper methods available in Collections class to create unmodifiable collections like Collections.unmodifiableSet to create unmodifiable set and Collections.unmodifiableMap to create unmodifiable map.

## Java 9 Immutable Collections
From Java 9, static factory methods are introduced to create immutable collections.

### 1) Immutable List

Immutable List is created by calling List.of() method. This method has other overloaded forms to facilitate the creation of immutable list with desired number of elements. They are as follows.

```java
//Returns immutable list with zero element.
of()

//Returns immutable list with one element.
of(E e1)

//Returns immutable list with two elements.
of(E e1, E e2)

//Returns immutable list with three elements.
of(E e1, E e2, E e3)

//Returns immutable list with four elements.
of(E e1, E e2, E e3, E e4)

//Returns immutable list with five elements.
of(E e1, E e2, E e3, E e4, E e5)

//Returns immutable list with six elements.
of(E e1, E e2, E e3, E e4, E e5, E e6)

//Returns immutable list with seven elements.
of(E e1, E e2, E e3, E e4, E e5, E e6, E e7)

//Returns immutable list with eight elements.
of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8)

//Returns immutable list with nine elements.
of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9)

//Returns immutable list with ten elements.
of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9, E e10)

//Returns immutable list with arbitrary number of elements.
of(E… elements)
```

**Examples :**

```java
//Creating immutable list with three elements
List<String> immutableSportList = List.of("Hockey", "Cricket", "Tennis");
         
//Creating immutable list with five elements
List<String> immutableNameList = List.of("John", "Michy", "Renu", "Arnold", "Srini");
         
//Creating immutable list with seven elements
List<Integer> immutaleNumberList = List.of(1, 2, 3, 4, 5, 6, 7);
```

## 2) Immutable Set

Immutable set is created by invoking Set.of() method. This method also has several overloaded versions to create immutable set with desired number of elements.

```java
//Returns immutable set with zero element.
of()

//Returns immutable set with one element.
of(E e1)

//Returns immutable set with two elements.
of(E e1, E e2)

//Returns immutable set with three elements.
of(E e1, E e2, E e3)

//Returns immutable set with four elements.
of(E e1, E e2, E e3, E e4)

//Returns immutable set with five elements.
of(E e1, E e2, E e3, E e4, E e5)

//Returns immutable set with six elements.
of(E e1, E e2, E e3, E e4, E e5, E e6)

//Returns immutable set with seven elements.
of(E e1, E e2, E e3, E e4, E e5, E e6, E e7)

//Returns immutable set with eight elements.
of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8)

//Returns immutable set with nine elements.
of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9)

//Returns immutable set with ten elements.
of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9, E e10)

//Returns immutable set with arbitrary number of elements.
of(E… elements)
```

**Examples :**

```java
//Creating immutable set with four elements
Set<String> immuatbleCitySet = Set.of("Mumbai", "New York", "London", "Colombo");
         
//Creating immutable set with six elements
Set<Double> immutableNumberSet = Set.of(25.71, 14.23, 18.75, 91.45, 51.23, 35.46);
```

## 3) Immutable Map

Immutable map is created by calling either Map.of() or Map.ofEntries() in which Map.of() has several overloaded forms.

```java
//Returns immutable map with zero mapping.
of()

//Returns immutable map with one mapping.
of(K k1, V v1)

//Returns immutable map with two mappings.
of(K k1, V v1, K k2, V v2)

//Returns immutable map with three mappings.
of(K k1, V v1, K k2, V v2, K k3, V v3)

//Returns immutable map with four mappings.
of(K k1, V v1, K k2, V v2, K k3, V v3, K k4, V v4)

//Returns immutable map with five mappings.
of(K k1, V v1, K k2, V v2, K k3, V v3, K k4, V v4, K k5, V v5)

//Returns immutable map with six mappings.
of(K k1, V v1, K k2, V v2, K k3, V v3, K k4, V v4, K k5, V v5, K k6, V v6)

//Returns immutable map with seven mappings.
of(K k1, V v1, K k2, V v2, K k3, V v3, K k4, V v4, K k5, V v5, K k6, V v6, K k7, V v7)

//Returns immutable map with eight mappings.
of(K k1, V v1, K k2, V v2, K k3, V v3, K k4, V v4, K k5, V v5, K k6, V v6, K k7, V v7, K k8, V v8)

//Returns immutable map with nine mappings.
of(K k1, V v1, K k2, V v2, K k3, V v3, K k4, V v4, K k5, V v5, K k6, V v6, K k7, V v7, K k8, V v8, K k9, V v9)

//Returns immutable map with ten mappings.
of(K k1, V v1, K k2, V v2, K k3, V v3, K k4, V v4, K k5, V v5, K k6, V v6, K k7, V v7, K k8, V v8, K k9, V v9, K k10, V v10)

//Returns immutable map with arbitrary number of mappings.
ofEntries(Entry<K k, V v>… entries)
```

**Examples :**

```java
//Creating immutable map with five mappings
Map<Integer, String> immutableNameIdMap = Map.of(1, "John", 2, "Michy", 3, "Renu", 4, "Arnold", 5, "Srini");
         
//Creating immutable map with six mappings
Map<Integer, String> immutableCityCodeMap = Map.ofEntries(
  Map.entry(111, "Mumbai"), 
  Map.entry(222, "London"), 
  Map.entry(333, "Bangalore"), 
  Map.entry(444, "Colombo"), 
  Map.entry(555, "New York"),
  Map.entry(666, "Chennai")
);
```

Below table shows some of before and after Java 9 code snippets.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2021/09/Java9ImmutableCollections.png?ssl=1" alt="Collections Framework Class Hierarchy"/></a>

## Immutable Vs Unmodifiable :

Java 9 Immutable collections and unmodifiable collections returned by the Collections.unmodifiableXXX() wrapper methods are not the same. Unmodifiable collections are just the read-only views of the original collection. You can perform modifying operations on the original collection and those modifications will be reflected in the collections returned by these methods. But, immutable collections returned by Java 9 static factory methods are 100% immutable. You can’t modify them once they are created.

## Characteristics Of Java 9 Immutable Collections :

1. Modifying operations on immutable collections are not allowed. If you try to modify them, UnsupportedOperationException will be thrown.
2. Null elements are not allowed. They will give NullPointerException at run time.
3. Java 9 immutable collections are thread safe. You can use them in a multi threaded environment without synchronization.
4. Immutable collections returned by Java 9 static factory methods are space efficient. They consume less memory than the mutable collections.

## Where to use them?

You can consider using Java 9 immutable collections if you have lots of known values and those values never change throughout the execution and those values are retrieved frequently. In such scenarios, immutable collections give better performance than mutable collections.

# Java 9 Stream API Improvements : takeWhile(), dropWhile(), ofNullable() And iterate()

Streams in Java are introduced from Java 8. The operations which operate on streams are kept in java.util.stream.Stream interface. From Java 9, four new operations are added to this interface. They are – takeWhile(), dropWhile(), ofNullable() and iterate() methods in which takeWhile() and dropWhile() methods are default methods and ofNullable() and iterate() methods are static methods. Let’s take a look at Java 9 Stream API improvements.

## Java 9 Stream API Improvements :

Four new methods are introduced in java.util.stream.Stream interface from Java 9 to improve the working with streams. Below table shows all four methods with their description.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2021/09/Java9StreamAPIImprovements.png?ssl=1" alt="Collections Framework Class Hierarchy"/></a>

Let’s see these methods with some simple examples one by one.

### 1) takeWhile() :
<br>

syntax :

```java
default Stream<T> takeWhile​(Predicate<? super T> predicate)
```

takeWhile() is a default method, takes one Predicate as an argument and returns a Stream. This method is a short-circuiting intermediate operation.

If calling stream is ordered, then this method returns a stream containing first n elements of the calling stream which satisfy the given predicate. It immediately terminates the operation as soon as it sees an element which doesn’t satisfy the predicate and it doesn’t evaluate remaining elements even though there may be elements which satisfy the given predicate.

If the calling stream is unordered then this method returns all or some elements which satisfy the given predicate. In such conditions, behavior of this method becomes non-deterministic.

For example, in the below code snippet, [1, 10, 100, 1000, 10000, 1000, 100, 10, 1, 0, 10000] is the calling stream and i<5000 is the predicate then takeWhile() returns first 4 elements [1, 10, 100, 1000] which satisfy the given predicate. When it sees 10000 which doesn’t satisfy i<5000, it breaks the operation and doesn’t evaluate remaining elements even though there are elements which satisfy i<5000.

```java
IntStream.of(1, 10, 100, 1000, 10000, 1000, 100, 10, 1, 0, 10000)
.takeWhile(i -> i < 5000)
.forEach(System.out::println);
```

Output :

```java
1
10
100
1000
```

### 2) dropWhile()
<br>

Syntax :

```java
default Stream<T> dropWhile​(Predicate<? super T> predicate)
```

dropWhile() is also a default method, takes one Predicate as an argument and returns a Stream. It is also a short-circuiting intermediate operation.

This method is total opposite of takeWhile(). This method drops first n elements which satisfy the given predicate and returns remaining elements if the calling stream is ordered.

For example, if we apply dropWhile() in the above example, we get the output as follows.

```java
IntStream.of(1, 10, 100, 1000, 10000, 1000, 100, 10, 1, 0, 10000)
.dropWhile(i -> i < 5000)
.forEach(System.out::println);
```

Output :

```java
10000
1000
100
10
1
0
10000
```

If the calling stream is unordered, then this method returns remaining elements after dropping the elements which satisfy the given predicate. In such cases, the behavior of this method becomes unpredictable.

### 3) ofNullable()
<br>

Syntax :

```java
static Stream<T> ofNullable​(T t)
```

ofNullable() is a static method which takes one element as an argument and returns a Stream containing that single element if the passed element is non-null. If the passed element is null, it returns an empty Stream.

```java
long count = Stream.ofNullable(25).count();   //Non-null element
         
System.out.println(count);                  //Output : 1
         
count = Stream.ofNullable(null).count();    //Null element
         
System.out.println(count);                  //Output : 0
```

### 4) iterate()
<br>

Syntax :

```java
static Stream<T> iterate​(T seed, Predicate<? super T> hasNext, UnaryOperator<T> next)
```

iterate() method is already there in Stream interface from Java 8. But, Java 9 provides another version of iterate() method which takes an extra argument hasNext of type Predicate which decides when to terminate the operation.

iterate() method is also a static method.

```java
Stream.iterate(1, i -> i <= 100000, i -> i*10).forEach(System.out::println);
```

Output :

```java
1
10
100
1000
10000
100000
```

# Java 9 Try With Resources Improvements

Try with resources blocks are introduced from Java 7. In these blocks, resources used in try blocks are auto-closed. No need to close the resources explicitly. But, Java 7 try with resources has one drawback. It requires resources to be declared locally within try block. It doesn’t recognize resources declared outside the try block. That issue has been resolved in Java 9. In this post, we will see how the resources are closed before Java 7, how the resources are closed after the introduction of try with resources blocks from Java 7 and improvements made to try with resources in Java 9.

## How the resources are closed before Java 7?

Any resource (File or database connection or network connection etc…) needs to be released after they are used to avoid resource leaks and also make them available for others to use. Before Java 7, try with finally blocks are used to close the resources. As you know, finally blocks are executed irrespective of whether try block is successfully executed or not. This makes sure that resources are released after their usage in try block if you keep resources closing statements in finally block.

For example, in the below program, FileOutputStream fos is the resource which is used in try block to write into Resource.txt and closed in finally block.

```java
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
 
public class ResourcesHandlingBeforeJava7
{
    public static void main(String[] args) throws FileNotFoundException
    {
        FileOutputStream fos = new FileOutputStream("Resource.txt");
         
        try
        {
            //Using the resources
             
            fos.write("First Line".getBytes());
        } 
        catch (IOException e) 
        {
            e.printStackTrace();
        }
        finally
        {
            //Releasing the resources
             
            try
            {
                fos.close();
            } 
            catch (IOException e) 
            {
                e.printStackTrace();
            }
        }
    }
}
```

## How the resources are closed after Java 7?

With the introduction of try with resources in Java 7, closing the resources have become even easier. There is no need to explicitly close the resources as in the above example. Try with resources auto closes the resources used in try block.

The above program using Java 7 try-with resources can be written as follows.

```java
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
 
public class ResourcesHandlingAfterJava7 
{
    public static void main(String[] args) throws FileNotFoundException
    {
        FileOutputStream fos = new FileOutputStream("Resource.txt");
         
        try(FileOutputStream localFos = fos)     //OR  try(FileOutputStream fos = new FileOutputStream("Resource.txt"))
        {
            //Using the resources
             
            fos.write("First Line".getBytes());
        } 
        catch (IOException e) 
        {
            e.printStackTrace();
        }
         
        //No need to close the resources explicitly.
        //Resources are implicitly closed.
    }
}
```

Notice that resources used in try block are implicitly closed. There is no need to close them explicitly.

## Drawback of Java 7 Try-With-Resources :

One drawback of Java 7 try with resources is that resources need to be declared within () of try block or else need to assign reference of resource declared outside to local variable of try block as in the above example. It doesn’t recognize resources declared outside its body. This issue has been addressed in Java 9.

## Java 9 Try With Resources Improvements :

From Java 9, try with resources will recognize resources declared outside its body. You can pass the reference of resource declared outside directly to try block. There is no need to declare resources locally within try block.

From Java 9, try-with-resources can be written as follows.

```java
import java.io.FileNotFoundException;
import java.io.FileOutputStream;
import java.io.IOException;
 
public class Java9TryWithResourcesImprovements 
{
    public static void main(String[] args) throws FileNotFoundException
    {
        FileOutputStream fos = new FileOutputStream("Resource.txt");
         
        try(fos)     //No need to declare resources locally
        {
            //Using the resources
             
            fos.write("First Line".getBytes());
        } 
        catch (IOException e) 
        {
            e.printStackTrace();
        }
         
        //No need to close the resources explicitly.
        //Resources are implicitly closed
    }
}
```

Below table shows how resources can be handled before Java 7, after Java 7 and after Java 9.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2021/09/Java9TryWithResources.png?ssl=1" alt="Collections Framework Class Hierarchy"/></a>

<br>

# Java 9 Diamond Operator Improvements

Diamond operator is used to denote the enclosing type of a class. For example, List<String> denotes list of strings, Set<Integer> denotes set of integers etc… Empty diamond operator <> is introduced from Java 7 to implement automatic type inference feature in the code. Empty diamond operator removes the redundant code by leaving the generic type in the right side of the declaration statement and thus removing the verbosity in the code. Till Java 9, empty diamond operator is allowed to use with normal classes only. It is not allowed to use with anonymous inner classes. But, from Java 9, empty diamond operator can also be used with anonymous inner classes. In this post, we will see the Java 9 improvements regarding anonymous inner classes and diamond operator.

## Diamond Operator : Before Java 7

According to oracle docs, type inference is the compiler’s ability to check each method invocation and corresponding declaration statements to determine the type of the arguments. In simple terms, Java compiler checks the type on the left side of the declaration statement to determine the type on the right side of the statement. Before Java 7, you need to explicitly mention type on both side of the declaration statement.

For example, in the below code snippet, type is mentioned on both the side using <>.

```java
List<String> list = new ArrayList<String>();
Set<Integer> set = new HashSet<Integer>();
Map<Integer, String> map = new HashMap<Integer, String>();
```

and the same rule applies to anonymous inner classes also.

```java
abstract class Addition<T>
{
    abstract void add(T t1, T t2);
}
 
public class Java6DiamondOperator 
{
    public static void main(String[] args) 
    {
        //Before Java 7, you need to mention type on both side of the declaration statement
         
        Addition<Integer> integerAddition = new Addition<Integer>() {
            @Override
            void add(Integer t1, Integer t2)
            {
                System.out.println(t1+t2);
            }
        };
    }
}
```

## Diamond Operator : After Java 7

With the introduction of empty diamond operator <> from Java 7, you need not mention type on the right side of the declaration statement. You can leave empty inside the diamond operator. Java compiler automatically determines the type on the right side of the declaration statement.

For example, above declaration statements can be written as below from Java 7.

```java
List<String> list = new ArrayList<>();
Set<Integer> set = new HashSet<>();
Map<Integer, String> map = new HashMap<>();
```

But, that rule doesn’t apply to anonymous inner classes. Empty diamond operator can not be used with anonymous inner classes.

For example, the below code gives compile time error if you run it in Java 7 environment.

```java
abstract class Addition<T>
{
    abstract void add(T t1, T t2);
}
 
public class Java7DiamondOperator 
{
    public static void main(String[] args) 
    {
        //Compile time error
        //'<>' cannot be used with anonymous classes
         
        Addition<Integer> integerAddition = new Addition<>() {
            @Override
            void add(Integer t1, Integer t2)
            {
                System.out.println(t1+t2);
            }
        };
    }
}
```

This issue has been resolved from Java 9.

## Diamond Operator : From Java 9
From Java 9, you can use empty diamond operator <> for anonymous inner classes also. The above code doesn’t show any compile time errors if you execute it in Java 9 environment.

```java
abstract class Addition<T>
{
    abstract void add(T t1, T t2);
}
 
public class Java9DiamondOperator 
{
    public static void main(String[] args) 
    {
        //No error, from Java 9
         
        Addition<Integer> integerAddition = new Addition<>() {
            @Override
            void add(Integer t1, Integer t2)
            {
                System.out.println(t1+t2);
            }
        };
    }
}
```

Below table summarizes how to use diamond operator before Java 7, after Java 7 and after Java 9.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2021/09/Java9DiamondOperator.png?ssl=1" alt="Collections Framework Class Hierarchy"/></a>

<br>

# Java 9 @SafeVarargs Annotation Changes

@SafeVarargs annotation is introduced from Java 7 to suppress the warnings thrown by the methods or constructors which take varargs arguments. It tells the compiler that following method or constructor doesn’t perform any unsafe operations on varargs arguments. Till Java 9, SafeVarargs annotation is allowed to use with final and static methods and constructors which take varargs arguments. From Java 9, it can be applied to private methods also. In this post, we will see the Java 9 changes made to @SafeVarargs annotation.

## @SafeVarargs Annotation : Before Java 9

Varargs are introduced from Java 5. Varargs means a method or constructor can take arguments of variable length i.e any number of arguments. It is denoted by ... Varargs could cause heap pollution if not used properly. That’s why compiler shows unsafe operation warning message for a method or a constructor which is having varargs arguments. To suppress those warning messages, @SafeVarargs is introduced from Java 7.

@SafeVarargs annotation tells the compiler that the following method or constructor doesn’t perform any unsafe operations on its varargs arguments. This annotation is meant to be used for constructors and methods which can not be overridden. As final and static methods can not be overridden, @SafeVarargs is allowed to use with them.

### Java 7 @SafeVarargs Annotation : Constructor Example

```java
public class Java7SafeVarargs 
{
    List<Integer>[] lists;
     
    @SafeVarargs   //If you don't use @SafeVarargs here, compiler shows warning : Potential heap pollution via varargs parameter lists
    public Java7SafeVarargs(List<Integer>...lists) 
    {
        this.lists = lists;
    }
}
```

### Java 7 @SafeVarargs Annotation : Final Method Example

```java
public class Java7SafeVarargs 
{
    @SafeVarargs    //If you don't use @SafeVarargs here, compiler shows warning : Potential heap pollution via varargs parameter lists
    final void finalMethod(List<Integer>...lists)
    {
        for (List<Integer> list : lists) 
        {
            System.out.println(list);
        }
    }
}
```

### Java 7 @SafeVarargs Annotation : Static Method Example

```java
public class Java7SafeVarargs 
{
    @SafeVarargs    //If you don't use @SafeVarargs here, compiler shows warning : Potential heap pollution via varargs parameter lists
    static void staticMethod(List<Integer>...lists)
    {
        for (List<Integer> list : lists) 
        {
            System.out.println(list);
        }
    }
}
```

### Java 7 @SafeVarargs Annotation : Static And Final Method Example

```java
public class Java7SafeVarargs 
{
    @SafeVarargs    //If you don't use @SafeVarargs here, compiler shows warning : Potential heap pollution via varargs parameter lists
    static final void staticFinalMethod(List<Integer>...lists)
    {
        for (List<Integer> list : lists) 
        {
            System.out.println(list);
        }
    }
}
```

### @SafeVarargs Annotation : After Java 9

As private methods also can not be overridden, @SafeVarargs is allowed to use with private methods also from Java 9. Below is an example how to use @SafeVarargs with private method.

```java
public class Java9SafeVarargs 
{
    //You can use @SafeVarargs for private methods also from Java 9
     
    @SafeVarargs   //If you don't use @SafeVarargs here, compiler shows warning : Potential heap pollution via varargs parameter lists
    private void privateMethod(List<Integer>...lists)
    {
        for (List<Integer> list : lists) 
        {
            System.out.println(list);
        }
    }
}
```

If you run the above code in Java 7 environment, compiler will throw an error : @SafeVarargs annotation cannot be applied to non-final instance method.

Below table shows where you can use @SafeVarargs annotation after Java 7 and after Java 9.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2021/10/Java9SafeVarargs.png?ssl=1" alt="Collections Framework Class Hierarchy"/></a>

<br>

# Java 9 Underscore Changes

From Java 9, underscore (_) is reserved as a keyword. That means, you can’t use underscore as an identifier from Java 9. In the earlier versions of Java, you can use _ as an identifier except Java 8 where compiler shows just the warning that ‘_’ should not be used as an identifier, since it is a reserved keyword from source level 1.8 on. From Java 9, it will be a compile time error if you use ‘_’ as an identifier. Let’s see underscore changes from earlier versions of Java to Java 8 and Java 9.

## Before Java 8 : Underscore (_)

Before Java 8, if you use underscore as an identifier, compiler doesn’t show any warnings or errors. You can use _ as an identifier in your code without any problem.

For example,

```java
public class Java7UnderscoreExample 
{
    public static void main(String[] args) 
    {
        String _ = "Underscore";
         
        System.out.println(_);
    }
}
```

if you run above code in the earlier versions of Java (before Java 8) output will be as follows.

**Output :**

```java
Underscore
```

## After Java 8 : Underscore (_)

If you run the above code in Java 8 environment, output will be the same but compiler shows warning that ‘_’ should not be used as an identifier, since it is a reserved keyword from source level 1.8 on.

```java
public class Java8UnderscoreExample 
{
    public static void main(String[] args) 
    {
        String _ = "Underscore";
         
        System.out.println(_);
    }
}
```

**Output :**

```java
Underscore

Warning : ‘_’ should not be used as an identifier, since it is a reserved keyword from source level 1.8 on
```

## After Java 9 : Underscore (_)

But from Java 9, it will be a compile time error if you use ‘_’ as an identifier.

If you run above program in Java 9 environment, compiler will show error as ‘_’ is a keyword from source level 9 onwards, cannot be used as identifier.

```java
public class Java9UnderscoreExample 
{
    public static void main(String[] args) 
    {
        String _ = "Underscore";
         
        System.out.println(_);
    }
}
```

Output :

```java
Error : ‘_’ is a keyword from source level 9 onwards, cannot be used as identifier.
```

Below table shows how you can use _ in a variable name before Java 8, after Java 8 and after Java 9.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2021/11/Java9UnderscoreChanges.png?ssl=1" alt="Collections Framework Class Hierarchy"/></a>

<br>

# Java 9 Optional Class Improvements

Optional class is introduced in Java 8 to avoid the null checks and NullPointerException. Before Java 8, if-constructs are used to check the null values. But, it is not an ideal way to check for null value as it doesn’t solve NullPointerException but it just hides it and propagates it to the next level. Therefore, inspired by other functional programming languages, Optional class is introduced in Java to handle the null values from Java 8.

## Java 9 Optional Class Improvements :

of(), empty(), ofNullable(), get(), ifPresent(), isPresent(), orElse(), orElseGet(), orElseThrow(), map(), flatMap() and filter() are the methods of Java 8 Optional class. Three more methods are added to Optional class from Java 9. They are – ifPresentOrElse(), or() and stream(). Let’s see these methods in detail.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2022/02/Java9OptionalClassMethods.png?ssl=1" alt="Collections Framework Class Hierarchy"/></a>

### ifPresentOrElse() Method :

This method performs the given action if the value is present in the Optional object. If the value is absent, performs the given empty-based action.

You can use this method when you want to perform different actions depending upon the presence and absence of a value.

```java
import java.util.Optional;
 
public class Java9OptionalImprovements 
{
    public static void main(String[] args) 
    {
        //Optional object with a value
         
        Optional<String> optionalAddress_1 = Optional.of("Address_1");
         
        optionalAddress_1.ifPresentOrElse(address -> System.out.println("Address : "+address), () -> System.out.println("No Address"));
         
        //Optional object without a value
         
        Optional<String> optionalAddress_2 = Optional.empty();
         
        optionalAddress_2.ifPresentOrElse(address -> System.out.println("Address : "+address), () -> System.out.println("No Address"));
    }
}
```

Output :

```java
Address : Address_1
No Address
```

### or() Method :

This method returns an Optional object containing the value if the value is present in the given Optional object. If the value is not present, it returns an Optional produced by the supplying function.

This method is similar to orElse() and orElseGet() which return unwrapped value where as this method returns the value wrapped in another Optional.

```java
import java.util.Optional;
 
public class Java9OptionalImprovements 
{
    public static void main(String[] args) 
    {
        //Optional object with a value
         
        Optional<String> optionalAddress_1 = Optional.of("Address_1");
         
        Optional<String> optional = optionalAddress_1.or(() -> Optional.of("No Address"));
         
        System.out.println(optional.get());
         
        //Optional object without a value
         
        Optional<String> optionalAddress_2 = Optional.empty();
         
        optional = optionalAddress_2.or(() -> Optional.of("No Address"));
         
        System.out.println(optional.get());
    }
}
```

Output :

```java
Address_1
No Address
```

### stream() Method :

This method returns a stream containing the value if the value is present in the given Optional object. If the value is not present, it returns an empty stream.

This method converts Optional into Stream and enables the developers to use all operations of Stream API with an Optional object also.

```java
import java.util.Optional;
 
public class Java9OptionalImprovements 
{
    public static void main(String[] args) 
    {
        //Optional object with a value
         
        Optional<String> optionalAddress_1 = Optional.of("Address_1");
         
        optionalAddress_1.stream().forEach(System.out::println);
         
        //Optional object without a value
         
        Optional<String> optionalAddress_2 = Optional.empty();
         
        optionalAddress_2.stream().forEach(System.out::println);
    }
}
```

Output :

```java
Address_1
```

<br>

# Java 9 JShell – REPL Tool

Java 9 JShell is a REPL tool i.e Read Eval Print Loop tool through that you can evaluate Java code snippet or any business logic without compiling and running the whole Java program. Such tool is already there in other languages like Scala and Python. From Java 9, Java also supports REPL tool called JShell. Let’s see how to use Java 9 Jshell to evaluate Java code.

# Why JShell?

JShell gives Java developer an oppurtunity to evaluate the business logic or any small piece of Java code like statements or expressions or methods or class definitions without compiling and running the whole Java program.

Creating a Java program involves 4 steps – typing, saving, compiling and running. You have to follow these steps until you get desired output.

Using JShell, one can quickly evaluate the business logic or any statement or any expression or any method definition or any class definition without following the above steps.

For example, to see the output of 2+3 expression, you have to write a Java program like below.

```java
public class ExpressionDemo 
{
    public static void main(String[] args) 
    {
        System.out.println(2+3);
    }
}
```

But, in JShell, you just have to type 2+3 to see its output.

```java
jshell> 2+3
$1 ==> 5
| created scratch variable $1 : int
```

JShell is not an alternative to your IDE or code editor. It is just a tool to test your code before actually writing it in an IDE or in an editor. Let’s see Java 9 JShell in detail.

# How To Start JShell?

To start JShell, you must have installed Java 9 in your PC. It is not available in the earlier versions of Java. To start JShell, path must be set to bin folder of the JDK 9 installation directory. If path is not set, navigate to that folder in the command prompt and type jshell. You can also set path only for current window using set path command. More about how to set path.

Open command prompt and type jshell. To open JShell in verbose mode use -v option.

```java
C:\Users\HP>set path=”C:\Program Files\Java\jdk-9.0.4\bin”;

C:\Users\HP>jshell -v
| Welcome to JShell — Version 9.0.4
| For an introduction type: /help intro
```

## How To Write Statements In JShell?

Statements in JShell are written normally as we do in any editor or in any IDE. But, semicolon(;) at the end of the statement is optional. i.e statements without semicolon at the end run normally.

```java
jshell> System.out.println(“Hello Java”);
Hello Java

jshell> System.out.println(“Hello Java”)
Hello Java
```

## How To Declare Variables In JShell?

You can declare variables of any type like int, float, long, double, String normally as we do in regular Java programs.

```java
jshell> int a=11;
a ==> 11
| created variable a : int

jshell> long l
l ==> 0
| created variable l : long

jshell> double d=1.1
d ==> 1.1
| created variable d : double

jshell> float f;
f ==> 0.0
| created variable f : float
```

## What are scratch variables in JShell?

In JShell, you can declare variables without names. These are called scratch variables. JShell implicitly gives names to such variables and they usually starts with $.

```java
jshell> 111
$6 ==> 111
| created scratch variable $6 : int

jshell> 11.11
$7 ==> 11.11
| created scratch variable $7 : double

jshell> “Hi, I am JShell”
$8 ==> “Hi, I am JShell”
| created scratch variable $8 : String
```

## How To Define Methods In JShell?

Below code snippet shows how to define methods in JShell and also shows how to call them, how to print their result and how to assign their result to a variable.

```java
jshell> int add(int a, int b)
…> {
…> return a+b;
…> }
| created method add(int,int)

jshell> add(10, 20);
$10 ==> 30
| created scratch variable $10 : int

jshell> System.out.println(add(100, 200));
300

jshell> int i = add(11, 22);
i ==> 33
| created variable i : int
```

## How To Define Classes In JShell?

Below code snippet shows how to define a class in JShell, how to instantiate it and how to call its methods.

```java
jshell> class MathsOps
…> {
…> static int add(int a, int b)
…> {
…> return a+b;
…> }
…> int multiply(int a, int b)
…> {
…> return a*b;
…> }
…> }
| created class MathsOps

jshell> MathsOps.add(50, 70);
$2 ==> 120
| created scratch variable $2 : int

jshell> new MathsOps().multiply(20, 30);
$3 ==> 600
| created scratch variable $3 : int

jshell> MathsOps mOps = new MathsOps();
mOps ==> MathsOps@1e397ed7
| created variable mOps : MathsOps

jshell> mOps.multiply(10, 10);
$5 ==> 100
| created scratch variable $5 : int
```

## How To Modify Variable, Method And Class in JShell?
'
You can modify definition of a variable or a method or a class in JShell. Just enter a new definition, old definition will be overwritten. (You can use /edit command to edit in JShell edit pad).

```java
jshell> int add(int a, int b)
…> {
…> return a+b;
…> }
| created method add(int,int)

jshell> int add(int a, int b)
…> {
…> return a+b+10;
…> }
| modified method add(int,int)
| update overwrote method add(int,int)

jshell> class Person
…> {
…> String firstName;
…> String lastName;
…> String getFirstName()
…> {
…> return firstName;
…> }
…> String getLastName()
…> {
…> return lastName;
…> }
…> }
| created class Person

jshell> class Person
…> {
…> int ID;
…> String firstName;
…> String lastName;
…> String getDetails()
…> {
…> return “ID : “+ID+”First Name : “+firstName+”Last Name : “+lastName;
…> }
…> }
| replaced class Person
| update overwrote class Person

jshell> String welcomeNote = “Hi…”;
welcomeNote ==> “Hi…”
| created variable welcomeNote : String

jshell> welcomeNote = “Hi…I am JShell. You can use me to test your Java code”
welcomeNote ==> “Hi…I am JShell. You can use me to test your Java code”
| assigned to welcomeNote : String

jshell> int salary;
salary ==> 0
| created variable salary : int

jshell> double salary;
salary ==> 0.0
| replaced variable salary : double
| update overwrote variable salary : int
```

## Java 9 JShell Commands :

Below is the list of all JShell Commands with their brief description.

### 1) /list

This command displays all the variables, methods, classes or any other sources you have typed.

```java
jshell> /list
1 : int i=10;
2 : long l;
3 : double d = 1.1;
4 : float f;
5 : String s = “Hi…I am JShell”;
6 : int add(int a, int b)
{
return a+b;
}
7 : class Person
{
int ID;
String firstName;
String lastName;
String getDetails()
{
return “ID : “+ID+”First Name : “+firstName+”Last Name : “+lastName;
}
}

jshell> /list -all
s1 : import java.io.; s2 : import java.math.;
s3 : import java.net.; s4 : import java.nio.file.;
s5 : import java.util.; s6 : import java.util.concurrent.;
s7 : import java.util.function.; s8 : import java.util.prefs.;
s9 : import java.util.regex.; s10 : import java.util.stream.;
1 : int i=10;
2 : long l;
3 : double d = 1.1;
4 : float f;
5 : String s = “Hi…I am JShell”;
6 : int add(int a, int b)
{
return a+b;
}
7 : class Person
{
int ID;
String firstName;
String lastName;
String getDetails()
{
return “ID : “+ID+”First Name : “+firstName+”Last Name : “+lastName;
}
}

jshell> /list -start
s1 : import java.io.; s2 : import java.math.;
s3 : import java.net.; s4 : import java.nio.file.;
s5 : import java.util.; s6 : import java.util.concurrent.;
s7 : import java.util.function.; s8 : import java.util.prefs.;
s9 : import java.util.regex.; s10 : import java.util.stream.;
s10 : import java.util.stream.*;
```

### 2) /edit

This command is used to edit a source you have typed in an JShell edit pad.

```java
jshell> /edit add
| modified method add(int,int)
| update overwrote method add(int,int)
```

### 3) /drop

This command is used to delete a varaiable or a method or a class.

```java
jshell> /drop add
| dropped method add(int,int)

jshell> /drop s
| dropped variable s
```

### 4) /save

This command saves the sources you have typed in JShell to a file.

```java
jshell> /save -all C:\Users\HP\JshellDemo.txt
```

### 5) /open

Using this command, you can open a file as a source in JShell.

```java
jshell> /open C:\Users\HP\inputFile.txt
```

### 6) /vars

This command lists all the declared variables.

```java
jshell> /vars
| long l = 0
| double d = 1.1
| float f = 0.0
| String s = “Hi…I am JShell”
| int i = 999

jshell> /vars -all
| int i = (not-active)
| long l = (not-active)
| double d = (not-active)
| float f = (not-active)
| String s = (not-active)
| int i = (not-active)
| int i = (not-active)
| long l = 0
| double d = 1.1
| float f = 0.0
| String s = “Hi…I am JShell”
| int i = 999
```

### 7) /methods

It lists all the declared methods with their signatures.

```java
jshell> /methods
| int add(int,int)
```

### 8) /types

This command lists all the declared types.

```java
jshell> /types
| class Person
| class MathsOps
```

### 9) /imports

It lists all imported classes and libraries.

```java
jshell> /imports
| import java.io.*
| import java.math.*
| import java.net.*
| import java.nio.file.*
| import java.util.*
| import java.util.concurrent.*
| import java.util.function.*
| import java.util.prefs.*
| import java.util.regex.*
| import java.util.stream.*
```

### 10) /history

It lists whatever you have typed in this session in JShell.

### 11) /reset

This command is used to reset JShell.

### 12) /reload

This command restarts and restores the JShell.

### 13) /set

This command is used to configure JShell like mode, editor, format etc.

### 14) /help

This command gives all information about JShell.

### 15) /exit

This command is used to exit JShell.

### <Tab> For Auto-Complete Suggestions :
You can use <Tab> key for auto-complete suggestions. For example, if you type / and press <Tab>, JShell gives list of all commands.

```java
jshell> /
/!    /?    /drop  /edit  /env  /exit
/help  /history  /imports  /list  /methods  /open
/reload  /reset  /save  /set  /types  /vars

<press tab again to see synopsis>

jshell> /
```

<br>

# 3 Creating Immutable Lists, Sets, and Maps - Oracle Doc

Convenience static factory methods on the List, Set, and Map interfaces, which were added in JDK 9, let you easily create immutable lists, sets, and maps.

An object is considered immutable if its state cannot change after it is constructed. After you create an immutable instance of a collection, it holds the same data as long as a reference to it exists.

If the collections created using these methods contain immutable objects, then they are automatically thread safe after construction. Because the structures do not need to support mutation, they can be made much more space efficient. Immutable collection instances generally consume much less memory than their mutable counterparts.

As discussed in About Immutability, an immutable collection can contain mutable objects, and if it does, the collection is neither immutable nor thread safe.

## Use Cases

The common use case for the immutable methods is a collection that is initialized from known values, and that never changes. Also consider using these methods if your data changes infrequently.

For optimal performance, the immutable collections store a data set that never changes. However, you may be able to take advantage of the performance and space-saving benefits even if your data is subject to change. These collections may provide better performance than the mutable collections, even if your data changes occasionally.

If you have a large number of values, you may consider storing them in a HashMap. If you are constantly adding and removing entries, then this is a good choice. But, if you have a set of values that never change, or rarely change, and you read from that set a lot, then the immutable Map is a more efficient choice. If the data set is read frequently, and the values change only rarely, then you may find that the overall speed is faster, even when you include the performance impact of destroying and rebuilding an immutable Map when a value changes.

## Syntax

The API for these new collections is simple, especially for small numbers of elements.

### Topics

* Immutable List Static Factory Methods

* Immutable Set Static Factory Methods

* Immutable Map Static Factory Methods

## Immutable List Static Factory Methods

The List.of static factory methods provide a convenient way to create immutable lists.

A list is an ordered collection, where duplicate elements are typically allowed. Null values are not allowed.

The syntax of these methods is:

```java
List.of()
List.of(e1)
List.of(e1, e2)         // fixed-argument form overloads up to 10 elements
List.of(elements...)   // varargs form supports an arbitrary number of elements or an array
```

**Example 3-1 Examples**

In JDK 8:

```java
List<String> stringList = Arrays.asList("a", "b", "c");
stringList = Collections.unmodifiableList(stringList);
```

In JDK 9:

```java
List stringList = List.of("a", "b", "c");
```

## Immutable Set Static Factory Methods

The Set.of static factory methods provide a convenient way to create immutable sets.

A set is a collection that does not contain duplicate elements. If a duplicate entry is detected, then an IllegalArgumentException is thrown. Null values are not allowed.

The syntax of these methods is:

```java
Set.of()
Set.of(e1)
Set.of(e1, e2)         // fixed-argument form overloads up to 10 elements
Set.of(elements...)   // varargs form supports an arbitrary number of elements or an array
```

**Example 3-2 Examples**

In JDK 8:

```java
Set<String> stringSet = new HashSet<>(Arrays.asList("a", "b", "c"));
stringSet = Collections.unmodifiableSet(stringSet);
```

In JDK 9:

```java
Set<String> stringSet = Set.of("a", "b", "c");
```

## Immutable Map Static Factory Methods

The Map.of and Map.ofEntries static factory methods provide a convenient way to create immutable maps.

A Map cannot contain duplicate keys; each key can map to at most one value. If a duplicate key is detected, then an IllegalArgumentException is thrown. Null values cannot be used as Map keys or values.

The syntax of these methods is:

```java
Map.of()
Map.of(k1, v1)
Map.of(k1, v1, k2, v2)    // fixed-argument form overloads up to 10 key-value pairs
Map.ofEntries(entry(k1, v1), entry(k2, v2),...)
 // varargs form supports an arbitrary number of Entry objects or an array
```

**Example 3-3 Examples**

In JDK 8:

```java
Map<String, Integer> stringMap = new HashMap<String, Integer>(); 
stringMap.put("a", 1); 
stringMap.put("b", 2);
stringMap.put("c", 3);
stringMap = Collections.unmodifiableMap(stringMap);
```

In JDK 9:

```java
Map stringMap = Map.of("a", 1, "b", 2, "c", 3);
```

**Example 3-4 Map with Arbitrary Number of Pairs**

If you have more than 10 key-value pairs, then create the map entries using the Map.entry method, and pass those objects to the Map.ofEntries method. For example:

```java
import static java.util.Map.entry;
Map <Integer, String> friendMap = Map.ofEntries(
   entry(1, "Tom"),
   entry(2, "Dick"),
   entry(3, "Harry"),
   ...
   entry(99, "Mathilde"));
```

## Randomized Iteration Order

The iteration order for Set elements and Map keys is randomized: it is likely to be different from one JVM run to the next. This is intentional — it makes it easier for you to identify code that depends on iteration order. Sometimes dependencies on iteration order inadvertently creep into code, and cause problems that are difficult to debug.

You can see how the iteration order is the same until jshell is restarted.

```java
jshell> Map stringMap = Map.of("a", 1, "b", 2, "c", 3);
stringMap ==> {b=2, c=3, a=1}

jshell> Map stringMap = Map.of("a", 1, "b", 2, "c", 3);
stringMap ==> {b=2, c=3, a=1}

jshell> /exit
|  Goodbye

C:\Program Files\Java\jdk-9\bin>jshell
|  Welcome to JShell -- Version 9-ea
|  For an introduction type: /help intro

jshell> Map stringMap = Map.of("a", 1, "b", 2, "c", 3);
stringMap ==> {a=1, b=2, c=3}
```

The collection instances created by the Set.of, Map.of, and Map.ofEntries methods are the only ones whose iteration orders are randomized. The iteration ordering of collection implementations such as HashMap and HashSet is unchanged.

## About Immutability

The collections returned by the convenience factory methods added in JDK 9 are conventionally immutable. Any attempt to add, set, or remove elements from these collections causes an UnsupportedOperationException to be thrown.

These collections are not "immutable persistent" or "functional" collections. If you are using one of those collections, then you can modify it, but when you do, you are returned a new updated collection that may share the structure of the first one.

One advantage of an immutable collection is that it is automatically thread safe. After you create a collection, you can hand it to multiple threads, and they will all see a consistent view.

However, an immutable collection of objects is not the same as a collection of immutable objects. If the contained elements are mutable, then this may cause the collection to behave inconsistently or make its contents to appear to change.

Let’s look at an example where an immutable collection contains mutable elements. Using jshell, create two lists of String objects using the ArrayList class, where the second list is a copy of the first. Trivial jshell output was removed.

```java
jshell> List<String> list1 = new ArrayList<>();
jshell> list1.add("a")
jshell> list1.add("b")
jshell> list1
list1 ==> [a, b]

jshell> List<String> list2 = new ArrayList<>(list1);
list2 ==> [a, b]
```

Next, using the List.of method, create ilist1 and ilist2 that point to the first lists. If you try to modify ilist1, then you see an exception error because ilist1 is immutable. Any modification attempt throws an exception.

```java
jshell> List<List<String>> ilist1 = List.of(list1, list1);
ilist1 ==> [[a, b], [a, b]]

jshell> List<List<String>> ilist2 = List.of(list2, list2);
ilist2 ==> [[a, b], [a, b]]

jshell> ilist1.add(new ArrayList<String>())
|  java.lang.UnsupportedOperationException thrown:
|        at ImmutableCollections.uoe (ImmutableCollections.java:70)
|        at ImmutableCollections$AbstractImmutableList.add (ImmutableCollections
.java:76)
|        at (#10:1)
```

But if you modify the original list1, ilist1 and ilist2 are no longer equal.

```java
jshell> list1.add("c")
jshell> list1
list1 ==> [a, b, c]
jshell> ilist1
ilist1 ==> [[a, b, c], [a, b, c]]

jshell> ilist2
ilist2 ==> [[a, b], [a, b]]

jshell> ilist1.equals(ilist2)
$14 ==> false
```

**Immutable and Unmodifiable Are Not the Same**

The immutable collections behave in the same way as the Collections.unmodifiable... wrappers. However, these collections are not wrappers — these are data structures implemented by classes where any attempt to modify the data causes an exception to be thrown.

If you create a List and pass it to the Collections.unmodifiableList method, then you get an unmodifiable view. The underlying list is still modifiable, and modifications to it are visible through the List that is returned, so it is not actually immutable.

To demonstrate this behavior, create a List and pass it to Collections.unmodifiableList. If you try to add to that List directly, then an exception is thrown.

```java
jshell> List<String> unmodlist1 = Collections.unmodifiableList(list1);
unmodlist1 ==> [a, b, c]

jshell> unmodlist1.add("d")
|  java.lang.UnsupportedOperationException thrown:
|        at Collections$UnmodifiableCollection.add (Collections.java:1056)
|        at (#17:1)
```

But, if you change the original list1, no error is generated, and the unmodlist1 list has been modified.

```java
jshell> list1.add("d")
$19 ==> true
jshell> list1
list1 ==> [a, b, c, d]

jshell> unmodlist1
unmodlist1 ==> [a, b, c, d]
```

## Space Efficiency
The collections returned by the convenience factory methods are more space efficient than their mutable equivalents.

All of the implementations of these collections are private classes hidden behind a static factory method. When it is called, the static factory method chooses the implementation class based on the size. The data may be stored in a compact field-based or array-based layout.

Let’s look at the heap space consumed by two alternative implementations. First, here’s an unmodifiable HashSet that contains two strings:

```java
Set<String> set = new HashSet<>(3);   // 3 buckets
set.add("silly");
set.add("string");
set = Collections.unmodifiableSet(set);
```

The set includes six objects: the unmodifiable wrapper; the HashSet, which contains a HashMap; the table of buckets (an array); and two Node instances (one for each element). On a typical VM, with a 12–byte header per object, the total overhead comes to 96 bytes + 28 * 2 = 152 bytes for the set. This is a large amount of overhead compared to the amount of data stored. Plus, access to the data unavoidably requires multiple method calls and pointer dereferences.
Instead, we can implement the set using Set.of:

```java
Set<String> set = Set.of("silly", "string");
```

Because this is a field-based implementation, the set contains one object and two fields. The overhead is 20 bytes. The new collections consume less heap space, both in terms of fixed overhead and on a per-element basis.

Not needing to support mutation also contributes to space savings. In addition, the locality of reference is improved, because there are fewer objects required to hold the data.

# The try-with-resources Statement - Oracle Doc

The try-with-resources statement is a try statement that declares one or more resources. A resource is an object that must be closed after the program is finished with it. The try-with-resources statement ensures that each resource is closed at the end of the statement. Any object that implements java.lang.AutoCloseable, which includes all objects which implement java.io.Closeable, can be used as a resource.

The following example reads the first line from a file. It uses an instance of FileReader and BufferedReader to read data from the file. FileReader and BufferedReader are resources that must be closed after the program is finished with it:

```java
static String readFirstLineFromFile(String path) throws IOException {
    try (FileReader fr = new FileReader(path);
          BufferedReader br = new BufferedReader(fr)) {
        return br.readLine();
    }
}	
```
In this example, the resources declared in the try-with-resources statement are a FileReader and a BufferedReader. The declaration statements of these resources appear within parentheses immediately after the try keyword. The classes FileReader and BufferedReader, in Java SE 7 and later, implement the interface java.lang.AutoCloseable. Because the FileReader and BufferedReader instances are declared in a try-with-resource statement, they will be closed regardless of whether the try statement completes normally or abruptly (as a result of the method BufferedReader.readLine throwing an IOException).

Prior to Java SE 7, you can use a finally block to ensure that a resource is closed regardless of whether the try statement completes normally or abruptly. The following example uses a finally block instead of a try-with-resources statement:

```java
static String readFirstLineFromFileWithFinallyBlock(String path) throws IOException {
   
    FileReader fr = new FileReader(path);
    BufferedReader br = new BufferedReader(fr);
    try {
        return br.readLine();
    } finally {
        br.close();
        fr.close();
    }
}
```

However, this example might have a resource leak. A program has to do more than rely on the garbage collector (GC) to reclaim a resource's memory when it's finished with it. The program must also release the resoure back to the operating system, typically by calling the resource's close method. However, if a program fails to do this before the GC reclaims the resource, then the information needed to release the resource is lost. The resource, which is still considered by the operaing system to be in use, has leaked.

In this example, if the readLine method throws an exception, and the statement br.close() in the finally block throws an exception, then the FileReader has leaked. Therefore, use a try-with-resources statement instead of a finally block to close your program's resources.

If the methods readLine and close both throw exceptions, then the method readFirstLineFromFileWithFinallyBlock throws the exception thrown from the finally block; the exception thrown from the try block is suppressed. In contrast, in the example readFirstLineFromFile, if exceptions are thrown from both the try block and the try-with-resources statement, then the method readFirstLineFromFile throws the exception thrown from the try block; the exception thrown from the try-with-resources block is suppressed. In Java SE 7 and later, you can retrieve suppressed exceptions; see the section Suppressed Exceptions for more information.

The following example retrieves the names of the files packaged in the zip file zipFileName and creates a text file that contains the names of these files:

```java
public static void writeToFileZipFileContents(String zipFileName, String outputFileName)throws java.io.IOException {

    java.nio.charset.Charset charset =
         java.nio.charset.StandardCharsets.US_ASCII;
    java.nio.file.Path outputFilePath =
         java.nio.file.Paths.get(outputFileName);

    // Open zip file and create output file with 
    // try-with-resources statement

    try (
        java.util.zip.ZipFile zf =
             new java.util.zip.ZipFile(zipFileName);
        java.io.BufferedWriter writer = 
            java.nio.file.Files.newBufferedWriter(outputFilePath, charset)
    ) {
        // Enumerate each entry
        for (java.util.Enumeration entries =
                                zf.entries(); entries.hasMoreElements();) {
            // Get the entry name and write it to the output file
            String newLine = System.getProperty("line.separator");
            String zipEntryName =
                 ((java.util.zip.ZipEntry)entries.nextElement()).getName() +
                 newLine;
            writer.write(zipEntryName, 0, zipEntryName.length());
        }
    }
}
```

In this example, the try-with-resources statement contains two declarations that are separated by a semicolon: ZipFile and BufferedWriter. When the block of code that directly follows it terminates, either normally or because of an exception, the close methods of the BufferedWriter and ZipFile objects are automatically called in this order. Note that the close methods of resources are called in the opposite order of their creation.

The following example uses a try-with-resources statement to automatically close a java.sql.Statement object:

```java
public static void viewTable(Connection con) throws SQLException {

    String query = "select COF_NAME, SUP_ID, PRICE, SALES, TOTAL from COFFEES";

    try (Statement stmt = con.createStatement()) {
        ResultSet rs = stmt.executeQuery(query);

        while (rs.next()) {
            String coffeeName = rs.getString("COF_NAME");
            int supplierID = rs.getInt("SUP_ID");
            float price = rs.getFloat("PRICE");
            int sales = rs.getInt("SALES");
            int total = rs.getInt("TOTAL");

            System.out.println(coffeeName + ", " + supplierID + ", " + 
                               price + ", " + sales + ", " + total);
        }
    } catch (SQLException e) {
        JDBCTutorialUtilities.printSQLException(e);
    }
}
```

The resource java.sql.Statement used in this example is part of the JDBC 4.1 and later API.

**Note**: A try-with-resources statement can have catch and finally blocks just like an ordinary try statement. In a try-with-resources statement, any catch or finally block is run after the resources declared have been closed.

## Suppressed Exceptions

An exception can be thrown from the block of code associated with the try-with-resources statement. In the example writeToFileZipFileContents, an exception can be thrown from the try block, and up to two exceptions can be thrown from the try-with-resources statement when it tries to close the ZipFile and BufferedWriter objects. If an exception is thrown from the try block and one or more exceptions are thrown from the try-with-resources statement, then those exceptions thrown from the try-with-resources statement are suppressed, and the exception thrown by the block is the one that is thrown by the writeToFileZipFileContents method. You can retrieve these suppressed exceptions by calling the Throwable.getSuppressed method from the exception thrown by the try block.

## Classes That Implement the AutoCloseable or Closeable Interface

See the Javadoc of the AutoCloseable and Closeable interfaces for a list of classes that implement either of these interfaces. The Closeable interface extends the AutoCloseable interface. The close method of the Closeable interface throws exceptions of type IOException while the close method of the AutoCloseable interface throws exceptions of type Exception. Consequently, subclasses of the AutoCloseable interface can override this behavior of the close method to throw specialized exceptions, such as IOException, or no exception at all.

<br>

# 6 Small Language Changes in Java SE 9 - Oracle Doc
There are several small language changes in Java SE 9.

## @SafeVarargs annotation is allowed on private instance methods.

The @SafeVarargs annotation can be applied only to methods that cannot be overridden. These include static methods, final instance methods, and, new in Java SE 9, private instance methods.

## You can use diamond syntax in conjunction with anonymous inner classes.

Types that can be written in a Java program, such as int or String, are called denotable types. The compiler-internal types that cannot be written in a Java program are called non-denotable types.

Non-denotable types can occur as the result of the inference used by the diamond operator. Because the inferred type using diamond with an anonymous class constructor could be outside of the set of types supported by the signature attribute in class files, using the diamond with anonymous classes was not allowed in Java SE 7.

In Java SE 9, as long as the inferred type is denotable, you can use the diamond operator when you create an anonymous inner class.

## The underscore character is not a legal name.

If you use the underscore character ("_") an identifier, your source code can no longer be compiled.

## Private interface methods are supported.

Private interface methods are supported. This support allows nonabstract methods of an interface to share code between them.

<br>

# Annotation Type SafeVarargs - Oracle Doc

```java
@Documented
@Retention(RUNTIME)
@Target({CONSTRUCTOR,METHOD})
public @interface SafeVarargs
```

A programmer assertion that the body of the annotated method or constructor does not perform potentially unsafe operations on its varargs parameter. Applying this annotation to a method or constructor suppresses unchecked warnings about a non-reifiable variable arity (vararg) type and suppresses unchecked warnings about parameterized array creation at call sites.

In addition to the usage restrictions imposed by its @Target meta-annotation, compilers are required to implement additional usage restrictions on this annotation type; it is a compile-time error if a method or constructor declaration is annotated with a @SafeVarargs annotation, and either:

* the declaration is a fixed arity method or constructor
* the declaration is a variable arity method that is neither static nor final nor private.

Compilers are encouraged to issue warnings when this annotation type is applied to a method or constructor declaration where:

* The variable arity parameter has a reifiable element type, which includes primitive types, Object, and String. (The unchecked warnings this annotation type suppresses already do not occur for a reifiable element type.)

* The body of the method or constructor declaration performs potentially unsafe operations, such as an assignment to an element of the variable arity parameter's array that generates an unchecked warning. Some unsafe operations do not trigger an unchecked warning. For example, the aliasing in

```java
@SafeVarargs // Not actually safe!
static void m(List<String>... stringLists) {
  Object[] array = stringLists;
  List<Integer> tmpList = Arrays.asList(42);
  array[0] = tmpList; // Semantically invalid, but compiles without warnings
  String s = stringLists[0].get(0); // Oh no, ClassCastException at runtime!
}
 ```
 
leads to a ClassCastException at runtime.
Future versions of the platform may mandate compiler errors for such unsafe operations.

<br>

# Introduction to JShell - Oracle Doc

The Java Shell tool (JShell) is an interactive tool for learning the Java programming language and prototyping Java code. JShell is a Read-Evaluate-Print Loop (REPL), which evaluates declarations, statements, and expressions as they are entered and immediately shows the results. The tool is run from the command line.


## Why Use JShell?

Using JShell, you can enter program elements one at a time, immediately see the result, and make adjustments as needed.

Java program development typically involves the following process:

* Write a complete program.

* Compile it and fix any errors.

* Run the program.

* Figure out what is wrong with it.

* Edit it.

* Repeat the process.

JShell helps you try out code and easily explore options as you develop your program. You can test individual statements, try out different variations of a method, and experiment with unfamiliar APIs within the JShell session. JShell doesn’t replace an IDE. As you develop your program, paste code into JShell to try it out, and then paste working code from JShell into your program editor or IDE.

## Starting and Stopping JShell

JShell is included in JDK 9. To start JShell, enter the jshell command on the command line.

JDK 9 must be installed on your system. If your path doesn’t include java-home/jdk-9/bin, start the tool from within that directory.

The following example shows the command and the response from JShell. Text that you enter is shown in bold:

```java
% jshell
|  Welcome to JShell -- Version 9
|  For an introduction type: /help intro

jshell>
```

The examples in this tutorial use the verbose mode. Verbose mode is recommended as you work through this tutorial so that what you see matches the examples. When you are more familiar with the tool, you might prefer to run in normal or a more concise mode.

To start JShell in verbose mode, use the -v option:

```java
% jshell -v
```

To exit JShell, enter /exit:

```java
jshell> /exit
|  Goodbye
```