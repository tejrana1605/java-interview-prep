
# Flyweight Design Pattern
The Proxy Pattern is a structural design pattern that provides a surrogate (substitute) or placeholder for another object to control access to it. It enables additional behavior such as lazy initialization, access control, logging, or caching without changing the original object's code.

Think of it like a gatekeeper that:

- Controls access to a real object,
- Adds extra behavior (like logging, access control, caching, etc.),
- But exposes the same interface as the real object.

### Real-World Analogy

- Imagine a bank account — you can’t directly access the bank’s internal servers.
Instead, you use an ATM machine (Proxy) that talks to the real bank system (RealSubject) on your behalf.

- Virtual proxies used in GUI frameworks to delay loading of heavy images.

- Access control proxies checking user permissions before allowing operations.

### Key Components:
Subject: An interface common to both RealSubject and Proxy, defining the methods client can invoke.

RealSubject: The actual object that performs the core operations.

Proxy: Implements the Subject interface and holds a reference to RealSubject. It manages access by forwarding requests and can add extra logic.

### Example: Image Loading Proxy

We’ll use a simple and classic example — lazy loading of images.

The idea:

- RealImage loads an image from disk (an expensive operation).

- ProxyImage delays loading until it’s actually needed.

```java
// Subject interface
interface Image {
    void display();
}

// RealSubject: The real object doing heavy work
class RealImage implements Image {
    private final String filename;

    public RealImage(String filename) {
        this.filename = filename;
        loadFromDisk(); // expensive operation
    }

    private void loadFromDisk() {
        System.out.println("Loading image from disk: " + filename);
    }

    @Override
    public void display() {
        System.out.println("Displaying image: " + filename);
    }
}

// Proxy: Controls access to RealImage
class ProxyImage implements Image {
    private RealImage realImage;
    private final String filename;

    public ProxyImage(String filename) {
        this.filename = filename;
    }

    @Override
    public void display() {
        // Only load when needed (lazy loading)
        if (realImage == null) {
            realImage = new RealImage(filename);
        }
        realImage.display();
    }
}

// Client code
public class ProxyPatternDemo {
    public static void main(String[] args) {
        Image image1 = new ProxyImage("photo1.jpg");

        // Image will be loaded only when display() is called
        System.out.println("Calling display first time:");
        image1.display();   // Loads from disk

        System.out.println("\nCalling display second time:");
        image1.display();   // Uses cached RealImage
    }
}

output:-

Calling display first time:
Loading image from disk: photo1.jpg
Displaying image: photo1.jpg

Calling display second time:
Displaying image: photo1.jpg
```


### Java Example: Virtual Proxy for Expensive Image Loading

```java
// Subject interface
interface Image {
    void display();
}

// RealSubject: resource-intensive object
class RealImage implements Image {
    private String filename;

    public RealImage(String filename) {
        this.filename = filename;
        loadFromDisk();
    }

    private void loadFromDisk() {
        System.out.println("Loading " + filename);
        // Simulate heavy loading
    }

    @Override
    public void display() {
        System.out.println("Displaying " + filename);
    }
}

// Proxy: controls access to RealImage
class ProxyImage implements Image {
    private RealImage realImage;
    private final String filename;

    public ProxyImage(String filename) {
        this.filename = filename;
    }

    @Override
    public void display() {
        if (realImage == null) {
            realImage = new RealImage(filename);  // Lazy initialization
        }
        realImage.display();
    }
}

// Client code
public class ProxyPatternDemo {
    public static void main(String[] args) {
        Image image = new ProxyImage("photo.jpg");
        
        // Image will be loaded from disk only on first display call
        image.display();  // Loading photo.jpg \n Displaying photo.jpg
        image.display();  // Displaying photo.jpg (no loading this time)
    }
}
```

### Benefits:
- Controls access to the original object, adding security, caching, or logging.

- Implements lazy loading (virtual proxy) for performance gains.

- Enables remote proxies for networked/remote objects.

- Provides a placeholder where the real object is expensive to create.

**[Back To Creational Design Patterns](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/structural-design-pattern.md#structural-design-patterns)**