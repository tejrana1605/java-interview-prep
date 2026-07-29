# Type Parameters

The type parameters naming conventions are important to learn generics thoroughly. The common type parameters are as follows:

T - Type

E - Element

K - Key

N - Number

V - Value

## Generic Method

Like the generic class, we can create a generic method that can accept any type of arguments. Here, the scope of arguments is limited to the method where it is declared. It allows static as well as non-static methods.

Let's see a simple example of Java generic method to print array elements. We are using here E to denote the element.

```java
public class TestGenerics4{  
  
   public static < E > void printArray(E[] elements) {  
        for ( E element : elements){          
            System.out.println(element );  
         }  
         System.out.println();  
    }  
    public static void main( String args[] ) {  
        Integer[] intArray = { 10, 20, 30, 40, 50 };  
        Character[] charArray = { 'J', 'A', 'V', 'A', 'T','P','O','I','N','T' };  
  
        System.out.println( "Printing Integer Array" );  
        printArray( intArray  );   
  
       System.out.println( "Printing Character Array" );  
        printArray( charArray );   
    }   
}  
```

```java
Output

Printing Integer Array
10
20
30
40
50
Printing Character Array
J
A
V
A
T
P
O
I
N
T

```

## Wildcard in Java Generics

The ? (question mark) symbol represents the wildcard element. It means any type. If we write <? extends Number>, it means any child class of Number. For example, Integer, Float, and double. Now we can call the method of Number class through any child class object.

We can use a wildcard as a **type of a parameter, field, return type, or local variable. However, it is not allowed to use a wildcard as a type argument for a generic method invocation, a generic class instance creation, or a supertype.**

Let's understand it by the example given below:

```java
import java.util.*;    
// Abstract class representing a Shape with an abstract draw method  
abstract class Shape {    
    abstract void draw();    
}    
// Class representing a Rectangle, subclass of Shape  
class Rectangle extends Shape {    
    void draw() {  
        System.out.println("drawing rectangle");  
    }    
}    
// Class representing a Circle, subclass of Shape  
class Circle extends Shape {    
    void draw() {  
        System.out.println("drawing circle");  
    }    
}    
// Class containing a generic method to draw shapes  
class GenericTest {    
    // Generic method that accepts a list of any type that extends Shape  
    public static void drawShapes(List<? extends Shape> lists) {    
        // Loop through each Shape in the list and call its draw method  
        for (Shape s : lists) {    
            s.draw(); // Calling the draw method of the Shape class, which is implemented by the child class  
        }    
    }    
    public static void main(String args[]) {    
        // Creating a list of Rectangle objects  
        List<Rectangle> list1 = new ArrayList<Rectangle>();    
        list1.add(new Rectangle());    
        // Creating a list of Circle objects  
        List<Circle> list2 = new ArrayList<Circle>();    
        list2.add(new Circle());    
        list2.add(new Circle());    
        // Calling drawShapes method with the list of Rectangle objects  
        drawShapes(list1);    
        // Calling drawShapes method with the list of Circle objects  
        drawShapes(list2);    
    }    
}    

```

```java
Output

drawing rectangle
drawing circle
drawing circle
```

## Upper Bounded Wildcards

The purpose of upper bounded wildcards is to decrease the restrictions on a variable. It restricts the unknown type to be a specific type or a subtype of that type. It is used by declaring wildcard character ("?") followed by the extends (in case of, class) or implements (in case of, interface) keyword, followed by its upper bound.

```java

Syntax

List<? extends Number> 

```

Here,

? is a wildcard character.

**extends**, is a keyword.

**Number**, is a class present in java.lang package

Suppose, we want to write the method for the list of Number and its subtypes (like Integer, Double). Using **List<? extends Number>** is suitable for a list of type Number or any of its subclasses whereas **List< Number >** works with the list of type Number only. So, **List<? extends Number>** is less restrictive than **List< Number >**.

### Example of Upper Bound Wildcard

In this example, we are using the upper bound wildcards to write the method for List<Integer> and List<Double>.

```java
import java.util.ArrayList;  
  
public class UpperBoundWildcard {  
  
      
    private static Double add(ArrayList<? extends Number> num) {  
      
        double sum=0.0;  
          
        for(Number n:num)  
        {  
            sum = sum+n.doubleValue();  
        }  
          
        return sum;  
    }  
  
    public static void main(String[] args) {  
          
        ArrayList<Integer> l1=new ArrayList<Integer>();  
        l1.add(10);  
        l1.add(20);  
        System.out.println("displaying the sum= "+add(l1));  
          
        ArrayList<Double> l2=new ArrayList<Double>();  
        l2.add(30.0);  
        l2.add(40.0);  
        System.out.println("displaying the sum= "+add(l2));  
          
          
    }  
      
}  
```

