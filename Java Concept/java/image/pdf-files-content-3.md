# Has a Relationship and dependency injection

![alt text](image-204.png)
![alt text](image-205.png)
![alt text](image-212.png)
![alt text](image-213.png)
![alt text](image-214.png)
![alt text](image-215.png)
![alt text](image-216.png)
![alt text](image-217.png)
![alt text](image-218.png)
![alt text](image-219.png)
![alt text](image-220.png)
![alt text](image-221.png)
![alt text](image-222.png)

# Advance Java Interview Questions

![alt text](image-223.png)
![alt text](image-224.png)
![alt text](image-225.png)
![alt text](image-226.png)
![alt text](image-227.png)
![alt text](image-228.png)
![alt text](image-229.png)
![alt text](image-230.png)
![alt text](image-231.png)
![alt text](image-232.png)
![alt text](image-233.png)
![alt text](image-234.png)

# Array Handwritten Notes

![alt text](image-235.png)
![alt text](image-236.png)
![alt text](image-237.png)
![alt text](image-238.png)
![alt text](image-239.png)
![alt text](image-240.png)
![alt text](image-241.png)
![alt text](image-242.png)
![alt text](image-243.png)
![alt text](image-244.png)
![alt text](image-245.png)
![alt text](image-246.png)
![alt text](image-247.png)
![alt text](image-248.png)
![alt text](image-249.png)
![alt text](image-250.png)
![alt text](image-251.png)
![alt text](image-252.png)
![alt text](image-253.png)
![alt text](image-254.png)
![alt text](image-255.png)
![alt text](image-256.png)
![alt text](image-257.png)
![alt text](image-258.png)

# Arrays in Java

An array is a collection of variables of the same type. When you need to store a list of values, such as numbers, you can store them in an array, instead of declaring separate variables for each number. To declare an array, you need to define the type of the elements with square brackets. For example, to declare an array of integers:

```java
int[ ] arr;
```

The name of the array is arr. The type of elements it will hold is int. Now, you need to define the array's capacity, or the number of elements it will hold. To accomplish this, use the keyword new

```java
int[ ] arr = new int[5];
```

The code above declares an array of 5 integers. In an array, the elements are ordered and each has a specific and constant position, which is called an index. 

To reference elements in an array, type the name of the array followed by the index position within a pair of square brackets. 

Example:

```java
arr[2] = 42;
```

This assigns a value of 42 to the element with 2 as its index.
Note that elements in the array are identified with zero-based index numbers, meaning that the first element's index is 0 rather than one. So, the maximum index of the array int[5] is 4.

Note that elements in the array are identified with zero-based index numbers, meaning that the first element's index is 0 rather than one. So, the maximum index of the array int[5] is 4.

## Initializing Arrays

Java provides a shortcut for instantiating arrays of primitive types and strings. If you already know what values to insert into the array, you can use an array literal. 

Example of an array literal:

```java
public class Program {
public static void main(String[] args) {
String[ ] myNames = { "A", "B", "C", "D"};
System.out.println(myNames[2]);
}
}

output:

C
```

Place the values in a comma-separated list, enclosed in curly braces. 

The code above automatically initializes an array containing 4 elements, and stores the provided values.
Sometimes you might see the square brackets placed after the array name, which also works, but the preferred way is to place the brackets after the array's data type.

### Problem

Your calendar program should output all the days of week, but it has errors. Change the code so that the program prints the days.

Notice that we use an array literal because we already know all the elements of the array we are going to create.

```java
public class Main
{
public static void main(String args[])
{
String[] days = {"Monday", "Tuesday", "Wednesday", "Thursday", "Friday", "Saturday", "Sunday"};
for (int i = 0; i < 7; i++)
{
System.out.println(days[i]);
}
}
}
```

```java
Output:

Monday
Tuesday
Wednesday
Thursday
Friday
Saturday
Sunday
```

### Array Length

You can access the length of an array (the number of elements it stores) via its length property. 

Example:

```java
public class Program {
public static void main(String[] args) {
int[ ] intArr = new int[5];
System.out.println(intArr.length);
}
}

Output:

5
```

Don't forget that in arrays, indexes start from 0. So, in the example above, the last index is 4.

Now that we know how to set and get array elements, we can calculate the sum of all elements in an array by using loops. The for loop is the most used loop when working with arrays, as we can use the length of the array to determine how many times to run the loop.

```java
public class Program {
public static void main(String[] args) {
int [ ] myArr = {6, 42, 3, 7};
int sum=0;
for(int x=0; x<myArr.length; x++) {
sum += myArr[x];
}
System.out.println(sum);
}
}

Output:

58
```

In the code above, we declared a variable sum to store the result and assigned it 0. Then we used a for loop to iterate through the array, and added each element's value to the variable.

The condition of the for loop is x<myArr.length, as the last element's index is myArr.length-1.

### Problem 

#### Summing Elements in Arrays

You are given a program that takes the length of the array as the first input, creates it, and then takes the next inputs as elements of the array. 

The program to go through the array and calculate the sum of the numbers that are multiples of 4. 

Sample Input 5 4 9 16 2 7 

Sample Output 20

To check if a number is a multiple of 4, use the modulo operator % to divide it by 4 and check the remainder.

```java
import java.util.Scanner;
public class Main {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
int length = scanner.nextInt();
int[] array = new int[length];
for (int i = 0; i < length; i++) {
array[i] = scanner.nextInt();
}
int sum = 0;
for (int x = 0; x<array.length; x++){
if (array[x]%4==0) {
sum += array[x];
}
}
System.out.println(sum);
}
}

```

```java
Input

5
4
9
16
2
7

Output

20
```

## Enhanced for Loop

The enhanced for loop (sometimes called a "for each" loop) is used to traverse elements in arrays. The advantages are that it eliminates the possibility of bugs and makes the code easier to read. 

Example:

Try it Yourself

```java
public class Program {
public static void main(String[] args) {
int[ ] primes = {2, 3, 5, 7};
for (int t: primes) {
System.out.println(t);
}
}
}


2
3
5
7
```

The enhanced for loop declares a variable of a type compatible with the elements of the array being accessed. The variable will be available within the for block, and its value will be the same as the current array element. 

So, on each iteration of the loop, the variable t will be equal to the corresponding element in the array.

Notice the colon after the variable in the syntax.

### Problem 

Your company is writing a program for a geometry course. The program takes the number of squares as the first input, creates an array, and then takes the sides of squares as its elements.

Write a program that receives a list of square sides and prints the area of those squares for the user.

Sample Input 2 3 4 

Output 9 16

Explanation In this example we have 2 squares (the first input) and their sides accordingly - 3 and 4 (the second and the third inputs). The area of the first square is 9 (3*3), the second one 16 (4*4).

The area of a square is a square of its edges.

```java
import java.util.Scanner;
public class Main {
public static void main(String[] args) {
Scanner scanner = new Scanner(System.in);
int length = scanner.nextInt();
int[] sides = new int[length];
for (int i = 0; i < length; i++) {
sides[i] = scanner.nextInt();
}
for (int t: sides){
int area = t * t;
System.out.println(area);
}
}
}

Input

3
2
3
5

Output

4
9
2
5
```

## Multidimensional Arrays

Multidimensional arrays are array that contain other arrays. The two-dimensional array is the most basic multidimensional array. To create multidimensional arrays, place each array within its own set of curly brackets. Example of a two-dimensional array:

```java
int[ ][ ] sample = { {1, 2, 3}, {4, 5, 6} };
```

This declares an array with two arrays as its elements. To access an element in the two-dimensional array, provide two indexes, one for the array, and another for the element inside that array. The following example accesses the first element in the second array of sample.

Try it Yourself

```java
public class Program {
public static void main(String[] args) {
int[ ][ ] sample = { {1, 2, 3}, {4, 5, 6} };
int x = sample[1][0];
System.out.println(x);
}
}

Output
4
```

The array's two indexes are called row index and column index.


You can get and set a multidimensional array's elements using the same pair of square brackets. 

Example:

Try it Yourself

```java
public class Program {
public static void main(String[] args) {
int[ ][ ] myArr = { {1, 2, 3}, {4}, {5, 6, 7} };
myArr[0][2] = 42;
int x = myArr[1][0];
System.out.println(x);
}
}

Output
4
```

The above two-dimensional array contains three arrays. The first array has three elements, the second has a single element and the last of these has three elements.

In Java, you're not limited to just two-dimensional arrays. Arrays can be nested within arrays to as many levels as your program needs. All you need to declare an array with more than two dimensions, is to add as many sets of empty brackets as you need. However, these are harder to maintain.
Remember, that all array members must be of the same type.

### Problem

#### Multidimensional Arrays

You are given a 3x3 matrix with numbers:

```java
int[][] matrix = { {8, 1, 6}, {3, 5, 7}, {4, 9, 0}, }
```

Output the numbers of the array, each on a new line.

Hint: You need to use two nested for loops to iterate over the array.

```java
public class Main {
public static void main(String[] args) {
//matrix
int[][] matrix = {
{8, 1, 6},
{3, 5, 7},
{4, 9, 0},
};
//task: display numbers in one column
for (int i=0; i<matrix.length; i++) {
for (int j=0; j<matrix.length; j++) {
System.out.println(matrix[i][j]);
}
}
}
}

result:
8
1
6
3
5
7
4
9
0
```

### Problem

#### Reverse a String

Write a program to take a string as input and output its reverse. The given code takes a string as input and converts it into a char array, which contains letters of the string as its elements. Sample 

Input: hello there Sample 

Output: ereht olleh

You can loop through the char array, starting from the end, using arr.length to get the size of the array.

```java
import java.util.*;
public class Program
{
public static void main(String[] args)
{
int vCount=0;//Vowel Couter variable
Scanner st= new Scanner(System.in);
String name = st.nextLine();
for(int x=name.length()-1;x>=0;x--)
{
System.out.print(name.charAt(x));
}
}
}

Input
this is some text

Output
txet emos si siht
```

# Binary Search in Java with code and implementation

```java
public class BinarySearch { 
    public static void main(String[] args) { 
        int[] array = {2, 4, 6, 8, 10, 12, 14, 16, 18, 20}; int target = 4; 
        int left = 0; 
        int right = array.length - 1; 
        int mid = 0; 
        boolean found = false; 
        while (left <= right) { 
            mid = (left + right) / 2; 
            if (array[mid] == target) { 
                found = true; 
                break; 
            } else if (array[mid] < target) {
                 left = mid + 1; 
            } else { 
                right = mid - 1; 
            } 
        } 
        
        if (found) { 
            System.out.println("Element found at index " + mid); 
        } else { 
            System.out.println("Element not found in the array."); 
        } 
    } 
}
```

## Explanation 

1. We define a class named BinarySearchExample. 

2. In the main() method, we declare and initialize an array called array with sorted values. 

3. We set the target variable to the element we want to find. 

4. We initialize the left variable to 0, representing the leftmost index of the search range. 

