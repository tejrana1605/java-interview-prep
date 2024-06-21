# Java 10 New Features

# JEPs

286 - Local-Variable Type Inference

296 - Consolidate the JDK Forest into a Single Repository

304 - Garbage-Collector Interface

307 - Parallel Full GC for G1

310 - Application Class-Data Sharing

312 - Thread-Local Handshakes

313 - Remove the Native-Header Generation Tool (javah)

314 - Additional Unicode Language-Tag Extensions

316 - Heap Allocation on Alternative Memory Devices

317 - Experimental Java-Based JIT Compiler

319 - Root Certificates

322 - Time-Based Release Versioning

## Features

* Process API improvements

* Collections API improvements

* Application Class-Data Sharing

* var keyword to declare variables

```java
    var universeAnswer = 42
```

# Java 10 var Keyword

Using Java 10 var keyword, you can declare local variables without mentioning their type. Compiler will automatically detects the type based on their initializers. This is called automatic type inference. This type of feature is already there in other languages like Python, Scala, JavaScript etc… From Java 10, it is available in Java also. Let’s see Java 10 var keyword or Java 10 local variable type inference in detail.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2021/11/Java10varKeyword.png?ssl=1"/></a>

## Java 10 var Keyword :

```java

//Before Java 10

int i = 10;
double d = 1.1;
char c = ‘C’;
boolean b = true;
String str = “string”;
List<Integer> list = List.of(1, 22, 333);
Map<Integer, String> map = Map.of(1, “Java”, 2, “Python”, 3, “JavaScript”);
```

This is how you declare local variables before Java 10. You have to mention datatype of the variable explicitly.

But from Java 10, you need not to mention type of the local variables. Compiler will automatically detects the type based on their initializer on the right hand side of the declaration statement.

```java

//After Java 10

var i = 10;
var d = 1.1;
var c = ‘C’;
var b = true;
var str = “string”;
var list = List.of(1, 22, 333);
var map = Map.of(1, “Java”, 2, “Python”, 3, “JavaScript”);
```

Let’s discuss some important points about Java 10 var keyword.

1) var works only when you initialize the variable explicitly. Because, compiler uses this initialization to determine the type of the variable. If you don’t initialize var variable, compiler shows the error.

```java
public class Java10VarKeywordExample 
{
    public static void main(String[] args) 
    {
        var i;     //Cannot use 'var' on variable without initializer
    }
}
```

2) var is only for local variables. It is not allowed for global variables.

```java

public class Java10VarKeywordExample 
{
    var str = "string";    //var is not allowed for global variables
     
    public static void main(String[] args) 
    {
        var i = 10;     //var is only for local variables
    }
}
```

3) You can’t use var as method parameters and return types.

```java

public class Java10VarKeywordExample 
{
    //compile time error
    //you can't use var as return types and method parameters
     
    var anyMethod(var i, var j)    
    {
        return i+j;
    }
}
```

4) var doesn’t work with lambda expressions because lambda expressions need an explicit target type.

```java

public class Java10VarKeywordExample 
{
    public static void main(String[] args) 
    {
        var i = (a, b) -> a+b;
         
        //Compile time error
        //Lambda expression needs an explicit target-type
    }
}
```

5) You can assign another value to var variable but it should be of same type, not of different type.

```java
public class Java10VarKeywordExample 
{
    public static void main(String[] args) 
    {
        var ID = 111;      //Here, type will be inferred as int
         
        ID = 222;       //You can re-assign another int value to ID
 
        //If you try to assign value of another type, compiler will show error
         
        ID = "333";     //Type mismatch: cannot convert from String to int
    }
}
```

6) You can’t initialize var variable with null. Because compiler will not be able to determine the type if you assign null.

```java
public class Java10VarKeywordExample 
{
    public static void main(String[] args) 
    {
        var ID = null;   //Cannot infer type for local variable initialized to 'null'
    }
}
```

7) As var removes unnecessary repetition of the code on the left side of the declaration statement, it makes the code more concise and readable. For example,

