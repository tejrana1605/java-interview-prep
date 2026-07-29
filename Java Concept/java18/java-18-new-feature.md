# Java 18 New Feature

Java SE 18 was released in March 2022. It is a non-LTS release after Java SE 17 and mainly introduced developer productivity improvements and API enhancements.

## Simple Web Server (New Feature)

Java 18 introduced a simple command-line web server for static files.

It is useful for:

- testing

- development

- learning

- quick demos

## Start Web Server

```java
</> Bash
jwebserver
```

✅ Benefits

No need to install Apache or Nginx

Very useful for quick testing

## 2️⃣ UTF-8 by Default

Java 18 made UTF-8 the default character encoding for the entire platform.

Before Java 18:

- Encoding depended on OS and locale

After Java 18:

- Default encoding is always UTF-8

Example:

```java
FileReader reader = new FileReader("file.txt");
```

Now it always uses UTF-8 encoding.

✅ Benefits

- Consistent behavior across systems

- Fewer encoding bugs

## Code Snippets in Javadoc

Java 18 added a new @snippet tag in Javadoc to show code examples.

Example

```java
/**
 * Example:
 * {@snippet :
 * int sum = a + b;
 * }
 */
```

Benefits:

- Better documentation

- Syntax highlighting

- Code validation

Very useful for library developers.

## Vector API (Third Incubator)

The Vector API was improved again.

Purpose:

- Perform calculations using CPU vector instructions

Use cases:

- machine learning

- data processing

- scientific computing

- graphics processing

Example operations:

- vector addition

- multiplication

- matrix calculations

## Foreign Function & Memory API (Second Incubator)

This API allows Java to call native code (C/C++) without JNI.

Example uses:

- high-performance libraries

- system-level programming

- interacting with native OS APIs

Benefits:

- simpler than JNI

- safer memory access

- better performance

## Internet Address Resolution SPI

Java 18 introduced a Service Provider Interface (SPI) for hostname resolution.

This allows developers to customize how hostnames and IP addresses are resolved.

Example:

- custom DNS resolver

- cloud-based networking