5. We initialize the right variable to array.length - 1, representing the rightmost index of the search range. 

6. We declare a mid variable to store the index of the middle element.

7. We initialize the found variable to false to keep track of whether the target element is found. 

8. We enter a while loop that continues as long as the left index is less than or equal to the right index. 

9. Inside the loop, we calculate the mid index as the average of the left and right indices. 

10. We compare the element at the mid index with the target element. If they are equal, we set found to true and break out of the loop. 

11. If the element at the mid index is less than the target, we update the left index to mid + 1 to search the right half of the array. 

12. If the element at the mid index is greater than the target, we update the right index to mid - 1 to search the left half of the array. 

13. After exiting the loop, we check the value of found. If it is true, we display a message indicating that the element was found at index mid. Otherwise, we display a message indicating that the element was not found in the array. 

In this example, the binary search algorithm efficiently searches for the target element by repeatedly dividing the search range in half until the element is found or the range becomes empty.

# Concurrency vs Parallelism

## Concurrency

Concurrency means more than onetask can appear to make progress over a unit of time. 

The key term over here is "APPEAR". 

Concurrency gives the illusion that the tasks are running at the sametime. In reality, the processor is switching between different tasks.

![alt text](image-259.png)

## Parallelism

Parallelism is when two or moretasks actually make progress at thesame time.

The key word is "ACTUALLY"

For parallelism, you need to havemore than one processor or a multi-core processor.

Multiple tasks can make progress atthe same exact time

![alt text](image-260.png)

## Combinations

In reality, tasks can beexecuted in several ways:

* Sequential

* Concurrent

* Parallel

* Parallel and Concurrent

## Scenario

Assume that you run a burgerjoint.

And John is the Chef.

Now, consider that you needJohn to prepare 10 burgers.

Think of them as 10 tasks

## Sequential

John prepares 1 burger at atime.

He starts with one burger,completes it and then startswith the next.

This is the Sequential approach

## Concurrently

Let's say preparing a burger is a multi-stepprocess.

Warm the bread, melt the cheese, cut theveggies, and assemble.

Also, assume there is a wait time while the breadis in the oven or the cheese is melting

John can start with 1st burger, then move to the2nd while the 1st is in waiting, and so on.

This is the concurrent approach.

## Parallel Execution

Let's say John is overwhelmed.

And therefore, you decide to bring in anotherchef, Mac.

Now John prepares 5 burgers one by one.

Mac also prepares 5 burgers one by one.

This is the parallel execution approach.

But notice John & Mac are not preparing burgers concurrently.

## Parallelism with Concurrency

As John & Mac prepare 5 burgers each...

...they realize they can prepare their set of burgers concurrently.

For example, when there is a wait time for one burger, they can work on the next one and so on.

Now, they are preparing burgers in a parallel manner as well as concurrently.

## Concurrency vs Parallelism

* Concurrency is about dealing with lotsof things at once.

* Parallelism is actually doing lots ofthings at once

* Application can be concurrent but notparallel.

* Application can also be parallel but notconcurrent

* All parallel executions need not beconcurrent

# Core Java Interview Question

## 7. What is a Class in Java? 

Class is defined as a template or a blueprint that is used to create objects and also to define objects and methods.

## 8. Define Object in Java? 

The instance of a class is called an object. Every object in Java has both state and behavior. The state of the object is stored in fields and the behavior of the objects is defined by methods.

## 11. Name the memory areas that are allocated by JVM and explain the class loader in JVM? 

There are totally five memory areas that are allocated by the JVM, and they are: 

• Class Area 

• Heap 

• Stack 

• Native Method Stack 

• PC Register

**ClassLoader**: class loader is a subschema of JVM which is used to load class files. Whenever we run Java programs, the data will be first loaded from the classloader. There are mainly three in-built classloaders in JVM, they are: 

• Application Classloader 

• Bootstrap Classloader 

• Extension Classloader

## 10. Define JVM? 

JVM is the abbreviation for Java Virtual Machine. It is a virtual machine that provides a runtime environment to write code. JVM is a part of JRE (Java Runtime Environment) and is used to convert the bytecode into machine-level language. This machine is responsible for allocating memory.

## 12. What is JDK? 

Java Development Kit is one of the three prominent technology packages used in Java programming. JDK is used as a standalone component to run the Java programs by JVM and JRE. This kit is used to implement Java platform specifications, including class libraries and compiler.

## 13. What do you mean by JRE? 

Java Runtime Environment (JRE) is a collection of software tools that are designed for the development of Java applications. This is a part of JDK, but it can be downloaded separately. JRE is mainly responsible for orchestrating the component activities.

## 14. What is the significant difference between JVM, JRE, and JDK? 

We can understand the difference between JVM, JDK, and JRE by the following diagram: 

• JVM: Java Virtual Machine is the main part of Java programming, which provides platform independence. JRE and JDK both contain JVM in order to run our Java programs. 

• JDK: This development kit is mainly used for developing programs. 

• JRE: Java Runtime Environment is mainly used for running Java programs.

## 15. Define the JIT compiler in Java? 

Just In Time Compiler is the component of JRE, which is used to compile the bytecodes of the particular method into the native machine code. This compiled code of the method is directly called by JVM without interpreting it

## 16. Define variables in Java and explain with example? 

Variables in Java can be defined as a basic storage unit of a program. It is a storage unit that holds the value during the program execution. Always the variable is assigned with a datatype.

## 17. What are the different types of variables in Java? 

There are mainly three different types of variables available in Java, and they are: 

• Static Variables

• Local Variables 
 
• Instance Variables 

**Static Variables**: A variable that is declared with the static keyword is called a static variable. A static variable cannot be a local variable, and the memory is allocated only once for these variables. 

**Local Variables**: A variable that is declared inside the body of the method within the class is called a local variable. A local variable cannot be declared using the static keyword. 

**Instance Variables**: The variable declared inside the class but outside the body of the method is called the instance variable. This variable cannot be declared as static and its value is instance-specific and cannot be shared among others.

## 18. What is Typecasting? 

Typecasting in Java is done explicitly by the programmer; this is done to convert one data type into another data type. 

Widening (automatically) - conversion of a smaller data type to a larger data type size. 

byte -> short -> char -> int -> long -> float -> double 

Narrowing (manually) - converting a larger type to a smaller size type 

double -> float -> long -> int -> char -> short -> byte

## 19. What is Type Conversion? 

Type conversion can be defined as converting one data type to another data type automatically by the compiler. 

There are two types of type conversions, and they are: 

• Implicit type conversion 

• Explicit type conversion.

## 20. What are the data types in Java? 

Datatypes in Java specify the values and sizes that can be stored in the variables. There are mainly two types of data types; they are: 

• Primitive Data Types 

• Non-primitive Data Types

## 21. What are primitive data types? 

Primitive data types in Java are the major constituents of data manipulation. These are the most basic data types that are available in Java. The primitive data types include int, char, byte, float, double, long, short, and boolean.

## 23. What are non-primitive data types? 

The non-primitive data types are something that is different from primitive data types, and these non-primitive data types include String, arrays, and structures.

## 24. Why char uses 2 bytes in Java and what is this ‘u0000’ notation called? 

This is only due to the reason that Java uses the Unicode system. The notation ‘u0000’ is the lowest range of the Unicode system, and it is the default value of the char data type.

## 26. What is the Unicode system? 

Unicode is a Universal International Standard Character Encoding which is an adequate resource for representing most of the languages written worldwide.

## 27. Why Java uses Unicode System? 

To overcome the problems present in the previous language standards, the Unicode system has been introduced. Java uses the Unicode system because the character default size provided by Unicode is 2 bytes and Java also needs only 2 bytes for the character.

## 28. What makes Java ‘Run Anywhere’ in nature?

It is because the Java compiler converts the code into byte code which is the main transitional language between machine code and source code. This byte code is not platform-dependent so that it can be compiled and executed on any platform.

## 30. What if we write public static void as static public void? 

Both the compilation and execution of the programs are done correctly because in Java specifiers order doesn’t matter.

## 31. Is there any default value for local variables? 

No, local variables are not initialized by any default values.

## 52. Describe in brief OOPs concepts? 

OOPs is an abbreviation for Object-Oriented Programming Language which entirely deals with an object. The main aim of OOPs is to implement real-world entities such as objects, classes, inheritance, polymorphism, and so on. Simula is considered the first object-oriented programming language. The most popular programming languages are Java, Python, PHP, C++, and many others. 

The following are the OOPs concepts that are included in Java: 

• Class 

• Object 

• Abstraction 

• Encapsulation 

• Inheritance 

• Polymorphism

## 53. What is Abstraction? 

In simple words, abstraction can be defined as hiding unnecessary data and showing or executing necessary data. In technical terms, abstraction can be defined as hiding internal processes and showing only the functionality.

## 54. Define encapsulation? 

Binding data and code together into a single unit are called encapsulation. The capsule is the best example of encapsulation.

## 55. What is Inheritance in Java?

When an object of child class has the ability to acquire the properties of a parent class then it is called inheritance. It is mainly used to acquire runtime polymorphism and also it provides code reusability.

## 56. What is Polymorphism in Java? 

Polymorphism in Java provides a way to perform one task in different possible ways. To achieve polymorphism in Java we use method overloading and method overriding. For example, the shape is the task and various possible ways in shapes are triangles, rectangle, circle, and so on.

## 57. What are the advantages of OOPs? 

The following are the advantages of OOPs, and they are: 

• OOPs provides data hiding 

• OOPs makes development and maintenance easier when compared to a procedural programming language. 

• OOPs has the ability to stimulate real-world entities more effectively.

## 59. What will be an initial value for an object reference that is defined as an instance variable?

All the object references in Java are initialized to null.

## 63. Define Constructor in Java? 

A constructor is a special type of method with a block of code to initialize the state of an object. A constructor is called only when the instance of the object is created. Every time in Java object is

## 64. What all the rules must be followed while creating a constructor in Java? 

The rules we need to follow while creating a constructor are:

• The constructor should have the same name as its class name. 

• There is no explicit return type for a constructor. 

• In Java, a constructor cannot be synchronized, abstract, final, and static.

## 65. What are the different types of constructors available in Java? 

There are two constructors in Java, and they are: 

• Default constructor 

• Parameterized constructor 

**Default constructor**: It is also called a no-argument constructor and it is mainly used to initialize the instance variable with the default value. Moreover, it is also used to perform some useful tasks on object creation. This default constructor is implicitly invoked by the compiler if there is no constructor for a particular class.

**Parameterized constructor**: A parameterized constructor is one type of constructor which is mainly used to initialize the instance variables with the given values. In simple words, the constructor that accepts arguments is called a parameterized constructor.

## 67. Does the constructor return any value? 

Yes, the constructor will return the current or present instance of the class.

## 68. Can the constructor be inherited? 

No, the constructor cannot be inherited.

## 69. Can the constructor be overloaded? 

