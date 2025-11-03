# Singleton Design Patterns

The Singleton Design Pattern is a creational design pattern that ensures a class has only one instance and provides a global point of access to that single instance. This pattern is useful when exactly one object is needed to coordinate actions across the system, such as a configuration manager, logging class, or database connection pool.

### Implementing a Singleton Class in Java
* Declare a private static variable to hold the single instance of the class.

* Make the constructor of the class private, so that no other instances can be created.

* Provide a public static method to return the single instance of the class, creating it if necessary.

### Key Characteristics of Singleton Pattern
1. The class has a private constructor to prevent other classes from instantiating it directly.

2. A static method (commonly called getInstance()) returns the single instance of the class. This method creates the instance only once (lazy initialization) and returns the same instance for every subsequent call.

3. The single instance is typically stored in a private static variable inside the class.

4. It is designed to be thread-safe in multi-threaded environments, often by synchronizing the getInstance() method or using other concurrency mechanisms.

```java
Example in java:-

public class Singleton {
    // Private static variable that holds the single instance
    private static Singleton single_instance = null;

    // An example member variable to demonstrate state
    public String s;

    // Private constructor to restrict instantiation from other classes
    private Singleton() {
        s = "Hello, I am a singleton!";
    }

    // Public static method to provide the global point of access
    // Uses synchronized for thread safety (lazy initialization)
    public static synchronized Singleton getInstance() {
        if (single_instance == null) {
            single_instance = new Singleton();
        }
        return single_instance;
    }
}
```

```java
Usage:-

public class Main {
    public static void main(String[] args) {
        Singleton x = Singleton.getInstance();
        Singleton y = Singleton.getInstance();
        Singleton z = Singleton.getInstance();

        // All instances will have the same memory address
        System.out.println("Hashcode of x: " + x.hashCode());
        System.out.println("Hashcode of y: " + y.hashCode());
        System.out.println("Hashcode of z: " + z.hashCode());

        if (x == y && y == z) {
            System.out.println("All three objects point to the same instance.");
        } else {
            System.out.println("Different instances exist.");
        }
    }
}

```

### Explanation
* When getInstance() is called for the first time, it creates the single instance of Singleton.

* Subsequent calls return the same instance, ensuring only one object exists.

* The hashCode() method outputs the same value for x, y, and z because they refer to the same instance.

* This pattern ensures controlled access to the unique instance and prevents multiple object creation, saving memory and avoiding state inconsistencies.

Singleton is widely used for resource management cases where a single shared resource is required in the application lifecycle.

## none thread-safe Java Singleton implementations

### 1. Basic Lazy Initialization (Not Thread-Safe)
```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {
        // private constructor to restrict instantiation
    }

    public static Singleton getInstance() {
        if (instance == null) {  // no synchronization - not thread-safe
            instance = new Singleton();
        }
        return instance;
    }
}

```
#### Explanation:
1. This implementation lazily initializes the singleton instance.

2. However, it is not thread-safe: if two or more threads call getInstance() concurrently or simultaneously when instance is null, multiple instances may be created.

3. This can lead to bugs in multithreaded environments.

This approach is generally not recommended in concurrent applications without adding synchronization mechanisms or other thread-safety patterns.

### 2. Non-Thread-Safe Eager Initialization (Thread-safe by loading but not lazy)
```java
public class Singleton {
    private static final Singleton instance = new Singleton();

    private Singleton() {
        // private constructor
    }

    public static Singleton getInstance() {
        return instance;
    }
}
```

Eager initialization is thread-safe due to JVM class loading but is not lazy.

If lazy instantiation is needed, this approach does not satisfy it.

#### Explanation:
1. These basic approaches do not synchronize the instance creation method or use special handling for concurrency.

2. Therefore, in a multithreaded scenario, they may create multiple instances violating Singleton principles.

3. They are suitable only in single-threaded contexts or when eager initialization always runs before multithreaded access.

For thread safety with lazy initialization, synchronization, double-checked locking, or the static inner class pattern are recommended.

## Show thread-safe Java Singleton implementations

Here are several common thread-safe Singleton design pattern implementations in Java, explaining each with code examples:

### 1. Synchronized Method Singleton
The simplest thread-safe implementation where getInstance() is synchronized to allow only one thread at a time.

