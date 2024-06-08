# Private Methods in Interfaces

## Need Of Default Methods inside interfaces:
Prior to Java 8,Every method present inside interface is always public and abstract whether we are declaring or not.

```java
  interface Prior2Java8Interf 
  { 
    public void m1(); 
    public void m2(); 
  } 
```
Assume this interface is implemented by 1000s of classes and each class provided implementation for both methods.

```java
  interface Prior2Java8Interf 
  { 
    public void m1(); 
    public void m2(); 
  } 

  class Test1 implements Prior2Java8Interf 
  { 
    public void m1(){} 
    public void m2(){} 
  } 

  class Test2 implements Prior2Java8Interf 
  { 
    public void m1(){} 
    public void m2(){} 
  } 

  class Test3 implements Prior2Java8Interf 
  { 
    public void m1(){} 
    public void m2(){} 
  } 

  class Test1000 implements Prior2Java8Interf 
  { 
    public void m1(){} 
    public void m2(){} 
  } 
```

It is valid b'z all implementation classes provided implementation for both m1() and m2().

Assume our programming requirement is we have to extend the functionality of this interface by adding a new method m3().

```java
interface Prior2Java8Interf 
  { 
    public void m1(); 
    public void m2(); 
    public void m3(); 
  }
```

If we add new method m3() to the interface then all the implementation classes will be effected and won't be compiled,b'z every implementation class should implement all methods of interface.

```java
  class Test1 implements Prior2Java8Interf 
  { 
    public void m1(){} 
    public void m2(){} 
  } 
```

CE: Test1 is not abstract and does not override abstract method m3() in PriorJava8Interf

Hence prior to java 8,it is impossible to extend the functionality of an existing interface without effecting implementation classes. JDK 8 Engineers addresses this issue and provides solution in the form of Default methods,which are also known as Defender methods or Virtual Extension Methods.

## How to Declare Default Methods inside interfaces:
In Java 8,inside interface we can define default methods with implementation as follows.

```java
interface Java8Interf 
  { 
    public void m1(); 
    public void m2(); 
    default void m3() 
    { 
      //"Default Implementation 
    } 
  } 
```
Interface default methods are by-default available to all implementation classes.Based on requirement implementation class can ignore these methods or use these default methods directly or can override. 

Hence the main advantage of Default Methods inside interfaces is, without effecting implementation classes we can extend functionality of interface by adding new methods.(backward compatibility). 

## Need of private Methods inside interface:
If several default methods having same common functionality then there may be a chance of duplicate code(Redundant Code).

Eg:

```java
  public interface Java8DBLogging 
  { 
    //Abstract Methods List 
    default void logInfo(String message) 
    { 
      Step1: Connect to DataBase 
      Setp2: Log Info Message 
      Setp3: Close the DataBase connection 
    } 


    default void logWarn(String message) 
    { 
      Step1: Connect to DataBase 
      Setp2: Log Warn Message 
      Setp3: Close the DataBase connection 
    } 


    default void logError(String message) 
    { 
      Step1: Connect to DataBase 
      Setp2: Log Error Message 
      Setp3: Close the DataBase connection 
    } 


    default void logFatal(String message) 
    { 
      Step1: Connect to DataBase 
      Setp2: Log Fatal Message 
      Setp3: Close the DataBase connection 
    } 

  } 
```

In the above code all log methods having some common code which increases length of the code and reduces readability.It creates maintenance problems also. In Java8 there is no solution for this.

## How to declare private Methods inside interface:
JDK 9 Engineers addresses this issue and provided private methods inside interfaces. We can seperate that common code into a private method and we can call that private method from every default method which required that functionality.

```java
  public interface Java9DBLogging 
  { 
    //Abstract Methods List 
    default void logInfo(String message) 
    { 
      log(message,"INFO"); 
    } 


    default void logWarn(String message) 
    { 
      log(message,"WARN"); 
    } 


    default void logError(String message) 
    { 
      log(message,"ERROR"); 
    } 


    default void logFatal(String message) 
    { 
     log(message,"FATAL"); 
    } 


    private void log(String msg,String logLevel) 
    { 
      Step1: Connect to DataBase 
      Step2: Log Message with the Provided logLevel 
      Step3: Close the DataBase Connection 
    } 
  } 
```

## Demo Program for private instance methods inside interface:

private instance methods will provide code reusability for default methods.

```java
  interface Java9Interf 
  { 
    default void m1() 
    { 
     m3(); 
    } 


    default void m2() 
    { 
      m3(); 
    }


    private void m3() 
    { 
      System.out.println("common functionality of methods m1 & m2"); 
    } 

  }


  class Test implements Java9Interf 
  { 
    public static void main(String[] args) 
    { 
      Test t = new Test(); 
      t.m1(); 
      t.m2(); 
      //t.m3(); ==>CE 
    } 
  } 
```

o/p:

```java
D:\java9durga>java Test
common functionality of methods m1 & m2
common functionality of methods m1 & m2

```

Inside Java 8 interaces,we can take public static methods also.If several static methods having some common functionality,we can seperate that common functionality into a private static method and we can call that private static method from public static methods where ever it is required.

## Demo Program for private static methods:

private static methods will provide code reusability for public static methods.


```java
  interface Java9Interf 
  { 
    public static void m1() 
    { 
      m3(); 
    } 


    public static void m2() 
    { 
      m3(); 
    } 


    private static void m3() 
    { 
      System.out.println("common functionality of methods m1 & m2"); 
    } 

  } 


  class Test implements Java9Interf 
  {
    public static void main(String[] args) 
    { 
      Java9Interf.m1(); 
      Java9Interf.m2(); 
    } 
  } 
```
o/p:

```java
D:\durga_classes>java Test
common functionality of methods m1 & m2
common functionality of methods m1 & m2
```

Note: Interface static methods should be called by using interface name only even in implementation classes also. 

## Advantages of private Methods inside interfaces: 

The main advantages of private methods inside interfaces are :
1. Code Reusability
2. We can expose only intended methods to the API clients (Implementation classes),b'z interface private methods are not visible to the implementation classses.

Note: 
1. private methods cannot be abstract and hence compulsory private methods should 
have the body.
2. private method inside interface can be either static or non-static.

## JDK 7 vs JDK 8 vs JDK9:
1. Prior to java 8,we can declare only public-abstract methods and public-static-final variables inside interfaces.

```java
  interface Prior2Java8Interface 
  { 
    public-static-final variables 
    public-abstract methods 
  } 
```

2. In Java 8 ,we can declare default and public-static methods also inside interface.

```java
  interface Java8Interface 
  { 
    public-static-final variables 
    public-abstract methods 
    default methods with implementation 
    public static methods with implementation 
  } 
```

3. In Java 9,We can declare private instance and private static methods also inside 
interface.

```java
interface Java9Interface 
  { 
    public-static-final variables 
    public-abstract methods 
    default methods with implementation 
    public static methods with implementation 
    private instance methods with implementation 
    private static methods with implementation 
  } 
```

Note: The main advantage of private methods inside interface is Code Reusablility without effecting implemenation classes

# Try with Resources Enahancements

## Need of Try with Resources: 
Until 1.6 version it is highly recommended to write finally block to close all resources which are open as part of try block. 

```java
  BufferedReader br=null; 
  try 
  { 
    br=new BufferedReader(new FileReader("abc.txt")); 
    //use br based on our requirements 
  } 
  catch(IOException e) 
  { 
    // handling code 
  } 
  finally 
  { 
    if(br != null) 
    br.close(); 
  } 
```

## Problems in this Approach:
1. Compulsory programmer is required to close all opened resources which increases the complexity of the programming

2. Compulsory we should write finally block explicitly which increases length of the code and reduces readability. 

To overcome these problems Sun People introduced "try with resources" in 1.7 version. 

## Try with Resoruces:
The main advantage of "try with resources" is the resources which are opened as part of try block will be closed automatically Once the control reaches end of the try block either normally or abnormally and hence we are not required to close explicitly so that the complexity of programming will be reduced. It is not required to write finally block 
explicitly and hence length of the code will be reduced and readability will be improved. 

```java
  try(BufferedReader br=new BufferedReader(new FileReade("abc.txt"))) 
  { 
    use br based on our requirement, br will be closed automatically , Onec control reaches end of try either normally or abnormally and we are not required to close explicitly 
  } 
  catch(IOException e) 
  { 
   // handling code 
  }
```

## Conclusions: 

1. We can declare any no of resources but all these resources should be seperated with ;(semicolon) 

  ```java
    try(R1 ; R2 ; R3) 
    { 
      ------------- 
    } 
  ```

2. All resources should be AutoCloseable resources. A resource is said to be auto closable if and only if the corresponding class implements the java.lang.AutoCloseable interface either directly or indirectly.

All database related, network related and file io related resources already implemented AutoCloseable interface. Being a programmer we should aware this point and we are not  required to do anything extra. 

3. AutoCloseable interface introduced in Java 1.7 Version and it contains only one method: close()

