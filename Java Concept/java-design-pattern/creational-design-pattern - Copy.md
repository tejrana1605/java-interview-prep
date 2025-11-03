# Abstract Factory Design Pattern
The Abstract Factory Design Pattern is a creational pattern that provides an interface for creating families of related or dependent objects without specifying their concrete classes. It works as a "factory of factories," allowing you to create a suite of related products easily and consistently.

### Key Idea:
Instead of creating objects directly via constructors or a single factory, you use an abstract factory interface with multiple concrete factory implementations.

Each concrete factory produces a family of related objects.

Client code works with factories and products abstractly, enabling flexibility and interchangeability of product families.

### Components of the Abstract Factory Design Pattern

* **Abstract Factory:** Interface that declares methods to create abstract product objects.

* **Concrete Factory:** Implements the Abstract Factory interface methods to create product objects that inherit from it.

* **Abstract Product:** Interface that declares methods which each concrete product must implement.

* **Concrete Product:** Classes that implement the Abstract Product interface to define the properties of their corresponding concrete factories.

### AbstractFactoryDemo.java

```java
interface AbstractCarsFactory  {  
    SUV createSUV();  
    Sedan createSedans();  
}  
class ToyotaFactory implements AbstractCarsFactory  {  
    @Override  
    public SUV createSUV() {  
        return new ToyotaSUV();  
    }  
    @Override  
    public Sedan createSedans() {  
        return new ToyotaSedan();  
    }  
}  
class FordFactory implements AbstractCarsFactory  {  
    @Override  
    public SUV createSUV() {  
        return new FordSUV();  
    }  
    @Override  
    public Sedan createSedans() {  
        return new FordSedan();  
    }  
}  
interface SUV {  
    void drive();  
}  
interface Sedan {  
    void drive();  
}  
class ToyotaSUV implements SUV {  
    @Override  
    public void drive() {  
        System.out.println("Drive a Toyotas SUV");  
    }  
}  
class ToyotaSedan implements Sedan {  
    @Override  
    public void drive() {  
        System.out.println("Drive a Toyotas Sedan");  
    }  
}  
class FordSUV implements SUV {  
    @Override  
    public void drive() {  
        System.out.println("Drive a Fords SUV");  
    }  
}  
class FordSedan implements Sedan {  
    @Override  
    public void drive() {  
        System.out.println("Drive a Fords Sedan");  
    }  
}  
public class AbstractFactoryDemo {  
    public static void main(String[] args) {  
        AbstractCarsFactory  toyotaFactory = new ToyotaFactory();  
        SUV toyotaSUV = toyotaFactory.createSUV();  
        Sedan toyotaSedan = toyotaFactory.createSedans();  
        toyotaSUV.drive();  
        toyotaSedan.drive();  
        AbstractCarsFactory  fordFactory = new FordFactory();  
        SUV fordSUV = fordFactory.createSUV();  
        Sedan fordSedan = fordFactory.createSedans();  
        fordSUV.drive();  
        fordSedan.drive();  
    }  
}  
```

### Example in Java
Imagine a UI toolkit with two themes (Windows and Mac), each with a specific style for buttons and checkboxes.

1. Abstract Products

```java
public interface Button {
    void paint();
}

public interface Checkbox {
    void paint();
}

```

2. Concrete Products - Windows Variants

```java
public class WindowsButton implements Button {
    public void paint() {
        System.out.println("Rendering Windows button");
    }
}

public class WindowsCheckbox implements Checkbox {
    public void paint() {
        System.out.println("Rendering Windows checkbox");
    }
}

```

3. Concrete Products - Mac Variants

```java
public class MacButton implements Button {
    public void paint() {
        System.out.println("Rendering Mac button");
    }
}

public class MacCheckbox implements Checkbox {
    public void paint() {
        System.out.println("Rendering Mac checkbox");
    }
}
```

4. Abstract Factory Interface

```java
public interface GUIFactory {
    Button createButton();
    Checkbox createCheckbox();
}
```

5. Concrete Factories

```java
public class WindowsFactory implements GUIFactory {
    public Button createButton() {
        return new WindowsButton();
    }

    public Checkbox createCheckbox() {
        return new WindowsCheckbox();
    }
}

public class MacFactory implements GUIFactory {
    public Button createButton() {
        return new MacButton();
    }

    public Checkbox createCheckbox() {
        return new MacCheckbox();
    }
}
```

6. Client Code

```java
public class Application {
    private Button button;
    private Checkbox checkbox;

    public Application(GUIFactory factory) {
        button = factory.createButton();
        checkbox = factory.createCheckbox();
    }

    public void paint() {
        button.paint();
        checkbox.paint();
    }
}

public class Demo {
    public static void main(String[] args) {
        GUIFactory factory;
        String osName = System.getProperty("os.name").toLowerCase();

        if (osName.contains("windows")) {
            factory = new WindowsFactory();
        } else {
            factory = new MacFactory();
        }

        Application app = new Application(factory);
        app.paint();
    }
}
```

### Benefits:
* Ensures consistency among products from the same family.

* Client is decoupled from concrete classes.

* Easy to add new product families without changing client code.

This pattern is widely used for UI themes, multi-platform support, and systems requiring interchangeable product families.