# Interface Segregation Principle

The principle states that the larger interfaces are split into smaller ones. Because the implementation classes use only the methods that are required, we should not force the client to use the techniques (or methods) that they do not want to use.

### Why ISP matters
1. Improves maintainability and modularity.

2. Reduces the risk of changes propagating through unrelated parts of a codebase.

3. Makes interfaces easier to understand and implement.

### Example: ISP Violation
Suppose you define a large interface:

```java
interface Worker {
    void work();
    void eat();
}
```

If you now have a RobotWorker class, it does not need to implement eat(), but must do so because it is required by the interface.

```java
class RobotWorker implements Worker {
    public void work() { /* do work */ }
    public void eat() { /* does not eat! maybe empty or throw */ }
}
```

This is a violation of ISP as RobotWorker is forced to implement methods it does not need.

### Example: ISP-Compliant Solution
Split the interface into smaller, role-based interfaces:

```java
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

class HumanWorker implements Workable, Eatable {
    public void work() { /* do work */ }
    public void eat() { /* eat food */ }
}

class RobotWorker implements Workable {
    public void work() { /* do work */ }
}
```

Now, RobotWorker only implements what it needs, while HumanWorker can implement both roles. Classes are not forced to depend on unused methods.

### Summary Table

| Approach        | Problem      |  Solution (ISP)      |
| ------------- |-------------|--------------|
| Large interface |Unused methods for some clients|Split into small interfaces|
| Forced empty or error code |Coupling and fragile implementations|Precise, relevant contracts|

This modular approach makes interfaces cleaner, more reusable, and easier to test. Each class only needs to fulfill the contract of the functionality it actually provides.

## 1. Show a short Java example that violates ISP and why it fails
Here is a short Java example that violates the Interface Segregation Principle (ISP) and why it fails:

```java
// Fat interface with unrelated methods
interface Worker {
    void work();
    void eat();
}

// Developer needs both methods
class Developer implements Worker {
    public void work() {
        System.out.println("Developer is coding.");
    }
    public void eat() {
        System.out.println("Developer is eating.");
    }
}

// Robot only needs to work but forced to implement eat()
class Robot implements Worker {
    public void work() {
        System.out.println("Robot is working.");
    }
    public void eat() {
        throw new UnsupportedOperationException("Robot does not eat.");
    }
}
```

### Why it fails ISP:
* Robot is forced to depend on eat() method it does not need.

* eat() throwing UnsupportedOperationException violates the interface contract and surprises clients.

* The single fat interface forces clients to implement irrelevant methods leading to fragile, hard-to-maintain code.

* This violates ISP because clients should not be forced to depend on methods they do not use.

By forcing all clients to implement Worker with work() and eat(), this design couples unrelated behaviors and breaks ISP.

A better design would split Worker into Workable and Eatable interfaces that clients implement as needed.

## 2. Refactor the example into smaller role interfaces

Here is a refactored version of the previous example using smaller, role-specific interfaces following the Interface Segregation Principle (ISP):

```java
// Smaller, role-based interfaces
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

// Human implements both Workable and Eatable
class HumanWorker implements Workable, Eatable {
    public void work() {
        System.out.println("Human is working.");
    }
    public void eat() {
        System.out.println("Human is eating.");
    }
}

// Robot only implements Workable
class RobotWorker implements Workable {
    public void work() {
        System.out.println("Robot is working.");
    }
}
```
### Why this follows ISP
* Each interface has a focused responsibility.

* Classes implement only the interfaces (and thus methods) they need.

* RobotWorker is not forced to implement eat() it does not require.

* This reduces unnecessary coupling and makes code easier to maintain and extend.

This refactoring splits the large interface into focused smaller interfaces. Clients (classes) only implement the methods relevant to their needs, avoiding unnecessary or unsupported methods, thus adhering to the Interface Segregation Principle.

## 3. Show a composition-based variant of the refactor
Here is a composition-based variant of the Interface Segregation Principle refactor example in Java:

```java
// Role-based interfaces
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

// WorkBehavior encapsulates work functionality
class WorkBehavior implements Workable {
    public void work() {
        System.out.println("Working...");
    }
}

// EatBehavior encapsulates eating functionality
class EatBehavior implements Eatable {
    public void eat() {
        System.out.println("Eating...");
    }
}

// HumanWorker composed of WorkBehavior and EatBehavior
class HumanWorker {
    private Workable workBehavior;
    private Eatable eatBehavior;

    public HumanWorker() {
        this.workBehavior = new WorkBehavior();
        this.eatBehavior = new EatBehavior();
    }

    public void work() { workBehavior.work(); }
    public void eat() { eatBehavior.eat(); }
}

// RobotWorker composed of WorkBehavior only
class RobotWorker {
    private Workable workBehavior;

    public RobotWorker() {
        this.workBehavior = new WorkBehavior();
    }

    public void work() { workBehavior.work(); }
}
```
### Benefits of composition here:
* Behavior implementations are separated out into dedicated classes.

