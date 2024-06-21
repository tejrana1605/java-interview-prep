# Java 11 Predicate Not Method Example

Predicate.not() is a static method which is introduced in Java 11 to negate the supplied Predicate. In this post, we will see how this method makes the code more clear and readable with the help of before Java 11 and after Java 11 coding example.

# Before Java 11 : Negating The Predicate

Suppose, we have a list of strings as below.

```java
List<String> listOfStrings = Arrays.asList(" ", "\t", "\n", "One", "Two", "Three");
```

And we want to extract only blank strings from this list. This is how we do it using Java 8 Streams and method reference before Java 11.

```java
	
List<String> blankStrings = listOfStrings.stream().filter(String::isBlank).collect(Collectors.toList());
```

Suppose there is a requirement of extracting only non-blank strings from this list i.e negating the current predicate, then the above code can be modified as below (before Java 11).

```java
	
List<String> nonBlankStrings = listOfStrings.stream().filter(str -> ! str.isBlank()).collect(Collectors.toList());
```

You notice that while negating the predicate, we have replaced the method reference String::isBlank with lambda expression str -> ! str.isBlank(). This is how we used to negate the predicate before Java 11.

But, from Java 11, with the introduction of static method not() in Predicate interface, you can easily negate the given predicate in more clear and readable way.

## After Java 11 : Negating The Predicate With not()
not() is introduced in Java 11 as a static method in Predicate interface to negate the given predicate.

For example, above code to extract non-blank strings from the list can be re-written using Java 11 Predicate not method as below.

```java
List<String> nonBlankStrings = listOfStrings.stream().filter(Predicate.not(String::isBlank)).collect(Collectors.toList());
```

This is how you can negate a predicate using Java 11 not() method. Isn’t it makes the code more readable?

Using static importing not() method, you can make it even more clear.

```java
import static java.util.function.Predicate.not;
....
....
....
List<String> nonBlankStrings = listOfStrings.stream().filter(not(String::isBlank)).collect(Collectors.toList());
```

Below table summarizes the how to negate the predicate before Java 11 and after Java 11.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2022/03/Java11PredicateNotMethodExample.png?ssl=1"/></a>


# Java 11 var In Lambda Expressions

var keyword is introduced from Java 10. Using var keyword, you can declare local variables without mentioning their types. Compiler will automatically determines the type based on their initializers. But, use of var in lambda expressions is not allowed in Java 10. That has been addressed in Java 11. Let’s see how to use Java 11 var in lambda expressions in detail.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2022/04/Java11VarInLambdas.png?ssl=1"/></a>

## Java 11 var In Lambda Expressions

Using var, you can declare local variables without mentioning their types like below.

```java
var i = 10;                //int variable
var d = 1.1;              //double variable
var c = 'C';               //char variable
var b = true;            //boolean variable
var str = "string";        //String variable
```

You can go through detailed article on Java 10 var here.

But, use of var with lambda parameters is not allowed in Java 10.

For example, consider one simple lambda expression.

```java
(int m, int n) -> m * n
```

This can also be written as,

```java
(m, n) -> m * n
```

As lambda parameters are also local variables, you can assume that var can also be used in lambdas just like below,

```java
(var m, var n) -> m * n
```

But this is not allowed in Java 10. This code gives compile time error in Java 10 environment.

This has been addressed in Java 11. From Java 11 onward, you can use var with lambda parameters also.

Above code gives no error if you run it in Java 11 environment.

## Rules To Follow While Using var In Lambdas :

1) Lambda parameters declared with var must be enclosed in parentheses ( ) even though there is only one parameter.

```java
var s -> Integer.valueOf(s)          //Compile time error
(var s) -> Integer.valueOf(s)       // No Error
```

2) Mixing var with other non-var parameters is not allowed. It has to be all var or no var.

```java
(var m, int n) -> m * n     //Compile Time Error
(var m, var n) -> m * n     //No Error
```

3) Using var for one parameter and skipping for other parameters is also not allowed.

```java
(var m, n) -> m * n            //Compile Time Error
(var m, var n) -> m * n         //No Error
```

## Why var In Lambdas?

You may be thinking that if lambda parameters can be declared with no type then what is the use of var in lambda? There are two benefits of using var in lambdas.

1) You can apply modifiers if you are making use of var in lambdas. Because, you can’t use modifiers for a variable without mentioning its type.