4. All resource reference variables should be final or effectively final and hence we can't perform reassignment within the try block. 

  ```java
    try(BufferedReader br=new BufferedReader(new FileReade("abc.txt"))) 
    { 
      br=new BufferedReader(new FileReader("abc.txt")); 
    } 
  ```

    CE : Can't reassign a value to final variable br

5. Untill 1.6 version try should be followed by either catch or finally but in 1.7 version we can take only try with resource without catch or finally 

  ```java
    try(R) 
    { 
      //valid 
    } 
  ```

6.The main advantage of "try with resources" is finally block will become dummy because we are not required to close resources of explicitly. 

## Problems with JDK 7 Try with Resources:
1. The resource reference variables which are created outside of try block cannot be used direclty in try with resources.
```java
  BufferedReader br=new BufferedReader(new FileReader("abc.txt")) 
  try(br) 
  { 
    // Risky code 
  } 
```

This syntax is invalid in until java 1.8V.

We should create the resource in try block primary list or we should declared with new reference variable in try block. i.e Resource reference variable should be local to try block.

## Solution-1: Creation of Resource in try block primary list

```java
  try(BufferedReader br=new BufferedReader(new FileReader("abc.txt"))) 
  { 
    // It is valid syntax in java 1.8V 
  } 
```

## Solution-2: Assign resource with new reference variable

```java
BufferedReader br=new BufferedReader(new FileReader("abc.txt")) 
try(BufferedReader br1=br) 
{ 
  // It is valid syntax in java 1.8V 
} 
```

But from JDK 9 onwards we can use the resource reference variables which are created outside of try block directly in try block resources list.i.e The resource reference variables 
need not be local to try block.

```java
BufferedReader br=new BufferedReader(new FileReader("abc.txt")) 
try(br) 
{ 
  // It is valid in JDK 9 but in valid until JDK 1.8V 
} 
```

But make sure resource(br) should be either final or effectively final. Effectively final means we should not perform reassignment.

This enhancement reduces length of the code and increases readability.

```java
MyResource r1 = new MyResource(); 
MyResource r2 = new MyResource(); 
MyResource r3 = new MyResource(); 
try(r1,r2,r3) 
{ 

} 
```

## Demo Program:
```java
class MyResource implements AutoCloseable 
{ 
  MyResource() 
  { 
    System.out.println("Resource Creation..."); 
  } 


  public void doProcess() 
  { 
    System.out.println("Resource Processing..."); 

  } 


  public void close() 
  { 
    System.out.println("Resource Closing..."); 
  } 
} 


class Test 
{ 
  public static void preJDK7() 
  { 
    MyResource r=null; 
    try 
    { 
      r=new MyResource(); 
      r.doProcess(); 
    } 
    catch (Exception e) 
    { 
      System.out.println("Handling:"+e); 
    } 
    finally 
    { 
      try 
      { 
        if (r!=null) 
        { 
          r.close(); 
        } 
      } 
      catch (Exception e) 
      { 
        System.out.println("Handling:"+e); 
      } 
    } 
  } 


  public static void JDK7() 
  { 
    try(MyResource r=new MyResource()) 
    { 
      r.doProcess(); 
    } 
    catch(Exception e) 
    { 
      System.out.println("Handling:"+e); 
    } 
  } 


  public static void JDK9() 
  { 
    MyResource r= new MyResource(); 
    try(r) 
    { 
      r.doProcess(); 
    } 
    catch(Exception e) 
    { 
      System.out.println("Handling:"+e); 
    } 
  } 


  public static void multipleJDK9() 
  { 
    MyResource r1= new MyResource(); 
    MyResource r2= new MyResource(); 
    MyResource r3= new MyResource(); 
    MyResource r4= new MyResource(); 
    try(r1;r2;r3;r4) 
    { 
      r1.doProcess(); 
      r2.doProcess(); 
      r3.doProcess(); 
      r4.doProcess(); 
    } 
    catch(Exception e) 
    { 
      System.out.println("Handling:"+e); 
    } 
  } 


  public static void main(String[] args) 
  { 
    System.out.println("Program Execution With PreJDK7"); 
    preJDK7(); 

    System.out.println("Program Execution With JDK7"); 
    JDK7(); 

    System.out.println("Program Execution With JDK9"); 
    JDK9(); 
    System.out.println("Program Execution Multiple Resources With JDK9"); 
    multipleJDK9(); 
  } 
}
```

Output:

```java
Program Execution With PreJDK7
Resource Creation...
Resource Processing...
Resource Closing...
Program Execution With JDK7
Resource Creation...
Resource Processing...
Resource Closing...
Program Execution With JDK9
Resource Creation...
Resource Processing...
Resource Closing...
Program Execution Multiple Resources With JDK9
Resource Creation...
Resource Creation...
Resource Creation...
Resource Creation...
Resource Processing...
Resource Processing...
Resource Processing...
Resource Processing...
Resource Closing...
Resource Closing...
Resource Closing...
Resource Closing...
```

# Diamond Operator Enhancements

This enhancement is as the part of Milling Project Coin (JEP 213).

Before understanding this enhancement, we should aware Generics concept, which has been introduced in java 1.5 version.

The main objectives of Generics are:

1. To provide Type Safety
2. To resolve Type Casting Problems.

## Case 1: Type-Safety

Arrays are always type safe. i.e we can give the guarantee for the type of elements present inside array. For example if our programming requirement is to hold String type of objects, it is recommended to use String array. For the string array we can add only string type of objects. By 
mistake if we are trying to add any other type we will get compile time error.

Eg:

```java
String[] s = new String[100]; 
s[0] = "Durga"; 
s[1] = "Pavan"; 
s[2] = new Integer(10);//error: incompatible types: Integer cannot be converted to String 
```

String[] can contains only String type of elements. Hence, we can always give guarantee for the type of elements present inside array. Due to this arrays are safe to use with respect to type. Hence arrays are type safe.

But collections are not type safe that is we can't give any guarantee for the type of elements present inside collection. For example if our programming requirement is to hold only string type of objects, and if we choose ArrayList, by mistake if we are trying to add any other type we won't 
get any compile time error but the program may fail at runtime.

```java
ArrayList l = new ArrayList(); 
l.add("Durga"); 
l.add("Pavan"); 
l.add(new Integer(10)); 
.... 
String name1=(String)l.get(0); 
String name2=(String)l.get(1); 
String name3=(String)l.get(2);//RE: java.lang ClassCastException
```

Hence we can't give any guarantee for the type of elements present inside collections. Due to this collections are not safe to use with respect to type, i.e collections are not Type-Safe.

## Case 2: Type-Casting
In the case of array at the time of retrieval it is not required to perform any type casting. 

```java
String[] s = new String[100]; 
s[0] = "Durga"; 
s[1] = "Pavan"; 
... 
String name1=s[0];//Type casting is not required. 
```

But in the case of collection at the time of retrieval compulsory we should perform type casting otherwise we will get compile time error. 

Eg:

```java
ArrayList l = new ArrayList(); 
l.add("Durga"); 
l.add("Pavan"); 
.... 
String name1=l.get(0);//error: incompatible types: Object cannot be converted to String 
String name1=(String)l.get(0);//valid 
```

Hence in Collections Type Casting is bigger headache. 

To overcome the above problems of collections(type-safety, type casting),Java people introduced Generics concept in 1.5 version.Hence the main objectives of Generics are:

 1. To provide Type Safety to the collections.
 2. To resolve Type casting problems. 

## Example for Generic Collection:

To hold only string type of objects, we can create a generic version of ArrayList as follows.

ArrayList<String> l = new ArrayList<String>();
Here String is called Parameter Type.

For this ArrayList we can add only string type of objects. By mistake if we are trying to add any other type then we will get compile time error.

```java
1) l.add("Durga");//valid 
2) l.add("Ravi");//valid 
3) l.add(new Integer(10));//error: no suitable method found for add(Integer) 
```

Hence, through generics we are getting type safety.

At the time of retrieval it is not required to perform any type casting we can assign elements directly to string type variables.

String name1 = l.get(0);//valid and Type Casting is not required.

Hence, through generic syntax we can resolve type casting problems.

## Difference between Generic and Non-Generic Collections:

## Java 7 Diamond Operator (<>):
Diamond Operator '<>' was introduced in JDK 7 under project Coin.

The main objective of Diamond Operator is to instantiate generic classes very easily.

Prior to Java 7, Programmer compulsory should explicitly include the Type of generic class in the Type Parameter of the constructor. 

```java
ArrayList<String> l = new ArrayList<String>();
```

Whenever we are using Diamond Operator, then the compiler will consider the type automatically based on context, Which is also known as Type inference. We are not required to specify Type Parameter of the Constructor explicitly.

```java
ArrayList<String> l = new ArrayList<>();
```

Hence the main advantage of Diamond Operator is we are not required to speicfy the type parameter in the constructor explicitly,length of the code will be reduced and readability will be improved.

Eg 2:

```java
 List<Map<String,Integer>> l = new ArrayList<Map<String,Integer>>();
 can be writtern with Diamond operator as follows
 List<Map<String,Integer>> l = new ArrayList<>();
```

But until Java 8 version we cannot apply diamond operator for Anonymous Generic classes. But in Java 9, we can use.