```java
Map<String, List<String>> studentToSubjectsMap = new HashMap<String, List<String>>();
         
for (Entry<String, List<String>> entry : studentToSubjectsMap.entrySet())
{
    String studentName = entry.getKey();
             
    List<String> subjectsTaken = entry.getValue();
}
```

can be written as,

```java
var studentToSubjectsMap = new HashMap<String, List<String>>();
         
for (var entry : studentToSubjectsMap.entrySet())
{
    var studentName = entry.getKey();
             
    var subjectsTaken = entry.getValue();
}
```

8) var is not a keyword. It is just a reserved type name like int, float etc. That means if you have used var as variable name or method name or class name in your previous code, that code still runs fine in Java 10 environment.

Example

Since Java 10, we can use the keyword var to declare local variables (local means: within methods). This allows, for example, the following definitions:

```java
var i = 10;
var hello = "Hello world!";
var list = List.of(1, 2, 3, 4, 5);
var httpClient = HttpClient.newBuilder().build();
var status = getStatus();
```

For comparison – this is how the definitions look in classic notation:

```java
int i = 10;
String hello = "Hello world!";
List<Integer> list = List.of(1, 2, 3, 4, 5);
HttpClient httpClient = HttpClient.newBuilder().build();
Status status = getStatus();
```

# Java 10 Collectors Methods

Java 10 has introduced three new methods to java.util.stream.Collectors class to collect the resulting elements into unmodifiable collections. They are toUnmodifiableList(), toUnmodifiableSet() and toUnmodifiableMap​(). These methods return Collector which accumulates the input elements into corresponding unmodifiable collection. Let’s see these methods in detail.

Before moving on to Java 10 Collectors methods, remember following two characteristics of unmodifiable or immutable collections.

* Immutable collections are the collections which can’t be modified once they are created. If you try to modify them, you will get java.lang.UnsupportedOperationException at run time.

* Immutable collections don’t allow null elements. If you try to add null elements, you will get java.lang.NullPointerException at run time.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2022/02/Java10CollectorsMethods.png?ssl=1"/></a>

## Java 10 Collectors.toUnmodifiableList()

This method returns a Collector which accumulates input elements into unmodifiable list. Input elements should not be null, otherwise it throws NullPointerException.

```java
import java.util.ArrayList;
import java.util.List;
import java.util.stream.Collectors;
 
public class Java10CollectorsMethods
{
    public static void main(String[] args)
    {
        List<String> cityList = new ArrayList<String>();
         
        cityList.add("Mumbai");
        cityList.add("London");
        cityList.add("Bangalore");
        cityList.add("New York");
        cityList.add("Pune");
         
        List<String> unModifiableCityList = cityList.stream()
                                                    .map((String s) -> s.toUpperCase())
                                                    .collect(Collectors.toUnmodifiableList());
         
        System.out.println(unModifiableCityList);
    }
}
```

Output :

```java

[MUMBAI, LONDON, BANGALORE, NEW YORK, PUNE]
```

## Java 10 Collectors.toUnmodifiableSet()

This method returns a Collector which accumulates input elements into an unmodifiable set. Input elements should not be null, otherwise it throws NullPointerException.

```java
import java.util.HashSet;
import java.util.Set;
import java.util.stream.Collectors;
 
public class Java10CollectorsMethods
{
    public static void main(String[] args)
    {
        Set<String> nameSet = new HashSet<String>();
         
        nameSet.add("Michael");
        nameSet.add("Lyon");
        nameSet.add("Benden");
        nameSet.add("Noku");
        nameSet.add("Praveen");
        nameSet.add("Lyon");
         
        Set<String> unModifiableNameSet = nameSet.stream()
                                                    .filter((String s) -> (s.length() > 5))
                                                    .collect(Collectors.toUnmodifiableSet());
         
        System.out.println(unModifiableNameSet);
    }
}
```

Output :

```java

[Praveen, Benden, Michael]
```

## Java 10 Collectors.toUnmodifiableMap()
This method returns a Collector that accumulates input elements into an unmodifiable map whose keys and values are derived after applying specified mapping functions to input elements. Input elements should not be null, otherwise it will throw NullPointerException.

