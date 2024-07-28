# Let’s Discuss all features of java 11 one by one

## New String Methods in java: 

The string class has a lot of methods to deal with String in java but Java 11 introduces several new methods into the String class, such as isBlank(), strip(), stripLeading(), stripTrailing(), and repeat(int count)

## Local variable type inference: 

To make it a better feature, Java 11 introduces the “var” keyword for local variable type inference, which allows developers to declare variables without explicitly specifying the type.

## New File Methods :

To provide more flexibility to file methods, Java 11 introduced new methods for reading and writing files using the readString() and writeString() methods, which can simplify file I/O operations.

## Collection to Array :

Java 11 introduces a new method toArray(IntFunction<T[]> generator) in the Collection interface, which allows collections to be easily converted into arrays

## Predicate Not Method :

Java 11 introduced a new method “not()” in the Predicate interface that returns a new predicate that represents the negation of the original predicate. This simplifies code that requires negating a predicate.

## HTTP Client API :

Java 11 introduced a new HTTP Client API that makes it easier for developers to send HTTP requests and handle responses asynchronously.

## Nest-Based Access Control :

Java 11 introduces Nest-Based Access Control, which allows classes that are logically part of the same code entity to access each other’s private members without the need for reflection.

## Enhanced Unicode Support :

Java 11 includes several enhancements to Unicode support, such as support for Unicode 10.0.0, additional scripts, and the ability to handle non-BMP Unicode characters.

## Flight Recorder :

Java 11 contains Java Flight Recorder, which is a profiling and diagnostic tool for collecting and analyzing runtime information about the JVM and the Java applications running on it.

## Low Overhead Heap Profiling :

Java 11 includes a new low-overhead heap profiling feature that can help developers diagnose memory-related issues in their applications more easily.

## Dynamic Class-File Constants :

Java 11 introduces a new constant-pool form, “Dynamic”, that allows constants to be dynamically computed at runtime.

## Epsilon :

Java 11 includes a new experimental garbage collector called Epsilon, which designes to be a no-op collector that simply allocates and discards memory without performing any actual garbage collection.

## ZGC :

Java 11 introduces a new experimental garbage collector called ZGC, which is designed to be a scalable, low-latency collector that can handle heaps ranging from a few hundred megabytes to several terabytes in size.

## ChaCha20 and Poly1305 Cryptographic Algorithms :

Java 11 supports the ChaCha20 and Poly1305 cryptographic algorithms, which can provide faster and more secure encryption and decryption than some of the older algorithms.

# Local Variable Type Inference
Local Variable Type Inference was introduced in java 10. This feature allows developers to declare and initialize local variables without explicitly stating their data type. But there was some improvement area. So Java 11 continued to support this feature and introduced some improvements to make it more usable. In this post, we will see these improvements with examples.

## Local variable type inference for lambda expressions in java 11
In java, the lambda expressions feature was introduced in java 8 that allows developers to write functional-style code. But we couldn’t use var as the parameter type for lambda expressions before java 11. After java 11, the compiler can identify the type of a lambda expression parameter based on its context. So now we can use var as the parameter type for lambda expressions.

Let’s take an example and use a lambda expression to sort a list of integers in descending order. First of all, we will see it with java 10 and then move the code to java 11.


```java
import java.util.Arrays;
import java.util.List;
public class VarInLambda {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(3, 5, 2, 6, 1, 4);
        numbers.sort((Integer a, Integer b) -> b.compareTo(a));
        System.out.println(numbers);
    }
}
```

```java
Output: [6, 5, 4, 3, 2, 1]
```

In the above code, we used the Integer type parameters for the lambda expression. Now let’s see it with the enhanced inference in Java 11, the parameter types can be omitted and replaced with var:

```java
import java.util.Arrays;
import java.util.List;
public class VarInLambda {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(3, 5, 2, 6, 1, 4);
        numbers.sort((var a, var b) -> b.compareTo(a));
        System.out.println(numbers);
    }
}
```

```java
Output: [6, 5, 4, 3, 2, 1]
```

## Using var with Anonymous Inner Classes
Java 11 did one more improvement in local variable type inference. Now developers can use the var keyword with anonymous inner classes. Before java 11, anonymous inner classes required an explicit type declaration for their variables, which could make the code more verbose and harder to read. With the ability to use var in anonymous inner classes, developers can now write more concise and readable code.

Let’s take an example of anonymous class.