## Usage of Diamond Operator for Anonymous Classes:

In JDK 9, Usage of Diamond Operator extended to Anonymous classes also.

###  Anonymous class:

Sometimes we can declare classes without having the name, such type of nameless classes are called Anonymous Classes.

Eg 1:

```java
1) Thread t = new Thread() 
2) { 
3) }; 
```

We are creating a child class that extends Thread class without name(Anonymous class) and we are creating object for that child class.

Eg 2:

```java
Runnable r = new Runnable() 
{ 
}; 
```

We are creating an implementation class for Runnable interface without name(Anonymous class) and we are creating object for that implementation class.

Eg 3:

```java
ArrayList<String> l = new ArrayList<String>() 
{ 
}; 
```

We are creating a child class that extends ArrayList class without name(Anonymous class) and we are creating object for that child class.

From JDK 9 onwards we can use Diamond Operator for Anonymous Classes also.

```java
ArrayList<String> l = new ArrayList<>() 
{ 
}; 
```

It is valid in Java 9 but invalid in Java 8.

**Demo Program - 1**: To demonstrate usage of diamond operator for Anonymous Class

```java
class MyGenClass<T> 
{ 
  T obj; 

  public MyGenClass(T obj) 
  { 
    this.obj = obj; 
  } 

  public T getObj() 
  { 
    return obj; 
  } 


  public void process() 
  { 
    System.out.println("Processing obj..."); 
  } 

} 


public class Test 
{ 
  public static void main(String[] args) 
  { 
    MyGenClass<String> c1 = new MyGenClass<String>("Durga") 
    { 
      public void process() 
      { 
        System.out.println("Processing... " + getObj()); 
      } 
    };

    c1.process(); 

    MyGenClass<String> c2 = new MyGenClass<>("Pavan") 
    { 
      public void process() 
      { 
        System.out.println("Processing... " + getObj()); 
      } 
    }; 

    c2.process(); 
  } 
} 
```

Output:

```java
Processing... Durga
Processing... Pavan
```

If we compile the above program according to Java 1.8 version,then we will get compile time error

```java
D:\durga_classes>javac -source 1.8 Test.java
error: cannot infer type arguments for MyGenClass<T>

MyGenClass<String> c2 = new MyGenClass<>("Pavan")
 ^
reason: cannot use '<>' with anonymous inner classes in -source 1.8 (use -source 9 or higher to enable '<>' with anonymous inner classes)
```

**Demo Program - 2**: To demonstrate usage of diamond operator for Anonymous Clas

```java
import java.util.Iterator; 
import java.util.NoSuchElementException; 
public class DiamondOperatorDemo 
{ 
  public static void main(String[] args) 
  { 
    String[] animals = { "Dog", "Cat", "Rat", "Tiger","Elephant" }; 
    Iterator<String> iter = new Iterator<>() 
    { 
      int i = 0; 

      public boolean hasNext() 
      { 
        return i < animals.length; 
      } 

      public String next() 
      { 
        if (!hasNext()) 
        throw new NoSuchElementException(); 
        return animals[i++]; 
      } 

    }; 

    while (iter.hasNext()) 
    { 
      System.out.println(iter.next()); 
    } 
  } 
} 
```

Output:

```java
Dog
Cat
Rat
Tiger
Elephant
```

Note - 1:

```java
ArrayList<String> preJava7 = new ArrayList<String>(); 
ArrayList<String> java7 = new ArrayList<>(); 
ArrayList<String> java9 = new ArrayList<>() 
{ 
}; 
```

Note - 2:

Be Ready for Partial Diamond Operator in the next versions of Java, as the part of Project "Amber". Open JDK people already working on this.

Eg: 

```java
new Test<String,_>();
```

# SafeVarargs Annotation Enhancements
This SafeVarargs Annotation was introduced in Java 7.

Prior to Java 9,we can use this annotation for final methods, static methods and constructors.

But from Java 9 onwards we can use for private methods also.

To understand the importance of this annotation, first we should aware var-arg methods and heap pollution problem.

## What is var-arg method?
Until 1.4 version, we can't declared a method with variable number of arguments. If there is a change in no of arguments compulsory we have to define a new method. This approach increases length of the code and reduces readability.

But from 1.5 version onwards, we can declare a method with variable number of arguments, such type of methods are called var-arg methods.

```java
public class Test 
{ 

  public static void m1(int... x) 
  { 
    System.out.println("var-arg method"); 
  } 


  public static void main(String[] args) 
  { 
    m1(); 
    m1(10); 
    m1(10,20,30); 
  } 

}
```

Output

```java
var-arg method
var-arg method
var-arg method
```

Internally var-arg parameter will be converted into array.

```java
public class Test 
{ 

  public static void sum(int... x) 
  { 
    int total=0; 
    for(int x1 : x) 
    { 
      total=total+x1; 
    } 
    System.out.println("The Sum:"+ total); 
  } 


  public static void main(String[] args) 
  { 
    sum(); 
    sum(10); 
    sum(10,20,30); 
  } 

} 
```

Output

```java
The Sum:0
The Sum:10
The Sum:60
```

## Var-arg method with Generic Type:
If we use var-arg methods with Generic Type then there may be a chance of Heap Pollution. At runtime if one type variable trying to point to another type value, then there may be a chance of ClasssCastException. This problem is called Heap Pollution.

In our code, if there is any chance of heap pollution then compiler will generate warnings.

```java
  import java.util.*; 
  public class Test 
  { 

    public static void main(String[] args) 
    { 
      List<String> l1= Arrays.asList("A","B"); 
      List<String> l2= Arrays.asList("C","D"); 
      m1(l1,l2); 
    } 


    public static void m1(List<String>... l)//argument will become List<String>[] 
    { 
      Object[] a = l;// we can assign List[] to Object[] 
      a[0]=Arrays.asList(10,20); 
      String name=(String)l[0].get(0);//String type pointing to Integer type 
      System.out.println(name); 
    } 

  } 
```

**Compilation**:

```java
javac Test.java
Note: Test.java uses unchecked or unsafe operations.
Note: Recompile with -Xlint:unchecked for details.

javac -Xlint:unchecked Test.java
warning: [unchecked] unchecked generic array creation for varargs parameter of type 
List<String>[]
m1(l1,l2);
 ^
warning: [unchecked] Possible heap pollution from parameterized vararg type List<String>
 public static void m1(List<String>... l)
 ^
2 warnings
```

**Execution**:

```java
java Test
RE: java.lang.ClassCastException: java.base/java.lang.Integer cannot be cast to 
java.base/java.lang.String
```

In the above program at runtime, String type variable name is trying to point to Integer type, which causes Heap Pollution and results ClassCastException.

```java
String name = (String)l[0].get(0)
```

## Need of @SafeVarargs Annotation:
Very few Var-arg Methods causes Heap Pollution, not all the var-arg methods. If we know that our method won't cause Heap Pollution, then we can suppress compiler warnings with @SafeVarargs annotation.

```java
import java.util.*; 
public class Test 
{ 

  public static void main(String[] args) 
  { 
    List<String> l1= Arrays.asList("A","B"); 
    List<String> l2= Arrays.asList("C","D"); 
    m1(l1,l2); 
  } 


  @SafeVarargs 
  public static void m1(List<String>... l) 
  { 
    for(List<String> l1: l) 
    { 
      System.out.println(l1); 
    } 
  } 

} 
```

Output:

```java
[A, B]
[C, D]
```

In the program, inside m1() method we are not performing any reassignments. Hence there is no chance of Heap Pollution Problem. Hence we can suppress Compiler generated warnings with @SafeVarargs annotation.

Note: At compile time observe the difference with and without SafeVarargs Annotation.

## Java 9 Enhancements to @SafeVarargs Annotation:
@SafeVarargs Annotation introduced in Java 7.

Unitl Java 8, this annotation is applicable only for static methods,final methods and constructors. But from Java 9 onwards,we can also use for private instance methods also.

```java
import java.util.*; 
public class Test 
{ 

  @SafeVarargs //valid 
  public Test(List<String>... l) 
  { 
  } 


  @SafeVarargs //valid 
  public static void m1(List<String>... l) 
  { 

  } 


  @SafeVarargs //valid 
  public final void m2(List<String>... l) 
  { 

  } 


  @SafeVarargs //valid in Java 9 but not in Java 8 
  private void m3(List<String>... l) 
  { 
  }

}
```

```java
javac -source 1.8 Test.java
error: Invalid SafeVarargs annotation. Instance method m3(List<String>...) is not final.
 private void m3(List<String>... l)
 ^
javac -source 1.9 Test.java
We won't get any compile time error.
```

## FAQs:

Q1. For which purpose we can use @SafeVarargs annotation?

Q2. What is Heap Pollution? 


# Factory Methods for creating unmodifiable Collections

**List**: An indexed Collection of elements where duplicates are allowed and insertion order is preserved.
<br>
<br>
**Set**: An unordered Collection of elements where duplicates are not allowed and insertion order is not preserved.
<br>
<br>
**Map**: A Map is a collection of key-value pairs and each key-value pair is called Entry.Entry is an inner interface present inside Map interface.Duplicate keys are not allowed,but values can be duplicated.

