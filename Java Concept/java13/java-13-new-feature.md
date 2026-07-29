# Java 13 new features

## Text Blocks (Preview Feature)

Java 13 introduced Text Blocks to write multi-line strings easily.

```java
Old Way

String json = "{\n" +
              "  \"name\": \"Tej\",\n" +
              "  \"age\": 25\n" +
              "}";
```

java 13 Text Block.

```java
String json = """
{
  "name": "Tej",
  "age": 25
}
""";
```

## Switch Expressions (Second Preview)

The Switch Expression introduced in Java SE 12 was improved in Java 13.

```java
int result = switch (day) {
    case MONDAY, FRIDAY -> 6;
    case TUESDAY -> 7;
    default -> {
        yield 0;
    }
};
```

**New keyword**

yield → used to return value from a block inside switch.

## Dynamic CDS Archives

Improvement to Class Data Sharing (CDS).

Now JVM can create CDS archive dynamically at application exit.

Benefits:

Faster startup

Less memory usage

Useful for cloud environments.

## ZGC Improvements

Enhancement to Z Garbage Collector (ZGC).

New features:

- Memory uncommit support

- Reduced heap memory usage

- Better performance for large applications

ZGC is a low-latency garbage collector.

## Reimplement Legacy Socket API

Java 13 introduced a new implementation of the legacy socket API.

Benefits:

- Better maintainability

- Improved performance

- Easier debugging.

## FileSystems.newFileSystem() Enhancement

Improved file system handling.

Example:

```java
FileSystem fs = FileSystems.newFileSystem(path);
```
Allows easier access to file systems.