* Clients like HumanWorker and RobotWorker compose desired behaviors instead of inheriting them.

* Change or extend behavior by swapping composed objects rather than altering inheritance hierarchy.

* Encourages flexible, reusable code and stronger adherence to ISP principles.

This is a clear example of preferring composition over inheritance to achieve interface segregation and clean design.

## 4. Show code examples for dependency injection of role components

Here is an example showing dependency injection of role components in Java using constructor injection:

```java
// Role interfaces
interface Workable {
    void work();
}

interface Eatable {
    void eat();
}

// Concrete implementations of roles
class WorkBehavior implements Workable {
    @Override
    public void work() {
        System.out.println("Working...");
    }
}

class EatBehavior implements Eatable {
    @Override
    public void eat() {
        System.out.println("Eating...");
    }
}

// Worker class that receives role components via dependency injection
class HumanWorker {
    private final Workable workBehavior;
    private final Eatable eatBehavior;

    // Constructor injection of dependencies
    public HumanWorker(Workable workBehavior, Eatable eatBehavior) {
        this.workBehavior = workBehavior;
        this.eatBehavior = eatBehavior;
    }

    public void work() {
        workBehavior.work();
    }

    public void eat() {
        eatBehavior.eat();
    }
}

// Robot only requires work behavior
class RobotWorker {
    private final Workable workBehavior;

    public RobotWorker(Workable workBehavior) {
        this.workBehavior = workBehavior;
    }

    public void work() {
        workBehavior.work();
    }
}

// Example usage
public class Main {
    public static void main(String[] args) {
        Workable work = new WorkBehavior();
        Eatable eat = new EatBehavior();

        HumanWorker human = new HumanWorker(work, eat);
        human.work();   // Output: Working...
        human.eat();    // Output: Eating...

        RobotWorker robot = new RobotWorker(work);
        robot.work();   // Output: Working...
        // robot has no eat behavior and does not need to implement it
    }
}
```
### Explanation
* HumanWorker and RobotWorker receive behaviors via constructor injection.

* Dependencies are passed as abstractions (interfaces for role behaviors).

* This setup supports flexible composition and adheres to ISP.

* Easy to replace behaviors with mocks or alternate implementations for testing or extension.

* This demonstrates clean dependency management and loose coupling with dependency injection of role components.

## 5. Compare constructor vs property injection for role interfaces
Here's a comparison of constructor injection vs property (setter) injection for role interfaces with Java code examples:

### Constructor Injection
* Dependencies are provided through the class constructor.

* Ensures dependencies are initialized before the object is used.

* Guarantees immutability of injected dependencies.

* Encourages fail-fast if a required dependency is missing.

```java
class HumanWorker {
    private final Workable workBehavior;
    private final Eatable eatBehavior;

    public HumanWorker(Workable workBehavior, Eatable eatBehavior) {
        this.workBehavior = workBehavior;
        this.eatBehavior = eatBehavior;
    }

    public void work() { workBehavior.work(); }
    public void eat() { eatBehavior.eat(); }
}
```

### Property (Setter) Injection
* Dependencies are provided through setter methods after object creation.

* Allows optional dependencies or changes at runtime.

* Introduces mutability; dependencies can be changed anytime.

* Requires careful null checks and may delay failure detection.

```java
class HumanWorker {
    private Workable workBehavior;
    private Eatable eatBehavior;

    public void setWorkBehavior(Workable workBehavior) {
        this.workBehavior = workBehavior;
    }

    public void setEatBehavior(Eatable eatBehavior) {
        this.eatBehavior = eatBehavior;
    }

    public void work() {
        if (workBehavior != null) workBehavior.work();
        else System.out.println("No work behavior assigned");
    }

    public void eat() {
        if (eatBehavior != null) eatBehavior.eat();
        else System.out.println("No eat behavior assigned");
    }
}
```

### Summary Comparison
| Aspect        | Constructor Injection      |  Property Injection      |
| ------------- |-------------|--------------|
| Initialization |Mandatory at creation|Optional, set after creation|
| Immutability |Yes|No|
| Null safety |Better (fail fast)|Weaker, needs null checks|
| Flexibility |Less (fixed dependencies)|More (can change dependencies)|
| Use case |Required dependencies|Optional or replaceable dependencies|

Constructor injection is generally preferred for required dependencies due to better immutability and fail-fast behavior, while property injection suits optional or changeable dependencies.

This helps managing role interfaces flexibly while maintaining clean, decoupled code.
