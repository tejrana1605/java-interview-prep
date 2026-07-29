# Why Generics?

Generics address several key issues in Java programming:

- **Type Safety:** Type safety is a critical aspect of Java programming. Before generics, collections in Java could hold any type of objects, which meant that type errors could only be caught at runtime, not compile time. Lack of type safety could lead to ClassCastException errors when an object was cast to the wrong type.

- **Code Reusability:** Generics allow for the creation of more general and reusable code. By parameterizing types, we can write methods and classes that can operate on any type, reducing code duplication and increasing flexibility.
Elimination of Casting: Generics reduce the need for explicit type casting, making the code cleaner and less error-prone. Without generics, developers often have to cast objects to the desired type, leading to cluttered code and potential runtime errors.

- **Enabling Generic Algorithms:** Generics enable the creation of generic algorithms that can work with any type, enhancing the versatility of code. It is particularly useful in collections and other data structures.

- **Enhancing the Java Collections Framework:** The introduction of generics significantly enhanced the Java Collections Framework, making it more powerful and type-safe. Collections can now be parameterized with specific types, ensuring type safety and reducing the risk of runtime errors.

- **Supporting More Readable and Maintainable Code:** Generics make the code more readable and maintainable by explicitly stating what types are being used. This clarity helps other developers understand the intended use of collections and methods, reducing the likelihood of errors.

- **Facilitating Type Inference:** Java's type inference mechanisms work well with generics, allowing the compiler to deduce the type parameters in many cases, which simplifies the code for the developer.

- **Backward Compatibility:** Generics in Java were designed with type erasure to ensure backward compatibility with older versions of Java. Type erasure means that generic type information is only available at compile time and is removed at runtime. It allows generic code to interoperate with legacy code that does not use generics.

## Advantage of Java Generics
There are mainly three advantages of generics are as follows:

1) **Type-safety:** We can hold only a single type of objects in generics. It does not allow to store other objects.

Without Generics, we can store any type of objects.

```java
List list = new ArrayList();    
list.add(10);  
list.add("10");  
With Generics, it is required to specify the type of object we need to store.  
List<Integer> list = new ArrayList<Integer>();    
list.add(10);  
list.add("10");// compile-time error  

```

2) **Type casting is not required:** There is no need to typecast the object.

Before Generics, we need to type cast.

```java
List list = new ArrayList();    
list.add("hello");    
String s = (String) list.get(0);//typecasting    
After Generics, we don't need to typecast the object.  
List<String> list = new ArrayList<String>();    
list.add("hello");    
String s = list.get(0);    
```

3) **Compile-Time Checking:** It is checked at compile time so problem will not occur at runtime. The good programming strategy says it is far better to handle the problem at compile time than runtime.

```java
List<String> list = new ArrayList<String>();    
list.add("hello");    
list.add(32);//Compile Time Error    
```

**Syntax** to use generic collection

```java
ClassOrInterface<Type>    
```

Example to use Generics in Java

```java
ArrayList<String>    
```

## Full Example of Generics in Java
Here, we are using the ArrayList class, but we can use any collection class such as ArrayList, LinkedList, HashSet, TreeSet, HashMap, Comparator etc.

```java
import java.util.*;  
class TestGenerics1{  
public static void main(String args[]){  
ArrayList<String> list=new ArrayList<String>();  
list.add("rahul");  
list.add("jai");  
//list.add(32);//compile time error  
  
String s=list.get(1);//type casting is not required  
System.out.println("element is: "+s);  
  
Iterator<String> itr=list.iterator();  
while(itr.hasNext()){  
System.out.println(itr.next());  
}  
}  
}
```

```java
Output:

element is: jai
rahul
jai
```

## Example of Java Generics using Map

Now we are going to use map elements using generics. Here, we need to pass key and value. Let us understand it by a simple example:

```java
import java.util.*;  
class TestGenerics2{  
public static void main(String args[]){  
Map<Integer,String> map=new HashMap<Integer,String>();  
map.put(1,"vijay");  
map.put(4,"umesh");  
map.put(2,"ankit");  
  
//Now use Map.Entry for Set and Iterator  
Set<Map.Entry<Integer,String>> set=map.entrySet();  
  
Iterator<Map.Entry<Integer,String>> itr=set.iterator();  
while(itr.hasNext()){  
Map.Entry e=itr.next();//no need to typecast  
System.out.println(e.getKey()+" "+e.getValue());  
}  
  
}}  
```

```java
Output:

1 vijay
2 ankit
4 umesh
```

## Generic Class

A class that can refer to any type is known as a generic class. Here, we are using the T type parameter to create the generic class of specific type.

Let's see a simple example to create and use the generic class.

### Creating a generic class:

```java
class MyGen<T>{  
T obj;  
void add(T obj){this.obj=obj;}  
T get(){return obj;}  
}  
```

The T type indicates that it can refer to any type (like String, Integer, and Employee). The type you specify for the class will be used to store and retrieve the data.

### Using Generic Class:

Let's see the code to use the generic class.

```java
class TestGenerics3{  
public static void main(String args[]){  
MyGen<Integer> m=new MyGen<Integer>();  
m.add(2);  
//m.add("vivek");//Compile time error  
System.out.println(m.get());  
}}  
```

```java
Output
2
```
