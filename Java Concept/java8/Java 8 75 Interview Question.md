# Java 8 Interview Questions and Answers

## 1. What is Java 8? 

Java 8 is a major release of the Java programming language that majorly changed the old style of programming by introducing several new features, such as, lambda expressions, functional interfaces, and streams.

## 2. What is a lambda expression? 

A lambda expression is a short way to express a function in Java. It allows us to write a function inline and pass it as an argument to another function as well.

## 3. What is a functional interface? 

A functional interface is an interface that contains exactly one abstract method. It is used to represent a single function contract.

## 4. What is a stream in Java 8? 

A stream is a sequence of elements that can be processed parallel or sequentially. Streams are a new addition to Java 8 and provide an easy way to work with collections.

## 5. What are the benefits of using streams? 

Streams provide a more concise and demonstrative way to work with collections. They also enable parallel processing of collections, which can lead to improved performance.

## 6. What is the difference between a parallel stream and a sequential stream in Java 8? 

A parallel stream allows for processing elements concurrently using multiple threads, while a sequential stream processes elements one-by-one in a single thread. To create a parallel stream, you can call the parallel() method on a stream.

## 7. What is the difference between a stream and a collection in Java 8? 

A stream is a sequence of elements that can be processed in parallel or sequentially, while a collection is a data structure that stores a group of elements. Additionally, Streams provide an easy way to work with Collections.

## 8. What are the common terminal operations on streams? 

Some common terminal operations on streams include forEach(), reduce(), collect(), min(), max(), findFirst(), findAny() and count() etc.

## 9. What is the difference between a terminal operation and an intermediate operation in a stream? 

An intermediate operation on a stream returns a new stream, while a terminal operation consumes the stream and produces a result.

## 10. What is the difference between a functional interface and a normal interface in Java 8? 

A functional interface contains only one abstract method, while a normal interface can contain any number of abstract methods.

## 11. What is a default method in Java 8? 

A default method is a method with the ‘default’ keyword that is defined in an interface and has a default implementation. It can be overridden by an implementing class if needed.

## 12. What is a static method in Java 8? 

A static method is a method with the ‘static’ keyword that is defined in a class and can be called without creating an instance of the class.

## 13. What is the syntax for a lambda expression in Java 8? 

The syntax for a lambda expression in Java 8 is:
(parameter list) -> expression

## 14. What is the difference between a lambda expression and an anonymous inner class in Java 8? 

A lambda expression is a concise way to express a function, while an anonymous inner class is a way to create a class without giving it a name.

## 15. What is a method reference in Java 8? 

A method reference is a shorthand way to write a lambda expression that calls a method. Method references can be used to simplify code and improve readability by eliminating the need for a separate lambda expression. For example, instead of using “x -> Math.sqrt(x)”, we can use “Math::sqrt” as a method reference.

## 16. What are the predefined functional interfaces in Java 8? 

Some common predefined functional interfaces in Java 8 include Function, Predicate, Consumer, and Supplier.

## 17. What is the Function interface in Java 8? 

The Function interface in Java 8 is a functional interface that takes an argument and returns a result.

## 18. What is the Predicate interface in Java 8? 

The Predicate interface in Java 8 is a functional interface that takes an argument and returns a Boolean result.

## 19. What is the Consumer interface in Java 8? 

The Consumer interface in Java 8 is a functional interface that takes an argument and returns no result.

## 20. What is the Supplier interface in Java 8? 

The Supplier interface in Java 8 is a functional interface that takes no argument and returns a result of a specified type.

## 21. What is the Optional class in Java 8? 

The Optional class in Java 8 is a container object that may or may not contain a value. It is used to avoid null pointer exceptions.

## 22. What is a CompletableFuture in Java 8? 

A CompletableFuture in Java 8 is a class that represents a task that will be completed in the future. It can be used for asynchronous programming.

## 23. What is the @FunctionalInterface annotation in Java 8? 

The @FunctionalInterface annotation in Java 8 is used to indicate that an interface is a functional interface.

## 24. What is the use of the map() method in Java 8 streams? 

The map() method in Java 8 streams is used to transform each element in a stream into a new element.

## 25. What is the use of the filter() method in Java 8 streams? 

The filter() method in Java 8 streams is used to filter out elements from a stream based on a specified condition.

## 26. What is the use of the reduce() method in Java 8 streams? 

The reduce() method in Java 8 streams is used to combine all the elements in a stream into a single result.

## 27. What is the use of the collect() method in Java 8 streams? 

The collect() method in Java 8 streams is used to collect the elements in a stream into a specified data structure.

## 28. What is the use of the flatMap() method in Java 8 streams? 