```java
(@Nullable var m, @NonNull var n) -> m * n;
```

2) Using var in lambdas makes uniform use of var across the code.

# Java New String Methods – From Java 8 To Java 17

Strings are the most used data type in Java. Almost every application in Java makes use of strings. That’s why strings are treated with special attention in Java. From time to time, new methods are added to String class so that working with strings becomes effortless and simple. join() in Java 8, chars() and codePoints() in Java 9, isBlank(), lines(), repeat(), strip(), stripLeading() and stripTrailing() in Java 11, indent(), transform(), describeConstable() and resolveConstantDesc() in Java 12, formatted(), stripIndent() and translateEscapes() in Java 15 are some new Java string methods. In this post, we will see all the new methods added to String class from Java 8 to Java 17.

<a href="#" target="_blank"><img src="https://i0.wp.com/javaconceptoftheday.com/wp-content/uploads/2022/02/JavaNewStringMethods.png?ssl=1"/></a>

## Java 8 New String Methods
Only one method is introduced to String class in Java 8 i.e. join().

**join() :**

This method is used to join the string elements separated by a delimiter. It has two versions. One which takes delimiter and an array of strings as arguments and another one which takes delimiter and an Iterable as arguments. Iterable may be the list of strings, set of strings etc…

```java
import java.util.Arrays;
import java.util.List;
 
public class Java8StringMethods
{
    public static void main(String[] args) 
    {
        String languages = String.join("_", "Java", "HTML", "Python", "CSS", "PHP");
         
        System.out.println(languages);     
         
        List<String> languageList = Arrays.asList("Java", "HTML", "Python", "CSS", "PHP");
         
        languages = String.join(", ", languageList);
         
        System.out.println(languages);     
    }
}
```

Output :

```java
Java_HTML_Python_CSS_PHP
Java, HTML, Python, CSS, PHP
```

## Java 9 New String Methods
chars() and codePoints() are the two new methods introduced in Java 9. Both return an IntStream.

**chars() :**

This method returns an IntStream of char values of the given string.

```java
public class Java9StringMethods
{
    public static void main(String[] args) 
    {
        "String".chars().forEach(System.out::println);
    }
}
```

Output :

```java
83
116
114
105
110
103
```

**codePoints() :**

This method returns an IntStream of Unicode code points of the chars of the given string.

```java
public class Java9StringMethods
{
    public static void main(String[] args) 
    {
        "String".codePoints().forEach(System.out::println);
    }
}
```

Output :

```java
83
116
114
105
110
103
```

## Java 10 New String Methods
No new methods.

## Java 11 New String Methods
There are 6 new string methods are introduced in Java 11. They are – isBlank(), lines(), repeat(), strip(), stripLeading() and stripTrailing().

**isBlank() :**

You can use this method to check whether given string is blank or not. A string is said to be blank if it is empty or contains only white spaces.

```java
public class Java11StringMethods
{
    public static void main(String[] args) 
    {
        System.out.println("".isBlank());                  //Output : true
        System.out.println("   ".isBlank());               //Output : true
        System.out.println("\t \t".isBlank());             //Output : true
        System.out.println("\n \n".isBlank());             //Output : true
        System.out.println("STRING".isBlank());            //Output : false
        System.out.println("String \t \n".isBlank());      //Output : false
    }
}
```

**lines() :**

This method returns a stream of lines extracted from the given string. A line can be defined as a sequence of zero or more characters followed by a line terminator.

```java
public class Java11StringMethods
{
    public static void main(String[] args) 
    {
        System.out.println("\n\n".lines().count());                //Output : 2
        System.out.println("abc \n xyz".lines().count());          //Output : 2
        System.out.println("123 \n 456 \n".lines().count());       //Output : 2
        System.out.println("abc \n 123 \n xyz".lines().count());   //Output : 3
    }
}
```

**repeat() :**

This method returns the calling string repeated n times.

```java
public class Java11StringMethods
{
    public static void main(String[] args) 
    {
        System.out.println("1".repeat(5));
        System.out.println("abc".repeat(3));
        System.out.println("1a2b3c".repeat(2));
    }
}
```

Output :

```java
11111
abcabcabc
1a2b3c1a2b3c
```

**strip() :**

You can use this method to remove all leading and trailing white spaces of the given string.

