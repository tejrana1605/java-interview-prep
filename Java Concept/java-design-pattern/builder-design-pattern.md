# Builder Design Pattern
The Builder Design Pattern is a creational pattern used to construct complex objects step by step. It separates the construction of an object from its representation, allowing the same building process to create different representations or configurations of the product.

### Key Features
Useful for constructing objects with many optional or required components.

Helps avoid "telescoping constructors" (constructors with many parameters).

Allows chaining of methods for readable, fluent code.

### Simple Java Example
Let’s say you want to create a Computer object. Some attributes are optional:

```java
public class Computer {
    private String CPU;
    private int RAM;
    private int storage;
    private boolean graphicsCard;

    // Private constructor
    private Computer(Builder builder) {
        this.CPU = builder.CPU;
        this.RAM = builder.RAM;
        this.storage = builder.storage;
        this.graphicsCard = builder.graphicsCard;
    }

    public static class Builder {
        private String CPU;
        private int RAM;
        private int storage;
        private boolean graphicsCard;

        public Builder setCPU(String c) {
            this.CPU = c;
            return this;
        }
        public Builder setRAM(int r) {
            this.RAM = r;
            return this;
        }
        public Builder setStorage(int s) {
            this.storage = s;
            return this;
        }
        public Builder setGraphicsCard(boolean g) {
            this.graphicsCard = g;
            return this;
        }

        public Computer build() {
            return new Computer(this);
        }
    }
}

Usage:

public class BuilderDemo {
    public static void main(String[] args) {
        Computer pc = new Computer.Builder()
            .setCPU("Intel i7")
            .setRAM(16)
            .setStorage(512)
            .setGraphicsCard(true)
            .build();

        Computer simplePC = new Computer.Builder()
            .setCPU("Intel i3")
            .setRAM(4)
            .build();
    }
}

```
### In Summary
Builder Pattern: Ideal for step-by-step construction of objects, particularly those with many configuration options or mandatory parameters. Improves code clarity and avoids complex constructors.​

Contrast to Factory Method: Factory Method instantly provides different implementations; Builder focuses on gradually assembling a single, often complex, product.

**[Back To Creational Design Patterns](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/creational-design-pattern.md#creational-design-patterns)**