Yes, It is possible to overload a constructor by changing the number of arguments for each constructor in a particular program or it is possible to overload a constructor by changing the parameter data types.

## 70. Can we declare a constructor as final? 

No, We can not declare the constructor as final, if we declare it as final compiler throws a “modified final not allowed” error.

## 71. Is there any Constructor class available in Java and what is its purpose of it? 

Yes, there is a class called Constructor class available in Java. The purpose of the Constructor class is to get the internal information of the constructor in the class. It is present in java.lang.reflect package.

## 72. What is the use of a copy constructor in Java? 

There is no copy constructor in Java, we can copy the values from one object to another same as that of a copy constructor in C++. In Java, there are many ways to copy the values of one object to another and they are: 

• By using Clone() of object class 

• By using constructor 

• By assigning the value of one object to another

## 73. Define the method in Java? 

In Java method is defined as a set of code that is represented by a name and can be invoked at any point in a program with the help of the method name. Each and every method in the program has its own name which is not the same as that of a class name.

## 75. What is the method signature in Java? 

In Java method signature is given the specified format followed by the method name, type, and order of its parameters. Exceptions are not considered as a part of the method signature.

## 76. What is the role of static keywords in Java? 

Keyword static in Java is mainly used for memory management and we can declare block, variable, method, and nested class as static.

## 78. What happens if we declare a method as static? 

If we declare a method as static, the following operations take place, and they are: 

• A static method can be invoked without creating an instance of the class. 

• Only a static method can access static data members and can change the value of a particular data member. 

• In most of the cases static method belongs to the class rather than the object of the class.

## 79. What are the cons observed if we declare a method as static in Java? 

The restrictions that we face if we declare a method as static are: 

• A static method cannot access non-static members and also cannot call the non-static method directly. 

• This and super keywords cannot be used in the context of the static method as they are non-static.

## 80. Why is the main method in Java is static? 

The main reason is that the object is not required to call for a static method so, if we declare the main method as non-static we need to create an object first and then call the main() method. In order to save memory, we declare the main method as static in Java.

## 81. Can we override the static method in Java? 

No, we can’t override the static method in Java.

## 82. What is a static block in Java? 

Static block in Java is mainly used to initialize the static data members. The specialty of the static block is that it is executed before the main method at the time of class loading.

## 83. Can we execute a program in Java without the main() method? 

Yes, we can execute the program in Java without the main method using a static block. It was possible only till JDK 1.6 and from JDK 1.7 it is not possible to execute the program without the main method in Java.

## 84. What happens if we remove the static modifier from the signature of the main() method?

The program will be compiled, but at runtime, it throws NoSuchMethodError error.

## 85. Can we declare a constructor using static? 

As we know that the static context is suitable for only class, variable, and method, not for the object. So the constructors are invoked only when an object is created, so there is no possibility to declare the constructor as static in Java.

## 86. Can we make abstract methods static in Java? 

No, if we declare abstract methods as static it becomes a part of the class, and we can directly call it which is not required. Calling an undefined method is unnecessary. Therefore declaring an abstract method as static is not allowed.

## 87. Can we declare static methods and variables in the abstract class? 

Yes, as we know that there is no need for an object to access the static block, therefore we can access static methods and variables declared inside the abstract class by using the abstract class name. Consider the following example.

## 88. Define this keyword in Java? 

The main use of this keyword is to refer to the current object in Java programming.

## 89. What is the usage of this keyword in Java? 

The following are the usage provided by this keyword in Java, and they are: 

• It is used to refer to the current class instance variable. 

• This is also used to invoke the current class constructor 

• It is used to invoke the current class method 

• It can be passed as an argument in the method call and in the constructor call

## 90. Can this keyword be used to refer to the current class instance variable?

Yes, this keyword is used to refer to the current class instance variable and it is also used to initiate or invoke the current class constructor.

## 91. Which class is the superclass for all the classes in Java? 

An object class is a superclass for all the classes in Java.

## 92. What is a singleton class in Java? 

Singleton class can be defined as the class that consists of only one single instance. In this class, all the methods and variables belong to only one instance. Singleton class is mainly used in a situation where we need to limit the objects for a class.

## 93. Why we use inheritance in Java? 

In Java, we use inheritance mainly for two uses, and they are: 

• For code reusability 

• For method overriding

## 96. Can the main() method in Java return any data? 

The main() method in Java doesn’t return any data because it is declared with a void return type.

## 99. Can we declare the main() method of our class as private? 

In Java, main() method must be always public static to run any application or program correctly. Suppose, if the main method is declared as private there will be no complications but it will give a runtime error.

## 100. Can a class in Java have multiple constructors? 

Yes, the classes present in Java can have multiple constructors with different parameters.

## 101. What is the method overloading in Java? 

If a class in Java has multiple numbers methods with the same name and different parameters, then it is called as method overloading. The main advantage of method overloading is that it increases the readability score of a program.

## 102. What are the different ways to overload a method? 

There are two different ways to overload a method, and they are: 

• By changing the data type 

• By changing the number of arguments

## 105. Why method overloading is not possible only by changing the return type of method only? 

Ambiguity is the main reason why method overloading is not possible by changing the return type of method only.

## 106. Can we overload main() method in Java? 

Yes, we can overload the main() method in Java by using method overloading but, JVM only calls the main() method that receives string array as arguments only.

## 107. What is method overriding in Java? 

If the subclass in the program has the same method as declared in superclass then it is known as method overriding.

## 108. What is the usage of method overriding in Java? 

Method overriding is used to achieve run-time polymorphism and also it is used to provide a specific implementation for a method that is already given by its subclass.

## 109. What are the rules we need to follow during method overriding? 

The rules are as follows: 

• The method must have the same parameters as present in the parent class. 

• There must be an IS-A relationship which is called inheritance. 

• The method should have the name same as that of the class name.

## 111. Can we override a static method? 

No, a static method cannot be overridden, it is because a static method is bounded with a class and an instance method is bounded with an object. So, the static belongs to the class area whereas, the instance method belongs to the heap area.

## 112. Can we override a main() method in Java? 

No, because the main() method is static.

## 113. What is the difference between aggregation and composition? 

Aggregation is built to represent the weak relationship whereas, the composition is built to represent the strong relationship.

## 114. Why does Java not support pointers? 

Pointer is a variable that mainly refers to the memory address. Java doesn’t support pointers because they are complex to understand and unsecured.

## 115. What is the super keyword in Java? 

Super keyword in Java is used to conjure immediate prompt parent class object. It is also called a reference variable.

## 116. What is the usage of super keywords in Java? 

The uses of the super keyword in Java are as follows: 

• Super can be used to conjure an immediate parent class method. 

• It is also used to indicate the immediate superclass instance variable.

• Super can be used to conjure an immediate parent class constructor. 

## 117. Can we have virtual functions in Java? 

Yes, all the functions in Java are virtual by default.

# Fail Fast and Fail safe iterator

## What are fail-fast and fail-safe iterators?

![alt text](image-261.png)
![alt text](image-262.png)
![alt text](image-263.png)
![alt text](image-264.png)
![alt text](image-265.png)
![alt text](image-266.png)

# Interview Question with Answers

![alt text](image-267.png)
![alt text](image-268.png)
![alt text](image-269.png)
![alt text](image-270.png)
![alt text](image-271.png)
![alt text](image-272.png)
![alt text](image-273.png)
![alt text](image-274.png)
![alt text](image-275.png)
![alt text](image-276.png)
![alt text](image-277.png)
![alt text](image-278.png)
![alt text](image-279.png)
![alt text](image-280.png)
![alt text](image-281.png)
![alt text](image-282.png)
![alt text](image-283.png)
![alt text](image-284.png)
![alt text](image-285.png)
![alt text](image-286.png)
![alt text](image-287.png)
![alt text](image-288.png)
![alt text](image-289.png)

# Interview Question

## 2.4 Can you access non static variable in static context ?

A static variable in Java belongs to its class and its value remains the same for all its instances. A static variable is initialized when the class is loaded by the JVM. If your code tries to access a non-static variable, without any instance, the compiler will complain, because those variables are not created yet and they are not associated with any instance.

## 2.7 What is a Constructor, Constructor Overloading in Java and Copy-Constructor

A constructor gets invoked when a new object is created. Every class has a constructor. In case the programmer does not provide a constructor for a class, the Java compiler (Javac) creates a default constructor for that class. The constructor overloading is similar to method overloading in Java. Different constructors can be created for a single class. Each constructor must have its own unique parameter list. Finally, Java does support copy constructors like C++, but the difference lies in the fact that Java doesn’t create a default copy constructor if you don’t write your own.

## 2.9 What is the difference between an Interface and an Abstract class ?

Java provides and supports the creation both of abstract classes and interfaces. Both implementations share some common characteristics, but they differ in the following features:

• All methods in an interface are implicitly abstract. On the other hand, an abstract class may contain both abstract and nonabstract methods.

• A class may implement a number of Interfaces, but can extend only one abstract class.

• In order for a class to implement an interface, it must implement all its declared methods. However, a class may not implement all declared methods of an abstract class. Though, in this case, the sub-class must also be declared as abstract.

• Abstract classes can implement interfaces without even providing the implementation of interface methods.

• Variables declared in a Java interface is by default final. An abstract class may contain non-final variables.

• Members of a Java interface are public by default. A member of an abstract class can either be private, protected or public.

• An interface is absolutely abstract and cannot be instantiated. An abstract class also cannot be instantiated, but can be invoked if it contains a main method.

## 2.10 What are pass by reference and pass by value ?

When an object is passed by value, this means that a copy of the object is passed. Thus, even if changes are made to that object, it doesn’t affect the original value. When an object is passed by reference, this means that the actual object is not passed, rather a reference of the object is passed. Thus, any changes made by the external method, are also reflected in all places.

## 3.2 Explain different ways of creating a thread. Which one would you prefer and why ?

There are three ways that can be used in order for a Thread to be created:

• A class may extend the Thread class.

• A class may implement the Runnable interface.

• An application can use the Executor framework, in order to create a thread pool.

The Runnable interface is preferred, as it does not require an object to inherit the Thread class. In case your application design requires multiple inheritance, only interfaces can help you. Also, the thread pool is very efficient and can be implemented and used very easily.

## 3.3 Explain the available thread states in a high-level.

During its execution, a thread can reside in one of the following states:

• Runnable: A thread becomes ready to run, but does not necessarily start running immediately.

• Running: The processor is actively executing the thread code.

• Waiting: A thread is in a blocked state waiting for some external processing to finish.

• Sleeping: The thread is forced to sleep.

• Blocked on I/O: Waiting for an I/O operation to complete.

• Blocked on Synchronization: Waiting to acquire a lock.

• Dead: The thread has finished its execution.

## 3.4 What is the difference between a synchronized method and a synchronized block ?

In Java programming, each object has a lock. A thread can acquire the lock for an object by using the synchronized keyword.