```java
public class Java11StringMethods
{
    public static void main(String[] args) 
    {
        System.out.println("   1   ".strip());
        System.out.println("\t A \t".strip());
        System.out.println("\n A1 \n".strip());
        System.out.println("1   A".strip());
    }
}
```

Output :

```java
1
A
A1
1   A
```

**stripLeading() :**

This method removes only leading white spaces of a string.

```java
public class Java11StringMethods
{
    public static void main(String[] args) 
    {
        System.out.println("    1".stripLeading());
        System.out.println("   11".stripLeading());
        System.out.println("  111".stripLeading());
        System.out.println(" 1111".stripLeading());
    }
}
```

Output :

```java
1
11
111
1111
```

**stripTrailing() :**

This method removes only trailing white spaces of a string.

```java
public class Java11StringMethods
{
    public static void main(String[] args) 
    {
        System.out.println("   1    ".stripTrailing());
        System.out.println("  11    ".stripTrailing());
        System.out.println(" 111    ".stripTrailing());
        System.out.println("1111    ".stripTrailing());
    }
}
```

Output :

```java
   1
  11
 111
1111
```

## Java 12 New String Methods

Four more new methods are introduced in Java 12. They are – indent(), transform(), describeConstable() and resolveConstantDesc().

**indent() :**

This method applies indentation for each line of the given string according to supplied value.

```java
public class Java12StringMethods 
{
    public static void main(String[] args) 
    {
        System.out.println("123\nabc\nABC".indent(4));
    }
}
```

Output :

```java
123
abc
ABC
```

**transform() :**

This method applies given Function to the string.

```java
public class Java12StringMethods 
{
    public static void main(String[] args) 
    {
        System.out.println("string".transform(String::toUpperCase));
         
        System.out.println("abc".transform(str -> str.concat("xyz"))
                                .transform(String::toUpperCase));
    }
}
```

Output :

```java
STRING
ABCXYZ
```

From Java 12, String class implements two more interfaces – Constable and ConstantDesc. From these two interfaces, String class inherits two more methods – describeConstable() from Constable and resolveConstantDesc() from ConstantDesc.

**describeConstable() :**

This method returns an Optional containing nominal descriptor for the given string, which is the string itself.

```java
public class Java12StringMethods 
{
    public static void main(String[] args) 
    {
        System.out.println("123".describeConstable().get());
        System.out.println("abc".describeConstable().get());
        System.out.println("ABC".describeConstable().get());
    }
}
```

Output :

```java
123
abc
ABC
```

**resolveConstantDesc() :**

This method resolves the given string as ConstantDesc and returns the string itself.

```java
import java.lang.invoke.MethodHandles;
 
public class Java12StringMethods 
{
    public static void main(String[] args) 
    {
        System.out.println("Java".resolveConstantDesc(MethodHandles.lookup()));
        System.out.println("Python".resolveConstantDesc(MethodHandles.lookup()));
        System.out.println("JavaScript".resolveConstantDesc(MethodHandles.lookup()));
    }
}
```

Output :

```java
Java
Python
JavaScript
```

## Java 13 New String Methods
No new methods.

## Java 14 New String Methods
No new methods.

## Java 15 New String Methods

**formatted() :**

This method formats the given string with the supplied arguments. This method is similar to String.format(this, args).

```java
public class Java15StringMethods 
{
    public static void main(String[] args) 
    {
        System.out.println("1) %s 2) %s 3) %s ".formatted("Java", "Python", "JavaScript"));
    }
}
```

Output :

```java
1) Java 2) Python 3) JavaScript
```

**stripIndent() :**

This method removes indentation of the given string at the beginning and at the end of every line.

```java
public class Java16StringMethods 
{
    public static void main(String[] args) 
    {
        System.out.println("   123".stripIndent());
        System.out.println("123   ".stripIndent());
        System.out.println("   123   ".stripIndent());
    }
}
```

Output :

```java
123
123
123
```

**translateEscapes() :**

This method returns a string with escape sequences translated as if in a string literal.

```java
public class Java15StringMethods 
{
    public static void main(String[] args) 
    {
        String str = "Tab \t Next Line \n Space \s Single Quote \' Double Quote \" ";
         
        System.out.println(str.translateEscapes());
    }
}
```

Output :

```java
Tab Next Line
Space Single Quote ‘ Double Quote “
```

## Java 16 New String Methods
No new methods.

## Java 17 New String Methods
No new methods.