```java
Runnable task = new Runnable() {
    @Override
    public void run() {
        System.out.println("Task executed");
    }
};
```

In the above code, We used to type with an anonymous inner class that implements the Runnable interface. The type declaration for the variable can be omitted:

```java
var task = new Runnable() {
    @Override
    public void run() {
        System.out.println("Task executed");
    }
};
```

# Converting a Collection to an Array
Java 11, introduces a new method in the **Collection interface** i.e. **toArray(IntFunction generator) method**. This method uses to convert a collection into an array. In this section, we will read about **Converting a Collection to an Array in java 11**

The **toArray() method** has been a part of the Collection interface since Java 1.2. But Java 11 provides a new method that allows for more control over the returned array. So now the **toArray() method** is an overloaded method. The method introduced in java 11 takes an **IntFunction** as an argument, which specifies the type of the returned array.


```java
default <T> T[] toArray(IntFunction<T[]> generator)
```

It’s a **default method** that takes only one parameter. The **IntFunction** is a **functional interface** that takes an integer value and returns an array of type T[]. It is useful where the size of the collection is known beforehand. because it provides more control over the returned array size.

```java
import java.util.ArrayList;
import java.util.List;

public class CollectionToArrayExample {
   public static void main(String[] args) {
      List<String> list = new ArrayList<>();
      list.add("apple");
      list.add("banana");
      list.add("orange");

      String[] array = list.stream().toArray(String[]::new);

      for (String s : array) {
         System.out.println(s);
      }
   }
}
```

```java
Output: apple
banana
orange
```

## How was this type of task performed before Java 11?

```java
Object[] toArray()
<T> T[] toArray(T[] a)
```

The 1st overload method (Object[] toArray()) returns an array of type Object[] that contains all of the elements in the collection.

The second overload method (T[] toArray(T[] a)) took an array of type T[] as an argument, and returns that same array if it was large enough to hold all of the elements in the collection, or a new array of the same type if it was not.

```java
import java.util.ArrayList;
import java.util.List;

public class CollectionToArrayExample {
   public static void main(String[] args) {
      List<String> list = new ArrayList<>();
      list.add("apple");
      list.add("banana");
      list.add("orange");

      String[] array = new String[list.size()];
      array = list.toArray(array);

      for (String s : array) {
         System.out.println(s);
      }
   }
}
```

```java
Output: apple
banana
orange
```

# Java 11 Files New Methods
Java 11 introduced some new methods in the Files class and these methods provide better handling. These methods are:

1. readString(Path path, Charset cs) method
2. writeString(Path path, CharSequence csq, OpenOption… options) method

## readString(Path path, Charset cs) method
The **readString(Path path, Charset cs) method** exists in the **java.nio.file.Files** class in **Java 11**. It uses to read the content from a file into a string using the specified charset. Let’s try to explain it with some scenarios where we can use it.

The syntax of the method is given below:

```java
public static String readString(Path path) throws IOException
```

### Scenario 1: Reading a Text File
Suppose we want to read a text file that contains data and process it in a java application.

```java
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.io.IOException;

public class FileReader {

    public static void main(String[] args) throws IOException {
        Path filePath = Paths.get("data.txt");
        String fileContent = Files.readString(filePath, StandardCharsets.UTF_8);
        System.out.println(fileContent);
    }
}
```

Here we create a Path object that represents the file we want to read. After that we can use the readString() method to read the content of the file into a string using the UTF-8 charset.


## Scenario 2: Parsing a CSV File
Let’s try to read the CSV file that you need to parse in your Java application.

```java
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.io.IOException;

public class CsvParser {

    public static void main(String[] args) throws IOException {
        Path filePath = Paths.get("data.csv");
        String fileContent = Files.readString(filePath, StandardCharsets.UTF_8);

        String[] rows = fileContent.split("\n");
        for (String row : rows) {
            String[] columns = row.split(",");
            System.out.println("Name: " + columns[0] + ", Age: " + columns[1]);
        }
    }
}
```

We used the **readString() method** to read the CSV file into a string using the UTF-8 charset. By use of the **split() method** the string is into rows using the newline character as the separator and split each row into columns using the comma character as the separator.

**Basic Example:**

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;