The synchronized keyword can be applied in a method level (coarse grained lock) or block level of code (fine grained lock).

## 3.5 How does thread synchronization occurs inside a monitor ? What levels of synchronization can you apply ?

The JVM uses locks in conjunction with monitors. A monitor is basically a guardian that watches over a sequence of synchronized code and ensuring that only one thread at a time executes a synchronized piece of code. Each monitor is associated with an object reference. The thread is not allowed to execute the code until it obtains the lock.

## 3.6 What’s a deadlock ?

A condition that occurs when two processes are waiting for each other to complete, before proceeding. The result is that both processes wait endlessly.

## 3.7 How do you ensure that N threads can access N resources without deadlock ?

A very simple way to avoid deadlock while using N threads is to impose an ordering on the locks and force each thread to follow that ordering. Thus, if all threads lock and unlock the mutexes in the same order, no deadlocks can arise.

## 4.2 Why Collection doesn’t extend Cloneable and Serializable interfaces ?

The Collection interface specifies groups of objects known as elements. Each concrete implementation of a Collection can choose its own way of how to maintain and order its elements. Some collections allow duplicate keys, while some other collections don’t. The semantics and the implications of either cloning or serialization come into play when dealing with actual implementations. Thus, the concrete implementations of collections should decide how they can be cloned or serialized.

## 4.3 What is an Iterator ?

The Iterator interface provides a number of methods that are able to iterate over any Collection. Each Java Collection contains the iterator method that returns an Iterator instance. Iterators are capable of removing elements from the underlying collection during the iteration.

## 4.4 What differences exist between Iterator and ListIterator ?

The differences of these elements are listed below:

• An Iterator can be used to traverse the Set and List collections, while the ListIterator can be used to iterate only over Lists.

• The Iterator can traverse a collection only in forward direction, while the ListIterator can traverse a List in both directions.

• The ListIterator implements the Iterator interface and contains extra functionality, such as adding an element, replacing an element, getting the index position for previous and next elements, etc.

## 4.5 What is difference between fail-fast and fail-safe ?

The Iterator’s fail-safe property works with the clone of the underlying collection and thus, it is not affected by any modification in the collection. All the collection classes in java.util package are fail-fast, while the collection classes in java.util.concurrent are fail-safe. Fail-fast iterators throw a ConcurrentModificationException, while fail-safe iterator never throws such an exception.

## 4.7 What is the importance of hashCode() and equals() methods ?

In Java, a HashMap uses the hashCode and equals methods to determine the index of the key-value pair and to detect duplicates. More specifically, the hashCode method is used in order to determine where the specified key will be stored. Since different keys may produce the same hash value, the equals method is used, in order to determine whether the specified key actually exists in the collection or not. Therefore, the implementation of both methods is crucial to the accuracy and efficiency of the HashMap.

## 4.8 What differences exist between HashMap and Hashtable ?

Both the HashMap and Hashtable classes implement the Map interface and thus, have very similar characteristics. However, they differ in the following features:

• A HashMap allows the existence of null keys and values, while a Hashtable doesn’t allow neither null keys, nor null values.

• A Hashtable is synchronized, while a HashMap is not. Thus, HashMap is preferred in single-threaded environments, while a
Hashtable is suitable for multi-threaded environments.

• A HashMap provides its set of keys and a Java application can iterate over them. Thus, a HashMap is fail-fast. On the other hand, a Hashtable provides an Enumeration of its keys.

• The Hashtable class is considered to be a legacy class.

## 4.9 What is difference between Array and ArrayList ? When will you use Array over ArrayList ?

The Array and ArrayList classes differ on the following features:

• Arrays can contain primitive or objects, while an ArrayList can contain only objects.

• Arrays have fixed size, while an ArrayList is dynamic.

• An ArrayList provides more methods and features, such as addAll, removeAll, iterator, etc.

• For a list of primitive data types, the collections use autoboxing to reduce the coding effort. However, this approach makes them slower when working on fixed size primitive data types.

## 4.10 What is difference between ArrayList and LinkedList ?

Both the ArrayList and LinkedList classes implement the List interface, but they differ on the following features:

• An ArrayList is an index based data structure backed by an Array. It provides random access to its elements with a performance equal to O(1). On the other hand, a LinkedList stores its data as list of elements and every element is linked to its previous and next element. In this case, the search operation for an element has execution time equal to O(n).

• The Insertion, addition and removal operations of an element are faster in a LinkedList compared to an ArrayList, because there is no need of resizing an array or updating the index when an element is added in some arbitrary position inside the collection.

• A LinkedList consumes more memory than an ArrayList, because every node in a LinkedList stores two references, one for its previous element and one for its next element.

## 4.11 What is Comparable and Comparator interface ? List their differences.

Java provides the Comparable interface, which contains only one method, called compareTo. This method compares two objects, in order to impose an order between them. Specifically, it returns a negative integer, zero, or a positive integer to indicate that the input object is less than, equal or greater than the existing object. Java provides the Comparator interface, which contains two methods, called compare and equals. The first method compares its two input arguments and imposes an order between them. It returns a negative integer, zero, or a positive integer to indicate that the first argument is less than, equal to, or greater than the second. The second method requires an object as a parameter and aims to decide whether the input object is equal to the comparator. The method returns true, only if the specified object is also a comparator and it imposes the same ordering as the
comparator.

## 4.12 What is Java Priority Queue ?

The PriorityQueue is an unbounded queue, based on a priority heap and its elements are ordered in their natural order. At the time of its creation, we can provide a Comparator that is responsible for ordering the elements of the PriorityQueue. A PriorityQueue doesn’t allow null values, those objects that doesn’t provide natural ordering, or those objects that don’t have any comparator associated with them. Finally, the Java PriorityQueue is not thread-safe and it requires O(log(n)) time for its enqueing and dequeing operations.

## 4.13 What do you know about the big-O notation and can you give some examples with respect to different data structures ?

The Big-O notation simply describes how well an algorithm scales or performs in the worst case scenario as the number of elements in a data structure increases. The Big-O notation can also be used to describe other behavior such as memory consumption. Since the collection classes are actually data structures, we usually use the Big-O notation to chose the best implementation to use, based on time, memory and performance. Big-O notation can give a good indication about performance for large amounts of data.

## 4.14 What is the tradeoff between using an unordered array versus an ordered array ?

The major advantage of an ordered array is that the search times have time complexity of O(log n), compared to that of an unordered array, which is O (n). The disadvantage of an ordered array is that the insertion operation has a time complexity of O(n), because the elements with higher values must be moved to make room for the new element. Instead, the insertion operation for an unordered array takes constant time of O(1).

## 4.15 What are some of the best practices relating to the Java Collection framework?

• Choosing the right type of the collection to use, based on the application’s needs, is very crucial for its performance. For example if the size of the elements is fixed and know a priori, we shall use an Array, instead of an ArrayList.

• Some collection classes allow us to specify their initial capacity. Thus, if we have an estimation on the number of elements that will be stored, we can use it to avoid rehashing or resizing.

• Always use Generics for type-safety, readability, and robustness. Also, by using Generics you avoid the ClassCastException during runtime.

• Use immutable classes provided by the Java Development Kit (JDK) as a key in a Map, in order to avoid the implementation
of the hashCode and equals methods for our custom class.

• Program in terms of interface not implementation.

• Return zero-length collections or arrays as opposed to returning a null in case the underlying collection is actually empty.

## 4.16 What’s the difference between Enumeration and Iterator interfaces ?

Enumeration is twice as fast as compared to an Iterator and uses very less memory. However, the Iterator is much safer compared to Enumeration, because other threads are not able to modify the collection object that is currently traversed by the iterator. Also, Iteratorsallow the caller to remove elements from the underlying collection, something which is not possible with Enumerations.

## 4.17 What is the difference between HashSet and TreeSet ?

The HashSet is Implemented using a hash table and thus, its elements are not ordered. The add, remove, and contains methods of a HashSet have constant time complexity O(1). On the other hand, a TreeSet is implemented using a tree structure. The elements in a TreeSet are sorted, and thus, the add, remove, and contains methods have time complexity of O(logn).

# Garbage Collectors

## 5.1 What is the purpose of garbage collection in Java, and when is it used ?

The purpose of garbage collection is to identify and discard those objects that are no longer needed by the application, in order for the resources to be reclaimed and reused.

## 5.2 What does System.gc() and Runtime.gc() methods do ?

These methods can be used as a hint to the JVM, in order to start a garbage collection. However, this it is up to the Java Virtual Machine (JVM) to start the garbage collection immediately or later in time.

## 5.3 When is the finalize() called ? What is the purpose of finalization ?

The finalize method is called by the garbage collector, just before releasing the object’s memory. It is normally advised to release resources held by the object inside the finalize method.

## 5.4 If an object reference is set to null, will the Garbage Collector immediately free the memory held by that object ?

No, the object will be available for garbage collection in the next cycle of the garbage collector.

## 5.5 What is structure of Java Heap ? What is Perm Gen space in Heap ?

The JVM has a heap that is the runtime data area from which memory for all class instances and arrays is allocated. It is created at the JVM start-up. Heap memory for objects is reclaimed by an automatic memory management system which is known as a garbage collector. Heap memory consists of live and dead objects. Live objects are accessible by the application and will not be a subject of garbage collection. Dead objects are those which will never be accessible by the application, but have not been collected by the garbage collector yet. Such objects occupy the heap memory space until they are eventually collected by the garbage collector.

## 5.6 What is the difference between Serial and Throughput Garbage collector ?

The throughput garbage collector uses a parallel version of the young generation collector and is meant to be used with applications that have medium to large data sets. On the other hand, the serial collector is usually adequate for most small applications (those requiring heaps of up to approximately 100MB on modern processors).

## 5.7 When does an Object becomes eligible for Garbage collection in Java ?

A Java object is subject to garbage collection when it becomes unreachable to the program in which it is currently used.

## 5.8 Does Garbage collection occur in permanent generation space in JVM ?

Garbage Collection does occur in PermGen space and if PermGen space is full or cross a threshold, it can trigger a full garbage collection. If you look carefully at the output of the garbage collector, you will find that PermGen space is also garbage collected. This is the reason why correct sizing of PermGen space is important to avoid frequent full garbage collections. Also check our article Java 8: PermGen to Metaspace.

# 25 Important Opps Concept

## Q 14. What is method hiding?

Feature engineering involves transforming raw datainto meaningful features to improve modelperformance.

## Q 15. What is a constructor chaining?

Constructor chaining is the process of calling oneconstructor from another within the same class orbetween a superclass and a subclass.

It allows for code reuse and efficient initialization.

![alt text](image-290.png)

## Q 17. What is a shallow copy and a deep copy?

A shallow copy copies the references of objectscontained within an object, while a deep copycreates new instances of the objects contained.

A deep copy results in a completely independentcopy of the original object and its contained objects.

## Q 18. What is a virtual method?

