# Java 9 Interview Questions

## 1. What are the major features introduced in Java 9?

Java Platform Module System (JPMS) a.k.a Project Jigsaw

- JShell (Java Shell)

- Stream API improvements

- Private methods in interfaces

- Improved Javadoc with search

- Collection factory methods

- Process API enhancements

- Reactive Streams (Flow API)

## 2. What is the Java Platform Module System (JPMS)?

It introduces a new module system that allows developers to modularize code for better maintainability, encapsulation, and performance. The key components:

- module-info.java file

- exports, requires keywords

## 3. How does Java 9 modularity improve the JDK and applications?

- Reduces JDK size by breaking it into modules (like java.base, java.sql, etc.)

- Improves security by restricting internal APIs

- Speeds up application startup

## 4. What is JShell and what is it used for?

JShell is an interactive REPL (Read-Eval-Print Loop) tool introduced in Java 9 to test Java snippets quickly without creating full classes.

```java
Example:
jshell> int x = 5 + 2
```

## 5. Explain collection factory methods introduced in Java 9.

New static methods like List.of(), Set.of(), Map.of() provide immutable collections easily.

```java
List<String> list = List.of("A", "B", "C");
```

## 6. Can you have private methods in interfaces in Java 9?

Yes. Java 9 allows private methods inside interfaces to share common code among default and static methods.

```java
interface MyInterface {
    private void log(String msg) {
        System.out.println("Log: " + msg);
    }
}
```

## 7. What enhancements were made to the Stream API in Java 9?

New methods added:

- takeWhile()

- dropWhile()

- iterate() (with predicate)

```java
Stream.of(1, 2, 3, 4, 5)
      .takeWhile(n -> n < 4)
      .forEach(System.out::println); // 1, 2, 3
```

## 8. What is the Flow API in Java 9?

Introduces Reactive Streams using Flow.Publisher, Flow.Subscriber, Flow.Processor, and Flow.Subscription for asynchronous, non-blocking stream processing.

## 9. How has Process API been improved in Java 9?

ProcessHandle interface was added to get process info:

```java
ProcessHandle.current().pid();
```

It allows interaction with OS processes (PID, CPU time, etc.).

### 10. What’s new in JavaDoc with Java 9?

- JavaDoc now has a built-in search feature

- Outputs valid HTML5

- Includes module info if used

## Can modules be used with older versions of Java?
No, modules require Java 9+.

## What is the default base module in Java 9?
java.base – implicitly available to all modules.

## Is Java 9 backward compatible?
Mostly, but some internal APIs (like sun.misc.Unsafe) are now restricted.

## Write a program to return all numbers less than 5 from a list until the condition fails (stop on first number ≥ 5).

Use **Stream.takeWhile()** to filter a list

```java
import java.util.List;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<Integer> numbers = List.of(1, 3, 5, 2, 4, 6);
        List<Integer> result = numbers.stream()
                                      .takeWhile(n -> n < 5)
                                      .collect(Collectors.toList());
        System.out.println(result);  // Output: [1, 3]
    }
}
```

## 2. Create an Immutable List Using Factory Methods
Create an immutable list of 3 cities in Java 9.

```java
import java.util.List;

public class Main {
    public static void main(String[] args) {
        List<String> cities = List.of("Paris", "London", "Tokyo");
        System.out.println(cities);
    }
}
```

## Create an interface with a private method and use it in a default method.

```java
interface Greeting {
    private String format(String name) {
        return "Hello, " + name;
    }

    default void sayHello(String name) {
        System.out.println(format(name));
    }
}

public class Main implements Greeting {
    public static void main(String[] args) {
        new Main().sayHello("Alice");  // Output: Hello, Alice
    }
}
```

## Print the current process ID using Java 9.

Use ProcessHandle to print current process PID

```java
public class Main {
    public static void main(String[] args) {
        long pid = ProcessHandle.current().pid();
        System.out.println("PID: " + pid);
    }
}
```

## What is the module-info.java file and how do you define a module?

Create a module and access it

```java
// module-info.java
module com.example.myapp {
    requires java.base;
    exports com.example.myapp;
}
```

## Generate a sequence of even numbers ≤ 10.

Using Stream.iterate() with Predicate

```java
import java.util.stream.Stream;

public class Main {
    public static void main(String[] args) {
        Stream.iterate(0, n -> n <= 10, n -> n + 2)
              .forEach(System.out::println);
    }
}
```

## Create a simple modular application with:

- A module named greetings

- A class HelloService that prints a message

**module-info.java**

```java
module greetings {
    exports com.example.greetings;
}
```

**HelloService.java**

```java
package com.example.greetings;

public class HelloService {
    public void sayHello(String name) {
        System.out.println("Hello, " + name);
    }
}
```

**MainApp.java (in another module):**

```java
import com.example.greetings.HelloService;

public class MainApp {
    public static void main(String[] args) {
        new HelloService().sayHello("Java 9");
    }
}

```

## Write a Java 8 and Java 9 version of generating numbers divisible by 3 up to 30 using Stream.iterate().

**Java 8:**

```java
Stream.iterate(0, n -> n + 3)
      .limit(11)
      .forEach(System.out::println);
```

