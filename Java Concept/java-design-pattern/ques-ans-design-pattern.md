# Table of Contents
| Sr.No.        | Question      | 
| ------------- |-------------| 
| 1             |[Explain differences between Abstract Factory and Factory Method?](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#explain-differences-between-abstract-factory-and-factory-method) | 
| 2             |[When should I choose Abstract Factory over Factory Method?](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#when-should-i-choose-abstract-factory-over-factory-method) |
| 3             |[Simple Example of Factory Method](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#simple-example-of-factory-method) |
| 4             |[Simple Abstract Factory Example](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#simple-abstract-factory-example) |
| 5             |[Show a minimal Java Builder pattern example](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#show-a-minimal-java-builder-pattern-example) |
| 6             |[When to use Builder vs Factory in Java](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#when-to-use-builder-vs-factory-in-java) | 
| 7             |[How to implement immutable objects with Builder](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#how-to-implement-immutable-objects-with-builder) |
| 8             |[How to implement thread-safe immutable builders for concurrency](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#how-to-implement-thread-safe-immutable-builders-for-concurrency) |
| 9             |[Provide a concrete Java example of a thread-safe builder producing immutable objects](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#provide-a-concrete-java-example-of-a-thread-safe-builder-producing-immutable-objects) |
| 10             |[Add validation and fluent error reporting to the thread-safe builder](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#add-validation-and-fluent-error-reporting-to-the-thread-safe-builder) |
| 11             |[Provide a Java example using deep cloning for Prototype](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#provide-a-java-example-using-deep-cloning-for-prototype) |
| 12             |[Show a thread-safe deep-clone implementation for Prototype](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#show-a-thread-safe-deep-clone-implementation-for-Prototype) |
| 13             |[Show a Java example of a thread-safe deep-clone using Cloneable](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#show-a-java-example-of-a-thread-safe-deep-clone-using-Cloneable) |


# Explain differences between Abstract Factory and Factory Method
The Abstract Factory and Factory Method design patterns are both creational patterns used to encapsulate object creation, but they differ in scope, complexity, and use case.

### Key Differences

| Aspect        | Factory Method      |  Abstract Factory      |
| ------------- |-------------|--------------|
| **Purpose** |Creates a single object, letting subclasses decide which class to instantiate|Creates families of related objects, without specifying their concrete classes|
| **Product Types** |Usually deals with one type of product (single hierarchy)|Deals with multiple related product types (product families)|
| **Implementation** |Typically a single factory method in a base class or interface, overridden by subclasses|An interface (or abstract class) with multiple factory methods—one for each product type; each concrete factory implements these methods|
| **Level of Abstraction** |Lower: focuses on delegating instantiation to subclasses|Higher: encapsulates creation of entire families of related products|
| **Example** |A document editor might let each subclass create a certain type of Document (createDocument())|A GUI toolkit might allow switching between Windows and MacOS themes by using an abstract factory that creates Button and Checkbox objects as a set|
| **Usage Scenario** |Use when a class can't anticipate which subclass to instantiate, or delegates object creation to subclasses|Use when system needs to create multiple families of related objects, ensuring consistency between them|
| **Structure** |One creation method per product class|Several creation methods grouped into a single factory object|
| **Client Knowledge** |Client works with a generic creator and the created objects|Client works only with abstract factories and abstract products, never with concrete implementations directly|

### Example Summary

* Factory Method:
```java
// Abstract creator
abstract class Dialog {
    public abstract Button createButton();
}
// Concrete creator
class WindowsDialog extends Dialog {
    public Button createButton() { return new WindowsButton(); }
}
```
* Abstract Factory:

```java
interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}
class WindowsFactory implements GUIFactory {
    public Button createButton() { return new WindowsButton(); }
    public Checkbox createCheckbox() { return new WindowsCheckbox(); }
}
```
### In Summary
- **Factory Method:** Use for single-product families (one hierarchy), delegates object creation to subclasses.

- **Abstract Factory:** Use for families of products (multiple hierarchies), encapsulates creation of interrelated products so that families are always used together and can be swapped easily.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# When should I choose Abstract Factory over Factory Method

Choose the Abstract Factory pattern over the Factory Method pattern when your application needs to create families of related or dependent objects that must be used together, and you want to ensure their compatibility and interchangeability.

### When to Prefer Abstract Factory

- **Multiple Related Products:**

Use Abstract Factory when you need to create several kinds of products (e.g., Button, Checkbox, Textbox) which belong to the same family (e.g., Windows or Mac UI components), and these product families can vary at runtime.​

- **Consistency Across Products:**

When your system requires that multiple objects created together should work well as a set (such as widgets that should look consistent), Abstract Factory guarantees that only compatible products are produced together.​

- **Swappable Product Families:**

If you want to be able to swap out entire sets of products (e.g., look-and-feel or OS-specific behaviors) without changing the application's code, Abstract Factory provides this level of abstraction.​

- **Decoupled Client Code:**

Abstract Factory hides concrete classes from client code, ensuring clients depend only on product and factory interfaces, not on implementation details.

### When Factory Method Suffices
If you only need to create one type of product and just want to delegate which subclass gets instantiated, Factory Method suffices and is simpler to use.

### Decision Rule of Thumb
- Choose Abstract Factory when you need to create multiple related objects as a family and those families may need to vary.

- Choose Factory Method when only a single product type needs to be varied or determined by subclass.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# Simple Example of Factory Method

Suppose you want to create Animal objects but you want subclasses to decide which animal to instantiate.

```java
// Product interface
interface Animal {
    void speak();
}

// Concrete products
class Dog implements Animal {
    public void speak() { System.out.println("Woof!"); }
}
class Cat implements Animal {
    public void speak() { System.out.println("Meow!"); }
}

// Creator (Factory)
abstract class AnimalFactory {
    // Factory Method
    public abstract Animal createAnimal();
}

// Concrete factories
class DogFactory extends AnimalFactory {
    public Animal createAnimal() { return new Dog(); }
}
class CatFactory extends AnimalFactory {
    public Animal createAnimal() { return new Cat(); }
}

// Usage
public class FactoryMethodDemo {
    public static void main(String[] args) {
        AnimalFactory dogFactory = new DogFactory();
        Animal dog = dogFactory.createAnimal();
        dog.speak(); // Woof!

        AnimalFactory catFactory = new CatFactory();
        Animal cat = catFactory.createAnimal();
        cat.speak(); // Meow!
    }
}
```
**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# Simple Abstract Factory Example
Suppose you have two animal families: land animals and sea animals, each with different variants.

```java
// Product interfaces
interface LandAnimal {
    void speak();
}
interface SeaAnimal {
    void speak();
}

// Land animal variants
class Lion implements LandAnimal {
    public void speak() { System.out.println("Roar!"); }
}
class Elephant implements LandAnimal {
    public void speak() { System.out.println("Trumpet!"); }
}

// Sea animal variants
class Shark implements SeaAnimal {
    public void speak() { System.out.println("Shark sound!"); }
}
class Dolphin implements SeaAnimal {
    public void speak() { System.out.println("Click!"); }
}

// Abstract Factory
interface AnimalFamilyFactory {
    LandAnimal createLandAnimal();
    SeaAnimal createSeaAnimal();
}

// Concrete factories
class AfricanAnimalFactory implements AnimalFamilyFactory {
    public LandAnimal createLandAnimal() { return new Lion(); }
    public SeaAnimal createSeaAnimal() { return new Shark(); }
}
class AsianAnimalFactory implements AnimalFamilyFactory {
    public LandAnimal createLandAnimal() { return new Elephant(); }
    public SeaAnimal createSeaAnimal() { return new Dolphin(); }
}

// Usage
public class AbstractFactoryDemo {
    public static void main(String[] args) {
        AnimalFamilyFactory africanFactory = new AfricanAnimalFactory();
        LandAnimal lion = africanFactory.createLandAnimal();
        SeaAnimal shark = africanFactory.createSeaAnimal();
        lion.speak(); // Roar!
        shark.speak(); // Shark sound!

        AnimalFamilyFactory asianFactory = new AsianAnimalFactory();
        LandAnimal elephant = asianFactory.createLandAnimal();
        SeaAnimal dolphin = asianFactory.createSeaAnimal();
        elephant.speak(); // Trumpet!
        dolphin.speak(); // Click!
    }
}
```

### Summary Table
|Pattern	|Key Purpose	|Example above|
|-----------|---------------|-------------|
|Factory Method|Create one type of object, subclass picks|Dog vs. Cat factory|
|Abstract Factory|Create families of related objects, swap families|African vs. Asian animal family|

Both patterns control object creation, but Factory Method is for one product at a time (single hierarchy), while Abstract Factory creates multiple related products at once (multiple hierarchies).

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# Show a minimal Java Builder pattern example
Here is a minimal Java Builder pattern example, illustrating the core concept with compact code:

```java
// Product class
public class Person {
    private final String name;
    private final int age;

    // Private constructor used by the builder
    private Person(Builder builder) {
        this.name = builder.name;
        this.age = builder.age;
    }

    // Static inner builder class
    public static class Builder {
        private String name;
        private int age;

        public Builder setName(String name) {
            this.name = name;
            return this;
        }

        public Builder setAge(int age) {
            this.age = age;
            return this;
        }

        public Person build() {
            return new Person(this);
        }
    }

    // Getters for demonstration
    public String getName() { return name; }
    public int getAge() { return age; }
}

// Usage example
public class Main {
    public static void main(String[] args) {
        Person person = new Person.Builder()
            .setName("Alice")
            .setAge(25)
            .build();

        System.out.println(person.getName() + ", " + person.getAge()); // Alice, 25
    }
}
```

- This pattern enables fluent, readable creation of objects with optional or required parameters.

- The builder hides object construction logic and lets you specify only what you need.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# When to use Builder vs Factory in Java
Choose between Builder and Factory patterns in Java based on the complexity of object creation and flexibility needs:

### When to Use Builder
- You need to construct a complex object step by step.

- The object has many optional or mandatory parameters that may make constructors confusing or cumbersome (avoids telescoping constructors).

- You want to create immutable or partially constructed objects and provide a clear, fluent API for construction.

- Example: Building a Computer object with optional GPU, multiple configuration options.

### When to Use Factory
- You want to encapsulate object creation logic and hide the actual instantiated class from the client.

- Typically used when you need to create one of several related or interchangeable objects from the same family.

- Object creation is simpler and usually happens in a single method call.

- Example: Creating different types of Animal objects based on input (Dog, Cat).

### Summary of Differences

|Aspect	|Builder	|Factory|
|-----------|---------------|-------------|
|Purpose|Step-by-step construction of a complex object|Creation of objects from a set of related types|
|Complexity|Handles many parameters and complex construction sequences|Simple object creation, often single method call|
|Object Lifecycle|Can create immutable objects, allows gradual building|Creates fully constructed objects immediately|
|API Style|Fluent, chainable method calls|Single method call returns object|
|Usage Examples|Building a customizable House or Computer|Creating different Button or Animal subtypes|

**In practice, Builder is for complex objects needing flexible construction, Factory is for simpler polymorphic creations.**

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# How to implement immutable objects with Builder
To implement immutable objects using the Builder pattern in Java, the typical approach is:

1. Make the class's fields private and final.

2. Provide no setters (mutators) in the immutable class.

3. Make the constructor private and accept a Builder object to initialize fields.

4. Define a public static inner Builder class with setter-like methods to set fields for the building process.

5. The Builder class has a build() method that returns a new immutable instance.

```java
public final class Person {
    private final String name;
    private final int age;

    private Person(Builder builder) {
        this.name = builder.name;
        this.age = builder.age;
    }

    public String getName() { return name; }
    public int getAge() { return age; }

    public static class Builder {
        private String name;
        private int age;

        public Builder setName(String name) {
            this.name = name;
            return this;
        }
        public Builder setAge(int age) {
            this.age = age;
            return this;
        }

        public Person build() {
            // Optionally validate fields here
            return new Person(this);
        }
    }
}

Usage:-

Person person = new Person.Builder()
    .setName("Alice")
    .setAge(30)
    .build();

```
### Why this is immutable:
- The fields of Person are final and private.

- No setters to change them after construction.

- The only way to instantiate is through Builder, which constructs a fully initialized and immutable object.

- The object state cannot be changed after creation.​

This pattern gives both immutability and readable, flexible construction of complex objects with many optional parameters.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# How to implement thread-safe immutable builders for concurrency

To implement thread-safe immutable objects with the Builder pattern for concurrency in Java, the key points are:

1. **Immutable Object:**
Ensure the target object is immutable: all fields are private final, no setters, and any mutable input objects are defensively copied.

2. **Builder Not Shared Between Threads:**
The Builder instance itself is typically not thread-safe and should be used by a single thread only during construction. Each thread gets its own Builder instance.

3. **Safe Publication:**
Once built, the immutable object can be safely shared across threads without synchronization due to Java's final field guarantees and safe publication via the build() method.

4. **Defensive Copies for Mutables:**
If fields include mutable objects like Date, perform defensive copies in the constructor and accessors to preserve immutability and thread safety.

Minimal Example Illustrating Thread-safe Immutable Object with Builder

```java
public final class Person {
    private final String name;
    private final int age;
    private final Date birthDate;

    private Person(Builder builder) {
        this.name = builder.name;
        this.age = builder.age;
        this.birthDate = new Date(builder.birthDate.getTime()); // Defensive copy
    }

    public String getName() { return name; }
    public int getAge() { return age; }
    public Date getBirthDate() {
        return new Date(birthDate.getTime()); // Defensive copy
    }

    public static class Builder {
        private String name;
        private int age;
        private Date birthDate;

        public Builder setName(String name) {
            this.name = name;
            return this;
        }

        public Builder setAge(int age) {
            this.age = age;
            return this;
        }

        public Builder setBirthDate(Date birthDate) {
            this.birthDate = new Date(birthDate.getTime()); // Defensive copy
            return this;
        }

        public Person build() {
            // Optional: validate fields here
            return new Person(this);
        }
    }
}

```

- **Usage in multithreaded context:** Each thread creates and uses its own Builder instance to configure the object, then the resulting immutable Person can be safely shared without further synchronization.

### Summary
- The immutable object built by Builder is inherently thread-safe once constructed.

- The Builder class itself is not thread-safe, but this is fine since it should be used in a single thread during construction.

- Proper use of defensive copies ensures no external mutable state escapes.

- This pattern balances flexibility in complex object creation with safe concurrency.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# Provide a concrete Java example of a thread-safe builder producing immutable objects
Here is a concrete Java example demonstrating a thread-safe Builder pattern producing immutable objects:

```java
import java.util.Date;

public final class Person {
    private final String name;
    private final int age;
    private final Date birthDate;

    private Person(Builder builder) {
        this.name = builder.name;
        this.age = builder.age;
        // Defensive copy for mutable Date
        this.birthDate = builder.birthDate != null ? new Date(builder.birthDate.getTime()) : null;
    }

    public String getName() { return name; }
    public int getAge() { return age; }
    public Date getBirthDate() { 
        return birthDate != null ? new Date(birthDate.getTime()) : null; 
    }

    public static class Builder {
        private String name;
        private int age;
        private Date birthDate;

        public Builder setName(String name) {
            this.name = name;
            return this;
        }

        public Builder setAge(int age) {
            this.age = age;
            return this;
        }

        public Builder setBirthDate(Date birthDate) {
            // Defensive copy to prevent external mutation
            this.birthDate = birthDate != null ? new Date(birthDate.getTime()) : null;
            return this;
        }

        public Person build() {
            // Validations can be added here if needed
            return new Person(this);
        }
    }
}
```
### Key Points for Thread Safety and Immutability:
- The Person class is final with private final fields — immutable after construction.

- Defensive copies of mutable fields (Date) are used in both builder setters and getters.

- The Builder is not thread-safe, but it does not need to be because each thread should use its own builder instance.

- The immutable Person object returned from build() is inherently thread-safe and can be shared freely across threads without synchronization.



```java
Usage Example:

public class Main {
    public static void main(String[] args) {
        Person person = new Person.Builder()
            .setName("Alice")
            .setAge(30)
            .setBirthDate(new Date())
            .build();

        System.out.println(person.getName());       // Alice
        System.out.println(person.getAge());        // 30
        System.out.println(person.getBirthDate());  // current date
    }
}
```
This approach ensures you can safely build complex immutable objects that are safe to use in concurrent programs while maintaining a readable and maintainable construction API.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# Add validation and fluent error reporting to the thread-safe builder

To add validation and fluent error reporting to a thread-safe builder producing immutable objects in Java, you can perform all validations inside the build() method and then throw detailed exceptions for fluent error reporting.

```java
import java.util.ArrayList;
import java.util.Date;
import java.util.List;

public final class Person {
    private final String name;
    private final int age;
    private final Date birthDate;

    private Person(Builder builder) {
        this.name = builder.name;
        this.age = builder.age;
        this.birthDate = builder.birthDate != null ? new Date(builder.birthDate.getTime()) : null; // Defensive copy
    }

    public String getName() { return name; }
    public int getAge() { return age; }

    public Date getBirthDate() {
        return birthDate != null ? new Date(birthDate.getTime()) : null; // Defensive copy
    }

    public static class Builder {
        private String name;
        private Integer age; // Use Integer to detect unset
        private Date birthDate;

        public Builder setName(String name) {
            this.name = name;
            return this;
        }

        public Builder setAge(int age) {
            this.age = age;
            return this;
        }

        public Builder setBirthDate(Date birthDate) {
            this.birthDate = birthDate != null ? new Date(birthDate.getTime()) : null;
            return this;
        }

        public Person build() {
            List<String> errors = new ArrayList<>();

            if (name == null || name.trim().isEmpty()) {
                errors.add("Name must not be empty");
            }

            if (age == null || age < 0 || age > 150) {
                errors.add("Age must be between 0 and 150");
            }

            if (birthDate == null) {
                errors.add("BirthDate must not be null");
            }

            if (!errors.isEmpty()) {
                throw new IllegalStateException("Person build failed: " + String.join(", ", errors));
            }

            return new Person(this);
        }
    }
}

```
### How this adds fluent validation and error reporting:
- All validation is done in the build() method.

- Validation errors are collected into a list of error messages.

- If any validation fails, an informative exception is thrown with all errors.

- The builder methods return this to allow chaining.

- Client code receives detailed errors in one go.

```java
public class Main {
    public static void main(String[] args) {
        try {
            Person p = new Person.Builder()
                .setName("")
                .setAge(-5)
                .build();
        } catch (IllegalStateException e) {
            System.out.println(e.getMessage());
            // Output: Person build failed: Name must not be empty, Age must be between 0 and 150, BirthDate must not be null
        }
    }
}
```

### Summary:
- Performing validation in build() keeps builder methods simple.

- Collecting all validation failures before throwing gives users comprehensive feedback.

- This approach is thread-safe as builder instances are not shared.

- It produces immutable, validated objects with clear error reporting.

This pattern is a straightforward way to add robust, fluent validation to thread-safe builders for immutable objects.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# Provide a Java example using deep cloning for Prototype

Here is a concrete Java example illustrating deep cloning in the Prototype Design Pattern. This shows how to implement deep copy so that nested mutable objects are cloned properly:

```java
// Address class used as a nested object
class Address implements Cloneable {
    private String city;

    public Address(String city) {
        this.city = city;
    }

    // Copy constructor for deep cloning
    public Address(Address that) {
        this.city = that.city;
    }

    public String getCity() {
        return city;
    }

    public void setCity(String city) {
        this.city = city;
    }

    @Override
    public Address clone() {
        return new Address(this);
    }
}

// Person class implementing deep cloning via Prototype pattern
class Person implements Cloneable {
    private String name;
    private Address address;

    public Person(String name, Address address) {
        this.name = name;
        this.address = address;
    }

    // Copy constructor for deep cloning
    public Person(Person that) {
        this.name = that.name;
        this.address = that.address.clone(); // Deep clone of nested object
    }

    @Override
    public Person clone() {
        return new Person(this);
    }

    public String getName() {
        return name;
    }

    public Address getAddress() {
        return address;
    }

    public void setAddress(Address address) {
        this.address = address;
    }
}

// Usage example
public class PrototypeDeepCloneExample {
    public static void main(String[] args) {
        Address addr = new Address("New York");
        Person p1 = new Person("Alice", addr);

        // Clone p1 to p2 (deep copy)
        Person p2 = p1.clone();

        // Change p2's address city
        p2.getAddress().setCity("London");

        System.out.println("p1 address city: " + p1.getAddress().getCity()); // New York
        System.out.println("p2 address city: " + p2.getAddress().getCity()); // London
    }
}
```

### Explanation:
- Person and Address classes implement clone() using copy constructors to perform deep cloning.

- Person.clone() explicitly clones the nested Address object to ensure deep copy.

- This prevents changes in the clone's nested objects from affecting the original object's nested objects.

- This pattern is a common way to implement Prototype with deep cloning in Java.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# Show a thread-safe deep-clone implementation for Prototype
Here is a thread-safe deep-clone implementation using the Prototype pattern in Java, combining deep copying with immutability and thread safety by using copy constructors and ensuring no shared mutable state leaks:


```java
// Address class with deep cloning support
final class Address implements Cloneable {
    private final String city;

    public Address(String city) {
        this.city = city;
    }

    // Copy constructor for deep cloning
    public Address(Address that) {
        this.city = that.city;
    }

    public String getCity() {
        return city;
    }

    @Override
    public Address clone() {
        return new Address(this);
    }
}

// Immutable Person class supporting deep cloning
final class Person implements Cloneable {
    private final String name;
    private final Address address;

    public Person(String name, Address address) {
        this.name = name;
        // Defensive copy ensures immutability
        this.address = address.clone();
    }

    // Copy constructor for deep cloning
    public Person(Person that) {
        this.name = that.name;
        this.address = that.address.clone();
    }

    public String getName() {
        return name;
    }

    public Address getAddress() {
        return address;
    }

    @Override
    public Person clone() {
        // Deep clone including nested objects
        return new Person(this);
    }
}

// Usage example
public class ThreadSafeDeepClonePrototype {
    public static void main(String[] args) {
        Address address = new Address("New York");
        Person original = new Person("Alice", address);

        // Clone the original person (deep clone)
        Person clone = original.clone();

        System.out.println("Original address: " + original.getAddress().getCity()); // New York
        System.out.println("Clone address: " + clone.getAddress().getCity());       // New York

        // Note: Fields are immutable, no thread synchronization needed for shared usage
    }
}
```

### Why this is thread-safe:
- Both Person and Address are immutable (final fields, no setters).

- Cloning creates a brand new deep copy; no shared mutable state exists.

- Immutable objects can be safely shared between threads without synchronization.

- The clone() method is thread-safe because it does not modify existing instances; it returns new instances.

This pattern offers a thread-safe way to implement deep cloning with Prototype in Java.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**

# Show a Java example of a thread-safe deep-clone using Cloneable

Here is a thread-safe deep clone example in Java using the Cloneable interface, with attention to thread safety, immutability, and proper cloning practices.

```java
import java.util.HashMap;
import java.util.Map;

// Address class supports deep cloning
final class Address implements Cloneable {
    private final String city;

    public Address(String city) {
        this.city = city;
    }

    public Address(Address that) {
        this.city = that.city;
    }

    public String getCity() {
        return city;
    }

    @Override
    public Address clone() {
        return new Address(this);
    }
}

// Employee class supporting deep cloning
final class Employee implements Cloneable {
    private final String name;
    private final Address address;
    private final Map<String, String> props;

    public Employee(String name, Address address, Map<String, String> props) {
        this.name = name;
        this.address = address.clone();
        this.props = new HashMap<>(props); // Defensive copy for thread safety
    }

    // Copy constructor for deep cloning
    private Employee(Employee that) {
        this.name = that.name;
        this.address = that.address.clone();
        this.props = new HashMap<>(that.props);
    }

    public String getName() { return name; }
    public Address getAddress() { return address; }
    public Map<String, String> getProps() { return new HashMap<>(props); }
    
    @Override
    public Employee clone() {
        return new Employee(this);
    }
}

// Usage example
public class ThreadSafeDeepClonePrototype {
    public static void main(String[] args) {
        Map<String, String> props = new HashMap<>();
        props.put("salary", "75000");
        Employee e1 = new Employee("Alice", new Address("San Francisco"), props);
        Employee e2 = e1.clone();

        // Mutate clone's nested address
        Address clonedAddress = e2.getAddress();
        // Note: Address is immutable here, so alternative approaches are needed for nested mutability.
        // For demonstration, you can replace Address with a mutable class if needed.
        
        System.out.println("Original Employee: " + e1.getName() + " in " + e1.getAddress().getCity());
        System.out.println("Cloned Employee: " + e2.getName() + " in " + e2.getAddress().getCity());
    }
}

```
### Key Points:
- The class is immutable (final, fields private final) with no setters.

- The clone method performs deep copy by cloning nested objects and copying mutable collections.

- Defensive copies (new HashMap<>(props)) are used when assigning collections, ensuring thread safety when sharing instances.

- Cloning and object creation are thread-safe because no mutable state is shared between cloned instances and clone creation is synchronized through the clone process itself, which creates independent, immutable objects.

This pattern guarantees thread safety, immutability, and deep cloning in concurrent environments.

**[Back To Top](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/ques-ans-design-pattern.md/#table-of-contents)**