```java
Output

displaying the sum= 30.0
displaying the sum= 70.0
```

## Unbounded Wildcards
The unbounded wildcard type represents the list of an unknown type such as List<?>. This approach can be useful in the following scenarios: -

- When the given method is implemented by using the functionality provided in the Object class.

- When the generic class contains the methods that don't depend on the type parameter.

### Example of Unbounded Wildcards

```java
import java.util.Arrays;  
import java.util.List;  
  
public class UnboundedWildcard {  
  
    public static void display(List<?> list)  
    {  
          
        for(Object o:list)  
        {  
            System.out.println(o);  
        }  
          
    }  
      
      
    public static void main(String[] args) {  
          
    List<Integer> l1=Arrays.asList(1,2,3);  
    System.out.println("displaying the Integer values");  
    display(l1);  
    List<String> l2=Arrays.asList("One","Two","Three");  
      System.out.println("displaying the String values");  
        display(l2);  
    }  
  
}  

```

```java
Output

displaying the Integer values
1
2
3
displaying the String values
One
Two
Three
```

## Lower Bounded Wildcards

The purpose of lower bounded wildcards is to restrict the unknown type to be a specific type or a supertype of that type. It is used by declaring wildcard character ("?") followed by the super keyword, followed by its lower bound.

```java
Syntax

List<? super Integer>  
```

Here,

? is a wildcard character.

**super**, is a keyword.

**Integer**, is a wrapper class.

Suppose, we want to write the method for the list of Integer and its supertype (like Number, Object). Using **List<? super Integer>** is suitable for a list of type Integer or any of its superclasses whereas **List< Integer >** works with the list of type Integer only. So, **List<? super Integer>** is less restrictive than **List< Integer >**.

### Example of Lower Bound Wildcard

In this example, we are using the lower bound wildcards to write the method for List< Integer > and List< Number >.

```java
import java.util.Arrays;  
import java.util.List;  
  
public class LowerBoundWildcard {  
  
    public static void addNumbers(List<? super Integer> list) {  
  
        for(Object n:list)  
        {  
              System.out.println(n);  
        }  
          
      
          
    }  
public static void main(String[] args) {  
      
    List<Integer> l1=Arrays.asList(1,2,3);  
      System.out.println("displaying the Integer values");  
    addNumbers(l1);  
      
    List<Number> l2=Arrays.asList(1.0,2.0,3.0);  
      System.out.println("displaying the Number values");  
    addNumbers(l2);  
}  
  
}  

```

```java
Output

displaying the Integer values
1
2
3
displaying the Number values
1.0
2.0
3.0
```

## Disadvantages of Java Generics

- **Type Erasure:** One of the fundamental limitations of Java Generics is type erasure. This design choice ensures backward compatibility with older versions of Java but introduces several issues:

- **No Runtime Type Information:** Because type information is erased at runtime, generic types cannot be used to obtain type-specific information. This limitation means you cannot directly check the type parameters of a generic instance at runtime using reflection.

```java
List<String> stringList = new ArrayList<>();  
if (stringList instanceof List<String>) { // Compile-time error  
    // This check is illegal due to type erasure  
}  
```

- **Type Casting and Type Safety:** Type erasure sometimes requires type casting, which can introduce ClassCastException at runtime if the type is not handled correctly.

```java
public <T> T getFirstElement(List<T> list) {  
    return (T) list.get(0); // Potential ClassCastException due to type erasure  
}
```

## Complexity and Learning Curve
Generics add a layer of complexity to the Java language, which can be challenging for developers to learn and use correctly:

**Syntax Complexity:** The syntax for generics can be complex and lengthy, especially when dealing with bounded type parameters, wildcards, and nested generic types. This complexity can make the code harder to read and understand, particularly for new developers.

```java
public <T extends Comparable<? super T>> void sort(List<T> list) {  
    // Method signature with bounded type parameters and wildcards  
} 
```

**Debugging Difficulty:** Debugging code that uses generics can be more challenging. Since type information is erased at runtime, the error messages related to type issues can be less informative and harder to trace back to the source.

**Advanced Features:** Features like bounded wildcards (<? extends T> and <? super T>), generic methods and generic constructors can be difficult to master and correctly apply in practical scenarios.

## Restrictions and Limitations
Generics come with several restrictions that can limit their flexibility and usability:

- **Cannot Use Primitive Types:** Java Generics do not support primitive types directly. You have to use wrapper classes like Integer and Double instead of int and double, which can lead to additional boxing and unboxing overhead.

```java
List<int> intList = new ArrayList<>(); // Compile-time error  
List<Integer> integerList = new ArrayList<>(); // Correct usage  
```