A virtual method is a method declared in a base classthat can be overridden by its subclasses. The actualimplementation invoked is determined by theruntime type of the object, supporting polymorphism.

## Q 21. What is the SOLID principle?

## Q 23. How is encapsulation related to data hiding?

Encapsulation involves bundling data and methodstogether.

Data hiding is the practice of making the internaldata of an object inaccessible to the outside world,except through well-defined methods. Encapsulationhelps achieve data hiding.

## Q 24. What is the difference between compositionand inheritance?

Inheritance creates a relationship between asubclass and a superclass, allowing the subclass toinherit properties and methods.

Composition involves creating an object withinanother object to achieve complex behavior withoutthe tight coupling of inheritance.

## Q 12. What is composition?

Composition is a design principle where a classcontains objects of other classes as part of itsattributes.

It allows creating complex structures by combiningsimpler classes.

![alt text](image-291.png)

![alt text](image-292.png)

## What is the difference between structure and a class?

Structure default access type is public , but class access type is private. A structure is used for grouping data whereas class can be used for grouping data and methods. Structures are exclusively used for data and it doesn’t require strict validation , but classes are used to encapsulates and inherit data which requires strict validation.

## What is a copy constructor?

This is a special constructor for creating a new object as a copy of an existing object. There will be always only on copy constructor that can be either defined by the user or the system.

## What is dynamic or run time polymorphism?

Dynamic or Run time polymorphism is also known as method overriding in which call to an overridden function is resolved during run time, not at the compile time. 

It means having two or more methods with the same name,same signature but with different implementation.

## What is static and dynamic binding?

Binding is nothing but the association of a name with the class. Static binding is a binding in which name can be associated with the class during compilation time , and it is also called as early Binding.

Dynamic binding is a binding in which name can be associated with the class during execution time , and it is also called as Late Binding.

## Define a constructor?

Constructor is a method used to initialize the state of an object, and it gets invoked at the time of object creation. Rules forconstructor are:
Constructor Name should be same asclass name. Constructor must have no return type.

## Define Destructor?

Destructor is a method which is automatically called when the object ismade ofscope or destroyed. Destructor name is also same asclass name but with the tilde symbol before the name.

## What is Inline function?

Inline function is a technique used by the compilers and instructs to insert complete body of the function wherever that function is used in the program source code.

## What is operator overloading?

Operator overloading is a function where different operators are applied and depends on the arguments. Operator,-,* can be used to pass through the function , and it has their own precedence to execute.

## What is an abstract class?

An abstract class is a class which cannot be instantiated. Creation of an object is not possible with abstract class , but it can be inherited. An abstract class can contain only Abstract method. Java allows only abstract method in abstract class while for other language it allows non-abstract method as well.

## What is Composition?

Composition is a special form of Aggregation where the part cannot exist without the whole. Composition is a strong Association. Composition relationship is represented like aggregation with one difference that the diamond shape is filled.

## What is Dependency?

When one class depends on another because it uses that at some point in time then this relationship is known as Dependency. One class depends on another if the independent class is a parameter variable or local variable of a method of the dependent class. A Dependency is drawn as a dotted line from the dependent class to the independent class with an open arrowhead pointing to the independent class.

## What is the difference between Association and Dependency?

The main difference between Association and Dependency is in case of Association one class has an attribute or member variable of the other class type but in case of Dependency a method takes an argument of the other class type or a method has a local variable of the other class type.

## What is Association?

Association is a relationship between two objects with multiplicity.

## What is Aggregation?

Aggregation is also known as “HAS-A” relationship. When class Car has a member reference variable of type Wheel then the relationship between the classes Car and Wheel is known as Aggregation. Aggregation can be understood as “whole to its parts” relationship.

Car is the whole and Wheel is part. Wheel can exist without the Car. Aggregation is a weak association.

## What is the meaning of “IS-A” and “HAS-A” relationship?

“IS-A” relationship implies inheritance. A sub class object is said to have “IS-A” relationship with the super class or interface. If class A extends B then A “IS-A” B. It is transitive, that is, if class A extends B and class B extends C then A “IS-A” C. The “instanceof” operator in java determines the “IS-A” relationship.

When a class A has a member reference variable of type B then A “HAS-A” B. It is also known as Aggregation.

## What is the diamond problem in inheritance?

In case of multiple inheritance, suppose class A has two subclasses B and C, and a class D has two super classes B and C.If a method present in A is overridden by both B and C but not by D then from which class D will inherit that method B or C? This problem is known as diamond problem.

## Why Java does not support multiple inheritance?

Java was designed to be a simple language and multiple inheritance introduces complexities like diamond problem. Inheriting states or behaviors from two different type of classes is a case which in reality very rare and it can be achieved easily through an object association.

## What is Static Binding and Dynamic Binding?

Static or early binding is resolved at compile time. Method overloading is an example of static binding.
Dynamic or late or virtual binding is resolved at run time. Method overriding is an example of dynamic binding.

## What is the diamond problem in inheritance?

In case of multiple inheritance, suppose class A has two subclasses B and C, and a class D has two super classes B and C.If a method present in A is overridden by both B and C but not by D then from which class D will inherit that method B or C? This problem is known as diamond problem.

## What is Abstraction?

Abstraction is an OOPS concept to construct the structure of the real world objects. During this construction only the general states and behaviors are taken and more specific states and behaviors are left aside for the implementers.

## What is Encapsulation?

Encapsulation is an OOPS concept to create and define the permissions and restrictions of an object and its member variables and methods. A very simple example to explain the concept is to make the member variables of a class private and providing public getter and setter methods.
Java provides four types of access level modifiers: public, protected, no modifier and private.

## What is the difference between Abstraction and Encapsulation?

“Program to interfaces, not implementations” is the principle for Abstraction and “Encapsulate what varies” is the OO principle for Encapsulation.

Abstraction provides a general structure of a class and leaves the details for the implementers. Encapsulation is to create and define the permissions and restrictions of an object and its member variables and methods.

Abstraction is implemented in Java using interface and abstract class while Encapsulation is implemented using four types of access level modifiers: public, protected, no modifier and private.

## What is Polymorphism?

Polymorphism is the occurrence of something in various forms. Java supports various forms of polymorphism like polymorphic reference variables, polymorphic method, polymorphic return types and polymorphic argument types.

## What are the core concepts of OOPS?

OOPS core concepts are; 

Abstraction 

Encapsulation

Polymorphism Inheritance 

Composition 

Association 

Aggregation

## What is Abstraction?

The first thing with which one is confronted when writing programs is the problem. Typically we are confronted with “real-life” problems and we want to make life easier by providing a program for the problem. However, real-life problems are nebulous and the first thing we have to do is to try to understand the problem to separate necessary from unnecessary details: We try to obtain our own abstract view, or model, of the problem. This process of modeling is called abstraction.

## What is Inheritance? What is the purpose?

The idea of inheritance is simple, a class is based on another class and uses data and implementation of the other class.

The purpose of inheritance is Code Reuse.

## What are main features of OOP?

Encapsulation 

Polymorphism 

Inheritance

# Java JDBC Tutorial 

JDBC stands for Java Database Connectivity. JDBC is a Java API to connect and execute the query with the database. It is a part of JavaSE (Java Standard Edition). JDBC API uses JDBC drivers to connect with the database. There are four types of JDBC drivers: o JDBC-ODBC Bridge Driver, o Native Driver, o Network Protocol Driver, and o Thin Driver We have discussed the above four drivers in the next chapter. We can use JDBC API to access tabular data stored in any relational database. By the help of JDBC API, we can save, update, delete and fetch data from the database. It is like Open Database Connectivity (ODBC) provided by Microsoft.

![alt text](image-293.png)

The current version of JDBC is 4.3. It is the stable release since 21st September, 2017.

## Why Should We Use JDBC? 

Before JDBC, ODBC API was the database API to connect and execute the query with the database. But, ODBC API uses ODBC driver which is written in C language (i.e. platform dependent and unsecured). That is why Java has defined its own API (JDBC API) that uses JDBC drivers (written in Java language). 

We can use JDBC API to handle database using Java program and can perform the following activities: 

1. Connect to the database 

2. Execute queries and update statements to the database 

3. Retrieve the result received from the database. 

## What is API? 

API (Application programming interface) is a document that contains a description of all the features of a product or software. It represents classes and interfaces that software programs can follow to communicate with each other. An API can be created for applications, libraries, operating systems, etc.

## Q1. What is the difference between an Inner Class and a Sub-Class?

An Inner class isa class which is nested within another class. An Inner class has access rights for the class which is nesting it and it can access all variables and methods defined in the outer class.

A sub-class is a class which inherits from another class called super class. Sub-class can access all public and protected methods and fields of its super class.

## Q3. What's the purpose of Static methods and static variables?

When there is a requirement to share a method or a variable between multiple objects of a class instead of creating separate copies for each object, we use static keyword to make a method or variable shared for all objects.

## Q4. What is data encapsulation and what's its significance?

Encapsulation is a concept in Object Oriented Programming for combining properties and methods in a single unit.

Encapsulation helps programmers to follow a modular approach for software development as each object has its own set of methods and variables and serves its functions independent of other objects. Encapsulation also serves data hiding purpose.

## Q5. What is a singleton class? Give a practical example of its usage.

A singleton class in java can have only one instance and hence all its methods and variables belong to just one instance. Singleton class concept is useful for the situations when there is a need to limit the number of objects for a class.

The best example of singleton usage scenario is when there is a limit of having only one connection to a database due to some driver limitations or because of any licensing issues.

## Q8. What is the difference between continue and break statement?

break and continue are two important keywords used in Loops. When a break keyword is used in a loop, loop is broken instantly while when continue keyword is used, current iteration is broken and loop continues with next iteration.

In below example, Loop is broken when counter reaches 4.

```java
for (counter-0;counter<10;counter+){
    system.out.println(counter);
    if (counter-=4){
        break:
    }
}
```

In the below example when counter reaches 4, loop jumps to next iteration and any statements after the continue keyword are skipped for current iteration.

```java
for (counter=0;counter<10;counter++){
    system.out.printin(counter);
    if (counter==4){
        continue;
        system.out.println("This will not get printed when counter is 4");
    }
}
```
## Q9. What is the difference between double and float variables in Java?

In java, float takes 4 bytes in memory while Double takes 8 bytes in memory. Float is single precision floating point decimal number while Double is double precision decimal number.

## Q14. What's the base class in Java from which all classes are derived?

java.lang.object

## Q15. Can main() method in Java can return any data?

In java, main() method can't return any data and hence, ite's always declared with a void return type.

## Q17. Can we declare a class as Abstract without having any abstract method?

Yes we can create an abstract class by using abstract keyword before class name even if it doesn't have any abstract method. However, if a class has even one abstract method, it must be declared as abstract otherwise it will give an error.

## Q18. What's the difference between an Abstract Class and Interface in Java?

