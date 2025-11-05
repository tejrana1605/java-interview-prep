# Liskov Substitution Principle
Barbara Liskov introduced the Liskov Substitution Principle (LSP). It applies to inheritance in such a way that the **derived classes must be completely substitutable for their base classes**.

The Liskov Substitution Principle (LSP) states that objects of a superclass should be replaceable by objects of its subclasses without affecting the correctness of the program.

In other words, if B is a subtype of A, then objects of type A can be replaced with objects of type B without altering the desirable properties of the program such as correctness and expected behavior.

### Explanation:
1. Subclasses should fulfill the contract of the base class.

2. They must not strengthen preconditions or weaken postconditions.

3. They should not throw new unexpected exceptions.

4. Method return types should be compatible (covariant).

### Example of LSP Violation and Fix

Consider a base class Rectangle and a subclass Square:

```java
class Rectangle {
    protected int width;
    protected int height;

    public void setWidth(int width) { this.width = width; }
    public void setHeight(int height) { this.height = height; }
    public int getArea() { return width * height; }
}

class Square extends Rectangle {
    @Override
    public void setWidth(int width) {
        this.width = width;
        this.height = width;  // Enforces square property
    }

    @Override
    public void setHeight(int height) {
        this.height = height;
        this.width = height;  // Enforces square property
    }
}

```

Here, substituting a Square instance wherever a Rectangle is expected can cause unexpected results because Square changes the behavior of setters, violating LSP.

### Fix by avoiding incorrect substitution
Use composition or redesign hierarchy so the subclass does not violate base class assumptions:

```java
interface Shape {
    int getArea();
}

class Rectangle implements Shape {
    private int width;
    private int height;
    // getters/setters
    public int getArea() { return width * height; }
}

class Square implements Shape {
    private int side;
    // getter/setter
    public int getArea() { return side * side; }
}
```

Now, Rectangle and Square implement a common interface, but are not forced into a problematic inheritance relationship, respecting LSP.

### Summary:
LSP ensures subclass objects can replace superclass objects without altering program behavior, enforcing substitutability and robust inheritance hierarchies.

## 1. Show a minimal Java example that obeys LSP for contrast
A minimal Java example that obeys the Liskov Substitution Principle (LSP) avoids inheriting incompatible behavior. Instead, it uses a common interface or abstract class while each subclass respects the base contract.

```java
Example:

// Base interface
interface Shape {
    int getArea();
}

// Rectangle implementation
class Rectangle implements Shape {
    protected int width;
    protected int height;

    public Rectangle(int width, int height) {
        this.width = width;
        this.height = height;
    }

    @Override
    public int getArea() {
        return width * height;
    }
}

// Square implementation without inheriting Rectangle
class Square implements Shape {
    private int side;

    public Square(int side) {
        this.side = side;
    }

    @Override
    public int getArea() {
        return side * side;
    }
}

// Usage demonstrates substitutability
public class LSPExample {
    public static void main(String[] args) {
        Shape rect = new Rectangle(4, 5);
        Shape square = new Square(7);

        System.out.println("Rectangle area: " + rect.getArea()); // 20
        System.out.println("Square area: " + square.getArea());   // 49
    }
}
```

### Why it obeys LSP:
1. Both Rectangle and Square implement the Shape interface.

2. Neither changes the contract in an unexpected way.

3. You can substitute any Shape implementation without breaking program correctness.

This design avoids the pitfalls of subclassing Square from Rectangle and respects substitutability governed by LSP.

## 2. Explain why the example violates LSP step by step

The example violating the Liskov Substitution Principle (LSP) does so step by step because it breaks the expected behavior of the base class's contract. Here's the detailed explanation:

### Step 1: Base Class Contract
1. The base class Rectangle defines methods setWidth(int) and setHeight(int) that allow changing width and height independently.

2. Clients of Rectangle expect that setting width or height separately will affect only that dimension.

### Step 2: Subclass Behavior Changes Contract
1. The subclass Square inherits from Rectangle but overrides setWidth and setHeight such that setting one dimension forces the other to the same value.

2. This means Square cannot treat width and height independently like Rectangle does.

### Step 3: Substituting Subclass for Base Class Breaks Client Expectations
1. When client code uses Rectangle rect = new Square(); it assumes independent height and width can be set.

2. Setting rect.setWidth(5) then rect.setHeight(10) expects area = 50.

3. Instead, due to Square enforcement, width and height both become 10, area becomes 100 unexpectedly.

### Step 4: Violation of LSP’s Contract for Substitutability
1. Because of changed method behavior, the Square subclass is not substitutable for Rectangle.

2. The subclass strengthens invariants (width = height) and alters method effects, violating the base class contract.

3. Client code relying on Rectangle loses correctness and predictability.

### Summary:
This breaks LSP because:

1. Subclass changes behavior expected by superclass clients.

2. Subclass narrows valid input conditions or alters outputs unexpectedly.

3. Client code depending on superclass cannot seamlessly use subclass without errors or surprises.

Hence, the design contracts are broken and substitutability is lost, violating the Liskov Substitution Principle.

**[Back To SOLID Principle](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/solid-principle.md#solid-principle)**