# Java 14 new features

## Switch Expressions (Final Feature)

The switch expression introduced in preview in Java SE 12 and Java SE 13 became final in Java 14.

Example

```java
int days = switch (month) {
    case JAN, MAR, MAY -> 31;
    case APR, JUN -> 30;
    case FEB -> 28;
};
```

✅ No break needed
✅ Less boilerplate code
✅ Can return value directly

## Records (Preview Feature)

Records were introduced to reduce boilerplate code for data classes.

Before Records

```java
public class Person {
    private final String name;
    private final int age;

    public Person(String name, int age){
        this.name = name;
        this.age = age;
    }

    public String getName(){ return name; }
    public int getAge(){ return age; }
}
```

With Record

```java
public record Person(String name, int age) {}
```

Java automatically creates:

- constructor

- getters

- toString()

- equals()

- hashCode()

Records became final in Java SE 16.

## Pattern Matching for instanceof (Preview)

Java 14 simplified type checking.

Old Way

```java
if (obj instanceof String) {
    String str = (String) obj;
    System.out.println(str.length());
}

```

Java 14

```java
if (obj instanceof String str) {
    System.out.println(str.length());
}
```

Benefits:

- No explicit casting

- Cleaner code

This feature became final in Java SE 16.

## Helpful NullPointerException

Java 14 improved NullPointerException messages.

Example

Before:

```java
NullPointerException
```

Now:

```java
Cannot invoke "user.getName()" because "user" is null

```

This helps developers quickly identify the null variable.

## Packaging Tool (jpackage)

Java 14 introduced jpackage tool.

Purpose:
Create native installers for Java applications.

Example installers:

- .exe (Windows)

- .dmg (Mac)

- .deb / .rpm (Linux)

Example command:

```java
jpackage --input target --name MyApp --main-jar app.jar
```

## ZGC Improvements

Java 14 improved Z Garbage Collector.

Benefits:

- Better performance

- Lower latency

- Support for macOS and Windows.