As the part of programming requirement, it is very common to use Immutable Collection objects to improve Memory utilization and performance.

Prior to Java 9,we can create unmodifiable Collection objects as follows

**Eg 1**: Creation of unmodifiable List object

```java
List<String> beers=new ArrayList<String>(); 
beers.add("KF"); 
beers.add("FO"); 
beers.add("RC"); 
beers.add("FO"); 
beers =Collections.unmodifiableList(beers); 
```


**Eg 2**: Creation of unmodifiable Set Object

```java
Set<String> beers=new HashSet<String>(); 
beers.add("KF"); 
beers.add("KO"); 
beers.add("RC"); 
beers.add("FO"); 
beers =Collections.unmodifiableSet(beers); 
```

**Eg 3**: Creation of unmodifiable Map object 

```java
Map<String,String> map=new HashMap<String,String>(); 
map.put("A","Apple"); 
map.put("B","Banana"); 
map.put("C","Cat"); 
map.put("D","Dog"); 
map =Collections.unmodifiableMap(map); 
```

This way of creating unmodifiable Collections is verbose and not convenient.It increases length of the code and reduces readability.

JDK Engineers addresses this problem and introduced several factory methods for creating unmodifiable collections.

## Creation of unmodifiable List (Immutable List) with Java 9 Factory Methods:

Java 9 List interface defines several factory methods for this.

```java
1. static <E> List<E> of() 
2. static <E> List<E> of(E e1) 
3. static <E> List<E> of(E e1, E e2) 
4. static <E> List<E> of(E e1, E e2, E e3) 
5. static <E> List<E> of(E e1, E e2, E e3, E e4) 
6. static <E> List<E> of(E e1, E e2, E e3, E e4, E e5) 
7. static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6) 
8. static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7) 
9. static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8) 
10.static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9) 
11.static <E> List<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9, E e10) 
12. static <E> List<E> of(E... elements) 
```

Upto 10 elements the matched method will be executed and for more than 10 elements internally var-arg method will be called.JDK Enginerrs identified List of upto 10 elements is 
the common requirement and hence they provided the corresponding methods. For remaining cases var-arg method will be executed,which is very costly. These many 
methods just to improve performance.

**Eg**: To create unmodifiable List with Java 9 Factory Methods.

```java
List<String> beers = List.of("KF","KO","RC","FO");
```
It is very simple and straight forward way.

**Note**:
1. While using these factory methods if any element is null then we will get NullPointerException.

```java
List<String> fruits = List.of("Apple","Banana",null); -> NullPointerException
```

2. After creating the List object,if we are trying to change the content(add|remove|replace elements)then we will get UnsupportedOperationException b'z List is immutable(unmodifiable).

```java
List<String> fruits=List.of("Apple","Banana","Mango");
fruits.add("Orange"); //UnsupportedOperationException
fruits.remove(1); //UnsupportedOperationException 
fruits.set(1,"Orange"); //UnsupportedOperationException
```

## Creation of unmodifiable Set(Immutable Set) with Java 9 Factory Methods:

Java 9 Set interface defines several factory methods for this.

```java
1. static <E> Set<E> of() 
2. static <E> Set<E> of(E e1) 
3. static <E> Set<E> of(E e1, E e2) 
4. static <E> Set<E> of(E e1, E e2, E e3) 
5. static <E> Set<E> of(E e1, E e2, E e3, E e4) 
6. static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5) 
7. static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6) 
8. static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7) 
9. static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8) 
10.static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9) 
11.static <E> Set<E> of(E e1, E e2, E e3, E e4, E e5, E e6, E e7, E e8, E e9, E e10) 
12. static <E> Set<E> of(E... elements) 
```

**Eg**: To create unmodifiable Set with Java 9 Factory Methods.

```java
 Set<String> beers = Set.of("KF","KO","RC","FO");
```

**Note**:
1. While using these Factory Methods if we are trying to add duplicate elements then we will get IllegalArgumentException,b'z Set won't allow duplicate elements

```java
Set<Integer> numbers=Set.of(10,20,30,10);
RE: IllegalArgumentException: duplicate element: 10
```

2. While using these factory methods if any element is null then we will get NullPointerException.

```java
 Set<String> fruits=Set.of("Apple","Banana",null); -> NullPointerException
 ```

3. After creating the Set object, if we are trying to change the content(add|remove elements)then we will get UnsupportedOperationException b'z Set is immutable(unmodifiable).

```java
 Set<String> fruits=Set.of("Apple","Banana","Mango");
 fruits.add("Orange"); //UnsupportedOperationException
 fruits.remove("Apple"); //UnsupportedOperationException
 ```

## Creation of unmodifiable Map (Immutable Map) with Java 9 Factory Methods:

Java 9 Map interface defines of() and ofEntries() Factory methods for this purpose.

```java
1. static <K,V> Map<K,V> of() 
2. static <K,V> Map<K,V> of(K k1,V v1)
3. static <K,V> Map<K,V> of(K k1,V v1,K k2,V v2)
4. static <K,V> Map<K,V> of(K k1,V v1,K k2,V v2,K k3,V v3)
5. static <K,V> Map<K,V> of(K k1,V v1,K k2,V v2,K k3,V v3,K k4,V v4)
6. static <K,V> Map<K,V> of(K k1,V v1,K k2,V v2,K k3,V v3,K k4,V v4,K k5,V v5)
7. static <K,V> Map<K,V> of(K k1,V v1,K k2,V v2,K k3,V v3,K k4,V v4,K k5,V v5,K k6,V v6)
8. static <K,V> Map<K,V> of(K k1,V v1,K k2,V v2,K k3,V v3,K k4,V v4,K k5,V v5,K k6,V v6,K 
k7,V v7)
9. static <K,V> Map<K,V> of(K k1,V v1,K k2,V v2,K k3,V v3,K k4,V v4,K k5,V v5,K k6,V v6,K 
k7,V v7,K k8,V v8)
10.static <K,V> Map<K,V> of(K k1,V v1,K k2,V v2,K k3,V v3,K k4,V v4,K k5,V v5,K k6,V v6,K 
k7,V v7,K k8,V v8,K k9,V v9)
11.static <K,V> Map<K,V> of(K k1,V v1,K k2,V v2,K k3,V v3,K k4,V v4,K k5,V v5,K k6,V v6,K 
k7,V v7,K k8,V v8,K k9,V v9,K k10,V v10)
12.static <K,V> Map<K,V> ofEntries(Map.Entry<? extends K,? extends V>... entries)
```

**Note**: 
Up to 10 entries,it is recommended to use of() methods and for more than 10 items we should use ofEntries() method.

**Eg**:

```java
Map<String,String> map=Map.of("A","Apple","B","Banana","C","Cat","D","Dog");
```

## How to use Map.ofEntries() method:
Map interface contains static Method entry() to create immutable Entry objects.

```java
Map.Entry<String,String> e=Map.entry("A","Apple");
```

This Entry object is immutable and we cannot modify its content. If we are trying to change we will get RE: UnsupportedOperationException

```java
e.setValue("Durga");  UnsupportedOperationException
```

By using these Entry objects we can create unmodifiable Map object with Map.ofEntries() method.

**Eg**:

```java
import java.util.*; 
class Test 
{ 

  public static void main(String[] args) 
  { 
    Map.Entry<String,String> e1=Map.entry("A","Apple"); 
    Map.Entry<String,String> e2=Map.entry("B","Banana"); 
    Map.Entry<String,String> e3=Map.entry("C","Cat"); 
    Map<String,String> m=Map.ofEntries(e1,e2,e3); 
    System.out.println(m); 

  } 
} 
```

In Short way we can also create as follows.

```java
import static java.util.Map.entry; 
Map<String,String> map=Map.ofEntries(entry("A","Apple"),entry("B","Banana"),entry("C","Cat"),entry("D","Dog")); 
```

**Note**:
1. While using these Factory Methods if we are trying to add duplicate keys then we will 
get IllegalArgumentException:duplicate key.But values can be duplicated.

```java
 Map<String,String> map=Map.of("A","Apple","A","Banana","C","Cat","D","Dog");
 RE: java.lang.IllegalArgumentException: duplicate key: A
 ```

2. While using these factory methods if any element is null(either key or value) then we will get NullPointerException.

```java
 Map<String,String> map=Map.of("A",null,"B","Banana"); ==>NullPointerException
 Map<String,String> map=Map.ofEntries(entry(null,"Apple"),entry("B","Banana"));
 -> NullPointerException 
 ```

 3. After creating the Map object, if we are trying to change the content(add|remove|replace elements)then we will get UnsupportedOperationException b'z Map is immutable(unmodifiable).

**Eg**:

```java
Map<String,String> map=Map.ofEntries(entry("A","Apple"),entry("B","Banana"));
map.put("C","Cat");  UnsupportedOperationException
map.remove("A");  UnsupportedOperationException
```

## Serialization for unmodifiable Collections:
The immutable collection objects are serializable iff all elements are serializable. In Brief form,the process of writing state of an object to a file is called Serialization and the process of reading state of an object from the file is called Deserialization.