```java
public class Singleton {
    private static Singleton instance;

    private Singleton() {}

    public static synchronized Singleton getInstance() {
        if (instance == null) {
            instance = new Singleton();
        }
        return instance;
    }
}
```

* Thread-safe but synchronized introduces performance overhead on every call.

### 2. Eager Initialization Singleton
Instance is created at class loading time, thread safety is guaranteed by the JVM class loader.

```java
public class Singleton {
    private static final Singleton instance = new Singleton();

    private Singleton() {}

    public static Singleton getInstance() {
        return instance;
    }
}
````
* No lazy loading, instance always created even if not used, but very fast.

### 3. Double-Checked Locking Singleton
Reduces synchronization overhead by first checking instance without locking, then synchronizing only when necessary.

```java
public class Singleton {
    private static volatile Singleton instance;

    private Singleton() {}

    public static Singleton getInstance() {
        if (instance == null) {
            synchronized (Singleton.class) {
                if (instance == null) {
                    instance = new Singleton();
                }
            }
        }
        return instance;
    }
}
```

* Uses volatile for visibility. Efficient and thread-safe.

### 4. Static Inner Class Singleton (Bill Pugh Singleton)

Relies on JVM lazy loading of static inner classes to create thread-safe, lazy-initialized singleton without synchronization overhead.

```java
public class Singleton {
    private Singleton() {}

    private static class SingletonHelper {
        private static final Singleton INSTANCE = new Singleton();
    }

    public static Singleton getInstance() {
        return SingletonHelper.INSTANCE;
    }
}
```

```java
public class Singleton {  
    // Static nested class to hold the singleton instance  
    private static class Nested {  
        static Singleton instance = new Singleton();  
    }  
  
    // Private Constructor to prevent direct instantiation  
    private Singleton() {  
        //Constructor is private to prevent direct instantiation.  
    }  
  
    // Static Method to retrieve the singleton instance  
    public static Singleton getInstance() {  
        return Nested.instance;  
    }  
  
    //Method to perform some action  
    public void doSomething() {  
        System.out.println("Hello World!");  
    }  
  
    // Main Method to demonstrate the singleton usage  
    public static void main(String[] args) {  
        // Get the singleton instance.  
        Singleton singleton = Singleton.getInstance();  
  
        // Do something with the singleton instance.  
        singleton.doSomething();  
    }  
}  
```

### Advantages of Nested Initialization:
* Lazy loading
* Thread-Safety

### Lazy loading
Lazy loading is a way of creating objects only when they are needed. It can improve performance because the program doesn't have to do as much work when it starts up. When the getInstance() method is used for the first time in a singleton class, the object is only then constructed.

### Thread-safety
Thread safety is a critical concern in multi-threaded programs. Multiple threads can execute a thread-safe program without causing data corruption or other problems. The nested initialization pattern is thread-safe because the Singleton class object is created and initialized only once, regardless of how many threads are trying to access it.

* Recommended approach for lazy initialization and thread safety, with no synchronization costs.

### 5. Enum Singleton
Using a single-element enum guarantees thread safety and serialization by default.

```java
public enum Singleton {
    INSTANCE;

    public void someMethod() {
        // method logic
    }
}

```

* Simplifies singleton implementation and protects against serialization/deserialization issues.

Each approach balances thread safety, lazy initialization, and performance differently. The static inner class and enum methods are generally preferred in modern Java for thread safety and simplicity.

## 1. Provide code for an enum-based Singleton implementation

Here is a concise and thread-safe Java Singleton implementation using an enum:

```java
public enum Singleton {
    INSTANCE;

    private int value;

    // Example method to get the value
    public int getValue() {
        return value;
    }

    // Example method to set the value
    public void setValue(int value) {
        this.value = value;
    }

