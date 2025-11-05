# Single Responsibility Principle
The single responsibility principle states that every Java class must perform a single functionality. 

Implementation of multiple functionalities in a single class mash up the code and, if any modification is required, may affect the whole class.

It precise the code and the code can be easily maintained.

e.g.:-
Suppose Main is a class having three methods, namely printDetails(), calculatePercentage(), and addStudent(). Hence, the Main class has three responsibilities: 
print the details of students, 
calculate percentages, 
and database. 

By using the single responsibility principle, we can separate these functionalities into three separate classes to fulfil the goal of the principle.

```java
public class Main {  
    // Method to print details  
    public void printDetails() {  
        System.out.println("Printing student details...");  
        // Add actual implementation here  
    }  
    // Method to calculate percentage  
    public void calculatePercentage() {  
        System.out.println("Calculating percentage...");  
        // Add actual implementation here  
    }  
    // Method to add a student  
    public void addStudent() {  
        System.out.println("Adding a new student...");  
        // Add actual implementation here  
    }  
    public static void main(String[] args) {  
        // Creating an object of the Main class  
        Main obj = new Main();  
        // Calling methods using the object  
        obj.addStudent();  
        obj.printDetails();  
        obj.calculatePercentage();  
    }  
}  
```

The above program violates the single responsibility principle. To achieve the goal, we should implement separate classes (as follows) that perform a single functionality only.

```java
Student.java

public class Student {    
public void addStudent(); {    
//functionality of the method    
}    
}  

PrintStudentDetails.java

public class PrintStudentDetails{    
public void printDetails();  {    
//functionality of the method    
}    
}  

Percentage.java

public class Percentage {    
public void calculatePercentage();  {    
//functionality of the method    
}    
} 
```

Hence, we have achieved the goal of the single responsibility principle by separating the functionality into three separate classes.

This separation enhances modularity, making each class easier to test, maintain, and evolve independently.

**[Back To SOLID Principle](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/java-design-pattern/solid-principle.md#solid-principle)**