public class Main {  
	public static void main(String[] args) throws IOException{
		try {
		Path path = Paths.get("abc.txt");
		String data = Files.readString(path);
		System.out.println(data);
		System.out.println(data.getClass().getName());
		}catch(IOException e) {
			System.out.println(e.getMessage());
		}
	}        
}
```

```java
OUTPUT:
Hello from Studytonight.
java.lang.String
```

## writeString(Path path, CharSequence csq, OpenOption… options)
The writeString(Path path, CharSequence csq, OpenOption… options) method was introduced in the java.nio.file.Files class in Java 11. It writes a string to a file using the specified charset and options.

Note:- This method is used to write a string to a file. Characters are encoded into bytes using the UTF-8 charset. Files provide one more method that allows setting charset:

The syntax of the method is given below:

```java
public static Path writeString?(Path path, CharSequence csq, OpenOption... options) throws IOException
public static Path writeString?(Path path, CharSequence csq, Charset cs, OpenOption... options) throws IOException
```

### Scenario 1: Writing a Text File
When we want to write to a text file in your Java application. Then we can use the writeString() method to write a string to a file.

```java
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.io.IOException;

public class FileWriter {

    public static void main(String[] args) throws IOException {
        Path filePath = Paths.get("data.txt");
        String fileContent = "Hello, world!";
        Files.writeString(filePath, fileContent, StandardCharsets.UTF_8);
    }
}
```

### Scenario 2: Appending to a Text File
Let’s try to read a text file that already contains some data. After that, we want to append some more data to the end of the file in your Java application.

```java
import java.nio.charset.StandardCharsets;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;
import java.io.IOException;
import java.nio.file.StandardOpenOption;

public class FileAppender {

    public static void main(String[] args) throws IOException {
        Path filePath = Paths.get("data.txt");
        String fileContent = "World!";
        Files.writeString(filePath, fileContent, StandardCharsets.UTF_8, StandardOpenOption.APPEND);
    }
}
```

### Basic Example:

In this example, we are writing a string to file "abc.txt" by using the writeString() method and reading the written string using readString() method.

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;

public class Main {  
	public static void main(String[] args) throws IOException{
		try {
		Path path = Paths.get("abc.txt");
		path = Files.writeString(path, "Welcome to studytonight!!");
		String data = Files.readString(path);
		System.out.println(data);
		}catch(IOException e) {
			System.out.println(e.getMessage());
		}
	}        
}
```

```java
OUTPUT: 
Welcome to studytonight!!
```

### Another Example: Specify Charset
If we want to specify charset of charSequence during writing to file then you can use forName() method. See the example below:

```java
import java.io.IOException;
import java.nio.charset.Charset;
import java.nio.file.Files;
import java.nio.file.Path;
import java.nio.file.Paths;

public class Main {  
	public static void main(String[] args) throws IOException{
		try {
		Path path = Paths.get("abc.txt");
		path = Files.writeString(path, "Welcome to studytonight!!", Charset.forName("UTF-8"));
		String data = Files.readString(path);
		System.out.println(data);
		}catch(IOException e) {
			System.out.println(e.getMessage());
		}
	}        
}
```

```java
OUTPUT:
Welcome to studytonight!!
```

## How was this type of task performed before Java 11?
Let’s see how we read the file before java 11:

```java
import java.io.BufferedReader;
import java.io.FileReader;
import java.io.IOException;

public class FileReaderExample {

    public static void main(String[] args) {
        BufferedReader reader = null;
        try {
            reader = new BufferedReader(new FileReader("data.txt"));
            String line = null;
            while ((line = reader.readLine()) != null) {
                System.out.println(line);
            }
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                if (reader != null) {
                    reader.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```
The readString() method allows us to read the entire contents of a file into a String with a single method call. It’s much simpler and more convenient than BufferedReader to read the file line by line.

## Advantages of readString() method over the BufferedReader approach


- **Simplicity**: The **readString() method** makes the code simpler and easier to read because we don’t need to deal with a BufferedReader and a loop.

- **Efficiency**: As we have seen above example **readString() method"** reads the entire file at once and we don’t need to take the overhead of repeatedly calling **readLine()** and concatenating strings.

- **Error handling**: The **readString() method** provide support to handle errors more consistently than the BufferedReader approach.

Let’s see how we wrote the file before java 11:

