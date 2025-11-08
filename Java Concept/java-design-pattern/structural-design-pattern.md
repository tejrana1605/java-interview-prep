# Structural Design Patterns

Structural Design Patterns are software design solutions focused on how classes and objects are composed or organized to form larger, functional structures. These patterns simplify relationships between entities, enabling flexible, efficient, and maintainable software architectures.

Key Points:
- These design patterns concern class and object composition. 
- decoupling Interfaces & implementation.
- Concept of inheritance is used to compose interfaces and define ways to compose objects to obtain new functionalities.

## Common Structural Patterns

### 1.  [Adapter](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/adapter-design-pattern.md/#adapter-design-patterns): 
Converts one interface of a class into another expected by clients, enabling incompatible interfaces to work together.

### 2. [Bridge:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/bridge-design-pattern.md/#bridge-design-pattern) 
Decouples an abstraction from its implementation so they can vary independently.

### 3. [Composite:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/composite-design-pattern.md/#composite-design-pattern) 
Composes objects into tree structures to represent part-whole hierarchies, letting clients treat individual and composite objects uniformly.

### 4. [Decorator:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/decorator-design-pattern.md/#decorator-design-pattern) 
Adds new responsibilities to objects dynamically without altering their structure.

### 5. [Facade:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/facade-design-patterns.md/#facade-design-patterns) 
Provides a simplified interface to a complex subsystem.

### 6. [Flyweight:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/flyweight-design-patterns.md/#flyweight-design-patterns) 
Shares common parts of objects to reduce memory usage for large numbers of fine-grained objects.

### 7. [Proxy:](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/proxy-design-patterns.md/#proxy-design-patterns) 
Provides a surrogate or placeholder controlling access to another object.

## Example Scenario
In a graphical editor, various shapes (lines, polygons) form pictures. Structural patterns help organize these shapes into composite structures (Composite), adapt different interfaces (Adapter), and add features like borders or shadows dynamically (Decorator).

## Benefits
- Simplify and clarify object relationships.

- Enhance flexibility and extensibility of systems.

- Improve code reuse and maintainability.

- Optimize resource usage with shared objects.

## Challenges
- Can introduce complexity and additional layers.

- Possible performance overhead in some cases.

- Risk of overengineering and harder debugging.

## Summary
Structural Design Patterns are critical for building scalable, modular software by focusing on how objects are put together. They complement creational and behavioral patterns by solving problems of composition and delegation in software design.