The primary difference between an abstract class and interface is that an interface can only possess declaration of public static methods with no concrete implementation while an abstract class can have members with any access specifiers (public, private etc) with or without concrete
implementation.

Another key difference in the use of abstract classes and interfaces is that a class which implements an interface must implement all the methods of the interface while a class which inherits from an abstract class doesn't require implementation of all the methods of its super class.

A class can implement multiple interfaces but it can extend only one abstract class.

## Q19. What are the performance implications of Interfaces over abstract classes?

Interfaces are slower in performance as compared to abstract classes as extra indirections are required for interfaces. Another key factor for developers to take into consideration is that any class can extend only one abstract class while a class can implement many interfaces.

Use of interfaces also puts an extra burden on the developers as any time an interface is implemented in a class; developer is forced to implement each and every method of interface.

## Qg20. Does Importing a package imports its sub-packages as well in Java?

In java, when a package is imported, its sub-packages aren't imported and developer needs to import therm separately if required.

For example, if a developer imports a package university.", all classes in the package named university are loaded but no classes from the sub-package are loaded. To load the classes from its sub-package ( say department), developer has to import it explicitly as follows:

```java
Import university.department.*
```

## Q21. Can we declare the main method of our class as private?

In java, main method must be public static in order to run any application correctly. If main method is declared as private, developer won't get any compilation error however, it will not get executed and will give a runtime error.

## Q22. How can we pass argument to a function by reference instead of pass by value?

In java, we can pass argument to a function only by value and not by reference.

## Q23. How an object is serialized in java?

In java, to convert an object into byte stream by serialization, an interface with the name Serializable is implemented by the class. All objects of a class implementing serializable interface get serialized and their state is saved in byte stream.

## 024. When we should use serialization?

Serialization is used when data needs to be transmitted over the network. Using serialization, object's state is saved and converted into byte stream .The byte stream is transferred over the network and the object is re-created at destination.

## Q25. Is it compulsory for a Try Block to be followed by a Catch Block in Java for Exception handling?

Try block needs to be followed by either Catch block or Finally block or both. Any exception thrown from try block needs to be either caught in the catch block or else any specific tasks to be performed before code abortion are put in the Finally block.

## Q26. Is there any way to skip Finally block of exception even if some exception occurs in the exception block?

If an exception is raised in Try block, control passes to catch block if it exists otherwise to finally block. Finally block is always executed when an exception occurs and the only way to avoid execution of any statements in Finally block is by aborting the code forcibly by writing following line of code at the end of try block:

```java
System.exit{0);
```

## Q27. When the constructor of a class is invoked?

The constructor of a class is invoked every time an object is created with new keyword. For example, in the following class two objects are created using new keyword and hence, constructor is invoked two times.

```java
public class const_example {
const_example() {
system.out.println("Inside constructor"};
public static void main(String argsl){
const_example cl=new const_example();
const example c2=new const_example();
}
}
```

## Q28. Can a class have multiple constructors?

Yes, a class can have multiple constructors with different parameters. Which constructor gets used for object creation depends on the arguments passed while creating the objects.

## Q29. Can we override static methods of a class?

We cannot override static methods. Static methods belong to a class and not to individual objects and are resolved at the time of compilation (not at runtime).

Even if we try to override static method,we wil not get an complitaion error,nor the impact of overriding when running the code.

## Q30. In the below example, what will be the output?

```java
public class superclass {
    public void displayResult(){
system.out.printin("Printing from superclass");
public class subclass extends superclass{
public void displayResult()
system.out.println("Displaying from subClass");
super.displayResult();
public static void main(String args[l){
subclass obj=new subclass);
obj.displayResuit();
}
}

Ans: Output will be:

Displaying from subclass
Displaying from superclass
```

## Q31. Is String a data type in java?

String is not a primitive data type in java. When a string is created in java, it's actually an object of Java. lang.String class that gets created. After creation of this string object, all built-in methods of String class can be used on the string object.

## Q32. In the below example, how many String Objects are created?

```java
String s1="l am Java Expert";
String s2-"l am C Expert";
String s3-"l am Java Expert"
```

In the above example, two objects of Java.Lang.String class are created. s1 and s3 are references to same object.

## 033. Why Strings in Java are called as Immutable?

In java, string objects are called immutable as once value has been assigned to a string, it can't be changed and if changed, a new object is created.

In below example, reference str refers to a string object having value "Value one".

```java
String str="Value One"
```

When a new value is assigned to it, a new String object gets created and the reference is moved to the new object.

```java
str="New Value";
```

## Q34. What's the difference between an array and Vector?

An array groups data of same primitive type and is static in nature while vectors are dynamic in nature and can hold data of different data types.

## Q35. What is multi-threading?

Multi threading is a programming concept to run multiple tasks in a concurrent manner within a single program. Threads share same process stack and running in parallel. It helps in performance improvement of any program.

## Q36. Why Runnable Interface is used in Java?

Runnable interface is used in java for implementing multi threaded applications. Java.Lang.Runnable interface is implemented by a class to support multi threading.

## Q38. When a lot of changes are required in data, which one should be a preference to be used? String or StringBuffer?

Since StringBuffers are dynamic in nature and we can change the values of StringBuffer objects unlike String which is immutable, it's always a good choice to use StringBuffer when data is being changed too much. If we use String in such a case, for every data change a new String object will be created which will be an extra overhead.

## Q39. What's the purpose of using Break in each case of Switch Statement?

Break is used after each case (except the last one) in a switch so that code breaks after the valid case and doesn't flow in the proceeding cases too.

If break isn't used after each case, all cases after the valid case also get executed resulting in wrong results.

## Q40. How garbage collection is done in Java?

In java, when an object is not referenced any more, garbage collection takes place and the object is destroyed automatically. For automatic garbage collection java calls either System.gc) method or Runtime.gc() method.

## Q41. How we can execute any code even before main method?

If we want to execute any statements before even creation of objects at load time of class, we can use a static block of code in the class. Any statements inside this static block of code will get executed once at the time of loading the class even before creation of objects in the main method.

## Q42. Can a class be a super class and a sub-class at the same time? Give example.

If there is a hierarchy of inheritance used, a class can be a super class for another class and a sub-class for another one at the same time.

## Q43. How objects of a class are created if no constructor is defined in the class?

Even if no explicit constructor is defined in a java class, objects get created successfully as a default constructor is implicitly used for object creation. This constructor has no parameters.

## Q44. In multi-threading how can we ensure that a resource isn't used by multiple threads simultaneously?

In multi-threading, access to the resources which are shared among multiple threads can be controlled by using the concept of synchronization. Using synchronized keyword, we can ensure that only one thread can use shared resource at a time and others can get control of the resource only once it has become free from the other one using it.

## Q45. Can we call the constructor of a class more than once for an object?

Constructor is called automatically when we create an object using new keyword. It's called only once for an object at the time of object creation and hence, we can't invoke the constructor again for an object after its creation.

## Q46. There are two classes named classA and classB. Both classes are in the same package. Can a private member of classA can be accessed by an object of classB?

Private members of a class aren't accessible outside the scope of that class and any other class even in the same package can't access them.

## Q47. Can we have two methods in a class with the same name?

We can define two methods in a class with the same name but with different number/type of parameters. Which method is to get invoked will depend upon the parameters passed.

For example in the class below we have two print methods with same name but different parameters. Depending upon the parameters, appropriate one will be called.

## Q48. How can we make copy of a java object?

We can use the concept of cloning to create copy of an object. Using clone, we create copies with the actual state of an object.

Clone() is a method of Cloneable interface and hence, Cloneable interface needs to be implemented for making object copies.

## Q49. What's the benefit of using inheritance?

Key benefit of using inheritance is reusability of code as inheritance enables sub-classes to reuse the code of its super class. Polymorphism (Extensibility ) is another great benefit which allow new functionality to be introduced without effecting existing derived classes.

## Q50. What's the default access specifier for variables and methods of a class?

Default access specifier for variables and method is package protected i.e variables and class is available to any other class but in the same package,not outside the package.

## Q50. What's the default access specifier for variables and methods of a class?

Default access specifier for variables and method is package protected i.e variables and class is available to any other class but in the same package,not outside the package.

## Q52. How can we restrict inheritance for a class so that no class can be inherited from it?

If we want a class not to be extended further by any class, we can use the keyword Final with the class name.

In the following example, Stone class is Final and can't be extend

```java
public Final Class Stone{

    // Class methods and Variables

}
```

## Q54. What's difference between Stack and Queue?

Stack and Queue both are used as placeholder for a collection of data. The primary difference between a stack and a queue is that stack is based on Last in First out (LIFO) principle while a queue is based on FIFO (First In First Out) principle.

## Q55. In java, how we can disallow serialization of variables?

If we want certain variables of a class not to be serialized, we can use the keyword transient while declaring them. For example, the variable trans_var below is a transient variable and can't be serialized:

```java
public class transientExample{

    private transient trans_var;
    // rest of the code

}

```

## Q56. How can we use primitive data types as objects?

Primitive data types like int can be handled as objects by the use of their respective wrapper classes. For example, Integer is a wrapper class for primitive data type int. We can apply different methods to a wrapper class, just like any other object.

## Q57. Which types of exceptions are caught at compile time?

Checked exceptions can be caught at the time of program compilation. Checked exceptions must be handled by using try catch block in the code in order to successfully compile the code.

## Q59. Can we use a default constructor of a class even if an explicit constructor is defined?

Java provides a default no argument constructor if no explicit constructor is defined in a Java class. But if an explicit constructor has been defined, default constructor can't be invoked and developer can use only those constructors which are defined in the class.

## Q60. Can we override a method by using same method name and arguments but different return types?

The basic condition of method overriding is that method name, arguments as well as return type must be exactly same as is that of the method being overridden. Hence usinga different return type doesn't override a method.

## Q61. A person says that he compiled a java class successfully without even having a main method in it? Is it possible?

main method is an entry point of Java class and is required for execution of the program however; a class gets compiled successfully even if it doesn't have a main method. It can't be run though.

## Q62. Can we call a non-static method from inside a static method?

Non-Static methods are owned by objects of a class and have object level scope and in order to call the non-Static methods from a static block (like froma static main method), an object of the class needs to be created first. Then using object reference, these methods can be invoked.

## Q63. What are the two environment variables that must be set in order to run any Java programs?

Java programs can be executed in a machine only once following two environment variables have been properly set:

1. PATH variable
2. CLASSPATH variable

## Q64. Can variables be used in Java without initialization?

In Java, if a variable is used ina code without prior initialization by a valid value, program doesn't compile and gives an error as no default value is assigned to variables in Java.

## Q65. Can a class in Java be inherited from more than one class?

In Java, a class can be derived from only one class and not from multiple classes. Multiple inheritances is not supported by Java.

## Q66. Can a constructor have different name than a Class name in Java?

Constructor in Java must have same name as the class name and if the name is different, it doesn't act as a constructor and compiler thinks of it as a normal method.

