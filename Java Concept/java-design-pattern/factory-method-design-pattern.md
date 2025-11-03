# Factory Method Design Pattern
The Factory Method design pattern is a creational pattern that provides an interface for creating objects but allows subclasses to decide which class to instantiate. It encapsulates object creation, promoting loose coupling and flexibility.

### Key Concept:
Instead of directly calling constructors using new, subclasses override a factoryMethod() to instantiate specific objects, enabling the main code to work with abstractions rather than concrete classes.

### Example in Java:
Suppose you are developing a system that handles different types of documents (e.g., PDF, Word). With the Factory Method, you define an interface or abstract class for documents and create subclasses for each specific type.

1. Abstract Product Interface

```java
public interface Document {
    void open();
}
```

2. Concrete Products

```java
public class PDFDocument implements Document {
    @Override
    public void open() {
        System.out.println("Opening PDF Document");
    }
}

public class WordDocument implements Document {
    @Override
    public void open() {
        System.out.println("Opening Word Document");
    }
}
```

3. Creator Abstract Class

```java
public abstract class DocumentCreator {
    // Factory method
    public abstract Document createDocument();

    // Business logic
    public void openDocument() {
        Document doc = createDocument();
        doc.open();
    }
}
```

4. Concrete Creators
```java
public class PDFCreator extends DocumentCreator {
    @Override
    public Document createDocument() {
        return new PDFDocument();
    }
}

public class WordCreator extends DocumentCreator {
    @Override
    public Document createDocument() {
        return new WordDocument();
    }
}
```

5. Client Code
```java
public class Main {
    public static void main(String[] args) {
        DocumentCreator creator = new PDFCreator();
        creator.openDocument();  // Output: Opening PDF Document

        creator = new WordCreator();
        creator.openDocument();  // Output: Opening Word Document
    }
}
```

### Summary:
1. The factory method pattern defers instantiation to subclasses.

2. Promotes open/closed principle: easy to extend new classes without changing existing code.

3. Ensures code works against interface or abstract class, not specific implementations.

This pattern is widely used in frameworks and libraries, for example, in Java's java.util package where methods like Calendar.getInstance() use factory methods.

## Factory Design Pattern Components

1. Product

It is a concept, an interface, or an abstract class that describes a framework to create the objects by the factory method.

```java
public interface Product {  
    void use();  
}
```

2. ConcreteProduct

These are the classes that are an instance of the Product interface. Every concrete product refers to a certain type of product.

```java
public class ConcreteProductA implements Product {  
    @Override  
    public void use() {  
        System.out.println("Using Product A");  
    }  
}  
public class ConcreteProductB implements Product {  
    @Override  
    public void use() {  
        System.out.println("Using Product B");  
    }  
}
```

3. Creator

It is a class that only defines the factory method, which returns an object of type Product; it can be an abstract class or an interface. The Creator class may also define some default implementation of the factory method as well.

```java
public abstract class Creator {  
    public abstract Product factoryMethod();  
    public void someOperation() {  
        Product product = factoryMethod();  
        product.use();  
    }  
}  
```

4. ConcreteCreator

Each of these classes extends the factoryMethod() to return ConcreteProduct. They contain the knowledge of how to assemble certain products.

```java
public class ConcreteCreatorA extends Creator {  
    @Override  
    public Product factoryMethod() {  
        return new ConcreteProductA();  
    }  
}  
public class ConcreteCreatorB extends Creator {  
    @Override  
    public Product factoryMethod() {  
        return new ConcreteProductB();  
    }  
}     
```

## When to Use the Factory Method Design Pattern?

It is best to use the Factory Method Design pattern when the method of creating a product must be abstracted away from the client.

**When the exact type of object is not known until runtime:** If the client does not know until runtime of a particular application the particular class of object, to use the factory pattern.

**When the creation process involves complex logic:** If object creation requires logic and setting up that is better done in a factory, then a factory can be used.

**To promote loose coupling:** If you wish that the client should not depend upon certain classes that it has to use directly, then using the Factory pattern would be ideal.

## Without the Factory Method Design Pattern
It must, however, be noted that the Factory Method Design Pattern is not easily implemented without much difficulty.

It would be interesting to look at an application that generates various types of vehicles, for example a Car, Bike, and Truck. Without the Factory Method Pattern, the client would instantiate these classes directly:

```java
Car car = new Car();  
Bike bike = new Bike();  
Truck truck = new Truck();     
```

