# Generic Topics

Generics in Java, introduced in J2SE 5.0 to deal with type-safe objects, provide a way to define classes, interfaces, and methods with placeholders for types. This capability allows for the creation of flexible and reusable code components that work with different data types while maintaining type safety at compile time. It makes the code stable by detecting the bugs at compile time.

Before generics, we can store any type of objects in the collection, i.e., non-generic. Now generics force the Java programmer to store a specific type of objects.

1. [Why We Need Generics In Java?](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics.md#why-we-need-generics-in-java)
2. [Defining Generic Class](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generic-class.md#defining-generic-class)
3. [Rules To Follow While Implementing Generic Interfaces](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generic-interface.md#rules-to-follow-while-implementing-generic-interfaces)
4. [Can We Define Methods And Constructors As Generic?](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generic-methods-constructor.md#can-we-define-methods-and-constructors-as-generic?)
5. [What Are Bounded Types And Why They Are Used?](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generic-bounded-types.md#what-are-bounded-types-and-why-they-are-used?)
6. [What Are Wildcard Arguments In Java?](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generic-wildcard-arguments.md#what-are-wildcard-arguments-in-java?)
7. [Generics And Their Inheritance](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generic-interface.md#generics-and-their-inheritance)
8. [Type Erasure](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generic-type-eraser.md#type-erasure)

9. [Some Interesting Observations About Generics In Java](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generic-observation.md#some-interesting-observations-about-generics-in-java)

10. [Why Generics?](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-why.md#why-generics)

11. [Advantage of Java Generics](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-why.md#advantage-of-java-generics)

12. [Full Example of Generics in Java](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-why.md#full-example-of-generics-in-java)


13. [Example of Java Generics using Map](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-why.md#example-of-java-generics-using-map)


14. [Generic Class](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-why.md#generic-class)

15. [Creating a generic class](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-why.md#creating-a-generic-class)

16. [Using Generic Class](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-why.md#using-generic-class)

17. [Type Parameters](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#type-parameters)


18. [Wildcard in Java Generics](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#wildcard-in-java-generics)


19. [Upper Bounded Wildcards](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#wupper-bounded-wildcards)


20. [Example of Upper Bound Wildcard](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#example-of-upper-bound-wildcard)

21. [Unbounded Wildcards](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#unbounded-wildcards)


22. [Example of Unbounded Wildcards](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#example-of-unbounded-wildcards)


23. [Lower Bounded Wildcards](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#lower-bounded-wildcards)

24. [Example of Lower Bound Wildcard](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#example-of-lower-bound-wildcard)

25. [Disadvantages of Java Generics](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#disadvantages-of-java-generics)

26. [Complexity and Learning Curve](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#complexity-and-learning-curve)

27. [Restrictions and Limitations](https://github.com/tejrana1605/java-interview-prep/tree/main/Java%20Concept/generics/generics-type-parameters.md#restrictions-and-limitations)