```java
import java.io.File;
import java.io.FileWriter;
import java.io.IOException;

public class FileWriterExample {

    public static void main(String[] args) {
        FileWriter writer = null;
        try {
            File file = new File("data.txt");
            writer = new FileWriter(file);
            String fileContent = "Hello, world!";
            writer.write(fileContent);
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                if (writer != null) {
                    writer.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

```java
import java.io.BufferedWriter;
import java.io.FileWriter;
import java.io.IOException;

public class BufferedWriterExample {

    public static void main(String[] args) {
        BufferedWriter writer = null;
        try {
            writer = new BufferedWriter(new FileWriter("data.txt"));
            String fileContent = "Hello, world!";
            writer.write(fileContent);
        } catch (IOException e) {
            e.printStackTrace();
        } finally {
            try {
                if (writer != null) {
                    writer.close();
                }
            } catch (IOException e) {
                e.printStackTrace();
            }
        }
    }
}
```

# Java 11 Predicate Not Method Example
Java 11 introduces a new method i.e. called the **“not() method”** which provides an easy way to negate a predicate. It presents in the **Predicate interface**. A **Predicate interface** is a functional interface that takes an argument and returns a boolean value. Mostly it uses to filter **collections** or **streams** of data.

Let’s understand what it does Negate a predicate is required using the “negate()” method. It’s a **default method** and **static method** that returns a new predicate that is the negation of the original predicate. Let’s see the syntax of not() method:

```java
static <T> Predicate<T> not(Predicate<? super T> target)
```

Let’s see how does Predicate not() method work. Suppose we want to check even or odd numbers by use of a predicate.

```java
import java.util.function.Predicate;

public class Example {
    public static void main(String[] args) {
        Predicate<Integer> isEven = num -> num % 2 == 0;
        Predicate<Integer> isOdd = isEven.not();

        System.out.println(isOdd.test(5)); // Output: true
    }
}
```

Here, we define a predicate called “isEven” that checks whether an integer is even. Now we want to create another predicate called “isOdd”, So we can use the “not()” method to create a new predicate called “isOdd” that checks whether an integer is odd.


We can use the “not()” method as in chained with other methods, like “and()” and “or()”, to create more complex predicates.

```java
import java.util.function.Predicate;

public class Example {
    public static void main(String[] args) {
        Predicate<Integer> isEven = num -> num % 2 == 0;
        Predicate<Integer> isDivisibleBy3 = num -> num % 3 == 0;
        Predicate<Integer> isEvenAndDivisibleBy3 = isEven.not().and(isDivisibleBy3);

        System.out.println(isEvenAndDivisibleBy3.test(6)); // Output: true
        System.out.println(isEvenAndDivisibleBy3.test(9)); // Output: false
    }
}
```

## Limitations
1. It only works for predicates that return a boolean value.
2. It’s not always easy to read and understand the code when multiple negations are involved.

# Java 11 String New Methods
In this post, we will discuss the Java 11 String New Methods. Let’s discuss all the Java 11 String API Additions which help developers.

1. repeat() method
2. isBlank() method
3. lines() method
4. strip() method
5. stripLeading() method
6. stripTrailing() method

## 1. repeat(int count) method
In **Java 11**, the **repeat(int count) method** is defined in the **String class**. It returns a string whose value concatenates with the original string repeated count times. We will see it with an example.

This method takes a single argument of **“int”** type i.e. count which represents the number of times the string should be repeated. The count parameter must be non-negative, or an **IllegalArgumentException** will be thrown.

Syntax

```java
public default String repeat(int count)
```

Let’s discuss the **String repeat() method with an example** and see how it works.

```java
import java.util.Scanner;

public class RepeatExample {

