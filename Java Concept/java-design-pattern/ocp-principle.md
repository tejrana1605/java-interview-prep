# Open-Closed Principle
The open-closed principle states that, according to new requirements, the software entity(module,class,method) should be open for extension but closed for modification. 

The extension allows us to implement new functionality in the module.

**"OCP states Software entities (such as classes, modules, and functions) should be open for extension but closed for modification."**

This means your code should be designed so that its behavior can be extended to support new functionality without changing the existing code that is already tested and working.

This reduces risk of introducing bugs and makes your system more maintainable and scalable.

### Explanation:
**Open for extension:** You should be able to add new features or behaviors by adding new code (e.g., subclassing, implementing interfaces) rather than changing existing code.

**Closed for modification:** Once a class or module is implemented and tested, it should not be modified to avoid affecting existing functionality.


**Example in Java:**

Suppose you have a calculator class that can perform addition only.

```java
class Calculator {
    public int add(int a, int b) {
        return a + b;
    }
}
```

If later you want to add multiplication, violating OCP, you might modify the class like this:

```java
class Calculator {
    public int add(int a, int b) {
        return a + b;
    }

    public int multiply(int a, int b) {  // Adding method modifies class
        return a * b;
    }
}
```

### Better approach (OCP-compliant):

Define a common interface and extend it:

```java
interface Operation {
    int perform(int a, int b);
}

class Addition implements Operation {
    public int perform(int a, int b) {
        return a + b;
    }
}

class Multiplication implements Operation {
    public int perform(int a, int b) {
        return a * b;
    }
}

class Calculator {
    public int calculate(Operation operation, int a, int b) {
        return operation.perform(a, b);
    }
}

```

Now, to add new operations, implement the Operation interface in new classes without modifying existing code.

### Benefits:
* Safer to add new features

* Existing code stays stable

* Code is easier to maintain and test

In summary, OCP encourages designing with abstraction and polymorphism so software can grow flexibly without risking existing behavior.

## 1. Show a Java example demonstrating OCP with strategy pattern

Here is a Java example demonstrating the Open-Closed Principle (OCP) using the Strategy Pattern:

```java
// Strategy interface
interface PaymentStrategy {
    void pay(int amount);
}

// Concrete strategy for Credit Card payment
class CreditCardPayment implements PaymentStrategy {
    private String cardNumber;

    public CreditCardPayment(String cardNumber) {
        this.cardNumber = cardNumber;
    }

    public void pay(int amount) {
        System.out.println(amount + " paid with credit card: " + cardNumber);
    }
}

// Concrete strategy for PayPal payment
class PaypalPayment implements PaymentStrategy {
    private String email;

    public PaypalPayment(String email) {
        this.email = email;
    }

    public void pay(int amount) {
        System.out.println(amount + " paid using PayPal account: " + email);
    }
}

// Context class using PaymentStrategy
class ShoppingCart {
    private PaymentStrategy paymentStrategy;

    public ShoppingCart(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }

    public void setPaymentStrategy(PaymentStrategy paymentStrategy) {
        this.paymentStrategy = paymentStrategy;
    }

    public void checkout(int amount) {
        paymentStrategy.pay(amount);
    }
}

// Usage
public class StrategyPatternExample {
    public static void main(String[] args) {
        ShoppingCart cart = new ShoppingCart(new CreditCardPayment("1234-5678-9876-5432"));
        cart.checkout(500); // Pay with credit card

        // Switch to PayPal without modifying ShoppingCart
        cart.setPaymentStrategy(new PaypalPayment("email@example.com"));
        cart.checkout(300); // Pay with PayPal
    }
}

```

### How it demonstrates OCP:
* The ShoppingCart class is closed for modification; you don't modify it when adding new payment methods.

* It is open for extension by adding new PaymentStrategy implementations like CreditCardPayment, PaypalPayment, or others without changing existing code.

* You can switch payment strategies dynamically without modifying ShoppingCart.

This pattern ensures your system is extendable without risking breaking existing functionality by modifying tested code.

## 2. Explain common OCP violations and how to fix them
Common Open-Closed Principle (OCP) violations occur when code is repeatedly modified to add new behavior instead of being extended through abstraction. These violations increase risk of bugs, reduce maintainability, and violate good design practices. Here are typical examples and how to fix them:

### Common OCP Violations
1. **Using large conditional statements to handle variations**

* Code has many if-else or switch branches checking for types or conditions to execute different behaviors.

* Example: A payment processor with if (type == "CreditCard") {...} else if (type == "PayPal") {...}, adding more conditions for new payment types over time.

* This violates OCP because you must change and re-test the class whenever you add new behaviors.

2. **Modifying existing classes to add features**

* Changing core classes to add new methods or modify existing ones whenever requirements change.

* Example: A Calculator class that is modified to add a new operation instead of extending it with new classes.

3. **Hard-coded dependencies and behavior**

* Classes tightly coupled to specific implementations prevent easy substitution or extension.

* Example: Directly instantiating concrete classes inside methods instead of depending on abstractions (interfaces).

### How to Fix/OCP-Compliant Approaches
1. **Use polymorphism and interfaces**

* Define common abstractions (e.g., interfaces or abstract classes) for varying behavior.

* Implement new functionality by creating new subclasses that extend or implement these abstractions.

* Example: Strategy Pattern for different algorithms or payment methods.

2. Apply design patterns that encourage extension

* Strategy, Decorator, Template Method, and Command patterns help achieve OCP by separating varying code from stable code.

* Example: Use Strategy pattern to encapsulate behaviors and switch them dynamically.

3. **Depend on abstractions, not concrete implementations**

* Leverage Dependency Injection (DI) to inject dependencies, making classes flexible and easy to extend.

* Example: Constructor or setter injection of interfaces rather than direct construction.

4. **Favor composition over inheritance where appropriate**

* Compose objects with extended behaviors rather than modify existing inheritance hierarchies.

* Example: Decorator pattern to add responsibilities dynamically.

### Summary Table

|Violation	|Description	|Fix Approach|