The flatMap() method in Java 8 streams is used to flatten a stream of streams into a single stream.

## 29. What is the use of the peek() method in Java 8 streams?

The peek() method in Java 8 streams is used to perform an operation on each element in a stream without modifying the stream.

## 30. What is the use of the sorted() method in Java 8 streams? 

The sorted() method in Java 8 streams is used to sort the elements in a stream.

## 31. What is the use of the distinct() method in Java 8 streams? 

The distinct() method in Java 8 streams is used to remove duplicate elements from a stream.

## 32. What is the use of the skip() method in Java 8 streams? The skip() method in Java 8 streams is used to skip a specified number of elements in a stream.

## 33. What is the use of the limit() method in Java 8 streams? 

The limit() method in Java 8 streams is used to limit the number of elements in a stream to a specified number.

## 34. What is the use of the parallel() method in Java 8 streams? 

The parallel() method in Java 8 streams is used to process the elements in a stream in parallel.

## 35. What is the use of the sequential() method in Java 8 streams? 

The sequential() method in Java 8 streams is used to process the elements in a stream in a sequential manner.

## 36. What is the use of the allMatch() method in Java 8 streams? 

The allMatch() method in Java 8 streams is used to check if all the elements in a stream satisfy a specified condition.

## 37. What is the use of the anyMatch() method in Java 8 streams? 

The anyMatch() method in Java 8 streams is used to check if any of the elements in a stream satisfy a specified condition.

## 38. What is the use of the noneMatch() method in Java 8 streams? 

The noneMatch() method in Java 8 streams is used to check if none of the elements in a stream satisfy a specified condition.

## 39. What is the use of the findFirst() method in Java 8 streams? 

The findFirst() method in Java 8 streams is used to return the first element in a stream that satisfies a specified condition.

## 40. What is the use of the findAny() method in Java 8 streams? 

The findAny() method in Java 8 streams is used to return any element in a stream that satisfies a specified condition.

## 41. What is the use of the count() method in Java 8 streams? 

The count() method in Java 8 streams is used to return the number of elements in a stream.

## 42. What is the use of the toArray() method in Java 8 streams? 

The toArray() method in Java 8 streams is used to convert a stream into an array.

## 43. What is the use of the parallelStream() method in Java 8?

The parallelStream() method in Java 8 is used to create a parallel stream.

## 44. What is the use of the sequentialStream() method in Java 8? 

The sequentialStream() method in Java 8 is used to create a sequential stream.

## 45. What is the use of the flatMapToInt() method in Java 8 streams? 

The flatMapToInt() method in Java 8 streams is used to flatten a stream of streams into a single stream of integers.

## 46. What is the use of the flatMapToLong() method in Java 8 streams? 

The flatMapToLong() method in Java 8 streams is used to flatten a stream of streams into a single stream of longs.

## 47. What is the use of the flatMapToDouble() method in Java 8 streams? 

The flatMapToDouble() method in Java 8 streams is used to flatten a stream of streams into a single stream of doubles.

## 48. Why was lambda expression introduced in Java 8? 

Lambda expressions were introduced in Java 8 to provide a concise and functional way of implementing interfaces with a single abstract method, also known as functional interfaces. Lambda expressions allow developers to write code that is more concise and expressive.

## 49. Why was the purpose of forEach() method added to the Iterable interface in Java 8? 

The forEach() method was added to the Iterable interface in Java 8 to provide a simple and concise way of iterating over collections. The forEach() method allows developers to write code that is more readable and expressive.

## 50. Why was the default method introduced in Java 8 interfaces? 

The default method was introduced in Java 8 interfaces to provide a way to add new methods to existing interfaces without breaking backwards compatibility. Default methods provide a way to extend the functionality of interfaces in a safe way.

## 51. Why was the Date and Time API introduced in Java 8? 

The Date and Time API was introduced in Java 8 to provide a more robust and flexible way of handling dates and times. The new API allows developers to handle dates and times in an easier way.

## 52. Why was the reduce() method added to the Stream interface in Java 8? 

The reduce() method was added to the Stream interface in Java 8 to provide a way of reducing a collection of data to a single value. The reduce() method allows developers to perform complex operations on data in a simple and efficient way.

## 53. Why was the parallel processing introduced in Java 8? 

Parallel processing was introduced in Java 8 to provide a way to take advantage of multi-core processors. Parallel processing allows developers to perform complex operations on data in a faster and more efficient way.

## 54. Why is the purpose of Spliterator interface in Java 8?

The Spliterator interface was introduced in Java 8 to provide a way to split a collection of data into smaller parts. The Spliterator interface allows developers to process large collections of data in a more efficient way.