    public static void main(String[] args) {
        
        // Create a Scanner object to read user input
        Scanner scanner = new Scanner(System.in);
        
        // Prompt the user to enter a string
        System.out.print("Enter a string: ");
        String input = scanner.nextLine();
        
        // Prompt the user to enter a repeat count
        System.out.print("Enter a repeat count: ");
        int count = scanner.nextInt();
        
        // Call the repeat() method to repeat the input string
        String repeatedString = input.repeat(count);
        
        // Print the repeated string
        System.out.println("Repeated string: " + repeatedString);
    }
}
```

```java
Output: Enter a string: JavaGoal.com
Enter a repeat count: 3
Repeated string: JavaGoal.comJavaGoal.comJavaGoal.com
```

In the above program, the user enters a string and a repeat count. The repeat() method repeats the input string the specified number of times.

1. Import the **Scanner class** from **java.util package** so that user we can read user input.
2. Created a public class called RepeatExample.
3. As usual, we created a public static main method, which is the entry point for the program.
4. Created a **Scanner object** named scanner to read user input.
5. Used **System.out.print** to prompt the user to enter a string.
6. Used the **nextLine() method** of the Scanner object to read a line of text entered by the user and store it in the input variable.
7. Then again used the **System.out.print** to prompt the user to enter a repeat count.
8. Used the **nextInt() method** of the Scanner object to read an integer entered by the user and store it in the count variable.
9. In the next line, we used the **repeat() method** on the input string, passing in the count variable to repeat the input string the specified number of times and store the result in the repeated string variable.
10. Used **System.out.println** that repeated string to the console, along with a message indicating that it is the repeated string.

### Why should we use the repeat() method with a practical example
Let’s say we want to create a program that needs to generate a string that consists of a repeated sequence of characters. For example, you need to generate a string that consists of alternating “A” and “B” characters, like this: ABABABABAB

**Solution 1 without repeat() method**

```java
public class RepeatWithLoopExample {
    public static void main(String[] args) {
        int sequenceLength = 10;
        String sequence = "";
        for (int i = 0; i < sequenceLength; i++) {
            if (i % 2 == 0) {
                sequence += "A";
            } else {
                sequence += "B";
            }
        }
        System.out.println(sequence);
    }
}
```

```java
Output: ABABABABAB
```

**Solution 2 with repeat() method**

```java
public class RepeatWithExample {
    public static void main(String[] args) {
        int sequenceLength = 10;
        String sequence = "AB".repeat(sequenceLength / 2);

        System.out.println(sequence);
    }
}
```

```java
Output: ABABABABAB
```

## 2. isBlank() method
Java 11 introduces a new method, isBlank() method in the String class in Java 11. This method returns a boolean value that indicates whether a string is empty or contains only whitespace characters. This method doesn’t take any parameters.

Syntax

```java
public boolean isBlank()
```

The **isBlank() method** uses to check whether the string is empty or contains only whitespace characters. If the string is blank, i.e., it is empty or contains only whitespace characters such as space, tab, newline, carriage return, then it returns true, etc. Otherwise, it returns false.

```java
public class IsBlankExample {
    public static void main(String[] args) {
        // empty string
        String str1 = "";
        // string containing only whitespace characters
        String str2 = "  \t \n";
        // non-blank string
        String str3 = "Hello";

        boolean isStr1Blank = str1.isBlank();    // true
        boolean isStr2Blank = str2.isBlank();    // true
        boolean isStr3Blank = str3.isBlank();    // false

        System.out.println("First result: str1: "+ isStr1Blank);
        System.out.println("Second result: str2: "+ isStr2Blank);
        System.out.println("Third result: str3: "+ isStr3Blank)l
    }
}
```

```java
Output: First result: str1: true
Second result: str2: true
Third result: str3: false
```

### Why should we use isBlank() method with a practical example
Data Validation: Whenever we process the user input, We should validate the data to ensure it is correct and complete. There are many cases, where we need to check if the user’s input contains only whitespace characters or is empty.
For example, Validation on the user’s password, name, etc so we can use the isBlank() method.

```java
String password = request.getParameter("password");

if (password.isBlank()) {
    // Show error message: "Password is required."
} else {
    // Process user input
}
```

**File Processing**: When we process the text files, the compiler encounters blank lines or lines that contain only whitespace characters. In such cases, we can use the isBlank() method to filter out those lines.

```java
List<String> urls = Files.lines(Paths.get("urls.txt"))
                            .filter(line -> !line.isBlank())
                            .collect(Collectors.toList());
```

## 3. lines() method

**Java 11** introduces a new method, **The lines() method** in the **String class** that returns a stream of lines extracted from a given string. It returns a sequential ordered stream, which means the lines will be returned in the order they occur in the string.

The **lines() method** works based on the **newline character (‘\n’)** and **carriage return (‘\r’)**. It extracts the lines based on the newline character (‘\n’) or the combination of the carriage return (‘\r’) followed by the newline character (‘\n’). It automatically removes any leading or trailing white space from each line before returning them.

Syntax

```java
public Stream<String> lines()
```

```java
import java.util.stream.Stream;

