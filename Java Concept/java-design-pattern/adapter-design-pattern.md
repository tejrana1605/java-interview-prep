# Adapter Design Pattern
The Adapter design pattern in Java is a way to make two objects with different interfaces work together. Sometimes, we have objects that we want to use together, but their interfaces are not compatible. In such cases, we can use the Adapter pattern.

The adapter pattern acts as a middleman or wrapper between these two objects. It takes the calls made to one object and translates them into a format that the other object can understand. This way, the two objects can collaborate seamlessly, even though they have incompatible interfaces.

**OR**

The Adapter Design Pattern is one of the most commonly used structural design patterns in Java, especially when integrating incompatible interfaces (e.g., connecting legacy code, third-party APIs, or different data formats).

### Components:
**Target Interface:** The interface expected by the client.

**Adaptee:** The existing class with an incompatible interface.

**Adapter:** Implements the Target interface and internally uses an instance of the Adaptee to convert requests.

**Client:** Uses the Target interface unaware of the Adaptee or Adapter.

Java Example:

```java
// Target Interface expected by client
public interface Printer {
    void print();
}

// Adaptee: existing class with incompatible interface
public class LegacyPrinter {
    public void printDocument() {
        System.out.println("Legacy Printer is printing a document.");
    }
}

// Adapter: makes LegacyPrinter compatible with Printer interface
public class PrinterAdapter implements Printer {
    private final LegacyPrinter legacyPrinter;

    public PrinterAdapter(LegacyPrinter legacyPrinter) {
        this.legacyPrinter = legacyPrinter;
    }

    @Override
    public void print() {
        legacyPrinter.printDocument();  // Adapt method call
    }
}

// Client code uses Printer
public class Client {
    public static void main(String[] args) {
        LegacyPrinter legacyPrinter = new LegacyPrinter();

        // Wrap LegacyPrinter in an adapter
        Printer adapter = new PrinterAdapter(legacyPrinter);
        
        // Client uses the adapter seamlessly
        adapter.print(); // Output: Legacy Printer is printing a document.
    }
}

```

### Summary:
* Adapter pattern is useful for integrating legacy or third-party components with an existing system.

* It promotes reusability and flexibility without modifying existing code.

* The pattern decouples client code from specific implementations behind a common interface.

### Advantages of Using the Adapter Design Pattern

- **Compatibility:** The Adapter pattern allows objects with incompatible interfaces to work together. This can be useful when working with legacy code or third-party libraries.

- **Reusability:** The Adapter pattern can make code more reusable. For example, if you have a class that implements a specific interface, you can use the Adapter pattern to create an adapter class that allows the class to be used with other interfaces.

- **Flexibility:** The Adapter pattern can make code more flexible. For example, if we have a class that uses a specific concrete implementation of an interface, we can use the Adapter pattern to create an adapter class that allows the class to be used with different concrete implementations of the interface.

### Real Life Example of Adapter Design Pattern
One of the great real-life example of adapter design pattern is mobile charger. Mobile battery needs 3 volts to charge but the normal socket produces either 120V (US) or 240V (India). So, the mobile charger works as an adapter between mobile charging socket and the wall socket.

We will try to implement multi-adapter using adapter design pattern in this section. So, first of all we will have two classes - Volt (to measure volts) and Socket (producing constant volts of 120V).

Volt.java

```java
public class Volt {  
    private int volts;  
    public Volt(int v){  
        this.volts=v;  
    }  
    public int getVolts() {  
        return volts;  
    }  
    public void setVolts(int volts) {  
        this.volts = volts;  
    }  
}  
public class Socket {  
    public Volt getVolt(){  
        return new Volt(120);  
    }  
}  
```

Now we want to build an adapter that can produce 3 volts, 12 volts and default 120 volts. In order to achieve this, we will create an adapter interface with these methods

```java
public interface SocketAdapter {  
    public Volt get120Volt();         
    public Volt get12Volt();  
    public Volt get3Volt();  
}  
```

