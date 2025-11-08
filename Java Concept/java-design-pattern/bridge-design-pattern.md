# Bridge Design Pattern
The Bridge Design Pattern is a structural design pattern that decouples an abstraction from its implementation, allowing both to be changed independently. This pattern helps avoid permanent binding between an abstraction and its implementation, improving extensibility and enabling changes in either without affecting the other.

### Core Components:

**Abstraction:** Defines the high-level control interface and maintains a reference to the Implementor.

**RefinedAbstraction:** Extends the Abstraction class.

**Implementor:** Defines the interface for implementation classes.

**ConcreteImplementor:** Implements the Implementor interface.

### Java Example: Vehicles and Workshops

```java
// Implementor interface
interface Workshop {
    void work();
}

// ConcreteImplementor 1
class Produce implements Workshop {
    public void work() {
        System.out.print("Produced");
    }
}

// ConcreteImplementor 2
class Assemble implements Workshop {
    public void work() {
        System.out.println(" and Assembled.");
    }
}

// Abstraction
abstract class Vehicle {
    protected Workshop workShop1;
    protected Workshop workShop2;

    protected Vehicle(Workshop w1, Workshop w2) {
        this.workShop1 = w1;
        this.workShop2 = w2;
    }
    abstract public void manufacture();
}

// RefinedAbstraction 1
class Car extends Vehicle {
    public Car(Workshop w1, Workshop w2) {
        super(w1, w2);
    }
    @Override
    public void manufacture() {
        System.out.print("Car ");
        workShop1.work();
        workShop2.work();
    }
}

// RefinedAbstraction 2
class Bike extends Vehicle {
    public Bike(Workshop w1, Workshop w2) {
        super(w1, w2);
    }
    @Override
    public void manufacture() {
        System.out.print("Bike ");
        workShop1.work();
        workShop2.work();
    }
}

// Client
public class BridgePattern {
    public static void main(String[] args) {
        Vehicle vehicle1 = new Car(new Produce(), new Assemble());
        vehicle1.manufacture();    // Output: Car Produced and Assembled.

        Vehicle vehicle2 = new Bike(new Produce(), new Assemble());
        vehicle2.manufacture();    // Output: Bike Produced and Assembled.
    }
}

```

### Benefits:
- Abstraction and implementation can vary independently.

- Easy to extend abstractions and implementations without modifying existing code.

- Improves code maintainability and scalability.

- Hides implementation details from clients.

### Use Cases:
- Cross-platform applications where abstraction varies independently of platform-specific details.

- GUI frameworks separating windows/controls from platform implementations.

- Device drivers separating device interface from hardware-specific operations.

This pattern clearly demonstrates composition over inheritance to achieve flexibility in software design.


**[Back To Creational Design Patterns](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/structural-design-pattern.md#structural-design-patterns)**