public class LinesMethodExample {
    public static void main(String[] args) {

        String str = "This is the first line.\nThis is the second line.\nThis is the third line.";
        Stream<String> lines = str.lines();
        lines.forEach(System.out::println);
    }
}
```

### Why should we use lines() method with a practical example
This method helps to organize the text data. Suppose you want to parse text data that is organized into separate lines. So lines() method can split a large string into a stream of individual lines, which can then be processed or analyzed individually.

Let’s suppose we have a large text file having data about customer orders. A single line of text is representing the order and order details are separated by commas. We just want to analyze data to determine the total number of orders and the total amount of money spent on all orders.

```java
import java.io.IOException;
import java.nio.file.Files;
import java.nio.file.Paths;
import java.util.stream.Stream;

public class UseOfLinesMethod {
    public static void main(String[] args) throws IOException {
        // Read the orders from the text file into a stream of lines
        Stream<String> orders = Files.lines(Paths.get("orders.txt"));

        // Compute the total number of orders and the total amount spent
        int numOrders = 0;
        double totalAmount = 0.0;
        for (String order : (Iterable<String>) orders::iterator) {
            String[] components = order.split(",");
            int quantity = Integer.parseInt(components[0]);
            double price = Double.parseDouble(components[1]);
            totalAmount += quantity * price;
            numOrders++;
        }

        // Print the results
        System.out.println("Total number of orders: " + numOrders);
        System.out.println("Total amount spent: $" + totalAmount);
    }
}
```

## 4. strip() method
The **strip() method** is also introduced in **java 11** in the **String class**. This method uses to remove the whitespace characters from both the **beginning** and **end** of a string. But It always returns a new string with the trimmed whitespace characters removed.

In whitespace characters, the spaces, tabs, and line breaks are included. The working of the **strip()** method is almost similar to the **trim()** method, but **strip() method** is more powerful as it can remove other Unicode white space characters in addition to the ASCII whitespace characters that trim() handles. We will discuss the **difference between strip() and trim() methods** later.

Syntax:

```java
public String strip()
```

```java
import java.util.Scanner;

public class UserLogin {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter your username: ");
        String username = scanner.nextLine().strip();

        System.out.print("Enter your password: ");
        String password = scanner.nextLine().strip();

        if (username.equals("admin") && password.equals("password123")) {
            System.out.println("Login successful!");
        } else {
            System.out.println("Invalid username or password!");
        }

        scanner.close();
    }
}
```

### Why should we use strip() method with a practical example
We can use the **strip() method** to remove leading (beginning) and trailing (ending) whitespace characters from a string. This type of method helps to prevent errors and improve data quality.

Suppose we are creating an application where we want to validate the email address to sign up for a newsletter. We want to validate the email address to make sure it’s in the correct format, and we also want to make sure that there are no leading or trailing spaces that could cause issues later on.

```java
import java.util.Scanner;

public class EmailSignup {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);

        System.out.print("Enter your email address: ");
        String email = scanner.nextLine().strip();

        // Validate the email address format
        if (!email.matches("[a-zA-Z0-9._%+-]+@[a-zA-Z0-9.-]+\\.[a-zA-Z]{2,}")) {
            System.out.println("Invalid email address format!");
        } else {
            // Send email confirmation or add email to database
            System.out.println("Thanks for signing up for our newsletter!");
        }

        scanner.close();
    }
}
```

### Difference between strip() and trim() method
Both methods use to remove leading and trailing whitespace characters from a string in Java. But there are a few differences between them, Let’s discuss them one by one

**Unicode support**: The **strip() method** removes all Unicode whitespace characters, while the trim() method only removes ASCII whitespace characters, such as spaces, tabs, and line breaks.

```java
public class DiffStripAndTrim {

    public static void main(String[] args) {
        String str = "  \t Hello World! \n　  ";

        // Using trim() method
        String trimmed = str.trim();
        System.out.println("Using trim() method:");
        System.out.println("Original string: \"" + str + "\"");
        System.out.println("Trimmed string: \"" + trimmed + "\"");

        // Using strip() method
        String stripped = str.strip();
        System.out.println("\nUsing strip() method:");
        System.out.println("Original string: \"" + str + "\"");
        System.out.println("Stripped string: \"" + stripped + "\"");
    }
}
```

```java

Output:

Using trim() method:
Original string: ” Hello World!
　 “
Trimmed string: “Hello World!
　”