## Q67.What will be the output of Round(3.7) and Ceill (3.7)?

Round(3.7) returns 4 and Ceil(3.7) returns 4.

## Q69. Can a dead thread be started again?

In java, a thread which is in dead state can't be started again. There is no way to restart a dead thread.

## Q70. Is the following class declaration correct?

```java
public abstract final class testClass{
    / Class methods and variables
}
```
The above class declaration is incorrect as an abstract class can't be declared as Final.

## Q71. Is JDK required on each machine to run a Java program?

JDK is development Kit of Java and is required for development only and to run a Java program on a machine, JDK isn't required. Only JRE is required.

## Q72. What's the difference between comparison done by equals method and == operator?

In Java, equals() method is used to compare the contents of two string objects and returns true if the two have same value while == operator compares the references of two string objects.

In the following example, equals() returns true as the two string objects have same values. However == operator returns false as both string objects are referencing to different objects.

## Q73. Is it possible to define a method in Java class but provide it's implementation in the code of another language like C?

Yes, we can do this by use of native methods. In case of native method based development, we define public static methods in our Java class without its implementation and then
implementation is done in another language like C separately.

## Q74. How are destructors defined in Java?

In Java, there are no destructors defined in the class as there is no need to do so. Java has its own garbage collection mechanism which does the job automatically by destroying the objects when no longer referenced.

## Q75. Can a variable be local and static at the same time?

No a variable can't be static as well as local at the same time. Defining a local variable as static gives compilation error.

## Q76. Can we have static methods in an Interface?

Static methods can't be overridden in any class while any methods in an interface are by default abstract and are supposed to be implemented in the classes being implementing the interface. So it makes no sense to have static methods in an interface in Java.

## Q77. In a class implementing an interface, can we change the value of any variable defined in the interface?

No, we can't change the value of any variable of an interface in the implementing class as all variables defined in the interface are by default public, static and Final and final variables are like constants which can't be changed later.

## Q78. Is it correct to say that due to garbage collection feature in Java, a java program never goes out of memory?

Even though automatic garbage collection is provided by Java, it doesn't ensure that a Java program will not go out of memory as there is a possibility that creation of Java objects is being done at a faster pace compared to garbage collection resulting in filling of all the available memory
resources.

So, garbage collection helps in reducing the chances of a program going out of memory but it doesn't ensure that.

## Q79. Can we have any other return type than void for main method?

No, Java class main method can have only void return type for the program to get successfully executed.

Nonetheless, if you absolutely must return a value to at the completion of main method, you can use System.exitint status)

## Q80.I want to re-reach and use an object once it has been garbage collected. How it's possible?

Once an object has been destroyed by garbage collector, it no longer exists on the heap and it can't be accessed again. There is no way to reference it again.

## Q81. In Java thread programming, which method is a must implemetation for all threads?

Run() is a method of Runnable interface that must be implemented by all threads.

## Q82. I want to control database connections in my program and want that only one thread should be able to make database connection at a time. How can I implement this logic?

This can be implemented by use of the concept of synchronization. Database related code can be placed in a method which hs synchronized keyword so that only one thread can access it at a time.

## Q83. How can an exception be thrown manually by a programmer?

## Q84. I want my class to be developed in sucha way that no other class (even derived class) can create its objects. How can I do so?

If we declare the constructor of a class as private, it will not be accessible by any other class and hence, no other class will be able to instantiate it and formation of its object will be limited to itself only.

## Q85. How objects are stored in Java?

In java, each object when created gets a memory space from a heap. When an object is destroyed by a garbage collector, the space allocated to it from the heap is re-allocated to the heap and becomes available for any new objects.

## Q86. How can we find the actual size of an object on the heap?

In java, there is no way to find out the exact size of an object on the heap.

## Q87. Which of the following classes will have more memory allocated? <br><br> Class A: Three methods, four variables, no object <br> Class B: Five methods, three variables, no object

Memory isn't allocated before creation of objects. Since for both classes, there are no objects created so no memory is allocated on heap for any class.

## Q88. What happens if an exception is not handled in a program?

If an exception is not handled in a program using try catch blocks, program gets aborted and no statement executes after the statement which caused exception throwing.

## Q89. I have multiple constructors defined in a class. Is it possible to call a constructor from another constructor's body?

If a class has multiple constructors, it's possible to call one constructor from the body of another one using this().

## Q90. What's meant by anonymous class?

An anonymous class is a class defined without any name in a single line of code using new keyword.

For example, in below code we have defined an anonymous class in one line of code:

```java
public java.util.Enumeration testMethod(){

    return new java.util.Enumeration(){
        @Override
        public boolean hasMoreElements(){
            /TODO Auto-generated method stub
            return false;
        }

        @Override
        public Object nextElement(){
            // TODO Auto-generated method stub
            return null
        }
        
    }
}
```

## Q91. Is there a way to increase the size of an array after its declaration?

Arrays are static and once we have specified its size, we can't change it. If we want to use such collections where we may require a change of size ( no of items), we should prefer vector Over array.

## Q92. If an application has multiple classes in it, is it okay to have a main method in more than one class?

If there is main method in more than one classes in a java application, it won't cause any issue as entry point for any application will be a specific class and code will start from the main method of that particular class only.

## Q93.I want to persist data of objects for later use. What's the best approach to do so?

The best way to persist data for future use is to use the concept of serialization.

## Q94. What is a Local class in Java?

In Java, if we define a new class inside a particular block, it's called a local class. Such a class has local scope and isn't usable outside the block where its defined.

## Q95. String and StringBuffer both represent String objects. Can we compare String and StringBuffer in Java?

Although String and StringBuffer both represent String objects, we can't compare them with each other and if we try to compare them, we get an error.

## Q96. Which APl is provided by Java for operations on set of objects?

Java provides a Collection APl which provides many useful methods which can be applied on a set of objects. Some of the important classes provided by Collection API include ArrayList, Hash Map, TreeSet and TreeMap.

## Q97. Can we cast any other type to Boolean Type with type casting?

No, we can neither cast any other primitive type to Boolean data type nor can cast Boolean data type to any other primitive data type.

## Q98. Can we use different return types for methods when overridden?

The basic requirement of method overriding in Java is that the overridden method should have same name, and parameters.But a method can be overridden with a different return type as long as the new return type extends the original.

## Q99. What's the base class of all exception classes?

In Java, Java.lang.Throwable is the super class of all exception classes and all exception classes are derived from this base class.

## Q100. What's the order of call of constructors in inheritiance?

In case of inheritance, whena new object of a derived class is created, first the constructor of the super class is invoked and then the constructor of the derived class is invoked.

# Arrays

## Single Dimensional Array in Java

Syntax to Declare an Array in Java

```java
dataType[] arr; (or)
dataType []arr; (or)
dataType arr[];
```
Instantiation of an Array in Java

```java
arrayRefVar=new datatype[size];
```

## Multidimensional Array

Syntax to Declare Multidimensional Array in Java

```java
dataType[][] arrayRefVar; (or)
dataType [][]arrayRefVar; (or)
dataType arrayRefVar[][]; (or)
dataType []arrayRefVar[];
```

Example to instantiate Multidimensional Array in Java

```java
int[][] arr=new int[3][3];//3 row and 3 column
```

## Classes

![alt text](image-294.png)

## Garbage Collection

An automatic garbage collector deallocates memory for objects that are no longer needed by your program, thereby relieving you from the tedious and error-prone task of deallocating your own memory.

As a consequence of automatic garbage collection and lack of pointers, a Java object is either null or valid--there is no way to refer to an invalid or stale object (one that has been deallocated).

To illustrate the effect of a garbage collector, consider the following C++ function that allocates 1000 objects on the heap via the new operator (a similar C function
would allocate memory using calloc/malloc):

```java
// C++ code
void f() {
T *t;
for (int i = 1; i <= 1000; i++) {
t = new T; // ack!!!!!
}
}
```

Every time the loop body is executed, a new instance of class T is instantiated, and t is pointed to it. But what happens to the instance that t used to point to? It's
still allocated, but nothing points to it and therefore it's inaccessible. Memory in this state is referred to as "leaked" memory.

In the Java language, memory leaks are not an issue. The following Java method causes no ill effects:

```java
// Java code
void f() {
T t;
for (int i = 1; i <= 1000; i++) {
t = new T();
}
}
```

In Java, each time t is assigned a new reference, the old reference is now available for garbage collection. Note that it isn't immediately freed; it remains allocated until the garbage collector thread is next executed and notices that it can be freed.

Put simply, automatic garbage collection reduces programming effort, programming errors, and program complexity.

## Java Abstraction

![alt text](image-295.png)
![alt text](image-296.png)
![alt text](image-297.png)
![alt text](image-298.png)
![alt text](image-299.png)
![alt text](image-300.png)

# Java 11 Notes

## Why is Java 11 important ?

Java 11 is the second LTS release after Java 8. Since Java 11, Oracle JDK would no longer be free for commercial use.

* You can use it in developing stages but to use it commercially, you need to buy a license. If you don’t, you can get an invoice bill from Oracle any day!

* Java 10 was the last free Oracle JDK that could be downloaded.

* Oracle stops Java 8 support from January 2019. You’ll need to pay for more support.

* You can continue using it, but won’t get any patches/security updates.

## We can run the Java program without compilation.

* From Java 11 we just run the program no need to compile separately. The Java command itself will compile internally.

* Java Test.java

## String Enhancements:

**repeat(int)**: This methos can be called on string object, it returns the given string object for the mentioned int number.

![alt text](image-301.png)

Output is:

![alt text](image-302.png)

* To this repeat() method if we provides negative value then it gives illegal argument exception

* This method accepts the integer number, Since it accepts the integer, after creating the new string the length should not cross the integer limit, if it crosses, it throws out of memory error.

![alt text](image-303.png)

![alt text](image-304.png)

**isBlank()**: It returns true, if the given string is empty or having only the spaces.

**strip()**: this method is same as trim() which removes the leading and trailing spaces from the string.

**stripLeading()**: This method is used to delete the leading spaces only

**stripTrailing()**: This method is used to delete the trailing spaces

![alt text](image-305.png)

## What is the difference between strip() and trim();

* trim()removes only characters <= U+0020 (space);strip()removes all Unicode whitespace characters (but not all control characters, such as \0)

* However, the strip() method uses Character.isWhitespace() method to check if the character is a whitespace. This method uses Unicode code points whereas trim() method identifies any character having codepoint value less than or equal to ‘U+0020’ as a whitespace character.

* The strip() method is the recommended way to remove whitespaces because it uses the Unicode standard.

* String::trim has existed from early days of Java when Unicode had not fully evolved to the standard we widely use today.

* The definition of space used by String::trim is any code point less than or equal to the space code point (\u0020), commonly referred to as ASCII or ISO control characters.

![alt text](image-306.png)

**lines()**:
Returns a stream of lines extracted from this string, separated by line terminators