```java
import java.util.*; 
import java.io.*; 
class Employee implements Serializable 
{ 
  private int eno; 
  private String ename; 

  Employee(int eno,String ename) 
  { 
    this.eno=eno; 
    this.ename=ename; 
  } 


  public String toString() 
  { 
    return String.format("%d=%s",eno,ename); 
  } 
} 
class Test 
{ 
  public static void main(String[] args) throws Exception 
  { 
    Employee e1= new Employee(100,"Sunny"); 
    Employee e2= new Employee(200,"Bunny"); 
    Employee e3= new Employee(300,"Chinny"); 
    List<Employee> l1=List.of(e1,e2,e3); 
    System.out.println(l1); 

    System.out.println("Serialization of List Object..."); 
    FileOutputStream fos=new FileOutputStream("emp.ser"); 
    ObjectOutputStream oos=new ObjectOutputStream(fos); 
    oos.writeObject(l1); 

    System.out.println("Deserialization of List Object..."); 
    FileInputStream fis=new FileInputStream("emp.ser"); 
    ObjectInputStream ois=new ObjectInputStream(fis); 
    List<Employee> l2=(List<Employee>)ois.readObject(); 
    System.out.println(l2); 
    //l2.add(new Employee(400,"Vinnny"));//UnsupportedOperationException 
  } 
} 
```

o/p: 

```java
D:\durga_classes>java Test
[100=Sunny, 200=Bunny, 300=Chinny]
Serialization of List Object...
Deserialization of List Object...
[100=Sunny, 200=Bunny, 300=Chinny]
```

After deserialization also we cannot modify the content,otherwise we will get UnsupportedOperationException.

**Note**: The Factroy Methods introduced in Java 9 are not to create general collections and 
these are meant for creating immutable collections.

# Stream API Enhancements
Streams concept has been introduced in Java 1.8 version.

The main objective of Streams concept is to process elements of Collection with Functional Programming (Lambda Expressions).

## What is the difference between java.util streams and java.io streams? 
java.util streams meant for processing objects from the collection. ie. it represents a stream of objects from the collection but java.io streams meant for processing binary and character data with respect to file. i.e it represents stream of binary data or character data from the file. Hence 
java.io streams and java.util streams are different concepts.

## What is the difference between Collections and Streams?
If we want to represent a group of individual objects as a single entity, then we should go for collection. If we want to process a group of objects from the collection then we should go for Streams.

## How to Create Stream Object?
We can create stream object to the collection by using stream() method of Collection interface. stream() method is a default method added to the Collection in 1.8 version. 

```java
default Stream stream()
```

**Ex**: 

```java
Stream s = c.stream(); // c is any Collection object

```

**Note**: Stream is an interface present in java.util.stream package.

## How to process Objects of Collection By using Stream:
Once we got the stream, by using that we can process objects of that collection. For this we can use either filter() method or map() method.

## Processing Objects by using filter() method:
We can use filter() method to filter elements from the collection based on some boolean condition.


```java
public Stream filter(Predicate<T> t)
```
Here (Predicate<T > t ) can be a boolean valued function/lambda expression 

## Demo Program:

```java
import java.util.*; 
import java.util.stream.*; 
public class Test 
{ 
  public static void main(String[] args) 
  { 
    ArrayList<Integer> l1 = new ArrayList<Integer>(); 
    for(int i =0; i <=10; i++) 
    { 
      l1.add(i); 
    } 
    System.out.println("Before Filtering:"+l1); 
    List<Integer> l2=l1.stream().filter(i->i%2==0).collect(Collectors.toList()); 
    System.out.println("After Filtering:"+l2); 
  } 
} 
```

Output:

```java
Before Filtering:[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
After Filtering:[0, 2, 4, 6, 8, 10]
```

## Processing Objects by using map() method:
If we want to create a separate new object, for every object present in the collection based on our requirement then we should go for map() method of Stream interface. 

```java
public Stream map (Function f);
```

The argument can be lambda expression also 

## Demo Program:

```java
import java.util.*; 
import java.util.stream.*; 
public class Test 
{ 
  public static void main(String[] args) 
  { 
    ArrayList<Integer> l1 = new ArrayList<Integer>(); 
    for(int i =0; i <=10; i++) 
    { 
      l1.add(i); 
    } 
    System.out.println("Before using map() method:"+l1); 
    List<Integer> l2=l1.stream().map(i->i*i).collect(Collectors.toList()); 
    System.out.println("After using map() method:"+l2); 
  } 
}
```

Output:

```java
Before using map() method:[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
After using map() method:[0, 1, 4, 9, 16, 25, 36, 49, 64, 81, 100]
```

## Processing Objects by using flatMap() method:

Both map and flatMap can be applied to a Stream<T> and they both return a Stream<R>. The difference is that the map operation produces one output value for each input value, whereas the flatMap operation produces an arbitrary number (zero or more) values for each input value.

Typical use is for the mapper function of flatMap to return Stream.empty() if it wants to send zero values, or something like Stream.of(x, y, z) if it wants to return several values.

## Demo Program:
```java
import java.util.*; 
import java.util.stream.*; 
public class Test 
{ 
  public static void main(String[] args) 
  { 

    ArrayList<Integer> l1 = new ArrayList<Integer>(); 
    for(int i =0; i <=10; i++) 
    { 
      l1.add(i); 
    } 
    System.out.println("Before using map() method:"+l1); 

    List<Integer> l2=l1.stream().flatMap(i->
    { 
      if (i%2 !=0) 
        return Stream.empty(); 
      else 
        return Stream.of(i); 
    }).collect(Collectors.toList()); 
    System.out.println("After using flatMap() method:"+l2); 

    List<Integer> l3=l1.stream().flatMap(i->
    { 
      if (i%2 !=0) 
        return Stream.empty(); 
      else 
        return Stream.of(i,i*i); 
    }).collect(Collectors.toList()); 
    System.out.println("After using flatMap() method:"+l3); 
  } 
} 
```

Output:

```java
D:\durga_classes>java Test
Before using map() method:[0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]
After using flatMap() method:[0, 2, 4, 6, 8, 10]
After using flatMap() method:[0, 0, 2, 4, 4, 16, 6, 36, 8, 64, 10, 100]
```

## Q. What is the difference between map() and flatMap() methods?

## Java 9 Enhancements for Stream API:

In Java 9 as the part of Stream API, the following new methods introduced.

1. takeWhile()
2. dropWhile()
3. Stream.iterate()
4. Stream.ofNullable()

**Note**: takeWhile() and dropWhile() methods are default methods and iterate() and ofNullable() 
are static methods of Stream interface.

## 1. takeWhile():
It is the default method present in Stream interface.

```java
default Stream takeWhile(Predicate p)
```

It returns the stream of elements that matches the given predicate.

It is similar to filter() method.

## Difference between takeWhile() and filter():
filter() method will process every element present in the stream and consider the element if predicate is true.

But, in the case of takeWhile() method, there is no guarantee that it will process every element of the Stream. It will take elements from the Stream as long as predicate returns true. If predicate returns false, at that point onwards remaining elements won't be processed, i.e rest of the Stream is discarded.

**Eg**: Take elements until we will get even numbers. Once we got odd number then stop and ignore rest of the stream.

## Demo Program:
```java
import java.util.*; 
import java.util.stream.*; 
public class Test 
{ 
  public static void main(String[] args) 
  { 
    ArrayList<Integer> l1 = new ArrayList<Integer>(); 
    l1.add(2); 
    l1.add(4); 
    l1.add(1); 
    l1.add(3); 
    l1.add(6); 
    l1.add(5); 
    l1.add(8); 
    System.out.println("Initial List:"+l1); 
    List<Integer> l2=l1.stream().filter(i->i%2==0).collect(Collectors.toList()); 
    System.out.println("After Filtering:"+l2); 
    List<Integer> l3=l1.stream().takeWhile(i->i%2==0).collect(Collectors.toList()); 
    System.out.println("After takeWhile:"+l3); 
  } 
} 
```

Output:

```java
Initial List:[2, 4, 1, 3, 6, 5, 8]
After Filtering:[2, 4, 6, 8]
After takeWhile:[2, 4]
```

**Eg 2**:

```java
Stream.of("A","AA","BBB","CCC","CC","C").takeWhile(s-
>s.length()<=2).forEach(System.out::println);
```

Output:

```java
A
AA
```

## 2. dropWhile()
It is the default method present in Stream interface.

```java
default Stream dropWhile(Predicate p)
```

It is the opposite of takeWhile() method.

It drops elements instead of taking them as long as predicate returns true. Once predicate returns false then rest of the Stream will be returned.

## Demo Program:

```java
import java.util.*; 
import java.util.stream.*; 
public class Test 
{ 
  public static void main(String[] args) 
  { 
    ArrayList<Integer> l1 = new ArrayList<Integer>(); 
    l1.add(2); 
    l1.add(4); 
    l1.add(1); 
    l1.add(3); 
    l1.add(6); 
    l1.add(5); 
    l1.add(8); 
    System.out.println("Initial List:"+l1); 
    List<Integer> l2=l1.stream().dropWhile(i->i%2==0).collect(Collectors.toList()); 
    System.out.println("After dropWhile:"+l2); 
  } 
} 
```