Using strip() method:
Original string: ” Hello World!
　 “
Stripped string: “Hello World!”
```

## 5. stripLeading() method
It uses to remove all leading white spaces from a string. The **stripLeading() method** was introduced with java 11 and it’s part of the **String class**. It returns a new string with all the leading white spaces removed.

```java
public String stripLeading()
```

```java
public class StripLeadingExample {
    public static void main(String[] args) {
        String str = "    Hello, World!";
        String strippedStr = str.stripLeading();
        System.out.println("Original string: " + str);
        System.out.println("Stripped string: " + strippedStr);
    }
}
```

## 6. stripTrailing() method
The **stripTrailing() method** was introduced in **java 11** that uses to remove all trailing white spaces from a string. It’s a part of the **String class** and returns a new string with all the trailing white spaces removed.

```java
public String stripTrailing()
```

```java
public class StripTrailingExample {
    public static void main(String[] args) {
        String str = "Hello, World!     ";
        String strippedStr = str.stripTrailing();
        System.out.println("Original string: " + str);
        System.out.println("Stripped string: " + strippedStr);
    }
}
```

# Nest-Based Access Control in Java 11

Java 11 introduced **nest-based access control** that allows classes to access each other's private members **without the need for bridge methods** created by the compiler. These methods are called **accessibility-broadening bridge methods** and the compiler inserts these into the code during the program execution.

Before Java 11, if we have private members in our code then the compiler creates accessibility-broadening bridge methods that increase the size of the deployed applications and may lead to confusion. That's why Java improved nest-based access control.

Java 11 allows classes and interfaces to be nested within each other. These nested type can be **private** fields, methods, and constructors.

## Basic Example: Java 11
In this example, we are calling a **private** method inside a nested class. If we execute this code using earlier versions of Java than Java 11, the compiler will create a bridge method to call the **private** method, but using Java 11 there is no need of a bridge method to call **private** members.

```java
public class Main {
	
	private void display() {
		System.out.println("hello from private method");
	}
	
	class NestedMain{
		void msg() {
			display();
		}
	}
	
	public static void main(String[] args){
		
		Main m = new Main();
		Main.NestedMain n = m.new NestedMain();
		n.msg();
		
	}   
}
```

```java
OUTPUT: 
hello from private method
```

This **output snippet** shows after executing **javap -v Main** command from the terminal and we get the following details of nest-members.

```java
  public static void main(java.lang.String[]);
    descriptor: ([Ljava/lang/String;)V
    flags: (0x0009) ACC_PUBLIC, ACC_STATIC
    Code:
      stack=4, locals=3, args_size=1
         0: new           #5                  // class myjavaproject/Main
         3: dup
         4: invokespecial #6                  // Method "<init>":()V
         7: astore_1
         8: new           #7                  // class myjavaproject/Main$NestedMain
        11: dup
        12: aload_1
        13: dup
        14: invokestatic  #8                  // Method java/util/Objects.requireNonNull:(Ljava/lang/Object;)Ljava/lang/Object;
        17: pop
        18: invokespecial #9                  // Method myjavaproject/Main$NestedMain."<init>":(Lmyjavaproject/Main;)V
        21: astore_2
        22: aload_2
        23: invokevirtual #10                 // Method myjavaproject/Main$NestedMain.msg:()V
        26: return
      LineNumberTable:
        line 17: 0
        line 18: 8
        line 19: 22
        line 21: 26
}
SourceFile: "Main.java"
NestMembers:
  myjavaproject/Main$NestedMain
InnerClasses:
  #12= #7 of #5;                          // NestedMain=class myjavaproject/Main$NestedMain of class myjavaproject/Main
```

The **getNestHost()** method is used to get the name of nest host while the **isNestmateOf()** method is used to check whether a class is a nestmate.

The **getNestMembers()** method returns an array of nest members including classes and interfaces.

## Example: Using getNestHost()
In Java, each class is a member of exactly one nest. We can use **getNestHost()** method to get the nest host of the nest.

```java
import java.util.Arrays;

public class Main {
	
	private void display() {
		System.out.println("hello from private method");
	}

