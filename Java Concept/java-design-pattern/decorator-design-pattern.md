# Decorator Design Pattern
The Decorator Design Pattern is a structural pattern that allows behavior to be added to individual objects, either statically or dynamically, without affecting the behavior of other objects from the same class. It provides a flexible alternative to subclassing for extending functionality.

**OR**
the Decorator Design Pattern is one of the most flexible and useful structural design patterns in Java, especially when you want to **add new behavior dynamically** to an object — without modifying its existing class.

“Attach additional responsibilities to an object dynamically. Decorators provide a flexible alternative to subclassing for extending functionality.”

### In simple terms

Decorator pattern lets you wrap an object with another object that adds extra behavior, without changing the original class.

### Core Components:

**Component Interface:** Declares the interface for objects that can have responsibilities added to them dynamically.

**Concrete Component:** Defines an object to which additional responsibilities can be attached.

**Decorator:** Maintains a reference to a Component object and defines an interface that conforms to Component's interface.

**Concrete Decorators:** Add responsibilities to the component.

### Java Example: Pizza Toppings

```java
// Component interface
public interface Pizza {
    String getDescription();
    double cost();
}

// Concrete Component
public class PlainPizza implements Pizza {
    @Override
    public String getDescription() {
        return "Plain pizza";
    }

    @Override
    public double cost() {
        return 8.0; // base price
    }
}

// Abstract Decorator implementing Pizza interface
public abstract class PizzaDecorator implements Pizza {
    protected Pizza decoratedPizza;

    public PizzaDecorator(Pizza pizza) {
        this.decoratedPizza = pizza;
    }

    @Override
    public String getDescription() {
        return decoratedPizza.getDescription();
    }

    @Override
    public double cost() {
        return decoratedPizza.cost();
    }
}

// Concrete Decorator: Cheese
public class CheeseDecorator extends PizzaDecorator {
    public CheeseDecorator(Pizza pizza) {
        super(pizza);
    }

    @Override
    public String getDescription() {
        return decoratedPizza.getDescription() + ", cheese";
    }

    @Override
    public double cost() {
        return decoratedPizza.cost() + 1.5;
    }
}

// Concrete Decorator: Pepperoni
public class PepperoniDecorator extends PizzaDecorator {
    public PepperoniDecorator(Pizza pizza) {
        super(pizza);
    }

    @Override
    public String getDescription() {
        return decoratedPizza.getDescription() + ", pepperoni";
    }

    @Override
    public double cost() {
        return decoratedPizza.cost() + 2.0;
    }
}

// Client
public class PizzaShop {
    public static void main(String[] args) {
        Pizza pizza = new PlainPizza();
        System.out.println(pizza.getDescription() + " cost: $" + pizza.cost());

        pizza = new CheeseDecorator(pizza);
        System.out.println(pizza.getDescription() + " cost: $" + pizza.cost());

        pizza = new PepperoniDecorator(pizza);
        System.out.println(pizza.getDescription() + " cost: $" + pizza.cost());
    }
}

Output:

Plain pizza cost: $8.0
Plain pizza, cheese cost: $9.5
Plain pizza, cheese, pepperoni cost: $11.5

```

### Benefits:

- Adds functionality to objects dynamically without subclassing.

- Reduces subclass explosion from combining features.

- Enhances flexibility in extending functionality.

- Keeps core objects simple and focused.

### Real-world Use Cases:

- Java I/O streams where decorators add buffering, compression, encryption (e.g., BufferedInputStream, DataInputStream).

- GUI frameworks where scrollbars, borders, or shadows are added as decorators to window components.

- Implementing features like logging, caching, or access control dynamically.


**[Back To Creational Design Patterns](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/structural-design-pattern.md#structural-design-patterns)**