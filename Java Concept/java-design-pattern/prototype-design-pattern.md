# Prototype Design Pattern
The Prototype Design Pattern is a creational pattern that allows creating new objects by copying (cloning) existing objects (prototypes) instead of creating new instances from scratch. This is especially useful when object creation is expensive or complex, enabling a more efficient way to create objects by duplicating a prototype.

### Key Concepts
- Prototype interface defines a method for cloning itself.

- Concrete prototypes implement the cloning method to duplicate themselves.

- Client requests new objects by cloning prototypes rather than using constructors.

### Simple Java Example

```java
// Prototype interface
interface Shape {
    Shape clone(); // Method to clone itself
    void draw();
}

// Concrete Prototype
class Circle implements Shape {
    private String color;

    public Circle(String color) {
        this.color = color;
    }

    @Override
    public Shape clone() {
        return new Circle(this.color); // Cloning logic
    }

    @Override
    public void draw() {
        System.out.println("Drawing a " + color + " circle.");
    }
}

// Client that uses prototype
class ShapeClient {
    private Shape prototype;

    public ShapeClient(Shape prototype) {
        this.prototype = prototype;
    }

    public Shape createShape() {
        return prototype.clone(); // New instance by cloning
    }
}

// Usage
public class PrototypeExample {
    public static void main(String[] args) {
        Shape circlePrototype = new Circle("red");

        ShapeClient client = new ShapeClient(circlePrototype);
        Shape redCircle = client.createShape();
        redCircle.draw();  // Output: Drawing a red circle.
    }
}


Usage:

// Prototype interface
interface Shape {
    Shape clone(); // Method to clone itself
    void draw();
}

// Concrete Prototype
class Circle implements Shape {
    private String color;

    public Circle(String color) {
        this.color = color;
    }

    @Override
    public Shape clone() {
        return new Circle(this.color); // Cloning logic
    }

    @Override
    public void draw() {
        System.out.println("Drawing a " + color + " circle.");
    }
}

// Client that uses prototype
class ShapeClient {
    private Shape prototype;

    public ShapeClient(Shape prototype) {
        this.prototype = prototype;
    }

    public Shape createShape() {
        return prototype.clone(); // New instance by cloning
    }
}

// Usage
public class PrototypeExample {
    public static void main(String[] args) {
        Shape circlePrototype = new Circle("red");

        ShapeClient client = new ShapeClient(circlePrototype);
        Shape redCircle = client.createShape();
        redCircle.draw();  // Output: Drawing a red circle.
    }
}


```
### When to Use Prototype Pattern
- When creating new instances is costly (e.g., loading data), cloning an existing initialized object is more efficient.

- When you need to keep the complexity of creating objects out of the client code.

- When the system needs to dynamically add or remove objects at runtime.

### Summary:
The Prototype pattern enables cloning of existing objects to create new ones, avoiding expensive or complex initialization processes, while keeping the system flexible and decoupled from concrete classes.