Output:

```java
Initial List:[2, 4, 1, 3, 6, 5, 8]
After dropWhile:[1, 3, 6, 5, 8]
```

**Eg 2**:
```java
Stream.of("A","AA","BBB","CCC","CC","C").dropWhile(s-
>s.length()<=2).forEach(System.out::println);
```

Output:

```java
BBB
CCC
CC
C
```

## 3. Stream.iterate():

It is the satic method present in Stream interface.

### Form-1: iterate() method with 2 Arguments

This method introduced in Java 8.

```java
public static Stream iterate (T initial,UnaryOperator<T> f)
```

It takes an initial value and a function that provides next value.

**Eg**: 

```java
Stream.iterate(1,x->x+1).forEach(System.out::println);
```

Output:

```java
1
2
3
...infinite times
```

## How to limit the number of iterations:

For this we can use limit() method.

**Eg**: 

```java
Stream.iterate(1,x->x+1).limit(5).forEach(System.out::println);
```
Output:

```java
1
2
3
4
5
```

## Form-2: iterate() method with 3 arguments

The problem with 2 argument iterate() method is there may be a chance of infinite loop. To avoid, we should use limit method.

To prevent infinite loops, in Java 9, another version of iterate() method introduced, which is nothing but 3-arg iterate() method.

This method is something like for loop

```java
for(int i =0;i<10;i++){}
public static Stream iterate(T initial,Predicate conditionCheck,UnaryOperator<T> f)
```

This method takes an initial value,

 A terminate Predicate

 A function that provides next value.

**Eg**: 
```java
Stream.iterate(1,x->x<5,x->x+1).forEach(System.out::println);
```

Output:

```java
1
2
3
4
```

## 4. ofNullable():

```java
public static Stream<T> ofNullable(T t)
```

This method will check whether the provided element is null or not. If it is not null, then this method returns the Stream of that element. If it is null then this method returns empty stream.

This method is helpful to deal with null values in the stream
The main advantage of this method is to we can avoid NullPointerException and null checks everywhere.

Usually we can use this method in flatMap() to handle null values.

**Eg 1**:

```java
List l=Stream.ofNullable(100).collect(Collectors.toList());
System.out.println(l);
```

Output:[100]

**Eg 2**:
```java
List l=Stream.ofNullable(null).collect(Collectors.toList());
System.out.println(l);
```

Output: []

## Demo Program:

```java
import java.util.*; 
import java.util.stream.*; 
import java.util.*; 
import java.util.stream.*; 
public class Test 
{ 
  public static void main(String[] args) 
  { 
    List<String> l=new ArrayList<String>(); 
    l.add("A"); 
    l.add("B"); 
    l.add(null); 
    l.add("C"); 
    l.add("D"); 
    l.add(null); 
    System.out.println(l); 

    List<String> l2= l.stream().filter(o->o!=null).collect(Collectors.toList()); 
    System.out.println(l2); 

    List<String> l3= l.stream()
    .flatMap(o->Stream.ofNullable(o)).collect(Collectors.toList()); 
    System.out.println(l3); 
  } 
} 
```

Output:

```java
[A, B, null, C, D, null]
[A, B, C, D]
[A, B, C, D]
```

## Demo Program:

```java
import java.util.*; 
import java.util.stream.*; 
public class Test 
{ 
  public static void main(String[] args) 
  { 
    Map<String,String> m=new HashMap<>(); 
    m.put("A","Apple"); 
    m.put("B","Banana"); 
    m.put("C",null); 
    m.put("D","Dog"); 
    m.put("E",null); 
    List<String> l=m.entrySet().stream().map(e->e.getKey()).collect(Collectors.toList()); 
    System.out.println(l); 

    List<String> l2=m.entrySet().stream()
    .flatMap(e->Stream.ofNullable(e.getValue())).collect(Collectors.toList()); 
    System.out.println(l2); 

  } 
} 
```

Output:

```java
[A, B, C, D, E]
[Apple, Banana, Dog]
```

# JLINK (Java Linker)

Until 1.8 version to run a small Java program (like Hello World program) also, we should use a bigger JRE which contains all java's inbuilt 4300+ classes. It increases the size of Java Runtime environment and Java applications. Due to this Java is not suitable for IOT devices and Micro
Services. (No one invite a bigger Elephant into their small house).

To overcome this problem, Java people introduced Compact Profiles in Java 8. But they didn't succeed that much. In Java 9, they introduced a permanent solution to reduce the size of Java Runtime Environment, which is nothing but JLINK.

JLINK is Java's new command line tool(which is available in JDK_HOME\bin) which allows us to link sets of only required modules (and their dependencies) to create a runtime image (our own JRE).

Now, our Custom JRE contains only required modules and classes instead of having all 4300+ classes.

It reduces the size of Java Runtime Environment, which makes java best suitable for IOT and micro 
services.

Hence, Jlink's main intention is to avoid shipping everything and, also, to run on very small devices with little memory. By using Jlink, we can get our own very small JRE.

Jlink also has a list of plugins(like compress) that will help optimize our solutions.

## How to use JLINK: Demo Program

src
|-demoModule
 |-module-info.java
 |-packA
 |-Test.java
 
## module-info.java**:

```java
module demoModule 
{ 
}
```

## Test.java:
```java
package packA; 
public class Test 
{ 
  public static void main(String[] args) 
  { 
    System.out.println("JLINK Demo To create our own customized & small JRE"); 
  } 
}
```

## Compilation:
```java
C:\Users\Durga\Desktop>javac --module-source-path src -d out -m demoModule
```

## Run with default JRE:

```java
C:\Users\Durga\Desktop>java --module-path out -m demoModule/packA.Test
```
o/p: JLINK Demo To create our own customized & small JRE

## Creation of our own JRE only with required modules:

demoModule requires java.base module. Hence add java.base module to out directory
(copy java.base.jmod from jdk-9\jmods to out folder)

```java
out
|-java.base.jmod
|-demoModule
 |-module-info.class
 |-packA
 |-Test.class
```

Now we can create our own JRE with JLINK command

C:\Users\Durga\Desktop>jlink --module-path out --add-modules demoModule,java.base --output durgajre

Now observe the size of durgajre is just 35.9MB which is very small when compared with default JRE size 203MB.

We can run our application with our own custom jre (durgajre) as follows

```java
C:\Users\Durga\Desktop\durgajre\bin>java -m demoModule/packA.Test
```

**o/p**: JLINK Demo To create our own customized & small JRE

## Compressing the size of JRE with compress plugin:

Still we can compress the size of JRE with compress plugin

```java
C:\Users\Durga\Desktop>jlink --module-path out --add-modules demoModule,java.base --compress 2 --output durgajre2
C:\Users\Durga\Desktop\durgajre2\bin>java -m demoModule/packA.Test
```
**o/p**: JLINK Demo To create our own customized & small JRE

## Providing our own name to the application with launcher plugin:

```java
C:\Users\Durga\Desktop>jlink --module-path out --add-modules demoModule,java.base --launcher demoapp=demoModule/packA.Test --compress 2 --output durgajre
```

## Providing our own name to the application with launcher plugin:

```java
C:\Users\Durga\Desktop>jlink --module-path out --add-modules demoModule,java.base --launcher demoapp=demoModule/packA.Test --compress 2 --output durgajre3
```

Now we can run our application only with the name demoapp

```java
C:\Users\Durga\Desktop\durgajre3\bin>demoapp
```

JLINK Demo To create our own customized & small JRE
If we set the path 

```java
PATH =C:\Users\Durga\Desktop\durgajre3\bin
```
Then we can run our application from anywhere.

```java
D:\>demoapp
E:\>demoap
```

# Process API Updates (JEP-102)

Unitl java 8, communicating with processor/os/machine is very difficult. We required to write very complex native code and we have to use 3rd party jar files.

The way of communication with processor is varied from system to system (i.e. os to os). For example, in windows one way, but in Mac other way. Being a programmer we have to write code based on operating system, which makes programming very complex.

To resolve this complexity, JDK 9 engineers introduced several enhancements to Process API. By using this Updated API, we can write java code to communicate with any processor very easily.

According to worldwide Java Developers, Process API Updates is the number 1 feature in Java 9.

With this Enhanced API, we can perform the following activities very easily.

1. Get the Process ID (PID) of running process.
2. Create a new process
3. Destroy already running process
4. Get the process handles for processes
5. Get the parent and child processes of running process
6. Get the process information like owner, children,...
etc...

## What's New in Java 9 Process API:
1. Added several new methods (like pid(),info() etc) to Process class.

2. Added several new methods (like startPipeline()) to ProcessBuilder class. We can use ProcessBuilder class to create operating system processes.

3. Introduced a new powerful interface ProcessHandle. With this interface, we can access current running process, we can access parent and child processes of a particular process etc.

4. Introduced a new interface ProcessHandle.Info, by using this we can get complete information of a particular process.

Note: All these classes and interfaces are part of java.lang package and hence we are not required to use any import statement.