Complete Example 2:-
```java
// Class representing a voltage value
class Volt {
    private int volts;
    public Volt(int v) { this.volts = v; }
    public int getVolts() { return volts; }
    public void setVolts(int volts) { this.volts = volts; }
}

// Adaptee: Socket producing fixed voltage
class Socket {
    public Volt getVolt() { return new Volt(120); }
}

// Target interface for mobile voltage
interface SocketAdapter {
    Volt get3Volt();
    Volt get12Volt();
    Volt get120Volt();
}

// Adapter: converts high voltage to required voltage
class SocketAdapterImpl implements SocketAdapter {
    private Socket socket;
    public SocketAdapterImpl(Socket socket) { this.socket = socket; }
    public Volt get3Volt() { return convertVolt(socket.getVolt(), 3); }
    public Volt get12Volt() { return convertVolt(socket.getVolt(), 12); }
    public Volt get120Volt() { return socket.getVolt(); }
    
    // Utility for conversion
    private Volt convertVolt(Volt v, int target) {
        return new Volt(target);
    }
}

// Client code
public class MobileChargerExample {
    public static void main(String[] args) {
        SocketAdapter adapter = new SocketAdapterImpl(new Socket());
        System.out.println("Mobile needs 3V, got: " + adapter.get3Volt().getVolts() + "V");
        System.out.println("Laptop needs 12V, got: " + adapter.get12Volt().getVolts() + "V");
        System.out.println("Home appliance needs 120V, got: " + adapter.get120Volt().getVolts() + "V");
    }
}
```

### How this matches your analogy:

- **Socket (Adaptee):** Only delivers 120V.

- **Mobile device (Client):** Needs an interface delivering 3V.

- **SocketAdapter (Adapter interface):** Defines how clients request specific voltages.

- **SocketAdapterImpl (Concrete Adapter):** Converts 120V input to desired outputs for different devices, just like a charger.

This code demonstrates the adapter's role: transforming incompatible interfaces so devices can charge safely.

## Two Way Adapter Pattern
While implementing Adapter pattern, there are two approaches class adapter and object adapter. However, both these approaches produce same result.

### Class Adapter
The Class Adapter pattern uses Java inheritance to extend the source interface and provide adapter functionality. The adapter class inherits from the source interface and implements the target interface. It then overrides the methods of the source interface to delegate to the target interface.

#### Advantages:

- Easy to implement.

- More efficient, as there is no additional object overhead.

#### Disadvantages:

- Less flexible, as the adapter class is tightly coupled to the source interface.

- It can lead to multiple inheritance problems.

#### Characteristics:
- Adapter inherits from the adaptee class.

- Adapter implements the target interface.

- Suitable when you can inherit from the adaptee class (in Java, you inherit one class and implement interfaces).

- Can override adaptee methods as needed.

#### Class Adapter Implementation Example in Java

```java

// Target interface expected by client
interface Target {
    void request();  // Method client expects
}

// Adaptee class with incompatible interface
class Adaptee {
    public void specificRequest() {
        System.out.println("Adaptee specificRequest called");
    }
}

// Class Adapter implementing Target by extending Adaptee
class ClassAdapter extends Adaptee implements Target {
    @Override
    public void request() {
        // Adapter translates Target.request() to Adaptee.specificRequest()
        specificRequest();
    }
}

// Client code
public class Client {
    public static void main(String[] args) {
        Target target = new ClassAdapter();
        target.request();  // Output: Adaptee specificRequest called
    }
}

```

#### Summary:
- Class Adapter uses inheritance, combining adaptee and target interface into one class.

- Allows adapter to override adaptee behavior if needed.

- Less flexible than Object Adapter (single inheritance limitation) but more efficient since it avoids delegation overhead.

- Suitable when inheritance is possible and desirable.

### Object Adapter
The Object Adapter pattern uses Java composition to wrap the source object and provide adapter functionality. The adapter class contains an instance of the source object and implements the target interface. It then delegates call to the target interface to the source object.

**OR**

The Object Adapter Pattern in Java involves creating an adapter class that contains an instance of the adaptee (the class with the incompatible interface) and delegates calls to this instance, often performing necessary transformations.

#### Advantages:

- More flexible, as the adapter class is not tightly coupled to the source interface.

- It does not lead to multiple inheritance problems.

#### Disadvantages:

- It is more complex to implement.

- Less efficient, as there is additional object overhead.

#### Implementation of Object Adapter Pattern in Java:

```java
// Target interface
interface Target {
    void request();  // Client expected method
}

// Adaptee class with incompatible interface
class Adaptee {
    public void specificRequest() {
        System.out.println("Adaptee specific request executed");
    }
}

// Object Adapter class
class ObjectAdapter implements Target {
    private final Adaptee adaptee;  // Composition: contains Adaptee

    public ObjectAdapter(Adaptee adaptee) {
        this.adaptee = adaptee;
    }

    @Override
    public void request() {
        // Delegate call and adapt behavior
        adaptee.specificRequest();
    }
}

// Usage
public class Main {
    public static void main(String[] args) {
        Adaptee adaptee = new Adaptee();
        Target adapter = new ObjectAdapter(adaptee);
        adapter.request();  // Output: Adaptee specific request executed
    }
}
```

