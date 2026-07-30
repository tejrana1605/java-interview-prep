# Java 8 Interview Questions and Answers

## Table of Contents

- [Java 8 Interview Questions and Answers](#java-8-interview-questions-and-answers)
  - [1. What is Java 8?](#1-what-is-java-8)
  - [2. What is a lambda expression?](#2-what-is-a-lambda-expression)
  - [3. What is a functional interface?](#3-what-is-a-functional-interface)
  - [4. What is a stream in Java 8?](#4-what-is-a-stream-in-java-8)
  - [5. What are the benefits of using streams?](#5-what-are-the-benefits-of-using-streams)
  - [6. What is the difference between a parallel stream and a sequential stream in Java 8?](#6-what-is-the-difference-between-a-parallel-stream-and-a-sequential-stream-in-java-8)
  - [7. What is the difference between a stream and a collection in Java 8?](#7-what-is-the-difference-between-a-stream-and-a-collection-in-java-8)
  - [8. What are the common terminal operations on streams?](#8-what-are-the-common-terminal-operations-on-streams)
  - [9. What is the difference between a terminal operation and an intermediate operation in a stream?](#9-what-is-the-difference-between-a-terminal-operation-and-an-intermediate-operation-in-a-stream)
  - [10. What is the difference between a functional interface and a normal interface in Java 8?](#10-what-is-the-difference-between-a-functional-interface-and-a-normal-interface-in-java-8)
  - [11. What is a default method in Java 8?](#11-what-is-a-default-method-in-java-8)
  - [12. What is a static method in Java 8?](#12-what-is-a-static-method-in-java-8)
  - [13. What is the syntax for a lambda expression in Java 8?](#13-what-is-the-syntax-for-a-lambda-expression-in-java-8)
  - [14. What is the difference between a lambda expression and an anonymous inner class in Java 8?](#14-what-is-the-difference-between-a-lambda-expression-and-an-anonymous-inner-class-in-java-8)
  - [15. What is a method reference in Java 8?](#15-what-is-a-method-reference-in-java-8)
  - [16. What are the predefined functional interfaces in Java 8?](#16-what-are-the-predefined-functional-interfaces-in-java-8)
  - [17. What is the Function interface in Java 8?](#17-what-is-the-function-interface-in-java-8)
  - [18. What is the Predicate interface in Java 8?](#18-what-is-the-predicate-interface-in-java-8)
  - [19. What is the Consumer interface in Java 8?](#19-what-is-the-consumer-interface-in-java-8)
  - [20. What is the Supplier interface in Java 8?](#20-what-is-the-supplier-interface-in-java-8)
  - [21. What is the Optional class in Java 8?](#21-what-is-the-optional-class-in-java-8)
  - [22. What is a CompletableFuture in Java 8?](#22-what-is-a-completablefuture-in-java-8)
  - [23. What is the @FunctionalInterface annotation in Java 8?](#23-what-is-the-functionalinterface-annotation-in-java-8)
  - [24. What is the use of the map() method in Java 8 streams?](#24-what-is-the-use-of-the-map-method-in-java-8-streams)
  - [25. What is the use of the filter() method in Java 8 streams?](#25-what-is-the-use-of-the-filter-method-in-java-8-streams)
  - [26. What is the use of the reduce() method in Java 8 streams?](#26-what-is-the-use-of-the-reduce-method-in-java-8-streams)
  - [27. What is the use of the collect() method in Java 8 streams?](#27-what-is-the-use-of-the-collect-method-in-java-8-streams)
  - [28. What is the use of the flatMap() method in Java 8 streams?](#28-what-is-the-use-of-the-flatmap-method-in-java-8-streams)
  - [29. What is the use of the peek() method in Java 8 streams?](#29-what-is-the-use-of-the-peek-method-in-java-8-streams)
  - [30. What is the use of the sorted() method in Java 8 streams?](#30-what-is-the-use-of-the-sorted-method-in-java-8-streams)
  - [31. What is the use of the distinct() method in Java 8 streams?](#31-what-is-the-use-of-the-distinct-method-in-java-8-streams)
  - [32. What is the use of the skip() method in Java 8 streams? The skip() method in Java 8 streams is used to skip a specified number of elements in a stream.](#32-what-is-the-use-of-the-skip-method-in-java-8-streams-the-skip-method-in-java-8-streams-is-used-to-skip-a-specified-number-of-elements-in-a-stream)
  - [33. What is the use of the limit() method in Java 8 streams?](#33-what-is-the-use-of-the-limit-method-in-java-8-streams)
  - [34. What is the use of the parallel() method in Java 8 streams?](#34-what-is-the-use-of-the-parallel-method-in-java-8-streams)
  - [35. What is the use of the sequential() method in Java 8 streams?](#35-what-is-the-use-of-the-sequential-method-in-java-8-streams)
  - [36. What is the use of the allMatch() method in Java 8 streams?](#36-what-is-the-use-of-the-allmatch-method-in-java-8-streams)
  - [37. What is the use of the anyMatch() method in Java 8 streams?](#37-what-is-the-use-of-the-anymatch-method-in-java-8-streams)
  - [38. What is the use of the noneMatch() method in Java 8 streams?](#38-what-is-the-use-of-the-nonematch-method-in-java-8-streams)
  - [39. What is the use of the findFirst() method in Java 8 streams?](#39-what-is-the-use-of-the-findfirst-method-in-java-8-streams)
  - [40. What is the use of the findAny() method in Java 8 streams?](#40-what-is-the-use-of-the-findany-method-in-java-8-streams)
  - [41. What is the use of the count() method in Java 8 streams?](#41-what-is-the-use-of-the-count-method-in-java-8-streams)
  - [42. What is the use of the toArray() method in Java 8 streams?](#42-what-is-the-use-of-the-toarray-method-in-java-8-streams)
  - [43. What is the use of the parallelStream() method in Java 8?](#43-what-is-the-use-of-the-parallelstream-method-in-java-8)
  - [44. What is the use of the sequentialStream() method in Java 8?](#44-what-is-the-use-of-the-sequentialstream-method-in-java-8)
  - [45. What is the use of the flatMapToInt() method in Java 8 streams?](#45-what-is-the-use-of-the-flatmaptoint-method-in-java-8-streams)
  - [46. What is the use of the flatMapToLong() method in Java 8 streams?](#46-what-is-the-use-of-the-flatmaptolong-method-in-java-8-streams)
  - [47. What is the use of the flatMapToDouble() method in Java 8 streams?](#47-what-is-the-use-of-the-flatmaptodouble-method-in-java-8-streams)
  - [48. Why was lambda expression introduced in Java 8?](#48-why-was-lambda-expression-introduced-in-java-8)
  - [49. Why was the purpose of forEach() method added to the Iterable interface in Java 8?](#49-why-was-the-purpose-of-foreach-method-added-to-the-iterable-interface-in-java-8)
  - [50. Why was the default method introduced in Java 8 interfaces?](#50-why-was-the-default-method-introduced-in-java-8-interfaces)
  - [51. Why was the Date and Time API introduced in Java 8?](#51-why-was-the-date-and-time-api-introduced-in-java-8)
  - [52. Why was the reduce() method added to the Stream interface in Java 8?](#52-why-was-the-reduce-method-added-to-the-stream-interface-in-java-8)
  - [53. Why was the parallel processing introduced in Java 8?](#53-why-was-the-parallel-processing-introduced-in-java-8)
  - [54. Why is the purpose of Spliterator interface in Java 8?](#54-why-is-the-purpose-of-spliterator-interface-in-java-8)
  - [55. Why is the purpose of BiFunction interface introduced in Java 8?](#55-why-is-the-purpose-of-bifunction-interface-introduced-in-java-8)
  - [56. Why was the CompletableFuture class introduced in Java 8?](#56-why-was-the-completablefuture-class-introduced-in-java-8)
  - [57. Why was the groupingBy() method added to the Collectors class in Java 8?](#57-why-was-the-groupingby-method-added-to-the-collectors-class-in-java-8)
  - [58. Why was the toArray() method added to the Stream interface in Java 8?](#58-why-was-the-toarray-method-added-to-the-stream-interface-in-java-8)
  - [59. Why is the java.util.function package important in Java 8?](#59-why-is-the-javautilfunction-package-important-in-java-8)
  - [60. Why was the peek() method added to the Stream API in Java 8?](#60-why-was-the-peek-method-added-to-the-stream-api-in-java-8)
  - [61. Why was the Optional class introduced in Java 8?](#61-why-was-the-optional-class-introduced-in-java-8)
  - [62. Why was the trySplit() method added to the Spliterator interface in Java 8?](#62-why-was-the-trysplit-method-added-to-the-spliterator-interface-in-java-8)
  - [63. Why was the min() and max() methods added to the Stream interface in Java 8?](#63-why-was-the-min-and-max-methods-added-to-the-stream-interface-in-java-8)
  - [64. Why is the purpose of getOrDefault() method added to the Map interface in Java 8?](#64-why-is-the-purpose-of-getordefault-method-added-to-the-map-interface-in-java-8)
  - [65. Why was the computeIfAbsent() method added to the Map interface in Java 8?](#65-why-was-the-computeifabsent-method-added-to-the-map-interface-in-java-8)
  - [66. Why was the takeWhile() method added to the Stream interface in Java 8?](#66-why-was-the-takewhile-method-added-to-the-stream-interface-in-java-8)
  - [67. Why was the dropWhile() method added to the Stream interface in Java 8?](#67-why-was-the-dropwhile-method-added-to-the-stream-interface-in-java-8)
  - [68. Why was the or() method added to the Predicate interface in Java 8?](#68-why-was-the-or-method-added-to-the-predicate-interface-in-java-8)
  - [69. Why was the and() method added to the Predicate interface in Java 8?](#69-why-was-the-and-method-added-to-the-predicate-interface-in-java-8)
  - [70. Why was the asDoubleStream() method added to the IntStream interface in Java 8?](#70-why-was-the-asdoublestream-method-added-to-the-intstream-interface-in-java-8)
  - [71. Why was the asLongStream() method added to the IntStream interface in Java 8?](#71-why-was-the-aslongstream-method-added-to-the-intstream-interface-in-java-8)
  - [72. Why was the ofNullable() method added to the Optional class in Java 8?](#72-why-was-the-ofnullable-method-added-to-the-optional-class-in-java-8)
  - [73. Why was the flatMapToInt() method added to the Stream interface in Java 8?](#73-why-was-the-flatmaptoint-method-added-to-the-stream-interface-in-java-8)
  - [74. Why was the toMap() method added to the Collectors class in Java 8?](#74-why-was-the-tomap-method-added-to-the-collectors-class-in-java-8)
  - [75. Why was the of() method added to the Optional class in Java 8?](#75-why-was-the-of-method-added-to-the-optional-class-in-java-8)

---


[⬆ Back to top](#table-of-contents)

## 1. What is Java 8? 

Java 8 is a major release of the Java programming language that majorly changed the old style of programming by introducing several new features, such as, lambda expressions, functional interfaces, and streams.

[⬆ Back to top](#table-of-contents)

## 2. What is a lambda expression? 

A lambda expression is a short way to express a function in Java. It allows us to write a function inline and pass it as an argument to another function as well.

[⬆ Back to top](#table-of-contents)

## 3. What is a functional interface? 

A functional interface is an interface that contains exactly one abstract method. It is used to represent a single function contract.

[⬆ Back to top](#table-of-contents)

## 4. What is a stream in Java 8? 

A stream is a sequence of elements that can be processed parallel or sequentially. Streams are a new addition to Java 8 and provide an easy way to work with collections.

[⬆ Back to top](#table-of-contents)

## 5. What are the benefits of using streams? 

Streams provide a more concise and demonstrative way to work with collections. They also enable parallel processing of collections, which can lead to improved performance.

[⬆ Back to top](#table-of-contents)

## 6. What is the difference between a parallel stream and a sequential stream in Java 8? 

A parallel stream allows for processing elements concurrently using multiple threads, while a sequential stream processes elements one-by-one in a single thread. To create a parallel stream, you can call the parallel() method on a stream.

[⬆ Back to top](#table-of-contents)

## 7. What is the difference between a stream and a collection in Java 8? 

A stream is a sequence of elements that can be processed in parallel or sequentially, while a collection is a data structure that stores a group of elements. Additionally, Streams provide an easy way to work with Collections.

[⬆ Back to top](#table-of-contents)

## 8. What are the common terminal operations on streams? 

Some common terminal operations on streams include forEach(), reduce(), collect(), min(), max(), findFirst(), findAny() and count() etc.

[⬆ Back to top](#table-of-contents)

## 9. What is the difference between a terminal operation and an intermediate operation in a stream? 

An intermediate operation on a stream returns a new stream, while a terminal operation consumes the stream and produces a result.

[⬆ Back to top](#table-of-contents)

## 10. What is the difference between a functional interface and a normal interface in Java 8? 

A functional interface contains only one abstract method, while a normal interface can contain any number of abstract methods.

[⬆ Back to top](#table-of-contents)

## 11. What is a default method in Java 8? 

A default method is a method with the ‘default’ keyword that is defined in an interface and has a default implementation. It can be overridden by an implementing class if needed.

[⬆ Back to top](#table-of-contents)

## 12. What is a static method in Java 8? 

A static method is a method with the ‘static’ keyword that is defined in a class and can be called without creating an instance of the class.

[⬆ Back to top](#table-of-contents)

## 13. What is the syntax for a lambda expression in Java 8? 

The syntax for a lambda expression in Java 8 is:
(parameter list) -> expression

[⬆ Back to top](#table-of-contents)

## 14. What is the difference between a lambda expression and an anonymous inner class in Java 8? 

A lambda expression is a concise way to express a function, while an anonymous inner class is a way to create a class without giving it a name.

[⬆ Back to top](#table-of-contents)

## 15. What is a method reference in Java 8? 

A method reference is a shorthand way to write a lambda expression that calls a method. Method references can be used to simplify code and improve readability by eliminating the need for a separate lambda expression. For example, instead of using “x -> Math.sqrt(x)”, we can use “Math::sqrt” as a method reference.

[⬆ Back to top](#table-of-contents)

## 16. What are the predefined functional interfaces in Java 8? 

Some common predefined functional interfaces in Java 8 include Function, Predicate, Consumer, and Supplier.

[⬆ Back to top](#table-of-contents)

## 17. What is the Function interface in Java 8? 

The Function interface in Java 8 is a functional interface that takes an argument and returns a result.

[⬆ Back to top](#table-of-contents)

## 18. What is the Predicate interface in Java 8? 

The Predicate interface in Java 8 is a functional interface that takes an argument and returns a Boolean result.

[⬆ Back to top](#table-of-contents)

## 19. What is the Consumer interface in Java 8? 

The Consumer interface in Java 8 is a functional interface that takes an argument and returns no result.

[⬆ Back to top](#table-of-contents)

## 20. What is the Supplier interface in Java 8? 

The Supplier interface in Java 8 is a functional interface that takes no argument and returns a result of a specified type.

[⬆ Back to top](#table-of-contents)

## 21. What is the Optional class in Java 8? 

The Optional class in Java 8 is a container object that may or may not contain a value. It is used to avoid null pointer exceptions.

[⬆ Back to top](#table-of-contents)

## 22. What is a CompletableFuture in Java 8? 

A CompletableFuture in Java 8 is a class that represents a task that will be completed in the future. It can be used for asynchronous programming.

[⬆ Back to top](#table-of-contents)

## 23. What is the @FunctionalInterface annotation in Java 8? 

The @FunctionalInterface annotation in Java 8 is used to indicate that an interface is a functional interface.

[⬆ Back to top](#table-of-contents)

## 24. What is the use of the map() method in Java 8 streams? 

The map() method in Java 8 streams is used to transform each element in a stream into a new element.

[⬆ Back to top](#table-of-contents)

## 25. What is the use of the filter() method in Java 8 streams? 

The filter() method in Java 8 streams is used to filter out elements from a stream based on a specified condition.

[⬆ Back to top](#table-of-contents)

## 26. What is the use of the reduce() method in Java 8 streams? 

The reduce() method in Java 8 streams is used to combine all the elements in a stream into a single result.

[⬆ Back to top](#table-of-contents)

## 27. What is the use of the collect() method in Java 8 streams? 

The collect() method in Java 8 streams is used to collect the elements in a stream into a specified data structure.

[⬆ Back to top](#table-of-contents)

## 28. What is the use of the flatMap() method in Java 8 streams? 

The flatMap() method in Java 8 streams is used to flatten a stream of streams into a single stream.

[⬆ Back to top](#table-of-contents)

## 29. What is the use of the peek() method in Java 8 streams?

The peek() method in Java 8 streams is used to perform an operation on each element in a stream without modifying the stream.

[⬆ Back to top](#table-of-contents)

## 30. What is the use of the sorted() method in Java 8 streams? 

The sorted() method in Java 8 streams is used to sort the elements in a stream.

[⬆ Back to top](#table-of-contents)

## 31. What is the use of the distinct() method in Java 8 streams? 

The distinct() method in Java 8 streams is used to remove duplicate elements from a stream.

[⬆ Back to top](#table-of-contents)

## 32. What is the use of the skip() method in Java 8 streams? The skip() method in Java 8 streams is used to skip a specified number of elements in a stream.

[⬆ Back to top](#table-of-contents)

## 33. What is the use of the limit() method in Java 8 streams? 

The limit() method in Java 8 streams is used to limit the number of elements in a stream to a specified number.

[⬆ Back to top](#table-of-contents)

## 34. What is the use of the parallel() method in Java 8 streams? 

The parallel() method in Java 8 streams is used to process the elements in a stream in parallel.

[⬆ Back to top](#table-of-contents)

## 35. What is the use of the sequential() method in Java 8 streams? 

The sequential() method in Java 8 streams is used to process the elements in a stream in a sequential manner.

[⬆ Back to top](#table-of-contents)

## 36. What is the use of the allMatch() method in Java 8 streams? 

The allMatch() method in Java 8 streams is used to check if all the elements in a stream satisfy a specified condition.

[⬆ Back to top](#table-of-contents)

## 37. What is the use of the anyMatch() method in Java 8 streams? 

The anyMatch() method in Java 8 streams is used to check if any of the elements in a stream satisfy a specified condition.

[⬆ Back to top](#table-of-contents)

## 38. What is the use of the noneMatch() method in Java 8 streams? 

The noneMatch() method in Java 8 streams is used to check if none of the elements in a stream satisfy a specified condition.

[⬆ Back to top](#table-of-contents)

## 39. What is the use of the findFirst() method in Java 8 streams? 

The findFirst() method in Java 8 streams is used to return the first element in a stream that satisfies a specified condition.

[⬆ Back to top](#table-of-contents)

## 40. What is the use of the findAny() method in Java 8 streams? 

The findAny() method in Java 8 streams is used to return any element in a stream that satisfies a specified condition.

[⬆ Back to top](#table-of-contents)

## 41. What is the use of the count() method in Java 8 streams? 

The count() method in Java 8 streams is used to return the number of elements in a stream.

[⬆ Back to top](#table-of-contents)

## 42. What is the use of the toArray() method in Java 8 streams? 

The toArray() method in Java 8 streams is used to convert a stream into an array.

[⬆ Back to top](#table-of-contents)

## 43. What is the use of the parallelStream() method in Java 8?

The parallelStream() method in Java 8 is used to create a parallel stream.

[⬆ Back to top](#table-of-contents)

## 44. What is the use of the sequentialStream() method in Java 8? 

The sequentialStream() method in Java 8 is used to create a sequential stream.

[⬆ Back to top](#table-of-contents)

## 45. What is the use of the flatMapToInt() method in Java 8 streams? 

The flatMapToInt() method in Java 8 streams is used to flatten a stream of streams into a single stream of integers.

[⬆ Back to top](#table-of-contents)

## 46. What is the use of the flatMapToLong() method in Java 8 streams? 

The flatMapToLong() method in Java 8 streams is used to flatten a stream of streams into a single stream of longs.

[⬆ Back to top](#table-of-contents)

## 47. What is the use of the flatMapToDouble() method in Java 8 streams? 

The flatMapToDouble() method in Java 8 streams is used to flatten a stream of streams into a single stream of doubles.

[⬆ Back to top](#table-of-contents)

## 48. Why was lambda expression introduced in Java 8? 

Lambda expressions were introduced in Java 8 to provide a concise and functional way of implementing interfaces with a single abstract method, also known as functional interfaces. Lambda expressions allow developers to write code that is more concise and expressive.

[⬆ Back to top](#table-of-contents)

## 49. Why was the purpose of forEach() method added to the Iterable interface in Java 8? 

The forEach() method was added to the Iterable interface in Java 8 to provide a simple and concise way of iterating over collections. The forEach() method allows developers to write code that is more readable and expressive.

[⬆ Back to top](#table-of-contents)

## 50. Why was the default method introduced in Java 8 interfaces? 

The default method was introduced in Java 8 interfaces to provide a way to add new methods to existing interfaces without breaking backwards compatibility. Default methods provide a way to extend the functionality of interfaces in a safe way.

[⬆ Back to top](#table-of-contents)

## 51. Why was the Date and Time API introduced in Java 8? 

The Date and Time API was introduced in Java 8 to provide a more robust and flexible way of handling dates and times. The new API allows developers to handle dates and times in an easier way.

[⬆ Back to top](#table-of-contents)

## 52. Why was the reduce() method added to the Stream interface in Java 8? 

The reduce() method was added to the Stream interface in Java 8 to provide a way of reducing a collection of data to a single value. The reduce() method allows developers to perform complex operations on data in a simple and efficient way.

[⬆ Back to top](#table-of-contents)

## 53. Why was the parallel processing introduced in Java 8? 

Parallel processing was introduced in Java 8 to provide a way to take advantage of multi-core processors. Parallel processing allows developers to perform complex operations on data in a faster and more efficient way.

[⬆ Back to top](#table-of-contents)

## 54. Why is the purpose of Spliterator interface in Java 8?

The Spliterator interface was introduced in Java 8 to provide a way to split a collection of data into smaller parts. The Spliterator interface allows developers to process large collections of data in a more efficient way.

[⬆ Back to top](#table-of-contents)

## 55. Why is the purpose of BiFunction interface introduced in Java 8? 

The BiFunction interface was introduced in Java 8 to allow a way of passing two arguments at a time to a function and returning a result. The BiFunction interface allows developers to write code that is more

[⬆ Back to top](#table-of-contents)

## 56. Why was the CompletableFuture class introduced in Java 8? 

The CompletableFuture class was introduced in Java 8 to provide a way of performing asynchronous operations. The CompletableFuture class allows developers to write code that is more responsive and efficient.

[⬆ Back to top](#table-of-contents)

## 57. Why was the groupingBy() method added to the Collectors class in Java 8? 

The groupingBy() method was added to the Collectors class in Java 8 to provide a way of grouping elements based on a certain criteria. The groupingBy() method allows developers to process collections of data in a more flexible and efficient way.

[⬆ Back to top](#table-of-contents)

## 58. Why was the toArray() method added to the Stream interface in Java 8? 

The toArray() method was added to the Stream interface in Java 8 to provide a way of converting a stream into an array. The toArray() method allows developers to process collections of data in a more flexible and efficient way.

[⬆ Back to top](#table-of-contents)

## 59. Why is the java.util.function package important in Java 8? 

The java.util.Function package is important in Java 8 because it offers a flavor of functional programming as a set of functional interfaces that can be used with lambda expressions. The java.util.function package allows developers to write code that is more expressive and concise.

[⬆ Back to top](#table-of-contents)

## 60. Why was the peek() method added to the Stream API in Java 8? 

The peek() method was added to the Stream API in Java 8 to allow developers to debug and understand their code more easily.

[⬆ Back to top](#table-of-contents)

## 61. Why was the Optional class introduced in Java 8?

The Optional class was introduced in Java 8 to provide a way of handling null values in a more concise and expressive way. The Optional class allows developers to write code that is more robust and bug-free.

[⬆ Back to top](#table-of-contents)

## 62. Why was the trySplit() method added to the Spliterator interface in Java 8? 

The trySplit() method was added to the Spliterator interface in Java 8 to provide a way of splitting a collection of data into two separate streams. The trySplit() method allows developers to write code that is more flexible and efficient.

[⬆ Back to top](#table-of-contents)

## 63. Why was the min() and max() methods added to the Stream interface in Java 8? 

The min() and max() methods were added to the Stream interface in Java 8 to provide an easy way of finding the minimum and maximum values in a collection of data.

[⬆ Back to top](#table-of-contents)

##  64. Why is the purpose of getOrDefault() method added to the Map interface in Java 8? 

The getOrDefault() method was added to the Map interface in Java 8 to provide a way of getting a value from a map with a default value if the key is not found.


[⬆ Back to top](#table-of-contents)

## 65. Why was the computeIfAbsent() method added to the Map interface in Java 8? 

The computeIfAbsent() method was added to the Map interface in Java 8 to provide a way of getting a value from a map and computing a new value if the key is not found.

[⬆ Back to top](#table-of-contents)

## 66. Why was the takeWhile() method added to the Stream interface in Java 8? 

The takeWhile() method was added to the Stream interface in Java 8 to provide a way of selecting elements from a stream until a certain condition is met.

[⬆ Back to top](#table-of-contents)

## 67. Why was the dropWhile() method added to the Stream interface in Java 8? 

The dropWhile() method was added to the Stream interface in Java 8 to provide a way of selecting elements from a stream after a certain condition is met.

[⬆ Back to top](#table-of-contents)

## 68. Why was the or() method added to the Predicate interface in Java 8? 

The or() method was added to the Predicate interface in Java 8 to provide a way of combining multiple predicates into a single predicate. It acts as a short-circuiting logical OR of this predicate and another.

[⬆ Back to top](#table-of-contents)

## 69. Why was the and() method added to the Predicate interface in Java 8? 

The and() method was added to the Predicate interface in Java 8 to provide a way of combining multiple predicates into a single predicate. It acts as a short-circuiting logical AND of this predicate and another.

[⬆ Back to top](#table-of-contents)

## 70. Why was the asDoubleStream() method added to the IntStream interface in Java 8? 

The asDoubleStream() method was added to the IntStream interface in Java 8 to provide a way of converting an IntStream to a DoubleStream.

[⬆ Back to top](#table-of-contents)

## 71. Why was the asLongStream() method added to the IntStream interface in Java 8? 

The asLongStream() method was added to the IntStream interface in Java 8 to provide a way of converting an IntStream to a LongStream.

[⬆ Back to top](#table-of-contents)

## 72. Why was the ofNullable() method added to the Optional class in Java 8? 

The ofNullable() method was added to the Optional class in Java 8 to provide a way of creating an Optional object with a null value. The ofNullable() method is used to get an instance of the Optional class with a specified value. If the value is null, then an empty Optional object is returned.

[⬆ Back to top](#table-of-contents)

## 73. Why was the flatMapToInt() method added to the Stream interface in Java 8? 

The flatMapToInt() method was added to the Stream interface in Java 8 to provide a way of flattening a stream of objects to an IntStream.

[⬆ Back to top](#table-of-contents)

## 74. Why was the toMap() method added to the Collectors class in Java 8? 

The toMap() method was added to the Collectors class in Java 8 to provide a way of collecting a stream of objects to a Map object.

[⬆ Back to top](#table-of-contents)

## 75. Why was the of() method added to the Optional class in Java 8? 

The of() method was added to the Optional class in Java 8 to provide a way of creating an Optional object. It will return an Optional object containing the given value if the value is non-null, or an empty Optional object if the value is null.
[⬆ Back to top](#table-of-contents)