## How to get ProcessHandle object:
It is the most powerful and useful interface introduced in java 9.

We can get ProcessHandle object as follows

1. **ProcessHandle handle=ProcessHandle.current();**
 Returns the ProcessHandle of current running Process

2. **ProcessHandle handle=p.toHandle();**
 Returns the ProcessHandle of specified Process object.

3. **Optional<ProcessHandle> handle=ProcessHandle.of(PID);**
 Returns the ProcessHandle of proccess with the specified pid.
 Here, the return type is Optional, because PID may exist or may not exist.

## Use Case-1: To get the process ID (PID) of current process

```java
public class Test 
{ 
  public static void main(String[] args) throws Exception 
  { 
    ProcessHandle p=ProcessHandle.current(); 
    long pid=p.pid(); 
    System.out.println("The PID of current running JVM instance :"+pid); 
    Thread.sleep(100000); 
  } 
} 
```

We can see this process id in Task Manager (alt+ctrl+delete in windows)

## ProcessHandle.Info:

We can get complete information of a particular process by using ProcessHandle.Info object.

We can get this Info object as follows.
```java
ProcessHandle p = ProcessHandle.current();
ProcessHandle.Info info = p.info();
```
Once we got Info object, we can call the following methods on that object.

1. **user()**:
 Return the user of the process.
```java
 public Optional<String> user()
```

2. **command()**:
 Returns the command,that can be used to start the process.

 ```java
 public Optional<String> command()
 ```

3. **startInstant()**:
 Returns the start time of the process.

 ```java
 public Optional<String> startInstant()
```

4. **totalCpuDuration()**:
 Returns the total cputime accumulated of the process.
  
```java
 public Optional<String> totalCpuDuration()
```

## Use Case-2: To get snapshot of the current running process info

```java
public class Test 
{ 
  public static void main(String[] args) throws Exception 
  { 
    ProcessHandle p=ProcessHandle.current(); 
    ProcessHandle.Info info=p.info(); 
    System.out.println("Complete Process Inforamtion:\n"+info); 
    System.out.println("User: "+info.user().get()); 
    System.out.println("Command: "+info.command().get()); 
    System.out.println("Start Time: "+info.startInstant().get()); 
    System.out.println("Total CPU Time Acquired: "+info.totalCpuDuration().get()); 
  } 
}
```

## Use Case-3: To get snapshot of the Particular Process Based on id

```java
import java.util.*; 
public class Test 
{ 
  public static void main(String[] args) throws Exception 
  { 
    Optional<ProcessHandle> opt=ProcessHandle.of(7532); 
    ProcessHandle p=opt.get(); 
    ProcessHandle.Info info=p.info(); 
    System.out.println("Complete Process Inforamtion:\n"+info); 
    System.out.println("User: "+info.user().get()); 
    System.out.println("Command: "+info.command().get()); 
    System.out.println("Start Time: "+info.startInstant().get()); 
    System.out.println("Total CPU Time Acquired: "+info.totalCpuDuration().get()); 
  } 
} 
```

## ProcessBuilder:
We can use ProcessBuilder to create processes.

We can create ProcessBuilder object by using the following constructor.

```java
public ProcessBuilder(String... command)
```

The argument should be valid command to invoke the process.

Eg:

```java
ProcessBuilder pb = new ProcessBuilder("javac","Test.java");
ProcessBuilder pb = new ProcessBuilder("java","Test");
ProcessBuilder pb = new ProcessBuilder("notepad.exe" "D:\\names.txt");
```

Once we create a ProcessBuilder object,we can start the process by using start() method.

```java
pb.start();
```

## Use Case-4: To create and Start a process by using ProcessBuilder

### FrameDemo.java:

```java
import java.awt.*; 
import java.awt.event.*; 
public class FrameDemo 
{ 
  public static void main(String[] args) 
  { 
    Frame f = new Frame(); 
    f.addWindowListener( new WindowAdapter() 
    { 
      public void windowClosing(WindowEvent e) 
      { 
      System.exit(0); 
      } 
      }
    ); 
    f.add(new Label("This Process Started from Java by using ProcessBuilder !!!")); 
    f.setSize(500,500); 
    f.setVisible(true); 
  } 
} 
```

### Test.java

```java
public class Test 
{ 
  public static void main(String[] args) throws Exception 
  { 
    ProcessBuilder pb=new ProcessBuilder("java","FrameDemo"); 
    pb.start(); 
  } 
} 
```

## Use Case-5: To open a file with notepad from java by using ProcessBuilder

```java
public class Test 
{ 
  public static void main(String[] args) throws Exception 
  { 
    new ProcessBuilder("notepad.exe","FrameDemo.java").start(); 
  } 
} 
```

## Use Case-6: To start and destroy a process from java by using ProcessBuilder

```java
class Test 
{ 
  public static void main(String[] args) throws Exception 
  { 
    ProcessBuilder pb=new ProcessBuilder("java","FrameDemo"); 
    Process p=pb.start(); 
    System.out.println("Process Started with id:"+p.pid()); 
    Thread.sleep(10000); 
    System.out.println("Destroying the process with id:"+p.pid()); 
    p.destroy(); 
  } 
} 
```

## Use Case-7: To destroy a process which is not created from Java

```java
import java.util.*; 
class Test 
{ 
  public static void main(String[] args) throws Exception 
  { 
    Optional<ProcessHandle> optph=ProcessHandle.of(5232); 
    ProcessHandle ph=optph.get(); 
    ph.destroy(); 
  } 
} 
```

## Use Case-8: To display all running process information

```java
import java.util.*; 
import java.util.stream.*; 
import java.time.*; 
class Test 
{ 

  public static void dumpProcessInfo(ProcessHandle p) 
  { 
    ProcessHandle.Info info=p.info(); 
    System.out.println("Process Id:"+p.pid()); 
    System.out.println("User: "+info.user().orElse("")); 
    System.out.println("Command: "+info.command().orElse("")); 
    System.out.println("Start Time: "+info.startInstant().orElse(Instant.now()).toString()); 
    System.out.println("Total CPU Time Acquired: "+info.totalCpuDuration().
    orElse(Duration.ofMillis(0)).toMillis()); 
    System.out.println(); 

  }


  public static void main(String[] args) throws Exception 
  { 
    Stream<ProcessHandle> allp=ProcessHandle.allProcesses(); 
    allp.limit(100).forEach(ph->dumpProcessInfo(ph)); 
  } 

} 
```
## Use Case-9: To display all child process information

```java
import java.util.stream.*; 
import java.time.*; 
class Test 
{ 

  public static void dumpProcessInfo(ProcessHandle p) 
  { 
    ProcessHandle.Info info=p.info(); 
    System.out.println("Process Id:"+p.pid()); 
    System.out.println("User: "+info.user().orElse("")); 
    System.out.println("Command: "+info.command().orElse("")); 
    System.out.println("Start Time: "+info.startInstant().orElse(Instant.now()).toString()); 
    System.out.println("Total CPU Time Acquired: "+info.totalCpuDuration() 
    .orElse(Duration.ofMillis(0)).toMillis()); 
    System.out.println(); 
  } 


  public static void main(String[] args) throws Exception 
  { 
    ProcessHandle handle=ProcessHandle.current(); 
    Stream<ProcessHandle> childp=handle.children(); 
    childp.forEach(ph->dumpProcessInfo(ph)); 
  } 

}
```

Note: If Current Process not having any child processes then we won't get any output

## Use Case-10: To perform a task at the time of Process Termination

```java
import java.util.concurrent.*; 
public class Test 
{ 

  public static void main(String[] args) throws Exception 
  { 
    ProcessBuilder pb=new ProcessBuilder("java","FrameDemo"); 
    Process p=pb.start(); 
    System.out.println("Process Started with id:"+p.pid()); 
    CompletableFuture<Process> future=p.onExit(); 
    future.thenAccept(p1->System.out.println("Process Terminated with Id:"+p1.pid())); 
    System.out.println(future.get()); 
  } 

} 
```

**Output [In Normal Termination]:**

```java
D:\durga_classes>java Test
Process Started with id:4828
Process[pid=4828, exitValue=0]
Process Terminated with Id:4828
```

**Output [In Abnormal Termination alt+ctrl+delete]:**

```java
D:\durga_classes>java Test
Process Started with id:12512
Process[pid=12512, exitValue=1]
Process Terminated with Id:12512
```

Observe exit value: 0 for normal termination and non-zero for abnormal terminatio

# Java 9 HTTP/2 Client

## What is the purpose of HTTP/2 Client:

HTTP/2 Client is one of the most exciting features, for which developers are waiting for long time.

By using this new HTTP/2 Client, from Java application, we can send HTTP Request and we can process HTTP Response.

Prior to Java 9, we are using HttpURLConnection class to send HTTP Request and to Process HTTP Response. It is the legacy class which was introduced as the part of JDK 1.1 (1997).There are several problems with this HttpURLConnection class.

## Problems with Traditional HttpURLConnection class:
1. It is very difficult to use.

2. It supports only HTTP/1.1 protocol but not HTTP/2(2015) where

  * We can send only one request at a time per TCP Connection, which creates network traffic problems and performance problems.

  * It supports only Text data but not binary data
  
