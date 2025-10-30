# Dependency Inversion Principle

The principle states that we must use abstraction (abstract classes and interfaces) instead of concrete implementations.

High-level modules should not depend on the low-level module, but both should depend on the abstraction. Because the abstraction does not depend on detail (concrete implementations), but the detail depends on the abstraction.

This principle make software components more flexible, reusable, and maintainable by reducing tight coupling between high-level logic and low-level implementations.

### Example demonstrating DIP:
Without DIP (high-level depends directly on low-level):

```java
class LightBulb {
    public void turnOn() {
        System.out.println("LightBulb on");
    }

    public void turnOff() {
        System.out.println("LightBulb off");
    }
}

class Switch {
    private LightBulb bulb;

    public Switch() {
        this.bulb = new LightBulb();  // Direct dependency on low-level class
    }

    public void operate() {
        bulb.turnOn();
    }
}
```
With DIP (both depend on abstraction):

```java
interface Switchable {
    void turnOn();
    void turnOff();
}

class LightBulb implements Switchable {
    public void turnOn() {
        System.out.println("LightBulb on");
    }
    public void turnOff() {
        System.out.println("LightBulb off");
    }
}

class Switch {
    private final Switchable device;

    public Switch(Switchable device) {
        this.device = device;  // Depend on abstraction
    }

    public void operate() {
        device.turnOn();
    }
}
```

### Why DIP matters:
* High-level Switch depends on abstraction Switchable instead of concrete LightBulb.

* Low-level LightBulb implements the abstraction.

* Changing or extending low-level details won’t affect high-level modules.

* Promotes loose coupling, easier testing (mock abstractions), and flexible designs.

DIP encourages designing via interfaces or abstract classes, making systems more maintainable and extensible.​

## Compare Dependency Inversion vs Dependency Injection with examples
Dependency Inversion Principle (DIP) and Dependency Injection (DI) are related but distinct concepts in software design:

### Dependency Inversion Principle (DIP)
* A design principle from SOLID guidelines.

* States that high-level modules should not depend on low-level modules; both should depend on abstractions (e.g., interfaces).

* Also, abstractions should not depend on details; details should depend on abstractions.

* Focuses on decoupling the system by relying on abstractions rather than concrete implementations.

* Guides the structure and architecture of code for flexibility and maintainability.

### Dependency Injection (DI)
* A design pattern / technique used to implement DIP.

* Involves injecting dependencies from outside a class instead of the class creating them internally.

* Common methods: constructor injection, setter (property) injection, or method injection.

* Enables loose coupling by allowing objects to receive their dependencies rather than creating them.

* Often facilitated by DI frameworks or containers (e.g., Spring, Dagger).

### Comparison Example

Without DIP and DI (tight coupling):-

```java
class LightBulb {
    void turnOn() { System.out.println("LightBulb on"); }
}

class Switch {
    private LightBulb bulb = new LightBulb();  // creates dependency directly

    void operate() { bulb.turnOn(); }
}
```

With DIP and DI:-

```java
interface Switchable {
    void turnOn();
}

class LightBulb implements Switchable {
    public void turnOn() { System.out.println("LightBulb on"); }
}

class Switch {
    private Switchable device;

    // Dependency Injection via constructor
    public Switch(Switchable device) { this.device = device; }

    void operate() { device.turnOn(); }
}

// Usage
Switchable bulb = new LightBulb();
Switch mySwitch = new Switch(bulb);  // Inject dependency here
mySwitch.operate();
```

In brief, DIP is the "what" (principle), and DI is the "how" (pattern to achieve it).