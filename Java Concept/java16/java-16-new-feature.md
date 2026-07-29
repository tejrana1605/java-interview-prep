# java 16 new feature

Java SE 16 was released in March 2021. It introduced several improvements, and some preview features from earlier versions became final in this release.

## Records (Final Feature)

Records were introduced as preview in Java SE 14 and became final in Java 16.

Records are used to create immutable data classes with very little code.

Example

```java
public record Person(String name, int age) {}
```

Java automatically generates:

- constructor

- getters

- equals()

- hashCode()

- toString()

## Generated Methods Example

```java
Person p = new Person("Tej", 25);
System.out.println(p.name());
```

✅ Benefits

- Reduces boilerplate code

- Ideal for DTO / API responses / data models

## Pattern Matching for instanceof (Final)

Pattern matching introduced in preview in Java SE 14 became final.

Old Way

```java
if (obj instanceof String) {
    String s = (String) obj;
    System.out.println(s.length());
}
```

Java 16

```java
if (obj instanceof String s) {
    System.out.println(s.length());
}
```

Benefits:

- No casting required

- Cleaner code

## Sealed Classes (Second Preview)

Sealed classes were improved in Java 16.

Example:

```java
public sealed class Shape
    permits Circle, Rectangle {
}

final class Circle extends Shape {}
final class Rectangle extends Shape {}
```

Sealed classes became final in Java SE 17.

## New Stream Method: toList()

Java 16 introduced Stream.toList() method.

Before

```java
List<Integer> list =
numbers.stream().collect(Collectors.toList());
```

Java 16

```java
List<Integer> list = numbers.stream().toList();
```

Benefits:

- Cleaner code

- Less boilerplate

## jpackage Tool (Final)

The jpackage tool introduced in Java SE 14 became final.

Purpose:
Create native installers for Java apps.

Example:

```java
jpackage --input target --name MyApp --main-jar app.jar
```

It generates installers like:

- .exe

- .msi

- .dmg

- .rpm

## Strongly Encapsulate JDK Internals

Java 16 strongly encapsulates internal JDK APIs.

Meaning:

Developers cannot access internal JDK classes like:

```java
sun.misc.Unsafe
```

unless explicitly allowed.

Benefits:

- Improved security

- Better maintainability

## Vector API (Incubator)

Java 16 introduced Vector API for high-performance computations.

Purpose:

- Use CPU vector instructions

- Improve performance for:

Examples:

- Machine learning

- Scientific computing

- Large data processing