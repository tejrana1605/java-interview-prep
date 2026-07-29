# Record Patterns (Second Preview) – JEP 432

ecord patterns were first introduced in Java 19. A record pattern can be used with instanceof or switch to access the fields of a record without casting and calling accessor methods.

Java 20 delivers an improved and refined version of record patterns. Let’s see some of the improvements in this release:

- Added support for type inference of arguments of generic record patterns.
- Added support for record patterns to be usable in the header of an enhanced for loop.
- Removed support for named record patterns, where we could provide an optional identifier to the record patterns that we can use to refer to the record pattern.

Here is a simple sample record:

```java
public record Position(int x, int y) {}
```

Using a record pattern, we can now write an instanceof expression as follows:

```java
Object object = ...

if (object instanceof Position(int x, int y)) {
  System.out.println("object is a position, x = " + x + ", y = " + y);
} 
```

We can then – provided object is of type Position – directly access its x and y values.

The same can be done in a switch expression:

```java
Object object = ...

switch (object) {
  case Position(int x, int y) 
      -> System.out.println("object is a position, x = " + x + ", y = " + y);

  // other cases ...
}
```

## Inference of Type Arguments of Generic Record Patterns

To explain this change, we need a more complex example.

Given are a generic interface Multi<T> and two implementing records, Tuple<T> and Triple<T>, which contain two and three values of type T, respectively:

```java
interface Multi<T> {}

record Tuple<T>(T t1, T t2) implements Multi<T> {}

record Triple<T>(T t1, T t2, T t3) implements Multi<T> {}
```

With the following code, we can check which concrete implementation a given Multi object is:

```java
Multi<String> multi = ...

if (multi instanceof Tuple<String>(var s1, var s2)) {
  System.out.println("Tuple: " + s1 + ", " + s2);
} else if (multi instanceof Triple<String>(var s1, var s2, var s3)) {
  System.out.println("Triple: " + s1 + ", " + s2 + ", " + s3);
}
```

So far, we had to specify the type parameter (String in this case) with each instanceof check.

As of Java 20, the compiler can infer the type so that we can omit it from the instanceof checks:

```java
if (multi instanceof Tuple(var s1, var s2)) {
  System.out.println("Tuple: " + s1 + ", " + s2);
} else if (multi instanceof Triple(var s1, var s2, var s3)) {
  System.out.println("Triple: " + s1 + ", " + s2 + ", " + s3);
}
```

I don’t particularly like the so-called “raw types” syntax used here. Raw types typically cause the compiler to ignore any type information. But that is not the case here.

I would therefore consider it more consistent to use the diamond operator, as follows:

```java
if (multi instanceof Tuple<>(var s1, var s2)) {
  System.out.println("Tuple: " + s1 + ", " + s2);
} else if (multi instanceof Triple<>(var s1, var s2, var s3)) {
  System.out.println("Triple: " + s1 + ", " + s2 + ", " + s3);
}
```

The type parameter can also be omitted from switch statements as of Java 20.

## Record Patterns in for Loops
Let’s say we have a list of positions and want to print them to the console. So far, we could do it like this:

```java
List<Position> positions = ...

for (Position p : positions) {
  System.out.printf("(%d, %d)%n", p.x(), p.y());
}
```

Starting with Java 20, we can also specify a record pattern in the for loop and then access x and y directly (just like with instanceof and switch):

```java
for (Position(int x, int y) : positions) {
  System.out.printf("(%d, %d)%n", x, y);
}
```

## Removal of Support for Named Record Patterns
Up to now, there were the following three ways to perform pattern matching on a record:

```java
Object object =  new Position(4, 3);

// 1. Pattern Matching for instanceof
if (object instanceof Position p) {
  System.out.println("object is a position, p.x = " + p.x() + ", p.y = " + p.y());
}

// 2. Record Pattern
if (object instanceof Position(int x, int y)) {
  System.out.println("object is a position, x = " + x + ", y = " + y);
}

// 3. Named Record Pattern
if (object instanceof Position(int x, int y) p) {
  System.out.println("object is a position, p.x = " + p.x() + ", p.y = " + p.y() 
                                         + ", x = " + x + ", y = " + y);
}
```

In the third variant (“named record pattern”), there are two ways to access the fields of the record – either via the x and y variables – or via p.x() and p.y().

This variant was decided to be superfluous and removed again in Java 20.