    // Additional methods can be added here
}
```

Usage Example

```java
public class Main {
    public static void main(String[] args) {
        Singleton singleton = Singleton.INSTANCE;

        singleton.setValue(10);
        System.out.println("Value: " + singleton.getValue());

        Singleton anotherReference = Singleton.INSTANCE;
        System.out.println("Value from another reference: " + anotherReference.getValue());

        // Confirm both references point to the same instance
        System.out.println(singleton == anotherReference);  // Output: true
    }
}
```

### Explanation:
* The Singleton enum has a single element INSTANCE which acts as the one and only instance.

* Enums provide implicit support for thread safety and serialization by the Java language.

* This approach prevents multiple instantiations even during deserialization or reflection attacks.

* Additional state and behavior can be encapsulated as needed inside the enum singleton.

This enum singleton implementation is considered the best practice for singletons in Java due to its simplicity, thread safety, and serialization guarantees.

## Example: enum Singleton with database connection methods

Here is an example of an enum Singleton implementation in Java with database connection methods:

```java
import java.sql.Connection;
import java.sql.DriverManager;
import java.sql.SQLException;

public enum DatabaseSingleton {
    INSTANCE;

    private Connection connection;

    // Initialize the database connection
    private DatabaseSingleton() {
        try {
            // Example: load the JDBC driver (optional in modern drivers)
            Class.forName("com.mysql.cj.jdbc.Driver");

            // Example connection parameters (replace with your DB credentials)
            String url = "jdbc:mysql://localhost:3306/mydb";
            String user = "root";
            String password = "password";

            connection = DriverManager.getConnection(url, user, password);
            System.out.println("Database connection established.");
        } catch (ClassNotFoundException | SQLException e) {
            e.printStackTrace();
            throw new RuntimeException("Failed to establish DB connection");
        }
    }

    // Method to get the single database connection
    public Connection getConnection() {
        return connection;
    }

    // Method to close the connection if needed
    public void closeConnection() {
        if (connection != null) {
            try {
                connection.close();
                System.out.println("Database connection closed.");
            } catch (SQLException e) {
                e.printStackTrace();
            }
        }
    }
}
```

Usage Example

```java
public class Main {
    public static void main(String[] args) {
        Connection conn = DatabaseSingleton.INSTANCE.getConnection();

        // Use the connection for database operations
        // ...

        // When done, optionally close the connection
        DatabaseSingleton.INSTANCE.closeConnection();
    }
}
```

### Explanation
* The enum DatabaseSingleton ensures thread-safe, single-instance database connection management.

* Connection setup is done once in the enum constructor.

* getConnection() provides the only connection instance.

* This avoids creating multiple connections unnecessarily, controlling database resource usage.

* Enum guarantees singleton properties including serializability and protection against reflection attacks.

Note: In real-world applications, connection pooling (e.g., with HikariCP, Apache DBCP) is recommended instead of a raw singleton connection to handle multi-threaded DB access efficiently.

This pattern is a clean, robust way to implement singleton database connection access in simple Java applications.

## Why lazy singletons are unsafe in multithreaded Java programs

Lazy singletons are unsafe in multithreaded Java programs primarily because of the risk of race conditions during instance creation. Here's why:

### 1. No Synchronization on Instance Creation:
In a basic lazy singleton, the instance is created when first requested:

```java
if (instance == null) {
    instance = new Singleton();
}

```
If two or more threads reach this condition simultaneously when instance is null, they might both create separate instances, breaking the singleton guarantee.

### 2. Out-of-Order Writes and Visibility Issues:

The process of creating an object involves:

1. Allocating memory.
2. Initializing the object,
3. Assignment the reference to the instance variable.

Without proper memory visibility controls (like volatile), writes to the instance variable can be reordered. One thread might see a non-null instance reference before the object is fully initialized and start using an incompletely constructed object, causing subtle bugs.

### Race Condition During First Access:
The critical race is only during the very first access when the instance is created. Once fully initialized, subsequent getInstance() calls will safely return the single instance. But the initial race can cause multiple creations or partially constructed objects.

### Why Synchronization Matters:
Adding synchronization (e.g., synchronizing the getInstance() method or using a synchronized block combined with double-checked locking) prevents multiple threads from entering the instance creation code simultaneously, ensuring only one complete construction.

### Alternatives:
To avoid these issues, techniques such as eager initialization, static inner class holder, or enum-based singletons provide simpler, safer thread-safe lazy or eager initialization.

In short, lazy initialization itself is not thread-safe unless combined with synchronization or Java concurrency features. Without these, multithreaded access risks creating multiple instances or using incompletely constructed objects.