**Java 9:**

```java
Stream.iterate(0, n -> n <= 30, n -> n + 3)
      .forEach(System.out::println);
```

**Difference:** Java 9's iterate() accepts a termination condition.

## From a list of integers, skip elements until the first even number appears.

Stream dropWhile() – Coding Use

```java
List<Integer> nums = List.of(1, 3, 5, 6, 8, 9);
List<Integer> result = nums.stream()
    .dropWhile(n -> n % 2 != 0)
    .collect(Collectors.toList());

System.out.println(result); // Output: [6, 8, 9]
```

## Group words by length and filter only those that start with "J".

Use Collectors.filtering() with groupingBy (Java 9+)

```java
import java.util.*;
import java.util.stream.Collectors;

public class Main {
    public static void main(String[] args) {
        List<String> words = List.of("Java", "Jack", "John", "Apple", "Code");

        Map<Integer, List<String>> result = words.stream()
            .collect(Collectors.groupingBy(
                String::length,
                Collectors.filtering(w -> w.startsWith("J"), Collectors.toList())
            ));

        System.out.println(result);
    }
}
```

## Create a basic publisher and subscriber using Java 9's Flow API.

Simulate Reactive Streams with Flow API

```java
import java.util.concurrent.Flow.*;

public class SimplePublisher implements Publisher<String> {
    public void subscribe(Subscriber<? super String> subscriber) {
        subscriber.onSubscribe(new Subscription() {
            public void request(long n) {
                subscriber.onNext("Hello Reactive");
                subscriber.onComplete();
            }

            public void cancel() {
                System.out.println("Subscription cancelled.");
            }
        });
    }

    public static void main(String[] args) {
        SimplePublisher publisher = new SimplePublisher();
        publisher.subscribe(new Subscriber<>() {
            public void onSubscribe(Subscription s) { s.request(1); }
            public void onNext(String item) { System.out.println("Received: " + item); }
            public void onError(Throwable t) {}
            public void onComplete() { System.out.println("Done"); }
        });
    }
}
```

## Scenario 1: Modularity in a Large Project
❓**Scenario:**

You’re working on a monolithic Java application with multiple packages. Your team wants to convert it into a modular architecture for better encapsulation and dependency management using Java 9.

Q: How would you apply Java 9's module system to achieve this?

- Identify logical modules (e.g., user.auth, payment.core, report.engine)

- Create module-info.java in each module to declare:

- exports (to make public APIs accessible)

- requires (to declare dependencies)

- Use jlink to build a custom runtime if needed

- Benefit: Limits classpath pollution, restricts reflection access, improves startup time

## 🔶 Scenario 2: Startup Time Optimization
❓Scenario:

Your Java application takes a long time to start due to loading of unnecessary classes and libraries. How can Java 9 help?

**Expected Answer:**

- Use Java 9 modules to include only required modules at runtime.

- Replace full JDK dependencies with only what's needed (via --add-modules).

- Use jlink to build a custom runtime image that includes only necessary modules, reducing footprint and improving startup.

## Scenario 4: Immutable Collections

❓Scenario:

You notice developers are still using Collections.unmodifiableList() to create read-only lists. How can Java 9 simplify this?

- Use Java 9’s new collection factory methods: List.of(), Set.of(), Map.of()

- They are more concise, immutable by default, and prevent null values.

```java
List<String> colors = List.of("Red", "Green", "Blue");
```

## Scenario 5: Stream API Improvement for Performance

❓Scenario:

You're processing a large data set. You want to terminate stream operations early based on a condition. What's a Java 9 way to do this?

- Use Stream.takeWhile() to process until a condition is met.

- dropWhile() to skip elements until a condition fails.

- These are more performant than filter() with infinite streams.

## Scenario 6: Reactive Programming with Flow API

❓Scenario:

You're building a chat application with asynchronous data streams. How can Java 9's Flow API help?

- Use Flow.Publisher, Flow.Subscriber, Flow.Processor, and Flow.Subscription.

- Helps build reactive, non-blocking pipelines.

- Integrates with reactive libraries like RxJava or Project Reactor.

## Scenario 7: Preventing Access to Internal APIs

❓Scenario:

Your code breaks in Java 9 due to use of sun.misc.Unsafe. How does Java 9 enforce access control and how do you handle it?

- Java 9 encapsulates internal APIs using the module system.

- Access to non-exported packages is restricted unless explicitly allowed using:

```java
--add-exports java.base/sun.misc=ALL-UNNAMED
```

- Best practice is to replace internal APIs with public standard APIs.

---

## 📌 Summary Table

| Scenario              | Java 9 Feature        | Outcome                      |
| --------------------- | --------------------- | ---------------------------- |
| Modularity            | JPMS (modules)        | Cleaner architecture         |
| Fast startup          | `jlink`               | Smaller, faster builds       |
| Rapid testing         | JShell                | Better developer experience  |
| Read-only collections | `List.of()`           | Simpler, safer code          |
| Efficient streams     | `takeWhile/dropWhile` | Early termination            |
| Reactive streams      | `Flow API`            | Async, back-pressure capable |
| Safe encapsulation    | Module encapsulation  | Prevents misuse of internals |

---