	class NestedMain{
		void msg() {
			display();
		}
	}	
	public static void main(String[] args){
		
		Main m = new Main();
		Main.NestedMain n = m.new NestedMain();
		n.msg();
		// Get Nest Host Name
		System.out.println(Main.class.getNestHost());
		// Get Nest Members
		System.out.println(Arrays.toString(Main.class.getNestMembers()));
		// Check whether a class is nestmateg
		System.out.println(Main.class.isNestmateOf(NestedMain.class));
	}   
}
```

```java
OUTPUT:
hello from private method
class myjavaproject.Main
[class myjavaproject.Main, class myjavaproject.Main$NestedMain]
true
```

# Java 11 HTTP Client API

Java 11 added a new **module java.net.http** and a **package java.net.http** to define the HTTP Client and WebSocket APIs.

This package contains several classes and interfaces to provide high-level client interfaces to HTTP and low-level client interfaces to WebSocket.

We can use these classes and interface to sent synchronous or asynchronous requests.

## List of Interfaces
The following are the interfaces of the java.net.http package and can be used to handle client requests and responses.

| Interface        | Description      |
|------------------|------------------|
|HttpClient.Builder|A builder of HTTP Clients|
|HttpRequest.BodyPublisher|A BodyPublisher converts high-level Java objects into a flow of byte buffers suitable for sending as a request body.|
|HttpRequest.Builder|A builder of HTTP requests.|
|HttpResponse<T>|An HTTP response.|
|HttpResponse.BodyHandler<T>|A handler for response bodies.|
|HttpResponse.BodySubscriber<T>|A BodySubscriber consumes response body bytes and converts them into a higher-level Java type.|
|HttpResponse.PushPromiseHandler<T>|A handler for push promises.|
|HttpResponse.ResponseInfo|Initial response information supplied to a BodyHandler when a response is initially received and before the body is processed.|
|WebSocket|A WebSocket Client.|
|WebSocket.Builder|A builder of WebSocket Clients.|
|WebSocket.Listener|The receiving interface of WebSocket.|

## List of Classes
The following are the classes under the java.net.http package and used to create HttpClient and connect to the host.

| Class            | Description      |
|------------------|------------------|
| HttpClient       | An HTTP Client.  |
|HttpHeaders|A read-only view of a set of HTTP headers.|
| HttpRequest        | An HTTP request.      |
|HttpRequest.BodyPublishers|Implementations of BodyPublisher that implement various useful publishers, such as publishing the request body from a String, or from a file.|
| HttpResponse.BodyHandlers        | Implementations of BodyHandler that implement various useful handlers, such as handling the response body as a String, or streaming the response body to a file.      |
|HttpResponse.BodySubscribers|Implementations of BodySubscriber that implement various useful subscribers, such as converting the response body bytes into a String, or streaming the bytes to a file.|

## Time for an Example:
In this example, we are sending a get request to "studytonight.com" by using HttpClient.

```java
import java.io.IOException;
import java.net.URI;
import java.net.http.HttpClient;
import java.net.http.HttpClient.Redirect;
import java.net.http.HttpClient.Version;
import java.net.http.HttpRequest;
import java.net.http.HttpResponse;
import java.net.http.HttpResponse.BodyHandlers;
import java.time.Duration;

public class Main {
	public static void main(String[] args) throws IOException, InterruptedException {
		HttpRequest request = HttpRequest.newBuilder()
				.GET()
				.uri(URI.create("https://www.studytonight.com"))
				.build();
		HttpClient httpClient = HttpClient.newBuilder()
				.version(Version.HTTP_2)
				.followRedirects(Redirect.NORMAL)
				.connectTimeout(Duration.ofSeconds(20))
				.build();
		HttpResponse<String> response = httpClient.send(request, BodyHandlers.ofString());
		System.out.println(response.statusCode());

	}
}
```

```java
OUTPUT:
200
```

# Execute Java File Without Compilation
From Java 11, Java provides flexibility to run Java code without compilation. It means we can execute Java code in a single step.

Before Java 11, if we execute Java file then first, we need to compile the code and then run the code. This whole process requires two major steps:

- Compile Java code

- Run Java code

To compile the code, we use **javac java_file.java** command. and

To run this file, we use **java java_file** command in the terminal (cmd in windows).

But if we are working with Java 11 then we don't need to follow these two steps. Just use single command **java java_file.java** and it will execute the file by producing the desired result.

**Note**: This feature is applicable if we have a single file of source code. It means all the code is in a single file, with no external dependency.

## Time for an Example:
This is a simple Java example that we are taking to execute using Java 11 compiler.

```java
public class Main {
	public static void main(String[] args){
		System.out.println("This code is executed without explicit compilation!");
	}
}
```

```java
OUTPUT:
This code is executed without explicit compilation!
```