## 55. Why is the purpose of BiFunction interface introduced in Java 8? 

The BiFunction interface was introduced in Java 8 to allow a way of passing two arguments at a time to a function and returning a result. The BiFunction interface allows developers to write code that is more

## 56. Why was the CompletableFuture class introduced in Java 8? 

The CompletableFuture class was introduced in Java 8 to provide a way of performing asynchronous operations. The CompletableFuture class allows developers to write code that is more responsive and efficient.

## 57. Why was the groupingBy() method added to the Collectors class in Java 8? 

The groupingBy() method was added to the Collectors class in Java 8 to provide a way of grouping elements based on a certain criteria. The groupingBy() method allows developers to process collections of data in a more flexible and efficient way.

## 58. Why was the toArray() method added to the Stream interface in Java 8? 

The toArray() method was added to the Stream interface in Java 8 to provide a way of converting a stream into an array. The toArray() method allows developers to process collections of data in a more flexible and efficient way.

## 59. Why is the java.util.function package important in Java 8? 

The java.util.Function package is important in Java 8 because it offers a flavor of functional programming as a set of functional interfaces that can be used with lambda expressions. The java.util.function package allows developers to write code that is more expressive and concise.

## 60. Why was the peek() method added to the Stream API in Java 8? 

The peek() method was added to the Stream API in Java 8 to allow developers to debug and understand their code more easily.

## 61. Why was the Optional class introduced in Java 8?

The Optional class was introduced in Java 8 to provide a way of handling null values in a more concise and expressive way. The Optional class allows developers to write code that is more robust and bug-free.

## 62. Why was the trySplit() method added to the Spliterator interface in Java 8? 

The trySplit() method was added to the Spliterator interface in Java 8 to provide a way of splitting a collection of data into two separate streams. The trySplit() method allows developers to write code that is more flexible and efficient.

## 63. Why was the min() and max() methods added to the Stream interface in Java 8? 

The min() and max() methods were added to the Stream interface in Java 8 to provide an easy way of finding the minimum and maximum values in a collection of data.

##  64. Why is the purpose of getOrDefault() method added to the Map interface in Java 8? 

The getOrDefault() method was added to the Map interface in Java 8 to provide a way of getting a value from a map with a default value if the key is not found.


## 65. Why was the computeIfAbsent() method added to the Map interface in Java 8? 

The computeIfAbsent() method was added to the Map interface in Java 8 to provide a way of getting a value from a map and computing a new value if the key is not found.

## 66. Why was the takeWhile() method added to the Stream interface in Java 8? 

The takeWhile() method was added to the Stream interface in Java 8 to provide a way of selecting elements from a stream until a certain condition is met.

## 67. Why was the dropWhile() method added to the Stream interface in Java 8? 

The dropWhile() method was added to the Stream interface in Java 8 to provide a way of selecting elements from a stream after a certain condition is met.

## 68. Why was the or() method added to the Predicate interface in Java 8? 

The or() method was added to the Predicate interface in Java 8 to provide a way of combining multiple predicates into a single predicate. It acts as a short-circuiting logical OR of this predicate and another.

## 69. Why was the and() method added to the Predicate interface in Java 8? 

The and() method was added to the Predicate interface in Java 8 to provide a way of combining multiple predicates into a single predicate. It acts as a short-circuiting logical AND of this predicate and another.

## 70. Why was the asDoubleStream() method added to the IntStream interface in Java 8? 

The asDoubleStream() method was added to the IntStream interface in Java 8 to provide a way of converting an IntStream to a DoubleStream.

## 71. Why was the asLongStream() method added to the IntStream interface in Java 8? 

The asLongStream() method was added to the IntStream interface in Java 8 to provide a way of converting an IntStream to a LongStream.

## 72. Why was the ofNullable() method added to the Optional class in Java 8? 

The ofNullable() method was added to the Optional class in Java 8 to provide a way of creating an Optional object with a null value. The ofNullable() method is used to get an instance of the Optional class with a specified value. If the value is null, then an empty Optional object is returned.

## 73. Why was the flatMapToInt() method added to the Stream interface in Java 8? 

The flatMapToInt() method was added to the Stream interface in Java 8 to provide a way of flattening a stream of objects to an IntStream.

## 74. Why was the toMap() method added to the Collectors class in Java 8? 

The toMap() method was added to the Collectors class in Java 8 to provide a way of collecting a stream of objects to a Map object.

## 75. Why was the of() method added to the Optional class in Java 8? 

The of() method was added to the Optional class in Java 8 to provide a way of creating an Optional object. It will return an Optional object containing the given value if the value is non-null, or an empty Optional object if the value is null.