Such an approach may result in issues such as tight coupling, duplication of code, and even difficulties when one has to alter the code.

## Problems with the Above Design?
**Tight Coupling:** It can be seen that the client is coupled very closely to the specific vehicle classes, implying that modification or even adding something to the vehicle types is not easily possible.

**Code Duplication:** Whenever there is a new vehicle type, it is required to alter the code of the client which makes this module unsuitable for actual practice.

**Reduced Maintainability:** Any variations in the classes of vehicles would imply similar modifications with the client code.

## How To Avoid the Above Problem?
The vast quantity of aggressive information can provoke emotional stress in people, so it's necessary to avoid contacting such information, to turn off the device, to start a conversation with friends or maybe just to leave home for a while.

These problems are solved in the Factory Method Design Pattern where the creation of an object is placed in a factory. The client communicates with the factory, instead of creating the objects directly, which makes the code more cohesive and easier to change.

## Implementing the Factory Pattern
Here's how you can implement the Factory Method Design Pattern for a vehicle creation system:

1. Describe Vehicle Interface (Product)

```java
public interface Vehicle {  
    void drive();  
}  
```

2. Implement the Vehicle Interface in Concrete Classes (ConcreteProduct)

```java
public class Car implements Vehicle {  
    @Override  
    public void drive() {  
        System.out.println("Driving a Car");  
    }  
}  
public class Bike implements Vehicle {  
    @Override  
    public void drive() {  
        System.out.println("Riding a Bike");  
    }  
}  
public class Truck implements Vehicle {  
    @Override  
    public void drive() {  
        System.out.println("Driving a Truck");  
    }  
}     
```

3. Design the VehicleFactory Abstract Class (Creator)

```java
public abstract class VehicleFactory {  
    public abstract Vehicle createVehicle();  
  
    public void driveVehicle() {  
        Vehicle vehicle = createVehicle();  
        vehicle.drive();  
    }  
}   
```

4. Concept of Factory Method (ConcreteCreator)

```java
public class CarFactory extends VehicleFactory {  
    @Override  
    public Vehicle createVehicle() {  
        return new Car();  
    }  
}  
public class BikeFactory extends VehicleFactory {  
    @Override  
    public Vehicle createVehicle() {  
        return new Bike();  
    }  
}  
public class TruckFactory extends VehicleFactory {  
    @Override  
    public Vehicle createVehicle() {  
        return new Truck();  
    }  
}    
```

5. Include the Factory in the Client Code

```java
public class VehicleService {  
    public static void main(String[] args) {  
        VehicleFactory carFactory = new CarFactory();  
        carFactory.driveVehicle(); // Output: Driving a Car  
        VehicleFactory bikeFactory = new BikeFactory();  
        bikeFactory.driveVehicle(); // Output: Riding a Bike  
        VehicleFactory truckFactory = new TruckFactory();  
        truckFactory.driveVehicle(); // Output: Driving a Truck  
    }  
}     
```

## Real-Time Example-Factory Design Pattern

**Vehicle Production Systems:** Using the factories that enclose the creation logic, One can produce different types of vessels, such as but not limited to Cars, Bikes, Trucks, etc.

**Operating Systems:** Windows, macOS, & Linux make up our different operating systems and might need different factories for OS-dependent GUIs.

**Payment Processing Systems:** Several instances of objects that use CreditCardProcessingFactory, PayPalProcessingFactory, and BitcoinProcessingFactory classes can be created to handle credit card, PayPal, and Bitcoin kinds of payments, respectively.

## Advantages
**Promotes Loose Coupling:** The client code is not tightly coupled with the actual classes required with the system hence making it more flexible.

**Enhances Flexibility:** New products can be easily included in the productive process without additional coding from the client.

**Encapsulates Object Creation:** This also implies that a lot of extra code is removed from the client because the logic for creating complicated objects is included in the factory class.

## Disadvantages
**Increased Complexity:** The pattern also defines new classes and interfaces and may cause increased design complexity.

**Subclassing:** In order to support each new product type, it is necessary to create new subclasses that result in an extensive amount of classes.

**Potential for Over-Engineering:** In less complex applications it is advisable to avoid the Factory Method Design Pattern because is more cumbersome than necessary. This pattern will be most helpful when it is important to plan for the future and to anticipate that structure may well change, but when used in small projects, the overhead can be overkill.

## Conclusion
The Factory Method Design Pattern is one of the most solid solutions that can be applied to the object creation process in order to achieve the objectives of flexibility, maintainability, and scalability.