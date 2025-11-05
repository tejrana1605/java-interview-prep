# Creational Design Patterns

Creational Design Patterns in Java focus on the best way to instantiate and create objects. These patterns provide various mechanisms to create objects in a flexible and reusable way, making the system independent from the object creation process.

There are five primary types of creational design patterns commonly used in Java:

### 1.  [Singleton](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/singleton-design-pattern.md/#singleton-design-patterns): 
Ensures a class has only one instance and provides a global access point to it. This is useful for managing shared resources like configuration or logging.

### 2. [Factory Method:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/factory-method-design-pattern.md/#factory-method-design-pattern) 
Defines an interface for creating an object but allows subclasses to alter the type of objects that will be created. It encapsulates object creation logic and promotes loose coupling.

### 3. [Abstract Factory:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/abstract-factory-design-pattern.md/#abstract-factory-design-pattern) 
Produces families of related or dependent objects without specifying their concrete classes. It is useful when the system needs to be independent of how its products are created.

### 4. [Builder:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/builder-design-pattern.md/#builder-design-pattern) 
Allows for the step-by-step construction of a complex object, enabling the production of different representations using the same construction process. It is useful for objects with many parameters.

### 5. [Prototype:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/prototype-design-patterns.md/#prototype-design-patterns) 
Creates new objects by copying an existing object (prototype) rather than creating a new one from scratch, useful to avoid expensive object creation.

In Java, these patterns are implemented with interfaces, abstract classes, or concrete classes to control object instantiation, promote code reuse, and increase flexibility.

**For example**, the Singleton pattern is often used to ensure a single instance of a class like a Logger, while the Builder pattern can be used to construct objects like a Person with optional parameters in a controlled manner.

**Note:-** In brief, creational design patterns address the problem of object creation in an elegant, controlled manner to increase code maintainability and scalability by abstracting the instantiation process.