#### Summary:
- The object adapter contains an instance of the adaptee.

- It delegates calls to the adaptee while adapting behavior to match the target interface.

- This pattern provides more flexibility than class adapters because it allows adapting multiple classes without inheritance constraints.

- Suitable when you cannot or do not want to extend the adaptee class.

In contrast to the class adapter, which extends the adaptee, the object adapter uses composition, making it more flexible when adopting multiple classes or hierarchies.

### Example of Class and object:-

```java
Class Adapter Implementation:-

SocketClassAdapterImpl.java

//Using inheritance for adapter pattern  
public class SocketClassAdapterImpl extends Socket implements SocketAdapter{  
    @Override  
    public Volt get120Volt() {  
        return getVolt();  
    }  
    @Override  
    public Volt get12Volt() {  
        Volt v= getVolt();  
        return convertVolt(v,10);  
    }  
    @Override  
    public Volt get3Volt() {  
        Volt v= getVolt();  
        return convertVolt(v,40);  
    }     
    private Volt convertVolt(Volt v, int i) {  
        return new Volt(v.getVolts()/i);  
    }  
}  

Object Adapter Implementation:-

SocketObjectAdapterImpl.java

public class SocketObjectAdapterImpl implements SocketAdapter{  
    //Using Composition for adapter pattern  
    private Socket sock = new Socket();  
    @Override  
    public Volt get120Volt() {  
        return sock.getVolt();  
    }  
    @Override  
    public Volt get12Volt() {  
        Volt v= sock.getVolt();  
        return convertVolt(v,10);  
    }  
    @Override  
    public Volt get3Volt() {  
        Volt v= sock.getVolt();  
        return convertVolt(v,40);  
    }     
    private Volt convertVolt(Volt v, int i) {  
        return new Volt(v.getVolts()/i);  
    }  
}

```

Note that both the adapter implementations are almost same and they implement the SocketAdapter interface. The adapter interface can also be an abstract class. Here, is a test program to consume our adapter design pattern implementation.

```java
AdapterPatternTest.java

import com.journaldev.design.adapter.SocketAdapter;  
import com.journaldev.design.adapter.SocketClassAdapterImpl;  
import com.journaldev.design.adapter.SocketObjectAdapterImpl;  
import com.journaldev.design.adapter.Volt;  
public class AdapterPatternTest {  
    public static void main(String[] args) {          
        testClassAdapter();  
        testObjectAdapter();  
    }  
    private static void testObjectAdapter() {  
        SocketAdapter sockAdapter = new SocketObjectAdapterImpl();  
        Volt v3 = getVolt(sockAdapter,3);  
        Volt v12 = getVolt(sockAdapter,12);  
        Volt v120 = getVolt(sockAdapter,120);  
        System.out.println("v3 volts using Object Adapter="+v3.getVolts());  
        System.out.println("v12 volts using Object Adapter="+v12.getVolts());  
        System.out.println("v120 volts using Object Adapter="+v120.getVolts());  
    }  
    private static void testClassAdapter() {  
        SocketAdapter sockAdapter = new SocketClassAdapterImpl();  
        Volt v3 = getVolt(sockAdapter,3);  
        Volt v12 = getVolt(sockAdapter,12);  
        Volt v120 = getVolt(sockAdapter,120);  
        System.out.println("v3 volts using Class Adapter="+v3.getVolts());  
        System.out.println("v12 volts using Class Adapter="+v12.getVolts());  
        System.out.println("v120 volts using Class Adapter="+v120.getVolts());  
    }     
    private static Volt getVolt(SocketAdapter sockAdapter, int i) {  
        switch (i){  
        case 3: return sockAdapter.get3Volt();  
        case 12: return sockAdapter.get12Volt();  
        case 120: return sockAdapter.get120Volt();  
        default: return sockAdapter.get120Volt();  
        }  
    }  
}  

Output:

v3 volts using Class Adapter=3
v12 volts using Class Adapter=12
v120 volts using Class Adapter=120
v3 volts using Object Adapter=3
v12 volts using Object Adapter=12
v120 volts using Object Adapter=120
```

Overall, the Adapter design pattern is a powerful tool that can be used to solve a variety of problems. It is especially useful when working with incompatible interfaces or legacy code.

**[Back To Creational Design Patterns](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/structural-design-pattern.md#structural-design-patterns)**