This method has two versions – one which takes keyMapper and valueMapper as arguments and another one which takes an extra argument mergeFunction which decides what to do if duplicate keys are found.

**Example With keyMapper and valueMapper**

```java
import java.util.Map;
import java.util.stream.Collectors;
import java.util.stream.Stream;
 
public class Java10CollectorsMethods
{
    public static void main(String[] args)
    {
        Map<String, Integer> unModifiableMap = Stream.of("Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine")
                                                        .collect(Collectors.toUnmodifiableMap(s -> s, String::length));
         
        System.out.println(unModifiableMap);
    }
}
```

Output :

```java
{Six=3, Three=5, Zero=4, Nine=4, Five=4, Seven=5, One=3, Eight=5, Two=3, Four=4}
```

**Example with keyMapper, valueMapper and mergeFunction**

```java
import java.util.Map;
import java.util.stream.Collectors;
import java.util.stream.Stream;
 
public class Java10CollectorsMethods
{
    public static void main(String[] args)
    {
        Map<Integer, String> unModifiableMap = Stream.of("Zero", "One", "Two", "Three", "Four", "Five", "Six", "Seven", "Eight", "Nine")
                                                        .collect(Collectors.toUnmodifiableMap(String::length, s -> s, (s1, s2) -> s1+", "+s2));
         
        System.out.println(unModifiableMap);
    }
}
```

Output :

```java
{5=Three, Seven, Eight, 4=Zero, Four, Five, Nine, 3=One, Two, Six}
```

# Java 10 List.copyOf(), Set.copyOf() And Map.copyOf() Methods

In Java 9, some static factory methods are introduced to easily create immutable collections. They are List.of(), Set.of() and Map.of(). These methods take individual elements as arguments and create immutable collections consisting of those elements. From Java 10, some more static factory methods are introduced to create immutable collections from existing collections. They are List.copyOf(), Set.copyOf() and Map.copyOf(). These methods take whole collection as an argument and create immutable copy of that collection. Let’s see these methods in detail.

Before moving on to those Java 10 copyOf() methods, remember following two characteristics of immutable collections.

* Immutable collections are the collections which can’t be modified once they are created. If you try to modify them, you will get java.lang.UnsupportedOperationException at run time.

* Immutable collections don’t allow null elements. If you try to add null elements, you will get java.lang.NullPointerException at run time.

## Java 10 List.copyOf() Method

* Java 10 List.copyOf() method is introduced to create immutable list from an existing collection.

* Existing collection must not be null and also must not have null elements.

* Any modifications to the original collection after the creation of immutable list will not be reflected in the immutable list.

For example,

```java
import java.util.ArrayList;
import java.util.List;
 
public class Java10CollectionAPIImprovements 
{
    public static void main(String[] args) 
    {
        List<String> sportList = new ArrayList<String>();
         
        sportList.add("Hockey");
        sportList.add("Cricket");
        sportList.add("Tennis");
         
        List<String> immutableSportList = List.copyOf(sportList);
         
        System.out.println(sportList);       //Output : [Hockey, Cricket, Tennis]
         
        System.out.println(immutableSportList);     //Output : [Hockey, Cricket, Tennis]
         
        immutableSportList.add("Wrestling");      //It gives run-time error : UnsupportedOperationException
         
        sportList.add("Kabaddi");       //It gives no error, but it will not be reflected in immutableSportList
         
        System.out.println(sportList);      //Output : [Hockey, Cricket, Tennis, Kabaddi]
         
        System.out.println(immutableSportList);     //Output : [Hockey, Cricket, Tennis]
    }
}
```

## Java 10 Set.copyOf() Method
* Java 10 Set.copyOf() is introduced to create immutable set from an existing collection.

* The given collection must not be null and must not have null elements.

* Any modifications to the given set after the creation of immutable set will not be reflected in the immutable set.

For example,