3. It works only in Blocking Mode (Synchronous Mode), which creates performance problems.

Because of these problems, slowly developers started using 3rd party Http Clients like Apache Http client and Google Http client etc.

JDK 9 Engineers addresses these issues and introduced a brand new HTTP/2 Client in Java 9. 

## Advantages of Java 9 HTTP/2 Client:
1. It is Lightweight and very easy to use.

2. It supports both HTTP/1.1 and HTTP/2.

3. It supports both Text data and Binary Data (Streams)

4. It can work in both Blocking and Non-Blocking Modes (Synchronous Communication and Asynchronous Communication)

5. It provides better performance and Scalability when compared with traditional HttpURLConnection.
etc... 

## Important Components of Java 9 HTTP/2 Client:

In Java 9, HTTP/2 Client provided as incubator module.

Module: jdk.incubator.httpclient

Package: jdk.incubator.http

Mainly 3 important classes are available:

1. HttpClient
2. HttpRequest
3. HttpResponse

**Note**:

Incubator module is by default not available to our java application. Hence compulsory we should 
read explicitly by using requires directive.

```java
module demoModule 
{ 
  requires jdk.incubator.httpclient; 
} 
```
## Steps to send Http Request and process Http Response from Java Application:

1. Create HttpClient Object
2. Create HttpRequest object
3. Send HttpRequest by using HttpClient and Get the HttpResponse
4. Process HttpResponse

## 1. Creation of HttpClient object:

We can use HttpClient object to send HttpRequest to the web server. We can create HttpClient object by using factory method: newHttpClient()

```java
HttpClient client = HttpClient.newHttpClient();
```

## 2. Creation of HttpRequest object:

We can create HttpRequest object as follows:

```java
String url="http://www.durgasoft.com";
HttpRequest req=HttpRequest.newBuilder(new URI(url)).GET().build();
```

Note:

newBuilder() method returns Builder object.

GET() method sets the request method of this builder to GET.

build() method builds and returns a HttpRequest.

```java
public static HttpRequest.Builder newBuilder(URI uri)
public static HttpRequest.Builder GET()
public abstract HttpRequest build()
```

## 3.Send HttpRequest by using HttpClient and Get the HttpResponse:

HttpClient contains the following methods:
 1. send() to send synchronous request(blocking mode)
 2. sendAsync() to send Asynchronous Request(Non Blocking Mode)

Eg:

```java
HttpResponse resp=client.send(req,HttpResponse.BodyHandler.asString());
HttpResponse resp=client.send(req,HttpResponse.BodyHandler.asFile(Paths.get("abc.txt")));
```

Note:

BodyHandler is a functional interface present inside HttpResponse. It can be used to handle body of HttpResponse.

## 4. Process HttpResponse:

HttpResponse contains the status code, response headers and body.

 Status Line

 Response Headers
 
 Response Body

HttpResponse class contains the following methods retrieve data from the response

1. **statusCode()**
 
 Returns status code of the response

 It may be (1XX,2XX,3XX,4XX,5XX)

2. **body()**

 Returns body of the response

3. **headers()**

 Returns header information of the response

Eg:

```java
System.out.println("Status Code:"+resp.statusCode());
System.out.println("Body:"+resp.body());
System.out.println("Response Headers Info");
HttpHeaders header=resp.headers();
Map<String,List<String>> map=header.map();
map.forEach((k,v)->System.out.println("\t"+k+":"+v));
```

## Demo Program to send GET Request in Blocking Mode:

### module-info.java:

```java
module demoModule 
{ 
  requires jdk.incubator.httpclient; 
} 
```

### Test.java:

```java
package packA; 
import jdk.incubator.http.HttpClient; 
import jdk.incubator.http.HttpRequest; 
import jdk.incubator.http.HttpResponse; 
import jdk.incubator.http.HttpHeaders; 
import java.net.URI; 
import java.util.Map; 
import java.util.List; 
public class Test 
{ 

  public static void main(String[] args) throws Exception 
  { 
    String url="https://www.redbus.in/info/aboutus"; 
    sendGetSyncRequest(url); 
  }

  public static void sendGetSyncRequest(String url) throws Exception 
  { 
    HttpClient client=HttpClient.newHttpClient(); 
    HttpRequest req=HttpRequest.newBuilder(new URI(url)).GET().build(); 
    HttpResponse resp=client.send(req,HttpResponse.BodyHandler.asString()); 
    processResponse(resp); 
  } 

  public static void processResponse(HttpResponse resp) 
  { 
    System.out.println("Status Code:"+resp.statusCode()); 
    HttpHeaders header=resp.headers(); 
    Map<String,List<String>> map=header.map(); 
    System.out.println("Response Headers"); 
    map.forEach((k,v)->System.out.println("\t"+k+":"+v)); 
  } 

}
```

Note:

## Writing Http Response body to file abc.html:

```java
HttpResponse resp = client.send(req,HttpResponse.BodyHandler.asFile(Paths.get("abc.html")));
```

Paths is a class present in java.nio.file package and hence we should write import as

```java
import java.nio.file.Paths;
```
In this case, abc.html file will be created in the current working directory which contains total response body.

## Demo Program:

### module-info.java:

```java
module demoModule 
{ 
requires jdk.incubator.httpclient; 
} 
```

### Test.java:

```java
package packA; 
import jdk.incubator.http.HttpClient; 
import jdk.incubator.http.HttpRequest; 
import jdk.incubator.http.HttpResponse; 
import jdk.incubator.http.HttpHeaders; 
import java.net.URI; 
import java.util.Map; 
import java.util.List; 
import java.nio.file.Paths; 
public class Test 
{

  public static void main(String[] args) throws Exception 
  { 
    String url="https://www.redbus.in/info/aboutus"; 
    sendGetSyncRequest(url); 
  } 


  public static void sendGetSyncRequest(String url) throws Exception 
  { 
    HttpClient client=HttpClient.newHttpClient(); 
    HttpRequest req=HttpRequest.newBuilder(new URI(url)).GET().build(); 
    HttpResponse resp=client.send(req,HttpResponse.BodyHandler.asFile(Paths.get("abc.
    html"))); 
    processResponse(resp); 
  } 


  public static void processResponse(HttpResponse resp) 
  { 
    System.out.println("Status Code:"+resp.statusCode()); 
    //System.out.println("Response Body:"+resp.body()); 
    HttpHeaders header=resp.headers(); 
    Map<String,List<String>> map=header.map(); 
    System.out.println("Response Headers"); 
    map.forEach((k,v)->System.out.println("\t"+k+":"+v)); 
  } 

} 
```

abc.html will be created in the current working directory. Open that file to see body of response.

## Asynchronous Communication:

In Blocking Mode (Synchronous Mode), Once we send Http Request, we should wait until getting response. It creates performance problems.

But in Non-Blocking Mode (Asynchronous Mode), we are not required to wait until getting the response. We can continue our execution and later point of time we can use that HttpResponse once it is ready, so that performance of the system will be improved.

HttpClient class contains sendAync() method to send asynchronous request.

```java
CompletableFuture<HttpResponse<String>> cf = 
client.sendAsync(req,HttpResponse.BodyHandler.asString());
```

CompletableFuture Object can be used to hold HttpResponse in aynchronous communication. This class present in java.util.concurrent package.This class contains isDone() method to check whether processing completed or not.

```java
public boolean isDone()
```

## Demo Program For Asynchronous Communication:

### module-info.java:

```java
module demoModule 
{ 
  requires jdk.incubator.httpclient; 
} 
```


### Test.java:

```java
package packA; 
import jdk.incubator.http.HttpClient; 
import jdk.incubator.http.HttpRequest; 
import jdk.incubator.http.HttpResponse; 
import jdk.incubator.http.HttpHeaders; 
import java.net.URI; 
import java.util.Map; 
import java.util.List; 
import java.util.concurrent.CompletableFuture; 
public class Test 
{ 
  public static void main(String[] args) throws Exception 
  { 
    String url="https://www.redbus.in/info/aboutus"; 
    sendGetAsyncRequest(url);
  }


  public static void sendGetAsyncRequest(String url) throws Exception 
  { 
    HttpClient client=HttpClient.newHttpClient(); 
    HttpRequest req=HttpRequest.newBuilder(new URI(url)).GET().build(); 
    System.out.println("Sending Asynchronous Request..."); 
    CompletableFuture<HttpResponse<String>> cf = client.sendAsync(req,HttpResponse.B
    odyHandler.asString()); 
    int count=0; 
    while(!cf.isDone()) 
    { 
      System.out.println("Processing not done and doing other activity:"+ ++count); 
    } 
    processResponse(cf.get()); 
  }
  
   
  public static void processResponse(HttpResponse resp) 
  { 
    System.out.println("Status Code:"+resp.statusCode()); 
    //System.out.println("Response Body:"+resp.body()); 
    HttpHeaders header=resp.headers(); 
    Map<String,List<String>> map=header.map(); 
    System.out.println("Response Headers"); 
    map.forEach((k,v)->System.out.println("\t"+k+":"+v)); 
  } 

}
```