* A line terminator is one of the following:

* a line feed character {@code "\n"} (U+000A),

* a carriage return character {@code "\r"} (U+000D),

* or a carriage return followed immediately by a line feed
{@code "\r\n"} (U+000D U+000A).

Lines example with \n symbol
![alt text](image-307.png)

Lines example with \r symbol
![alt text](image-308.png)

## Collection Enhancements in Java 11:

**toArray()**: In Java 11 new default method has been introduced in collection interface.
![alt text](image-309.png)

This toArray() takes the functional interface and converts into Array.

![alt text](image-310.png)

## File API Changes:

Reading and writing text files has been continuously simplified since Java 6. In Java 6, we had to open aFileInputStream, wrap it with anInputStreamReaderand aBufferedReader, then load the text file line by line into aStringBuilder(alternatively, omit theBufferedReaderand read the data inchar[]blocks) and close the readers and theInputStreamin thefinallyblock.

* Luckily, we had libraries likeApache Commons IOthat did this work for us with theFileUtils.readFileToString()andwriteFileToString()methods.

![alt text](image-311.png)

* The above is the general way of reading the data from the file.

* Below is the Java 11 implementation.

* **readString()**: This method reads all content from a file into a String. Using UTF-8 charset it decodes from bytes to characters. This function makes sure that the file is closed when all content have been read or an I/O Error or other runtime exception, is thrown.

![alt text](image-312.png)

* **writeString()**:This method is used to write the data to the file.

Syntax: static Path writeString(Path path, CharSequence csq, OpenOption... options)

* The first argument is path where the file is present.

* The Second argument is Char Sequence which is nothing but the String that we want to write to the file

* The third parameter var args options ->optionsspecifies how the file is opened.

![alt text](image-313.png)

* Here third parameter is StandardOpenOption.Append-> This will append the text to the data that is already present in the file. The append will happen at the end of the data in the file

Example: in the contact.txt -> the file contains Test as word then output of the WriteString above method is shown below
![alt text](image-314.png)

If you open the file then below content is shown
![alt text](image-315.png)

StandardOpenOption.CREATE ->This method will override the content that is present in the mentioned file.
![alt text](image-316.png)

Document after the operation:
![alt text](image-317.png)

The below is the other way of creating the file using createTempFile method

Path path = Files.writeString(Files.createTempFile(“test”, “.txt”), “Java 11 features”);

## Local Variable Declaration for Lamda:

Java 11 adds the support for Local-Variable syntax for lambda expressions. Lambdas can infer the type, but using the var keyword allows us to use annotations like @NotNull or @Nullable with the parameters.

* (@NotNull var str) -> "$" + str

* In order to mention the local variable we can use var.

* In Java 10, Local-variable type-inference was introduced.

* It allows us to use var as data type of local variable instead of actual data type. (Example: var x=10)

* Local variable are those variables, which are defined inside a particular block of code like method, constructor and init blocks

* We cannot use this var for the method parameter, constructor parameter

* This var should be initialized where it is declared

* Java compiler infers the data type based on the value assigned to the variable.

```java
Example:
void m1(){
String x="ABC"
Int y=10;
} //Here in the above m1 method compiler knew that x is String type and y is int type
```

Same method we can like below from java 10.

```java
void m1(){
var x="ABC"
Var y=10; // here by looking at the 10 compiler understand sthat it takes int value but late you can re initialize this y with another int value like below
y=25 but not you cannot change the type (y="A")
}//The difference here is that instead of specifying the data type, by assigned value compiler will understand infer the data type.
```

* Here when we use local variable like var-> Initialization is mandatory.

* From Java 11 the new feature is we can declare this local variable var In lamda expression

* Rules for Lamda local variables.

    • (var s1, s2) -> s1 + s2 //no skipping allowed


    • (var s1, String y) -> s1 + y //no mixing allowed

    • var s1 -> s1 //not allowed. Need parentheses if you use var in lambda.

1. If there are multiple parameters then usevarwith all the parameters. No skipping allowed.

2. If one parameter usevarthen other parameters must usevarrather than other types likeint,float, etc.

3. Must use parenthesis()while using thevarwith the parameters.

## Predicate Interface Changes:

* The not() Method

* A static not() method has been added to the Predicate interface in Java 11. As the name suggests, this method is used to negate a Predicate. The not() method can also be used with method references.

* Predicate.not() is a static method which is introduced in Java 11 to negate the supplied Predicate

Syntax of not method of predicate interface

![alt text](image-318.png)

This not() static method is taking the predicate as input and returning the negate [predicate as output. Internally it is calling the negate() method

Before Java 11 : Negating The Predicate

This is the implementation before Java 11

![alt text](image-319.png)

Using the same example with the Predicate.not() method
![alt text](image-320.png)

## Http Client:

• In Java 11, HTTP Client has introduced newly, through which we can send the request and get the response.

• This HttpClient is present in java.net.httppackage.

• Making HTTP requests is a core feature of modern programming, and is often one of the first things you want to do when learning a new programming language. For Java programmers there are many ways to do it -core libraries in the JDK and third-party libraries

• Using HttpURLConnection or ApacheHttpClient HTTP request and response can be obtained.

• An enhanced HttpClient API was introduced in Java 9 as an experimental feature. With Java 11, now HttpClient is a standard. It is recommended to use instead of other HTTP Client APIs like Apache Http Client API. It is quite feature rich and now Java based applications can make HTTP requests without using any external dependency.

Steps

* Following are the steps to use an HttpClient.

    • Create HttpClient instance using HttpClient.newBuilder() instance
    
    • Create HttpRequest instance using HttpRequest.newBuilder() instance

    • Make a request using httpClient.send() and get a response object
![alt text](image-321.png)
![alt text](image-322.png)

![alt text](image-323.png)
![alt text](image-324.png)

## NestedBasedAccess

* Java 11 introduced a concept of nested class where we can declare a class within a class. This nesting of classes allows to logically group the classes to be used in one place, making them more readable and maintainable. Nested class can be of four types −

    ○ Static nested classes

    ○ Non-static nested classes

    ○ Local classes

    ○ Anonymous classes

    ○ Java 11 also provide the concept of nestmate to allow communication and verification of nested classes.

* Java 11 introducednest-based access controlthat allows classes to access each other's private memberswithout the need for bridge methodscreated by the compiler. These methods are calledaccessibility-broadening bridge methodsand the compiler inserts these into the code during the program execution.

* Before Java 11, if we have private members in our code then the compiler creates accessibility-broadening bridge methods that increase the size of the deployed applications and may lead to confusion. That's why Java improved nest-based access control.

* Java 11 allows classes and interfaces to be nested within each other. These nested type can beprivatefields, methods, and constructors.

![alt text](image-325.png)

# Exception Propagation

![alt text](image-326.png)
![alt text](image-327.png)
![alt text](image-328.png)

## Checked VS Unchecked exception propagation

![alt text](image-329.png)
![alt text](image-330.png)

## Custom Exception Propagation

![alt text](image-331.png)
![alt text](image-332.png)

## An exception is a case where the normal flow of the program execution is disrupted.

Java provides a few built-in exceptions, which are again segregated as compile-time and runtime exceptions. We are in a sunny day scenario until our use case is satisfied with one of the built-in exceptions, but what if there's no such exception that fits our use case, or do we want to customize the exception?

User-defined exceptions are also referred to as custom exceptions. The exceptions created per our use case and thrown using the throw keyword are user-defined exceptions, and such exceptions are derived classes of the Exception class from the java.lang package.

## Why Use Custom Exceptions?

Although java provides the Exception class, which covers almost all cases of exceptions that could be raised during program execution, custom exceptions will bring the spotlight onto exception handling.

Custom exceptions enable the flexibility of adding messages and methods that are not part of the Exception class. They can be used to store case-specific messages like status codes and error codes or override an existing method to present the exception as per the use case.

Custom exceptions are helpful while writing exceptions for business logic. It helps the application developers to better understand the exception, which is business-specific.

Now that we are aware of custom exceptions in java and their use cases, let's have a look at how to create them.

## How to Create User-Defined Exceptions in Java?

To create a custom exception in java, we have to create a class by extending it with an Exception class from the java.lang package.

It's always a good practice to add comments and follow naming conventions to easily identify and recognize the benefit of our exception class.

Below is the template to be followed for creating a user-defined exception in java.

```java
//user-defined exception in java 
public class SimpleCustomException extends Exception{ 

}
```

Let's add our custom message to the exception class. This can be done in two ways :

**1. Pass the Exception Message to Super Class Constructor and Retrieve It Using the getMesssage() Method**

Here's the code to demonstrate that in java.

```java
//simple custom exception in java 
public class SimpleCustomException extends Exception { 
    
    //parameter constructor 
    SimpleCustomException(String msg) { 
        //passing the parameter to the super class constructor 
        super(msg); 
    } 
}
```

In the above code, we've made a call to the parent class constructor using the super keyword. Since the custom class is extended by the Exception class, it is considered to be the parent class, and the Exception class has a parameter constructor which expects a string. It will construct a new exception with the specified message that can be retrieved later using the getMessage() method.

**2. Override the toString() Method and Customize It with Our Exception Message**

Here's the code to demonstrate that in Java

```java
//simple custom exception in java 
public class SimpleCustomException extends Exception{ 
    //member variable to store our custom message 
    String msg; 
    SimpleCustomException(String msg) { 
        this.msg=msg; 
    } 
    //overriding with our custom message 
    @Override 
    public String toString() { 
        return msg; 
    }
}
```

in the above code, we've overridden the toString() method. Usually, when we print an object of a java class, it prints the hashcode of that object (default implementation of the toString() method). Overriding the toString() method provides the flexibility to customize the print statement when we print an object. Now that we've overridden the method with our custom message, the user only needs to print the exception object to know the exception message.

Example :

User-defined Exception for Validity of an Entity

```java
//user-defined exception in java
import java.util.*; 
//custom exception to check if the given id is active or not 
class IdDoesnotExistException extends Exception { 
    //member variable to store our custom message 
    String msg; 
    IdDoesnotExistException(String msg) { 
        //passing the parameter to the super class constructor 
        super(msg); 
        this.msg=msg; 
    } 
    //overriding with our custom message 
    @Override 
    public String toString() { 
        return msg; 
    } 
} 

public class Main { 
    public static void main(String[] args) { 
        Scanner sc=new Scanner(System.in); 
        int id = sc.nextInt(); 
        HashSet<Integer> IdList = getIdList();  //returns HashSet with all IDs 

        try { 
            if(!IdList.contains(id)) { //checking if current id is active or not 
            
                throw new IdDoesnotExistException("Entered id is invalid or no more active"); 
            }
        } catch(IdDoesnotExistException ex) { 
            
            //calls override toString() method 
            System.out.println(ex); 
            //prints message passed to the super constructor 
            System.out.println(ex.getMessage()); 
        } 
    } 
}
```