```java
import java.util.HashSet;
import java.util.Set;
 
public class Java10CollectionAPIImprovements 
{
    public static void main(String[] args) 
    {
        Set<String> citySet = new HashSet<String>();
         
        citySet.add("Mumbai");
        citySet.add("New York");
        citySet.add("London");
         
        Set<String> immutableCitySet = Set.copyOf(citySet);
         
        System.out.println(citySet);       //Output : [New York, London, Mumbai]
         
        System.out.println(immutableCitySet);     //Output : [New York, Mumbai, London]
         
        immutableCitySet.add("Colombo");      //It gives run-time error : UnsupportedOperationException
         
        citySet.add("Bangalore");       //It gives no error, but it will not be reflected in immutableCitySet
         
        System.out.println(citySet);      //Output : [New York, London, Mumbai, Bangalore]
         
        System.out.println(immutableCitySet);     //Output : [London, Mumbai, New York]
    }
}
```

## Java 10 Map.copyOf() Method
* Java 10 Map.copyOf() method is introduced to create immutable copy of an existing map.

* Existing map must not be null and must not have null keys and values.

* Any modifications to the original map after the creation of immutable map will not be reflected in the immutable map.

Below is an example.

```java
import java.util.HashMap;
import java.util.Map;
 
public class Java10CollectionAPIImprovements 
{
    public static void main(String[] args) 
    {
        Map<Integer, String> cityCodeMap = new HashMap<Integer, String>();
         
        cityCodeMap.put(111, "Mumbai");
        cityCodeMap.put(222, "New York");
        cityCodeMap.put(333, "London");
         
        Map<Integer, String> immutableCityCodeMap = Map.copyOf(cityCodeMap);
         
        System.out.println(cityCodeMap);     //Output : {333=London, 222=New York, 111=Mumbai}
         
        System.out.println(immutableCityCodeMap);     //Output : {333=London, 111=Mumbai, 222=New York}
         
        immutableCityCodeMap.put(444, "Colombo");     //It gives run-time error : UnsupportedOperationException
         
        cityCodeMap.put(555, "Bangalore");    //It gives no error, but this entry will not be reflected in immutableCityCodeMap
         
        System.out.println(cityCodeMap);     //Output : {555=Bangalore, 333=London, 222=New York, 111=Mumbai}
         
        System.out.println(immutableCityCodeMap);     //Output : {333=London, 111=Mumbai, 222=New York}
    }
}
```

Below is the summary of Java 10 List.copyOf(), Set.copyOf() and Map.copyOf() methods.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2022/01/Java10CopyOfMethods.png?ssl=1"/></a>

# Immutable Collections

With the methods Collections.unmodifiableList(), unmodifiableSet(), unmodifiableMap(), unmodifiableCollection() – and four further variants for sorted and navigable sets and maps – the Java Collections Framework offers the possibility to create unmodifiable wrappers for collection classes.

Here is an example:

```java
List<Integer> list = new ArrayList<>();
list.add(1);
list.add(2);
list.add(3);
List<Integer> unmodifiable = Collections.unmodifiableList(list);
```

If we now try to add an element via the wrapper, we get an UnsupportedOperationException:

```java
unmodifiable.add(4);

⟶

Exception in thread "main" java.lang.UnsupportedOperationException
	at java.base/java.util.Collections$UnmodifiableCollection.add(...)
	at ...
```

However, the wrapper does not prevent us from modifying the underlying list. All subsequent changes to it are also visible in the wrapper. This is because the wrapper does not contain a copy of the list, but a view:

```java
list.add(4);
System.out.println("unmodifiable = " + unmodifiable);

⟶

unmodifiable = [1, 2, 3, 4]
```

## List.copyOf(), Set.copyOf(), and Map.copyOf()

With Java 10, we now also have the possibility to create immutable copies of collections. For this purpose, we have the static interface methods List.copyOf(), Set.copyOf() and Map.copyOf().

If we create such a copy and then modify the original collection, the changes will no longer affect the copy:

```java
List<Integer> immutable = List.copyOf(list);
list.add(4);
System.out.println("immutable = " + immutable);

⟶

immutable = [1, 2, 3]
```

The attempt to change the copy is – just like when using unmodifiableList() – acknowledged with an UnsupportedOperationException:

```java
immutable.add(4);

⟶

Exception in thread "main" java.lang.UnsupportedOperationException
    at java.base/java.util.ImmutableCollections.uoe(...)
    at java.base/java.util.ImmutableCollections$AbstractImmutableCollection.add(...)
    at ...
```

