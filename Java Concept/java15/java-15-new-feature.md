# Text Blocks (Final Feature)

Text Blocks introduced as preview in Java SE 13 became final in Java 15.
Text Blocks allow writing multi-line strings easily.

Example

```java
String json = """
{
  "name": "Tej",
  "city": "Haldwani"
}
""";
```

Benefits

✅ No need for \n
✅ No string concatenation
✅ More readable code
✅ Useful for SQL, JSON, XML

## Sealed Classes (Preview Feature)

Sealed classes restrict which classes can extend or implement them.

Example

```java
public sealed class Vehicle
    permits Car, Bike {
}

final class Car extends Vehicle {}
final class Bike extends Vehicle {}
```

Benefits

✅ Better control over inheritance
✅ Safer API design
✅ Useful in framework development

This feature became final in Java SE 17.

## 3️⃣ Hidden Classes

Java 15 introduced Hidden Classes mainly for frameworks.

Purpose:

- Used internally by frameworks

- Cannot be accessed directly by normal code

Frameworks like:

- Bytecode libraries

- Dynamic proxies

Example use cases:

- Lambda implementation

- Runtime generated classes

## ZGC Improvements

Enhancements to Z Garbage Collector.

New improvements:

- Better performance

- Reduced memory overhead

- More platform support

## EdDSA Cryptographic Algorithm

Java 15 added support for Edwards-Curve Digital Signature Algorithm (EdDSA).

Benefits:

- Faster digital signatures

- Stronger security

- Used in modern cryptography

## Remove Nashorn JavaScript Engine

Java 15 removed Nashorn JavaScript engine.

Previously Java could run JavaScript like this:

```java
ScriptEngine engine = new ScriptEngineManager().getEngineByName("nashorn");
```

Now developers use external engines like:

- GraalVM JavaScript.

## Remove RMI Activation

Old Remote Method Invocation (RMI) activation mechanism was removed.

Reason:

- Rarely used

- Modern distributed systems use:

1. REST APIs

2. gRPC

3. Microservices