# Composite Design Pattern
The Composite Design Pattern is a structural design pattern that allows you to compose objects into tree structures and treat both individual objects (leaves) and compositions of objects (composites) uniformly. This pattern facilitates representing part-whole hierarchies and simplifies client code by treating individual and composite objects the same way.

### Features of Composite Design Pattern:

**Components:** 

It is an abstract class or interface that declares a common interface for all concrete classes. It can be an interface or an abstract class with methods that define generic operations.

```java
public interface Component {  
    void operation();  
} 
```

**leaf:** 

The leaf class represents individual objects that have no children. It uses the functionality defined by the Component interface.

```java
public class Leaf implements Component {  
    @Override  
    public void operation() {  
        // Leaf-specific operation  
    }  
} 
```

**Composite:** 

Represents complex objects that may have children (both leaf and other composites) and implements child-related operations (add, remove, getChild).

```java
import java.util.ArrayList;  
import java.util.List;  
public class Composite implements Component {  
    private List<Component> children = new ArrayList<>();  
    public void add(Component component) {  
        children.add(component);  
    }  
    public void remove(Component component) {  
        children.remove(component);  
    }  
    @Override  
    public void operation() {  
        // Composite-specific operation  
        for (Component component : children) {  
            component.operation();  
        }  
    }  
}
```

**Client:** 

Interacts with objects through the component interface, treating leaves and composites uniformly.

### How does it work?
Composite pattern allows customers to handle individual items and packages in the same way. Customers can use the same types of functionality without having to distinguish between Leaf and Composite objects. It is achieved by defining a common interface (Component) and having it used by the Leaf and Composite classes.

### Implementation of Composite Design Pattern in Java

Let's go through a simple example to illustrate the use of Composite Design Pattern in Java. Suppose, we want to model a corporate structure, where individual employees and departments can be treated equally.

```java
public interface CompanyComponent {  
    void showDetails();  
}  
// Leaf  
public class Employee implements CompanyComponent {  
    private String name;  
    public Employee(String name) {  
        this.name = name;  
    }  
    @Override  
    public void showDetails() {  
        System.out.println("Employee: " + name);  
    }  
}  
// Composite  
import java.util.ArrayList;  
import java.util.List;  
public class Department implements CompanyComponent {  
    private String name;  
    private List<CompanyComponent> employees = new ArrayList<>();  
    public Department(String name) {  
        this.name = name;  
    }  
    public void addEmployee(CompanyComponent employee) {  
        employees.add(employee);  
    }  
    @Override  
    public void showDetails() {  
        System.out.println("Department: " + name);  
        for (CompanyComponent employee : employees) {  
            employee.showDetails();  
        }  
    }  
}  
```

Now, we can use the Composite pattern to create a company hierarchy that includes both individual employees and departments.

```java
Client.java

public class Client {  
    public static void main(String[] args) {  
        Employee emp1 = new Employee("Manoj Mamilla");  
        Employee emp2 = new Employee("Kamal bittu");  
        Department engineering = new Department("Engineering");  
        engineering.addEmployee(new Employee("Narasimha Rao"));  
        engineering.addEmployee(new Employee("Manoj kumar"));  
        Department marketing = new Department("Marketing");  
        marketing.addEmployee(new Employee("Pradeep marchi"));  
        Department company = new Department("Tejas Cropo");  
        company.addEmployee(emp1);  
        company.addEmployee(emp2);  
        company.addEmployee(engineering);  
        company.addEmployee(marketing);  
        company.showDetails();  
    }  
}  


Output:

Department: Tejas Corpo
Employee: Manoj Mamilla
Employee: Kamal bittu
Department: Engineering
Employee: Narasimha Rao
Employee: Manoj kumar
Department: Marketing
Employee: Pradeep marchi

```

### Real-World Applications

Image systems:-

Consider a graphical layout in which we have to create shapes such as circles, triangles, and rectangles. Using a composite pattern allows us to treat individual shapes and compositions as one.

```java
import java.util.ArrayList;  
import java.util.List;  
// Component  
public interface Shape {  
    void draw();  
}  
// Leaf  
public class Circle implements Shape {  
    @Override  
    public void draw() {  
        System.out.println("Drawing Circle");  
    }  
}  
// Leaf  
public class Square implements Shape {  
    @Override  
    public void draw() {  
        System.out.println("Drawing Square");  
    }  
}  
// Composite  
public class CompositeShape implements Shape {  
    private List<Shape> shapes = new ArrayList<>();  
    public void addShape(Shape shape) {  
        shapes.add(shape);  
    }  
    @Override  
    public void draw() {  
        for (Shape shape : shapes) {  
            shape.draw();  
        }  
    }  
}  
public class Client {  
    public static void main(String[] args) {  
        Circle circle = new Circle();  
        Square square = new Square();  
        CompositeShape compositeShape = new CompositeShape();  
        compositeShape.addShape(circle);  
        compositeShape.addShape(square);  
        compositeShape.draw();  
    }  
}  

Output:

Drawing Circle
Drawing Square

```

### Java Example: Task Management System

```java
import java.util.ArrayList;
import java.util.List;

// Component interface
interface Task {
    void display();
}

// Leaf class
class SimpleTask implements Task {
    private String description;

    public SimpleTask(String description) {
        this.description = description;
    }

    @Override
    public void display() {
        System.out.println("- " + description);
    }
}

// Composite class
class TaskList implements Task {
    private String name;
    private List<Task> tasks = new ArrayList<>();

    public TaskList(String name) {
        this.name = name;
    }

    public void addTask(Task task) {
        tasks.add(task);
    }

    public void removeTask(Task task) {
        tasks.remove(task);
    }

    @Override
    public void display() {
        System.out.println(name + ":");
        for (Task task : tasks) {
            task.display();
        }
    }
}

// Client code
public class CompositePatternDemo {
    public static void main(String[] args) {
        // Simple tasks
        Task simpleTask1 = new SimpleTask("Write code");
        Task simpleTask2 = new SimpleTask("Prepare report");

        // Create composite task list
        TaskList projectTasks = new TaskList("Project Tasks");
        projectTasks.addTask(simpleTask1);
        projectTasks.addTask(simpleTask2);

        // Create a nested composite task list
        TaskList phase1Tasks = new TaskList("Phase 1 Tasks");
        phase1Tasks.addTask(new SimpleTask("Design"));
        phase1Tasks.addTask(new SimpleTask("Implementation"));

        // Add nested list to main list
        projectTasks.addTask(phase1Tasks);

        // Display all tasks hierarchically
        projectTasks.display();
    }
}


Output:

Project Tasks:
- Write code
- Prepare report
Phase 1 Tasks:
- Design
- Implementation
```

### Benefits:
- Simplifies client code by allowing uniform treatment of simple and complex elements.

- Makes it easier to add new kinds of components.

- Supports hierarchical tree structures naturally.

### Real-World Use Cases:
- GUI frameworks where UI elements contain other elements.

- Filesystem directory trees with files and folders.

- Organization charts with employees and departments.

**[Back To Creational Design Patterns](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/structural-design-pattern.md#structural-design-patterns)**