Note: Should you need a modifiable copy of the list, you can always use the copy constructor:

```java
List<Integer> copy = new ArrayList<>(list);
```

## Collectors.toUnmodifiableList(), toUnmodifiableSet(), and toUnmodifiableMap()

The collectors created using Collectors.toList(), toSet() and toMap() collect the elements of a Stream into mutable lists, sets and maps. The following example shows the use of these collectors and the subsequent modification of the results:

```java
List<Integer> list = IntStream.rangeClosed(1, 3).boxed().collect(Collectors.toList());
Set<Integer> set = IntStream.rangeClosed(1, 3).boxed().collect(Collectors.toSet());
Map<Integer, String> map = IntStream.rangeClosed(1, 3).boxed()
        .collect(Collectors.toMap(Function.identity(), String::valueOf));

list.add(4);
set.add(4);
map.put(4, "4");

System.out.println("list = " + list);
System.out.println("set  = " + set);
System.out.println("map  = " + map);
```

As you would expect, the program produces the following output (although the elements of the set and map may appear in a different order):

```java
list = [1, 2, 3, 4]
set  = [1, 2, 3, 4]
map  = {1=1, 2=2, 3=3, 4=4}
```

In Java 10, the methods Collectors.toUnmodifiableList(), toUnmodifiableSet(), and toUnmodifiableMap() have been added, which now allow us to collect stream elements into immutable lists, sets, and maps:

```java
List<Integer> list =
    IntStream.rangeClosed(1, 3).boxed().collect(Collectors.toUnmodifiableList());

Set<Integer> set =
    IntStream.rangeClosed(1, 3).boxed().collect(Collectors.toUnmodifiableSet());

Map<Integer, String> map = 
    IntStream.rangeClosed(1, 3)
        .boxed()
        .collect(Collectors.toUnmodifiableMap(Function.identity(), String::valueOf));
```

Attempting to modify such a list, set or map is met with an UnsupportedOperationException.

## Optional.orElseThrow()

Optional, introduced in Java 8, provides the get() method to retrieve the value wrapped by the Optional. Before calling get(), you should always check with isPresent() whether a value exists:

```java
Optional<String> result = getResult();
if (result.isPresent()) {
  System.out.println(result.get());
}
```

If the Optional is empty, get() would otherwise throw a NoSuchElementException.

To minimize the risk of an unintended exception, IDEs and static code analysis tools issue a warning if get() is used without isPresent():

<a href="#" target="_blank"><img src="https://www.happycoders.eu/wp-content/uploads/2021/10/Optional-get-warning-v2-600x92.png"/></a>

IntelliJ warning for Optional.get() without isPresent()

However, there are also cases where such an exception is desired. Previously, one had to add appropriate @SuppressWarnings annotations to the code to suppress the warnings.

Java 10 offers a nicer solution with the method orElseThrow(): The method is an exact copy of the get() method – only the name is different. Since it is clear from the name that this method can throw an exception, misunderstandings are ruled out. The static code analysis no longer criticizes the usage as a code smell.

Here is the source code of both methods for comparison:

```java
public T get() {
  if (value == null) {
    throw new NoSuchElementException("No value present");
  }
  return value;
}

public T orElseThrow() {
  if (value == null) {
    throw new NoSuchElementException("No value present");
  }
  return value;
}
```

# Time-Based Release Versioning

After the version format was (finally) changed from the somewhat cryptic 1.8.0_291 to a much more readable 9.0.4 from Java 8 to 9, JEP 322 added the release date in Java 10 – and for Java 11, an "LTS" (Long-Term Support) in advance.

The command java -version returns the following answers in Java 8 to 11:

Java 8:

```java
$ java -version
java version "1.8.0_291"
```
Java 9:

```java
$ java -version
java version "9.0.4"
```

Java 10:

```java
$ java -version
java version "10.0.2" 2018-07-17
```

Java 11:

```java
$ java -version
java version "11.0.11" 2021-04-20 LTS
```

To date, there has been no further change to the versioning scheme.