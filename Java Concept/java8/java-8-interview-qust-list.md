## Table of Contents

  - [**1. Functional Interfaces & Lambda Expressions**](#1-functional-interfaces-lambda-expressions)
  - [**2. Streams API**](#2-streams-api)
  - [**3. Optional Class**](#3-optional-class)
  - [**4. Default & Static Methods in Interfaces**](#4-default-static-methods-in-interfaces)
  - [**5. Method References**](#5-method-references)
  - [**6. Date & Time API (java.time Package)**](#6-date-time-api-javatime-package)
  - [**7. Parallel Streams**](#7-parallel-streams)
  - [**8. Collectors API**](#8-collectors-api)
  - [**9. CompletableFuture & Concurrency Enhancements**](#9-completablefuture-concurrency-enhancements)
  - [**10. Miscellaneous**](#10-miscellaneous)
- [Here are some **Java 8 programming interview questions** that require coding solutions:](#here-are-some-java-8-programming-interview-questions-that-require-coding-solutions)
  - [**1. Reverse a List Using Java 8 Streams**](#1-reverse-a-list-using-java-8-streams)
  - [**2. Find Duplicate Elements in a List**](#2-find-duplicate-elements-in-a-list)
  - [**3. Find the First Non-Repeating Character in a String**](#3-find-the-first-non-repeating-character-in-a-string)
  - [**4. Convert a List of Strings to Uppercase**](#4-convert-a-list-of-strings-to-uppercase)
  - [**5. Sum of Even Numbers in a List**](#5-sum-of-even-numbers-in-a-list)
  - [**6. Find the Second-Highest Number in a List**](#6-find-the-second-highest-number-in-a-list)
  - [**7. Count the Frequency of Each Character in a String**](#7-count-the-frequency-of-each-character-in-a-string)
  - [**8. Convert a List to a Map**](#8-convert-a-list-to-a-map)
  - [**9. Check if a String is a Palindrome**](#9-check-if-a-string-is-a-palindrome)
  - [**10. Find the Maximum Number in a List**](#10-find-the-maximum-number-in-a-list)
- [Here are some **complex Java 8 coding interview questions** that require advanced knowledge of **Streams, Lambdas, Optional, Collectors, Parallel Streams, and Functional Programming**. 🚀](#here-are-some-complex-java-8-coding-interview-questions-that-require-advanced-knowledge-of-streams-lambdas-optional-collectors-parallel-streams-and-functional-programming)
- [**1. Employee Salary Calculation (Grouping & Reduction)**](#1-employee-salary-calculation-grouping-reduction)
- [**2. Find the Longest Word in a Sentence**](#2-find-the-longest-word-in-a-sentence)
- [**3. Group Transactions by Currency and Sum Amounts**](#3-group-transactions-by-currency-and-sum-amounts)
- [**4. Find Kth Largest Element in a List**](#4-find-kth-largest-element-in-a-list)
- [**5. Convert Nested Lists into a Single Flattened List**](#5-convert-nested-lists-into-a-single-flattened-list)
- [**6. Find the Most Frequent Word in a List**](#6-find-the-most-frequent-word-in-a-list)
- [**7. Implement a Custom Comparator Using Lambda**](#7-implement-a-custom-comparator-using-lambda)
- [**8. Find the First Repeated Character in a String**](#8-find-the-first-repeated-character-in-a-string)
- [**9. Generate Fibonacci Series Using Stream API**](#9-generate-fibonacci-series-using-stream-api)
- [**10. Parallel Stream Performance Optimization**](#10-parallel-stream-performance-optimization)
- [Here is a **comprehensive list** of Java 8 **sorting interview questions**, covering different scenarios and techniques using **Streams, Lambdas, and Comparators**. 🚀](#here-is-a-comprehensive-list-of-java-8-sorting-interview-questions-covering-different-scenarios-and-techniques-using-streams-lambdas-and-comparators)
- [**1. Sort a List of Integers in Ascending and Descending Order**](#1-sort-a-list-of-integers-in-ascending-and-descending-order)
- [**2. Sort a List of Strings Alphabetically and by Length**](#2-sort-a-list-of-strings-alphabetically-and-by-length)
- [**3. Sort a List of Custom Objects (Sorting by Single Field)**](#3-sort-a-list-of-custom-objects-sorting-by-single-field)
- [**4. Sort a List of Custom Objects by Multiple Fields (Chained Sorting)**](#4-sort-a-list-of-custom-objects-by-multiple-fields-chained-sorting)
- [**5. Sort a List of Strings Ignoring Case Sensitivity**](#5-sort-a-list-of-strings-ignoring-case-sensitivity)
- [**6. Sort a Map by Keys and Values Using Java 8**](#6-sort-a-map-by-keys-and-values-using-java-8)
- [**7. Sort a List in Reverse Order Using Comparator.reverseOrder()**](#7-sort-a-list-in-reverse-order-using-comparatorreverseorder)
- [**8. Sort a List of Objects with Null Values (Null-Safe Sorting)**](#8-sort-a-list-of-objects-with-null-values-null-safe-sorting)
- [**9. Sort a List of Dates in Java 8**](#9-sort-a-list-of-dates-in-java-8)
- [**10. Sort a List Using Parallel Sorting (Efficient Sorting for Large Data)**](#10-sort-a-list-using-parallel-sorting-efficient-sorting-for-large-data)
- [**11. Custom Sorting Using a Comparator with Lambda**](#11-custom-sorting-using-a-comparator-with-lambda)
- [**12. Sort a List Using Stream.sorted() with Custom Comparator**](#12-sort-a-list-using-streamsorted-with-custom-comparator)
- [### **Java 8 `Optional` Class - Coding Interview Questions** 🚀](#java-8-optional-class---coding-interview-questions)
  - [**1. Convert a `String` to `Optional` and Handle Null Values**](#1-convert-a-string-to-optional-and-handle-null-values)
  - [**2. Use `Optional` to Avoid `NullPointerException`**](#2-use-optional-to-avoid-nullpointerexception)
  - [**3. Get Default Value Using `orElse()` and `orElseGet()`**](#3-get-default-value-using-orelse-and-orelseget)
  - [**4. Find Maximum Value in a List Using `Optional`**](#4-find-maximum-value-in-a-list-using-optional)
  - [**5. Check If a Value Exists Using `isPresent()`**](#5-check-if-a-value-exists-using-ispresent)
  - [**6. Use `Optional` with `filter()` to Check a Condition**](#6-use-optional-with-filter-to-check-a-condition)
  - [**7. Use `Optional` with `map()` and `flatMap()` for Nested Objects**](#7-use-optional-with-map-and-flatmap-for-nested-objects)
  - [**8. Use `orElseThrow()` to Throw an Exception if Value is Absent**](#8-use-orelsethrow-to-throw-an-exception-if-value-is-absent)
  - [**9. Find First Non-Empty `Optional` Using `Optional.ofNullable()`**](#9-find-first-non-empty-optional-using-optionalofnullable)
  - [**10. Use `Optional` in Streams to Avoid `NullPointerException`**](#10-use-optional-in-streams-to-avoid-nullpointerexception)
- [### **Java 8 Lambda Expressions - Coding Interview Questions** 🚀](#java-8-lambda-expressions---coding-interview-questions)
- [**1. Implement a Functional Interface Using Lambda**](#1-implement-a-functional-interface-using-lambda)
- [**2. Sort a List Using Lambda**](#2-sort-a-list-using-lambda)
- [**3. Find Even Numbers in a List Using Lambda & Streams**](#3-find-even-numbers-in-a-list-using-lambda-streams)
- [**4. Convert List of Strings to Uppercase Using Lambda**](#4-convert-list-of-strings-to-uppercase-using-lambda)
- [**5. Find the First Name That Starts with "A" Using Lambda**](#5-find-the-first-name-that-starts-with-a-using-lambda)
- [**6. Find the Sum of All Numbers in a List Using Lambda**](#6-find-the-sum-of-all-numbers-in-a-list-using-lambda)
- [**7. Implement Runnable Using Lambda**](#7-implement-runnable-using-lambda)
- [**8. Remove Null Values from a List Using Lambda**](#8-remove-null-values-from-a-list-using-lambda)
- [**9. Count Names That Start with "J" Using Lambda**](#9-count-names-that-start-with-j-using-lambda)
- [**10. Convert a List of Integers to a List of Strings Using Lambda**](#10-convert-a-list-of-integers-to-a-list-of-strings-using-lambda)
- [**11. Find the Maximum Value in a List Using Lambda**](#11-find-the-maximum-value-in-a-list-using-lambda)
- [**12. Find the Length of Each String in a List Using Lambda**](#12-find-the-length-of-each-string-in-a-list-using-lambda)
- [**13. Find Distinct Elements in a List Using Lambda**](#13-find-distinct-elements-in-a-list-using-lambda)
- [**14. Implement a Custom Comparator Using Lambda**](#14-implement-a-custom-comparator-using-lambda)
- [**15. Convert a Map to a List Using Lambda**](#15-convert-a-map-to-a-list-using-lambda)
- [### **Java 8 Functional Interface - Coding Interview Questions** 🚀](#java-8-functional-interface---coding-interview-questions)
- [**1. Create a Custom Functional Interface**](#1-create-a-custom-functional-interface)
- [**2. Use `Predicate` to Check If a Number is Even**](#2-use-predicate-to-check-if-a-number-is-even)
- [**3. Use `Function` to Convert String to Uppercase**](#3-use-function-to-convert-string-to-uppercase)
- [**4. Use `Consumer` to Print a List of Names**](#4-use-consumer-to-print-a-list-of-names)
- [**5. Use `Supplier` to Generate a Random Number**](#5-use-supplier-to-generate-a-random-number)
- [**6. Use `BiFunction` to Multiply Two Numbers**](#6-use-bifunction-to-multiply-two-numbers)
- [**7. Use `UnaryOperator` to Square a Number**](#7-use-unaryoperator-to-square-a-number)
- [**8. Use `BinaryOperator` for String Concatenation**](#8-use-binaryoperator-for-string-concatenation)
- [**9. Implement `Comparator` Using a Functional Interface**](#9-implement-comparator-using-a-functional-interface)
- [**10. Find Names Starting with "A" Using `Predicate`**](#10-find-names-starting-with-a-using-predicate)
- [**11. Chain `Predicate` Functions**](#11-chain-predicate-functions)
- [**12. Chain `Function` to Perform Two Operations**](#12-chain-function-to-perform-two-operations)
- [**13. Use `Consumer` to Log a Message Before Execution**](#13-use-consumer-to-log-a-message-before-execution)
- [**14. Use `BiPredicate` to Compare Two Numbers**](#14-use-bipredicate-to-compare-two-numbers)
- [**15. Implement Custom Functional Interface With Lambda**](#15-implement-custom-functional-interface-with-lambda)
- [### **Java 8 Streams - Coding Interview Questions** 🚀](#java-8-streams---coding-interview-questions)
- [**1. Find Even Numbers Using Streams**](#1-find-even-numbers-using-streams)
- [**2. Find the First Element Greater Than 10**](#2-find-the-first-element-greater-than-10)
- [**3. Find the Maximum Number in a List**](#3-find-the-maximum-number-in-a-list)
- [**4. Convert a List of Strings to Uppercase**](#4-convert-a-list-of-strings-to-uppercase-2)
- [**5. Sort a List of Strings in Descending Order**](#5-sort-a-list-of-strings-in-descending-order)
- [**6. Count the Number of Strings with Length Greater Than 4**](#6-count-the-number-of-strings-with-length-greater-than-4)
- [**7. Find the Sum of All Numbers in a List**](#7-find-the-sum-of-all-numbers-in-a-list)
- [**8. Find Distinct Elements in a List**](#8-find-distinct-elements-in-a-list)
- [**9. Find Names Starting with "J"**](#9-find-names-starting-with-j)
- [**10. Find the Average of a List of Numbers**](#10-find-the-average-of-a-list-of-numbers)
- [**11. Convert a List of Strings to a Single Comma-Separated String**](#11-convert-a-list-of-strings-to-a-single-comma-separated-string)
- [**12. Find the Second Largest Number in a List**](#12-find-the-second-largest-number-in-a-list)
- [**13. Convert a List of Objects to a List of Strings Using Streams**](#13-convert-a-list-of-objects-to-a-list-of-strings-using-streams)
- [**14. Find the First Non-Repeating Character in a String**](#14-find-the-first-non-repeating-character-in-a-string)
- [**15. Convert a Map to a List of Keys Using Streams**](#15-convert-a-map-to-a-list-of-keys-using-streams)
- [### **Java 8 Parallel Streams - Coding Interview Questions** 🚀](#java-8-parallel-streams---coding-interview-questions)
- [**1. Convert a List to Parallel Stream and Filter Even Numbers**](#1-convert-a-list-to-parallel-stream-and-filter-even-numbers)
- [**2. Find the Maximum Number Using Parallel Stream**](#2-find-the-maximum-number-using-parallel-stream)
- [**3. Sum of All Elements Using Parallel Stream**](#3-sum-of-all-elements-using-parallel-stream)
- [**4. Convert a List of Strings to Uppercase Using Parallel Stream**](#4-convert-a-list-of-strings-to-uppercase-using-parallel-stream)
- [**5. Sort a List in Parallel**](#5-sort-a-list-in-parallel)
- [**6. Find Distinct Elements Using Parallel Stream**](#6-find-distinct-elements-using-parallel-stream)
- [**7. Count Elements Greater Than 10 Using Parallel Stream**](#7-count-elements-greater-than-10-using-parallel-stream)
- [**8. Find the Average of a List of Numbers Using Parallel Stream**](#8-find-the-average-of-a-list-of-numbers-using-parallel-stream)
- [**9. Convert a List of Strings to a Single Comma-Separated String Using Parallel Stream**](#9-convert-a-list-of-strings-to-a-single-comma-separated-string-using-parallel-stream)
- [**10. Find the First Element Greater Than 50 Using Parallel Stream**](#10-find-the-first-element-greater-than-50-using-parallel-stream)
- [**11. Convert a List of Objects to a List of Names Using Parallel Stream**](#11-convert-a-list-of-objects-to-a-list-of-names-using-parallel-stream)
- [**12. Parallel Stream vs Sequential Stream Performance Test**](#12-parallel-stream-vs-sequential-stream-performance-test)
- [**13. Use `forEachOrdered` with Parallel Stream**](#13-use-foreachordered-with-parallel-stream)
- [**14. Convert a Map to a List of Values Using Parallel Stream**](#14-convert-a-map-to-a-list-of-values-using-parallel-stream)
- [**15. Apply a Function to Each Element and Collect Results Using Parallel Stream**](#15-apply-a-function-to-each-element-and-collect-results-using-parallel-stream)
- [### **Java 8 Parallel Streams - Coding Interview Questions** 🚀](#java-8-parallel-streams---coding-interview-questions-2)
- [**1. Convert a List to Parallel Stream and Filter Even Numbers**](#1-convert-a-list-to-parallel-stream-and-filter-even-numbers-2)
- [**2. Find the Maximum Number Using Parallel Stream**](#2-find-the-maximum-number-using-parallel-stream-2)
- [**3. Sum of All Elements Using Parallel Stream**](#3-sum-of-all-elements-using-parallel-stream-2)
- [**4. Convert a List of Strings to Uppercase Using Parallel Stream**](#4-convert-a-list-of-strings-to-uppercase-using-parallel-stream-2)
- [**5. Sort a List in Parallel**](#5-sort-a-list-in-parallel-2)
- [**6. Find Distinct Elements Using Parallel Stream**](#6-find-distinct-elements-using-parallel-stream-2)
- [**7. Count Elements Greater Than 10 Using Parallel Stream**](#7-count-elements-greater-than-10-using-parallel-stream-2)
- [**8. Find the Average of a List of Numbers Using Parallel Stream**](#8-find-the-average-of-a-list-of-numbers-using-parallel-stream-2)
- [**9. Convert a List of Strings to a Single Comma-Separated String Using Parallel Stream**](#9-convert-a-list-of-strings-to-a-single-comma-separated-string-using-parallel-stream-2)
- [**10. Find the First Element Greater Than 50 Using Parallel Stream**](#10-find-the-first-element-greater-than-50-using-parallel-stream-2)
- [**11. Convert a List of Objects to a List of Names Using Parallel Stream**](#11-convert-a-list-of-objects-to-a-list-of-names-using-parallel-stream-2)
- [**12. Parallel Stream vs Sequential Stream Performance Test**](#12-parallel-stream-vs-sequential-stream-performance-test-2)
- [**13. Use `forEachOrdered` with Parallel Stream**](#13-use-foreachordered-with-parallel-stream-2)
- [**14. Convert a Map to a List of Values Using Parallel Stream**](#14-convert-a-map-to-a-list-of-values-using-parallel-stream-2)
- [**15. Apply a Function to Each Element and Collect Results Using Parallel Stream**](#15-apply-a-function-to-each-element-and-collect-results-using-parallel-stream-2)
- [### **Java 8 `map()` Method - Interview Questions** 🚀](#java-8-map-method---interview-questions)
  - [**1. Convert a List of Integers to Their Squares**](#1-convert-a-list-of-integers-to-their-squares)
  - [**2. Convert a List of Strings to Uppercase**](#2-convert-a-list-of-strings-to-uppercase)
  - [**3. Extract Name from a List of Objects**](#3-extract-name-from-a-list-of-objects)
  - [**4. Convert a List of Strings to Their Lengths**](#4-convert-a-list-of-strings-to-their-lengths)
  - [**5. Convert a List of Integers to a List of Their Double Values**](#5-convert-a-list-of-integers-to-a-list-of-their-double-values)
  - [**6. Convert a List of Prices from INR to USD (Assume 1 INR = 0.012 USD)**](#6-convert-a-list-of-prices-from-inr-to-usd-assume-1-inr-0012-usd)
  - [**7. Convert a List of Strings to a List of First Characters**](#7-convert-a-list-of-strings-to-a-list-of-first-characters)
  - [**8. Extract Domain Names from Email Addresses**](#8-extract-domain-names-from-email-addresses)
  - [**9. Convert a Map to a List of Values Using `map()`**](#9-convert-a-map-to-a-list-of-values-using-map)
  - [**10. Convert a List of Dates to a List of Formatted Strings**](#10-convert-a-list-of-dates-to-a-list-of-formatted-strings)
  - [**11. Find the Square Root of Numbers Using `map()`**](#11-find-the-square-root-of-numbers-using-map)
  - [**12. Convert a List of Strings to a List of Integers**](#12-convert-a-list-of-strings-to-a-list-of-integers)
  - [**13. Extract File Extensions from a List of Filenames**](#13-extract-file-extensions-from-a-list-of-filenames)
  - [**14. Find the ASCII Values of Characters Using `map()`**](#14-find-the-ascii-values-of-characters-using-map)
  - [**15. Handle Null Values Safely Using `Optional.map()`**](#15-handle-null-values-safely-using-optionalmap)
- [### **Java 8 `flatMap()` - Interview Questions** 🚀](#java-8-flatmap---interview-questions)
- [**1. Difference Between `map()` and `flatMap()`**](#1-difference-between-map-and-flatmap)
- [**2. Flatten a List of Lists Using `flatMap()`**](#2-flatten-a-list-of-lists-using-flatmap)
- [**3. Convert a List of Strings to a List of Characters Using `flatMap()`**](#3-convert-a-list-of-strings-to-a-list-of-characters-using-flatmap)
- [**4. Flatten a List of Sentences Into a List of Words**](#4-flatten-a-list-of-sentences-into-a-list-of-words)
- [**5. Extract All Unique Words from a List of Sentences Using `flatMap()`**](#5-extract-all-unique-words-from-a-list-of-sentences-using-flatmap)
- [**6. Extract Phone Numbers from a List of Users Using `flatMap()`**](#6-extract-phone-numbers-from-a-list-of-users-using-flatmap)
- [**7. Convert a List of `Optional<String>` to a List of Strings Using `flatMap()`**](#7-convert-a-list-of-optionalstring-to-a-list-of-strings-using-flatmap)
- [**8. Flatten a List of `Optional<Integer>` Values Using `flatMap()`**](#8-flatten-a-list-of-optionalinteger-values-using-flatmap)
- [**9. Flatten a List of Employee Departments into a Single List Using `flatMap()`**](#9-flatten-a-list-of-employee-departments-into-a-single-list-using-flatmap)
- [**10. Flatten a Stream of Lists Using `flatMap()`**](#10-flatten-a-stream-of-lists-using-flatmap)
- [**11. Find All Unique Characters in a List of Words Using `flatMap()`**](#11-find-all-unique-characters-in-a-list-of-words-using-flatmap)
- [**12. Convert a List of Arrays to a Single Flattened List Using `flatMap()`**](#12-convert-a-list-of-arrays-to-a-single-flattened-list-using-flatmap)
- [### **Java 8 Functional Interfaces Supporting Primitive Types - Interview Questions** 🚀](#java-8-functional-interfaces-supporting-primitive-types---interview-questions)
- [**1. Find the Square of an Integer Using `IntFunction<R>`**](#1-find-the-square-of-an-integer-using-intfunctionr)
- [**2. Convert an Integer to a String Using `IntFunction<String>`**](#2-convert-an-integer-to-a-string-using-intfunctionstring)
- [**3. Print a List of Integers Using `IntConsumer`**](#3-print-a-list-of-integers-using-intconsumer)
- [**4. Check If a Number Is Even Using `IntPredicate`**](#4-check-if-a-number-is-even-using-intpredicate)
- [**5. Generate a Random Number Using `IntSupplier`**](#5-generate-a-random-number-using-intsupplier)
- [**6. Double a Given Number Using `IntUnaryOperator`**](#6-double-a-given-number-using-intunaryoperator)
- [**7. Find the Sum of Two Numbers Using `IntBinaryOperator`**](#7-find-the-sum-of-two-numbers-using-intbinaryoperator)
- [**8. Find Maximum of Two Long Numbers Using `LongBinaryOperator`**](#8-find-maximum-of-two-long-numbers-using-longbinaryoperator)
- [**9. Convert a Double Value to a String Using `DoubleFunction<String>`**](#9-convert-a-double-value-to-a-string-using-doublefunctionstring)
- [**10. Filter Even Numbers from a List Using `IntPredicate`**](#10-filter-even-numbers-from-a-list-using-intpredicate)
- [**11. Find Factorial of a Number Using `IntUnaryOperator`**](#11-find-factorial-of-a-number-using-intunaryoperator)
- [**12. Check If a Number Is Prime Using `IntPredicate`**](#12-check-if-a-number-is-prime-using-intpredicate)
- [**13. Convert a List of Integers to Their Squares Using `IntFunction<List<Integer>>`**](#13-convert-a-list-of-integers-to-their-squares-using-intfunctionlistinteger)
- [**14. Find the Sum of an Array Using `IntBinaryOperator`**](#14-find-the-sum-of-an-array-using-intbinaryoperator)
- [**15. Generate Fibonacci Sequence Using `IntSupplier`**](#15-generate-fibonacci-sequence-using-intsupplier)
- [### **Avoiding Boxing and Unboxing with Java 8 Functional Interfaces for Primitives** 🚀](#avoiding-boxing-and-unboxing-with-java-8-functional-interfaces-for-primitives)
    - [🔹 **What Is Boxing and Unboxing?**](#what-is-boxing-and-unboxing)
    - [🔹 **Why Is Boxing/Unboxing a Problem?**](#why-is-boxingunboxing-a-problem)
- [**💡 How Do Primitive Functional Interfaces Help?**](#how-do-primitive-functional-interfaces-help)
  - [**🚀 Example: Without Primitive Functional Interface (Boxing & Unboxing Overhead)**](#example-without-primitive-functional-interface-boxing-unboxing-overhead)
    - [❌ **Using `Function<Integer, Integer>` (Causes Boxing & Unboxing)**](#using-functioninteger-integer-causes-boxing-unboxing)
  - [**🔴 Problem in Above Code**](#problem-in-above-code)
  - [**✅ Optimized Code Using `IntFunction<R>` (Avoids Boxing & Unboxing)**](#optimized-code-using-intfunctionr-avoids-boxing-unboxing)
  - [**🔵 Why This Is Better?**](#why-this-is-better)
- [**✅ Functional Interfaces for Primitives and Their Benefits**](#functional-interfaces-for-primitives-and-their-benefits)
- [**🚀 More Examples of Avoiding Boxing/Unboxing**](#more-examples-of-avoiding-boxingunboxing)
  - [**1️⃣ Find Square of a Number Using `IntUnaryOperator` (No Boxing)**](#1-find-square-of-a-number-using-intunaryoperator-no-boxing)
  - [**2️⃣ Print a List of Integers Using `IntConsumer` (No Boxing)**](#2-print-a-list-of-integers-using-intconsumer-no-boxing)
  - [**3️⃣ Filter Even Numbers from a List Using `IntPredicate` (No Boxing)**](#3-filter-even-numbers-from-a-list-using-intpredicate-no-boxing)
- [**🔥 Key Takeaways**](#key-takeaways)
  - [**🔴 Without Primitive Functional Interface (Causes Boxing & Unboxing)**](#without-primitive-functional-interface-causes-boxing-unboxing)
  - [**✅ Using `IntUnaryOperator` (Avoids Boxing & Unboxing)**](#using-intunaryoperator-avoids-boxing-unboxing)
- [### **Java 8 Default Method - Coding Interview Questions** 🚀](#java-8-default-method---coding-interview-questions)
  - [**1️⃣ Define and Use a Default Method in an Interface**](#1-define-and-use-a-default-method-in-an-interface)
  - [**2️⃣ Override a Default Method in a Class**](#2-override-a-default-method-in-a-class)
  - [**3️⃣ Multiple Interfaces with Same Default Method - How to Resolve Conflict?**](#3-multiple-interfaces-with-same-default-method---how-to-resolve-conflict)
  - [**4️⃣ Call a Default Method from a Subclass**](#4-call-a-default-method-from-a-subclass)
  - [**5️⃣ Use a Default Method in Functional Interface**](#5-use-a-default-method-in-functional-interface)
  - [**6️⃣ Modify a Default Method in a Sub-interface**](#6-modify-a-default-method-in-a-sub-interface)
  - [**7️⃣ Using Default Method in Java 8 Streams**](#7-using-default-method-in-java-8-streams)
  - [**8️⃣ Prevent a Class from Using a Default Method**](#8-prevent-a-class-from-using-a-default-method)
  - [**9️⃣ Default Methods in Multiple Inheritance**](#9-default-methods-in-multiple-inheritance)
  - [**🔟 Default Methods and Static Methods in an Interface**](#default-methods-and-static-methods-in-an-interface)
- [**🔥 Summary of Java 8 Default Methods Concepts:**](#summary-of-java-8-default-methods-concepts)
- [### **Java 8 Default Method - Scenario-Based Interview Questions** 🚀](#java-8-default-method---scenario-based-interview-questions)
- [**🔹 Scenario 1: Adding New Features to an Existing Interface Without Breaking Old Code**](#scenario-1-adding-new-features-to-an-existing-interface-without-breaking-old-code)
- [**🔹 Scenario 2: Resolving Conflict When Implementing Multiple Interfaces with Same Default Method**](#scenario-2-resolving-conflict-when-implementing-multiple-interfaces-with-same-default-method)
- [**🔹 Scenario 3: Calling Default Methods from Implementing Class**](#scenario-3-calling-default-methods-from-implementing-class)
- [**🔹 Scenario 4: Default Method in a Functional Interface**](#scenario-4-default-method-in-a-functional-interface)
- [**🔹 Scenario 5: Overriding a Default Method in a Sub-interface**](#scenario-5-overriding-a-default-method-in-a-sub-interface)
- [**🔹 Scenario 6: Preventing a Class from Using a Default Method**](#scenario-6-preventing-a-class-from-using-a-default-method)
- [**🔹 Scenario 7: Superclass vs. Interface Default Method Conflict**](#scenario-7-superclass-vs-interface-default-method-conflict)
- [**🔹 Scenario 8: Using Default Methods in Java 8 Streams**](#scenario-8-using-default-methods-in-java-8-streams)
- [**🔹 Scenario 9: Static vs. Default Methods in Interfaces**](#scenario-9-static-vs-default-methods-in-interfaces)
- [**🔹 Scenario 10: Can Default Methods Call Other Abstract Methods?**](#scenario-10-can-default-methods-call-other-abstract-methods)
- [**🔥 Key Takeaways on Java 8 Default Methods:**](#key-takeaways-on-java-8-default-methods)
- [### **Java 8 `reduce()` - Counting, Average, Max & Min in Streams** 🚀](#java-8-reduce---counting-average-max-min-in-streams)
- [**🔹 1. Counting Elements Using `reduce()`**](#1-counting-elements-using-reduce)
  - [**✅ Solution:**](#solution)
- [**🔹 2. Calculating Average Using `reduce()`**](#2-calculating-average-using-reduce)
  - [**✅ Solution:**](#solution-2)
- [**🔹 3. Finding Maximum Using `reduce()`**](#3-finding-maximum-using-reduce)
  - [**✅ Solution:**](#solution-3)
- [**🔹 4. Finding Minimum Using `reduce()`**](#4-finding-minimum-using-reduce)
  - [**✅ Solution:**](#solution-4)
- [**🔹 5. Sum of Numbers Using `reduce()`**](#5-sum-of-numbers-using-reduce)
  - [**✅ Solution:**](#solution-5)
- [**🔹 6. Finding Product of Elements Using `reduce()`**](#6-finding-product-of-elements-using-reduce)
  - [**✅ Solution:**](#solution-6)
- [**🔹 7. Concatenating Strings Using `reduce()`**](#7-concatenating-strings-using-reduce)
  - [**✅ Solution:**](#solution-7)
- [**🔥 Summary**](#summary)
- [### **Java 8 `Collector` Interface – All Functions Explained with Examples** 🚀](#java-8-collector-interface-all-functions-explained-with-examples)
    - [✅ **Key Collector Functions:**](#key-collector-functions)
- [**1️⃣ Using `Collectors.toList()` – Convert Stream to List**](#1-using-collectorstolist-convert-stream-to-list)
- [**2️⃣ Using `Collectors.toSet()` – Convert Stream to Set**](#2-using-collectorstoset-convert-stream-to-set)
- [**3️⃣ Using `Collectors.toMap()` – Convert Stream to Map**](#3-using-collectorstomap-convert-stream-to-map)
- [**4️⃣ Using `Collectors.joining()` – Concatenating Strings**](#4-using-collectorsjoining-concatenating-strings)
- [**5️⃣ Using `Collectors.summarizingInt()` – Summary Statistics**](#5-using-collectorssummarizingint-summary-statistics)
- [**6️⃣ Using `Collectors.partitioningBy()` – Partition Data**](#6-using-collectorspartitioningby-partition-data)
- [**7️⃣ Using `Collectors.groupingBy()` – Group Data**](#7-using-collectorsgroupingby-group-data)
- [**8️⃣ Using `Collectors.counting()` – Count Elements**](#8-using-collectorscounting-count-elements)
- [**🔥 Summary: Collectors Functions**](#summary-collectors-functions)
- [### **Java `Collector` Interface - Four Core Functions Explained** 🚀](#java-collector-interface---four-core-functions-explained)
- [**1️⃣ `supplier()` – Creates a New Container**](#1-supplier-creates-a-new-container)
  - [**Example: Creating a `List`**](#example-creating-a-list)
- [**2️⃣ `accumulator()` – Adds Elements to the Container**](#2-accumulator-adds-elements-to-the-container)
  - [**Example: Adding Elements to a `List`**](#example-adding-elements-to-a-list)
- [**3️⃣ `combiner()` – Merges Two Partial Results**](#3-combiner-merges-two-partial-results)
  - [**Example: Merging Two Lists**](#example-merging-two-lists)
- [**4️⃣ `finisher()` – Transforms the Result (Optional)**](#4-finisher-transforms-the-result-optional)
  - [**Example: Returning an Unmodifiable List**](#example-returning-an-unmodifiable-list)
- [**📌 Example: Custom Collector Using All Four Functions**](#example-custom-collector-using-all-four-functions)
  - [**✅ Solution:**](#solution-8)
- [**🔥 Summary Table**](#summary-table)
- [### **`Stream.of(T t)` - Creating a Stream with a Single Element** 🚀](#streamoft-t---creating-a-stream-with-a-single-element)
- [**📌 Syntax**](#syntax)
- [**✅ Example 1: Creating a Single-Element Stream**](#example-1-creating-a-single-element-stream)
  - [**📝 Output:**](#output)
- [**✅ Example 2: Applying Stream Operations on a Single Element**](#example-2-applying-stream-operations-on-a-single-element)
  - [**📝 Output:**](#output-2)
- [**✅ Example 3: Using `Stream.of()` with `Optional`**](#example-3-using-streamof-with-optional)
  - [**📝 Output:**](#output-3)
- [**🔥 Key Takeaways**](#key-takeaways-2)
- [### **`Stream.of(Optional<T>.get())` - Explanation with Example** 🚀](#streamofoptionaltget---explanation-with-example)
  - [**⚠️ Important Warning:**](#important-warning)
- [**❌ Incorrect Approach: Using `Optional.get()` Directly**](#incorrect-approach-using-optionalget-directly)
  - [**🛑 Output (Exception)**](#output-exception)
- [**✅ Correct Approach: Using `Optional.orElse()`**](#correct-approach-using-optionalorelse)
  - [**📝 Output:**](#output-4)
- [**✅ Best Approach: Using `optional.stream()` (Preferred)**](#best-approach-using-optionalstream-preferred)
  - [**📝 Output:**](#output-5)
  - [**🔥 Key Takeaways**](#key-takeaways-3)
  - [**🚀 Final Recommendation:** **Always use `optional.stream()` instead of `Stream.of(optional.get())` for safe and functional programming in Java 8+!**](#final-recommendation-always-use-optionalstream-instead-of-streamofoptionalget-for-safe-and-functional-programming-in-java-8)
- [### **`Collectors.toCollection()` - Explanation with Examples** 🚀](#collectorstocollection---explanation-with-examples)
- [**📌 Syntax**](#syntax-2)
- [**✅ 1. Collecting Elements into an `ArrayList`**](#1-collecting-elements-into-an-arraylist)
- [**✅ 2. Collecting Elements into a `LinkedList`**](#2-collecting-elements-into-a-linkedlist)
- [**✅ 3. Collecting Elements into a `HashSet`**](#3-collecting-elements-into-a-hashset)
- [**✅ 4. Collecting Elements into a `TreeSet` (Sorted Order)**](#4-collecting-elements-into-a-treeset-sorted-order)
- [**✅ 5. Collecting Elements into a `LinkedHashSet` (Maintains Insertion Order)**](#5-collecting-elements-into-a-linkedhashset-maintains-insertion-order)
- [**✅ 6. Collecting Elements into a `PriorityQueue`**](#6-collecting-elements-into-a-priorityqueue)
- [**⚠️ Can We Use `Collectors.toCollection()` to Collect into a `Map`?**](#can-we-use-collectorstocollection-to-collect-into-a-map)
- [**🔥 Summary Table of `Collectors.toCollection()` Usage**](#summary-table-of-collectorstocollection-usage)
- [**🎯 Key Takeaways**](#key-takeaways-4)
- [**`Comparator` Class Utility Methods in Java (Up to Java 8)** 🚀](#comparator-class-utility-methods-in-java-up-to-java-8)
- [**✅ 1. `comparing()` - Creates a Comparator for an Object Field**](#1-comparing---creates-a-comparator-for-an-object-field)
- [**✅ 2. `comparingInt()`, `comparingLong()`, `comparingDouble()` - Primitive Comparisons**](#2-comparingint-comparinglong-comparingdouble---primitive-comparisons)
- [**✅ 3. `thenComparing()` - Secondary Sorting**](#3-thencomparing---secondary-sorting)
- [**✅ 4. `reverseOrder()` - Reverse Natural Ordering**](#4-reverseorder---reverse-natural-ordering)
- [**✅ 5. `naturalOrder()` - Sorting in Ascending Order**](#5-naturalorder---sorting-in-ascending-order)
- [**✅ 6. `nullsFirst()` & `nullsLast()` - Handling `null` Values**](#6-nullsfirst-nullslast---handling-null-values)
- [**🔥 Summary Table**](#summary-table-2)
- [**🎯 Key Takeaways**](#key-takeaways-5)
- [**`Comparator.naturalOrder()`**](#comparatornaturalorder)
- [**`Comparator.reverseOrder()`**](#comparatorreverseorder)
- [**🚀 Key Differences**](#key-differences)
- [**🎯 Key Takeaways**](#key-takeaways-6)
  - [**Java 8 `Collectors` Class - All Utility Methods with Examples** 🚀](#java-8-collectors-class---all-utility-methods-with-examples)
- [**📌 1. Collecting into a List, Set, or Map**](#1-collecting-into-a-list-set-or-map)
  - [**✅ `toList()` - Collects Elements into a List**](#tolist---collects-elements-into-a-list)
  - [**✅ `toSet()` - Collects Elements into a Set**](#toset---collects-elements-into-a-set)
  - [**✅ `toMap()` - Collects Elements into a Map**](#tomap---collects-elements-into-a-map)
- [**📌 2. Grouping and Partitioning**](#2-grouping-and-partitioning)
  - [**✅ `groupingBy()` - Groups Elements by a Key**](#groupingby---groups-elements-by-a-key)
  - [**✅ `partitioningBy()` - Splits Data into Two Groups (Boolean Predicate)**](#partitioningby---splits-data-into-two-groups-boolean-predicate)
- [**📌 3. Reducing and Summarizing**](#3-reducing-and-summarizing)
  - [**✅ `counting()` - Counts the Number of Elements**](#counting---counts-the-number-of-elements)
  - [**✅ `summarizingInt()` / `summarizingDouble()` / `summarizingLong()` - Summary Statistics**](#summarizingint-summarizingdouble-summarizinglong---summary-statistics)
  - [**✅ `reducing()` - Custom Reduction**](#reducing---custom-reduction)
- [**📌 4. Joining Strings**](#4-joining-strings)
  - [**✅ `joining()` - Concatenates Strings**](#joining---concatenates-strings)
- [**📌 5. Mapping & Collecting**](#5-mapping-collecting)
  - [**✅ `mapping()` - Transforms Elements Before Collecting**](#mapping---transforms-elements-before-collecting)
- [**📌 6. Collecting into Custom Collections**](#6-collecting-into-custom-collections)
  - [**✅ `toCollection()` - Collecting into a Specific Collection Type**](#tocollection---collecting-into-a-specific-collection-type)
- [**📌 Summary Table**](#summary-table-3)
- [**🔥 Key Takeaways**](#key-takeaways-7)
- [**`Collectors.collectingAndThen()` - Java 8 Explained with Examples** 🚀](#collectorscollectingandthen---java-8-explained-with-examples)
  - [**📌 What is `collectingAndThen()`?**](#what-is-collectingandthen)
  - [**📌 Method Signature:**](#method-signature)
  - [**📌 Key Points:**](#key-points)
- [**1️⃣ Example: Collect List and Make it Immutable**](#1-example-collect-list-and-make-it-immutable)
  - [✅ **Use Case: Prevent Modification After Collection**](#use-case-prevent-modification-after-collection)
- [**2️⃣ Example: Get Maximum Value Using CollectingAndThen**](#2-example-get-maximum-value-using-collectingandthen)
  - [✅ **Use Case: Find Maximum Element Using a Comparator**](#use-case-find-maximum-element-using-a-comparator)
- [**3️⃣ Example: Counting Elements and Converting to String**](#3-example-counting-elements-and-converting-to-string)
  - [✅ **Use Case: Get Number of Elements as String**](#use-case-get-number-of-elements-as-string)
- [**4️⃣ Example: Collect into a Custom Collection**](#4-example-collect-into-a-custom-collection)
  - [✅ **Use Case: Collect as `TreeSet` (Sorted Order)**](#use-case-collect-as-treeset-sorted-order)
- [**5️⃣ Example: Convert List to Comma-Separated String**](#5-example-convert-list-to-comma-separated-string)
  - [✅ **Use Case: Format List as a String**](#use-case-format-list-as-a-string)
- [**6️⃣ Example: Convert List to Uppercase After Collection**](#6-example-convert-list-to-uppercase-after-collection)
  - [✅ **Use Case: Modify List After Collection**](#use-case-modify-list-after-collection)
- [**🔥 Summary of Use Cases**](#summary-of-use-cases)
  - [**🚀 Key Takeaways**](#key-takeaways-8)
- [**🎯 Interview Question**](#interview-question)
- [## **📌 Complete List of Utility Methods in `Collectors` Class (Java 8+)**](#complete-list-of-utility-methods-in-collectors-class-java-8)
- [**🔹 List of All Utility Methods in `Collectors`**](#list-of-all-utility-methods-in-collectors)
  - [**1️⃣ Basic Collection Methods**](#1-basic-collection-methods)
  - [**2️⃣ Counting and Summarization**](#2-counting-and-summarization)
  - [**3️⃣ Finding Min & Max**](#3-finding-min-max)
  - [**4️⃣ String Joining**](#4-string-joining)
  - [**5️⃣ Grouping and Partitioning**](#5-grouping-and-partitioning)
  - [**6️⃣ Custom Collection Transformation**](#6-custom-collection-transformation)
- [**🚀 Example Usage of Each Method**](#example-usage-of-each-method)
  - [**1️⃣ Collecting into List, Set, and Map**](#1-collecting-into-list-set-and-map)
  - [**2️⃣ Counting and Summing**](#2-counting-and-summing)
  - [**3️⃣ Grouping and Partitioning**](#3-grouping-and-partitioning)
  - [**4️⃣ `collectingAndThen()` - Convert List to Unmodifiable List**](#4-collectingandthen---convert-list-to-unmodifiable-list)
- [**🔥 Summary Table**](#summary-table-4)
- [# **📌 `Stream.collect()` Variations Based on Supplied Collector in Java 8+**](#streamcollect-variations-based-on-supplied-collector-in-java-8)
- [**🚀 Syntax of `collect()`**](#syntax-of-collect)
- [**🔹 Different `collect()` Variations Based on Supplied `Collector`**](#different-collect-variations-based-on-supplied-collector)
  - [**1️⃣ Collect Elements into a `List`**](#1-collect-elements-into-a-list)
  - [**2️⃣ Collect Elements into a `Set`**](#2-collect-elements-into-a-set)
  - [**3️⃣ Collect Elements into a `Map`**](#3-collect-elements-into-a-map)
  - [**4️⃣ Collect Elements into an Immutable List**](#4-collect-elements-into-an-immutable-list)
  - [**5️⃣ Counting Elements in a Stream**](#5-counting-elements-in-a-stream)
  - [**6️⃣ Joining Strings with a Delimiter**](#6-joining-strings-with-a-delimiter)
  - [**7️⃣ Finding the Maximum or Minimum Element**](#7-finding-the-maximum-or-minimum-element)
  - [**8️⃣ Summing or Averaging Numbers**](#8-summing-or-averaging-numbers)
  - [**9️⃣ Grouping Elements Using `groupingBy()`**](#9-grouping-elements-using-groupingby)
  - [**🔟 Partitioning Elements Using `partitioningBy()`**](#partitioning-elements-using-partitioningby)
- [**🔥 Summary of `collect()` Variations**](#summary-of-collect-variations)
- [## **📌 Complete List of Methods in `Stream` Class (Java 8+)**](#complete-list-of-methods-in-stream-class-java-8)
- [**🔹 List of All Methods in `Stream` Interface**](#list-of-all-methods-in-stream-interface)
  - [**1️⃣ Stream Creation**](#1-stream-creation)
  - [**2️⃣ Filtering & Matching**](#2-filtering-matching)
  - [**3️⃣ Transforming Elements**](#3-transforming-elements)
  - [**4️⃣ Sorting & Limiting**](#4-sorting-limiting)
  - [**5️⃣ Reducing & Collecting**](#5-reducing-collecting)
  - [**6️⃣ Parallel Processing**](#6-parallel-processing)
  - [**7️⃣ Terminal Operations (ForEach & Iteration)**](#7-terminal-operations-foreach-iteration)
  - [**8️⃣ Converting Stream to an Array**](#8-converting-stream-to-an-array)
  - [**9️⃣ Short-Circuiting Methods**](#9-short-circuiting-methods)
- [**🚀 Examples for Each Type of Method**](#examples-for-each-type-of-method)
  - [**1️⃣ Creating Streams**](#1-creating-streams)
  - [**2️⃣ Filtering & Matching**](#2-filtering-matching-2)
  - [**3️⃣ Transforming with `map()`**](#3-transforming-with-map)
  - [**4️⃣ Sorting & Limiting**](#4-sorting-limiting-2)
  - [**5️⃣ Reducing Elements**](#5-reducing-elements)
  - [**6️⃣ Collecting into a List**](#6-collecting-into-a-list)
  - [**7️⃣ Parallel Processing**](#7-parallel-processing)
- [**🔥 Summary Table of `Stream` Methods**](#summary-table-of-stream-methods)
- [**Merging Two Maps Using `Map.merge()` and Anonymous Inner Class in Java 8**](#merging-two-maps-using-mapmerge-and-anonymous-inner-class-in-java-8)
- [**📌 Syntax of `merge()`**](#syntax-of-merge)
- [**🚀 Example: Merging Two Maps with `Map.merge()` and Anonymous Inner Class**](#example-merging-two-maps-with-mapmerge-and-anonymous-inner-class)
- [**🔹 Explanation**](#explanation)
- [**💡 Alternative: Using Lambda Expression**](#alternative-using-lambda-expression)
- [## **📌 `Collectors.toMap()` - All Variants and Examples in Java 8**](#collectorstomap---all-variants-and-examples-in-java-8)
- [**📌 1️⃣ Basic Syntax: `toMap(KeyMapper, ValueMapper)`**](#1-basic-syntax-tomapkeymapper-valuemapper)
  - [**🚀 Example**](#example)
- [**📌 2️⃣ Handling Duplicate Keys: `toMap(KeyMapper, ValueMapper, MergeFunction)`**](#2-handling-duplicate-keys-tomapkeymapper-valuemapper-mergefunction)
  - [**🚀 Example (Handling Duplicate Keys)**](#example-handling-duplicate-keys)
- [**📌 3️⃣ Using a Specific `Map` Type: `toMap(KeyMapper, ValueMapper, MergeFunction, MapSupplier)`**](#3-using-a-specific-map-type-tomapkeymapper-valuemapper-mergefunction-mapsupplier)
  - [**🚀 Example (Using `LinkedHashMap` for Order)**](#example-using-linkedhashmap-for-order)
- [**📌 4️⃣ Handling Null Values in `toMap()`**](#4-handling-null-values-in-tomap)
  - [**🚀 Example (Handling Nulls)**](#example-handling-nulls)
- [**🔹 Summary Table of `toMap()` Variants**](#summary-table-of-tomap-variants)
- [**🔥 Key Takeaways**](#key-takeaways-9)
- [## **📌 `Stream.concat()` in Java 8**](#streamconcat-in-java-8)
- [**📌 Syntax**](#syntax-3)
  - [**🔹 Parameters**](#parameters)
  - [**🔹 Returns**](#returns)
  - [**🔹 Important Notes**](#important-notes)
- [**📌 Example 1: Merging Two Streams of Strings**](#example-1-merging-two-streams-of-strings)
  - [**🔹 Output**](#output-6)
- [**📌 Example 2: Concatenating Streams with Different Data Types**](#example-2-concatenating-streams-with-different-data-types)
  - [**🔹 Output**](#output-7)
- [**📌 Example 3: Handling Empty Streams**](#example-3-handling-empty-streams)
  - [**🔹 Output**](#output-8)
- [**📌 Example 4: Using `Stream.concat()` Multiple Times**](#example-4-using-streamconcat-multiple-times)
  - [**🔹 Output**](#output-9)
- [**📌 Example 5: Avoiding `IllegalStateException`**](#example-5-avoiding-illegalstateexception)
- [**📌 Alternative to `Stream.concat()`**](#alternative-to-streamconcat)
- [**✅ Summary of `Stream.concat()`**](#summary-of-streamconcat)
- [## **Merging Two Maps Using `Stream.concat()` and Anonymous Inner Class in Java 8**](#merging-two-maps-using-streamconcat-and-anonymous-inner-class-in-java-8)
- [**📌 Example: Merging Two Maps with `Stream.concat()` and Anonymous Inner Class**](#example-merging-two-maps-with-streamconcat-and-anonymous-inner-class)
- [**🔹 Explanation**](#explanation-2)
- [**🔹 Output**](#output-10)
- [**✅ Alternative Using Lambda (More Concise)**](#alternative-using-lambda-more-concise)
- [**🚀 Key Takeaways**](#key-takeaways-10)
- [## **Merging Two Maps Using `Stream.concat()`, `toMap()` with `MapSupplier`, and an Anonymous Inner Class in Java 8**](#merging-two-maps-using-streamconcat-tomap-with-mapsupplier-and-an-anonymous-inner-class-in-java-8)
  - [**📌 Example: Merging Two Maps into a `LinkedHashMap` (Maintaining Order)**](#example-merging-two-maps-into-a-linkedhashmap-maintaining-order)
- [**🔹 Explanation**](#explanation-3)
- [**🔹 Output**](#output-11)
- [**✅ Alternative Using Lambda for Merge Function**](#alternative-using-lambda-for-merge-function)
- [**🔥 Key Takeaways**](#key-takeaways-11)
- [## **Merging Two Maps with Same Keys in Java 8**](#merging-two-maps-with-same-keys-in-java-8)
- [**📌 Approach 1: Using `Stream.concat()` and `Collectors.toMap()`**](#approach-1-using-streamconcat-and-collectorstomap)
  - [**🔹 Output**](#output-12)
- [**📌 Approach 2: Using `Map.merge()`**](#approach-2-using-mapmerge)
  - [**🔹 Output**](#output-13)
- [**📌 Approach 3: Using `Collectors.toMap()` with a Custom Map (LinkedHashMap)**](#approach-3-using-collectorstomap-with-a-custom-map-linkedhashmap)
  - [**🔹 Output**](#output-14)
- [**📌 Approach 4: Using Java 8 `reduce()`**](#approach-4-using-java-8-reduce)
  - [**🔹 Output**](#output-15)
- [**🔥 Comparison of Methods**](#comparison-of-methods)
- [**✅ Best Choice Based on Use Case**](#best-choice-based-on-use-case)
- [**🚀 Summary**](#summary-2)

---

Here’s a list of commonly asked **Java 8** interview questions for a verbal interview:  

---

### **1. Functional Interfaces & Lambda Expressions**  
- What is a **functional interface** in Java 8?  
- Can you name some built-in functional interfaces in Java 8?  
- How do lambda expressions work in Java 8?  
- What is the difference between a lambda expression and an anonymous class?  
- Can a functional interface have multiple methods?  

---

[⬆ Back to top](#table-of-contents)

### **2. Streams API**  
- What are **Streams** in Java 8?  
- How is a Stream different from a Collection?  
- What is the difference between **intermediate** and **terminal** operations?  
- How does the **filter()** method work in a Stream?  
- What is the difference between **map()** and **flatMap()**?  
- What is the use of **collect()** in Streams?  
- How do you count elements in a Stream?  
- Can a Stream be reused once it is consumed?  

---

[⬆ Back to top](#table-of-contents)

### **3. Optional Class**  
- What is the purpose of **Optional** in Java 8?  
- How do you avoid **NullPointerException** using Optional?  
- What is the difference between **orElse()** and **orElseGet()**?  
- What is the purpose of **ifPresent()** in Optional?  

---

[⬆ Back to top](#table-of-contents)

### **4. Default & Static Methods in Interfaces**  
- What are **default methods** in Java 8 interfaces?  
- Why were default methods introduced?  
- Can a Java 8 interface have multiple default methods?  
- How does Java resolve conflicts when multiple interfaces have default methods?  
- Can an interface have a **static method**?  

---

[⬆ Back to top](#table-of-contents)

### **5. Method References**  
- What are **method references** in Java 8?  
- What are the different types of method references?  
- How do you convert a lambda expression into a method reference?  

---

[⬆ Back to top](#table-of-contents)

### **6. Date & Time API (java.time Package)**  
- What are the improvements in Java 8’s Date and Time API?  
- What is the difference between **LocalDate**, **LocalTime**, and **LocalDateTime**?  
- How do you format dates using the new API?  
- What is the difference between **ZonedDateTime** and **OffsetDateTime**?  

---

[⬆ Back to top](#table-of-contents)

### **7. Parallel Streams**  
- What is a **parallel stream** in Java 8?  
- How do parallel streams improve performance?  
- What are some pitfalls of using parallel streams?  

---

[⬆ Back to top](#table-of-contents)

### **8. Collectors API**  
- What is the **Collectors** utility class?  
- How do you group elements using **Collectors.groupingBy()**?  
- How do you perform partitioning using **Collectors.partitioningBy()**?  

---

[⬆ Back to top](#table-of-contents)

### **9. CompletableFuture & Concurrency Enhancements**  
- What is **CompletableFuture** in Java 8?  
- How does **CompletableFuture** improve asynchronous programming?  
- What is the difference between **thenApply()** and **thenAccept()**?  

---

[⬆ Back to top](#table-of-contents)

### **10. Miscellaneous**  
- What are the key differences between Java 7 and Java 8?  
- Why is Java 8 considered a major release?  
- Can you use Java 8 features in older versions of Java?  

[⬆ Back to top](#table-of-contents)

## Here are some **Java 8 programming interview questions** that require coding solutions:  

---

[⬆ Back to top](#table-of-contents)

### **1. Reverse a List Using Java 8 Streams**  
💡 **Question:** Given a list of integers, reverse the list using Java 8 Streams.  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
```

🔹 **Expected Output:** `[5, 4, 3, 2, 1]`  

---

[⬆ Back to top](#table-of-contents)

### **2. Find Duplicate Elements in a List**  
💡 **Question:** Given a list of integers, find the duplicate elements using Java 8 Streams.  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 2, 3, 6, 7, 8, 1);
```

🔹 **Expected Output:** `[1, 2, 3]`  

---

[⬆ Back to top](#table-of-contents)

### **3. Find the First Non-Repeating Character in a String**  
💡 **Question:** Given a string, find the first non-repeating character using Java 8 Streams.  
```java
String input = "swiss";
```

🔹 **Expected Output:** `'w'`  

---

[⬆ Back to top](#table-of-contents)

### **4. Convert a List of Strings to Uppercase**  
💡 **Question:** Given a list of strings, convert each string to uppercase using Java 8 Streams.  
```java
List<String> names = Arrays.asList("apple", "banana", "cherry");
```

🔹 **Expected Output:** `["APPLE", "BANANA", "CHERRY"]`  

---

[⬆ Back to top](#table-of-contents)

### **5. Sum of Even Numbers in a List**  
💡 **Question:** Given a list of integers, find the sum of all even numbers using Java 8 Streams.  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```

🔹 **Expected Output:** `30` (2 + 4 + 6 + 8 + 10)  

---

[⬆ Back to top](#table-of-contents)

### **6. Find the Second-Highest Number in a List**  
💡 **Question:** Given a list of integers, find the second-highest number using Java 8 Streams.  
```java
List<Integer> numbers = Arrays.asList(5, 8, 12, 7, 19, 21, 19);
```

🔹 **Expected Output:** `19`  

---

[⬆ Back to top](#table-of-contents)

### **7. Count the Frequency of Each Character in a String**  
💡 **Question:** Given a string, count the occurrences of each character using Java 8 Streams.  
```java
String input = "hello world";
```

🔹 **Expected Output:** `{h=1, e=1, l=3, o=2, w=1, r=1, d=1}`  

---

[⬆ Back to top](#table-of-contents)

### **8. Convert a List to a Map**  
💡 **Question:** Given a list of strings, convert it to a map where the key is the string and the value is its length.  
```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
```

🔹 **Expected Output:** `{apple=5, banana=6, cherry=6}`  

---

[⬆ Back to top](#table-of-contents)

### **9. Check if a String is a Palindrome**  
💡 **Question:** Given a string, check if it is a palindrome using Java 8 features.  
```java
String input = "madam";
```

🔹 **Expected Output:** `true`  

---

[⬆ Back to top](#table-of-contents)

### **10. Find the Maximum Number in a List**  
💡 **Question:** Given a list of integers, find the maximum number using Java 8 Streams.  
```java
List<Integer> numbers = Arrays.asList(10, 23, 45, 78, 96, 45, 12);
```

🔹 **Expected Output:** `96`  

---

[⬆ Back to top](#table-of-contents)

## Here are some **complex Java 8 coding interview questions** that require advanced knowledge of **Streams, Lambdas, Optional, Collectors, Parallel Streams, and Functional Programming**. 🚀  

---

[⬆ Back to top](#table-of-contents)

## **1. Employee Salary Calculation (Grouping & Reduction)**
💡 **Question:**  
Given a list of `Employee` objects, write a Java 8 program to calculate the **total salary per department** using `Collectors.groupingBy()`.  

```java
class Employee {
    String name;
    String department;
    double salary;

    public Employee(String name, String department, double salary) {
        this.name = name;
        this.department = department;
        this.salary = salary;
    }
}
```

🔹 **Input:**  
```java
List<Employee> employees = Arrays.asList(
    new Employee("Alice", "HR", 5000),
    new Employee("Bob", "IT", 7000),
    new Employee("Charlie", "HR", 5500),
    new Employee("David", "Finance", 6000),
    new Employee("Eve", "IT", 7500)
);
```
🔹 **Expected Output:**  
```
HR -> 10500  
IT -> 14500  
Finance -> 6000  
```

---

[⬆ Back to top](#table-of-contents)

## **2. Find the Longest Word in a Sentence**
💡 **Question:**  
Given a sentence, find the **longest word** using Java 8 Streams.

🔹 **Input:**  
```java
String sentence = "Java 8 streams provide functional programming capabilities";
```
🔹 **Expected Output:**  
```
programming
```

---

[⬆ Back to top](#table-of-contents)

## **3. Group Transactions by Currency and Sum Amounts**
💡 **Question:**  
Given a list of `Transaction` objects, write a Java 8 program to group them by currency and sum their amounts.

```java
class Transaction {
    String currency;
    double amount;

    public Transaction(String currency, double amount) {
        this.currency = currency;
        this.amount = amount;
    }
}
```

🔹 **Input:**  
```java
List<Transaction> transactions = Arrays.asList(
    new Transaction("USD", 1000),
    new Transaction("EUR", 500),
    new Transaction("USD", 2000),
    new Transaction("GBP", 700),
    new Transaction("EUR", 300)
);
```
🔹 **Expected Output:**  
```
USD -> 3000  
EUR -> 800  
GBP -> 700  
```

---

[⬆ Back to top](#table-of-contents)

## **4. Find Kth Largest Element in a List**
💡 **Question:**  
Given a list of integers, find the **Kth largest element** using Java 8 Streams.

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 50, 20, 40, 80, 60, 90);
int k = 3;
```
🔹 **Expected Output:**  
```
60
```

---

[⬆ Back to top](#table-of-contents)

## **5. Convert Nested Lists into a Single Flattened List**
💡 **Question:**  
Given a list of lists, flatten it into a single list using `flatMap()`.

🔹 **Input:**  
```java
List<List<Integer>> nestedList = Arrays.asList(
    Arrays.asList(1, 2, 3),
    Arrays.asList(4, 5),
    Arrays.asList(6, 7, 8, 9)
);
```
🔹 **Expected Output:**  
```
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

---

[⬆ Back to top](#table-of-contents)

## **6. Find the Most Frequent Word in a List**
💡 **Question:**  
Given a list of words, find the most frequently occurring word using Java 8 Streams.

🔹 **Input:**  
```java
List<String> words = Arrays.asList("apple", "banana", "apple", "orange", "banana", "apple");
```
🔹 **Expected Output:**  
```
apple
```

---

[⬆ Back to top](#table-of-contents)

## **7. Implement a Custom Comparator Using Lambda**
💡 **Question:**  
Sort a list of `Person` objects based on age using Java 8 Lambda.

```java
class Person {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```

🔹 **Input:**  
```java
List<Person> people = Arrays.asList(
    new Person("Alice", 25),
    new Person("Bob", 30),
    new Person("Charlie", 22)
);
```
🔹 **Expected Output (Sorted by Age):**  
```
Charlie (22)
Alice (25)
Bob (30)
```

---

[⬆ Back to top](#table-of-contents)

## **8. Find the First Repeated Character in a String**
💡 **Question:**  
Given a string, find the first character that appears more than once.

🔹 **Input:**  
```java
String input = "programming";
```
🔹 **Expected Output:**  
```
r
```

---

[⬆ Back to top](#table-of-contents)

## **9. Generate Fibonacci Series Using Stream API**
💡 **Question:**  
Write a Java 8 program to generate the **first N Fibonacci numbers** using `Stream.iterate()`.

🔹 **Input:**  
```java
int N = 10;
```
🔹 **Expected Output:**  
```
0, 1, 1, 2, 3, 5, 8, 13, 21, 34
```

---

[⬆ Back to top](#table-of-contents)

## **10. Parallel Stream Performance Optimization**
💡 **Question:**  
Given a large list of integers, use **parallel streams** to compute the sum efficiently.

🔹 **Input:**  
```java
List<Integer> numbers = IntStream.rangeClosed(1, 1_000_000).boxed().collect(Collectors.toList());
```
🔹 **Expected Output:**  
```
Sum = 500000500000
```
(Note: The sum of the first 1 million numbers)

---

[⬆ Back to top](#table-of-contents)

## Here is a **comprehensive list** of Java 8 **sorting interview questions**, covering different scenarios and techniques using **Streams, Lambdas, and Comparators**. 🚀  

---

[⬆ Back to top](#table-of-contents)

## **1. Sort a List of Integers in Ascending and Descending Order**  
💡 **Question:** Given a list of integers, sort it in **ascending** and **descending** order using Java 8 Streams.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(5, 2, 8, 1, 3);
```
🔹 **Expected Output:**  
```
Ascending: [1, 2, 3, 5, 8]  
Descending: [8, 5, 3, 2, 1]  
```

---

[⬆ Back to top](#table-of-contents)

## **2. Sort a List of Strings Alphabetically and by Length**  
💡 **Question:** Given a list of strings, sort them **alphabetically** and **by length** using Java 8.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("apple", "banana", "cherry", "kiwi");
```
🔹 **Expected Output:**  
```
Alphabetically: [apple, banana, cherry, kiwi]  
By Length: [kiwi, apple, cherry, banana]  
```

---

[⬆ Back to top](#table-of-contents)

## **3. Sort a List of Custom Objects (Sorting by Single Field)**  
💡 **Question:** Given a list of `Person` objects, sort them by **age** in ascending order using Java 8.  

🔹 **Class Definition:**  
```java
class Person {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```
🔹 **Input:**  
```java
List<Person> people = Arrays.asList(
    new Person("Alice", 30),
    new Person("Bob", 25),
    new Person("Charlie", 35)
);
```
🔹 **Expected Output (Sorted by Age):**  
```
Bob (25), Alice (30), Charlie (35)
```

---

[⬆ Back to top](#table-of-contents)

## **4. Sort a List of Custom Objects by Multiple Fields (Chained Sorting)**  
💡 **Question:** Sort a list of `Employee` objects first by **salary (descending)** and then by **name (ascending)**.  

🔹 **Class Definition:**  
```java
class Employee {
    String name;
    double salary;

    public Employee(String name, double salary) {
        this.name = name;
        this.salary = salary;
    }
}
```
🔹 **Input:**  
```java
List<Employee> employees = Arrays.asList(
    new Employee("Alice", 5000),
    new Employee("Bob", 7000),
    new Employee("Charlie", 5000),
    new Employee("David", 6000)
);
```
🔹 **Expected Output:**  
```
Bob (7000), David (6000), Alice (5000), Charlie (5000)
```
(Sorted by salary descending, then name ascending)

---

[⬆ Back to top](#table-of-contents)

## **5. Sort a List of Strings Ignoring Case Sensitivity**  
💡 **Question:** Sort a list of strings ignoring case sensitivity using Java 8.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("Banana", "apple", "cherry", "Apricot");
```
🔹 **Expected Output:**  
```
[apple, Apricot, Banana, cherry]
```

---

[⬆ Back to top](#table-of-contents)

## **6. Sort a Map by Keys and Values Using Java 8**  
💡 **Question:** Given a `Map<String, Integer>`, sort it by **keys** and **values**.  

🔹 **Input:**  
```java
Map<String, Integer> scores = new HashMap<>();
scores.put("Alice", 90);
scores.put("Bob", 80);
scores.put("Charlie", 85);
```
🔹 **Expected Output:**  
```
Sorted by Key: {Alice=90, Bob=80, Charlie=85}  
Sorted by Value: {Bob=80, Charlie=85, Alice=90}  
```

---

[⬆ Back to top](#table-of-contents)

## **7. Sort a List in Reverse Order Using Comparator.reverseOrder()**  
💡 **Question:** Sort a list of numbers in reverse order using Java 8.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(5, 2, 8, 1, 3);
```
🔹 **Expected Output:**  
```
[8, 5, 3, 2, 1]
```

---

[⬆ Back to top](#table-of-contents)

## **8. Sort a List of Objects with Null Values (Null-Safe Sorting)**  
💡 **Question:** Sort a list of `Person` objects where some names are `null`.  

🔹 **Input:**  
```java
List<String> names = Arrays.asList("John", null, "Alice", "Bob", null);
```
🔹 **Expected Output:**  
```
[null, null, Alice, Bob, John]  // Nulls first
OR
[Alice, Bob, John, null, null]  // Nulls last
```

---

[⬆ Back to top](#table-of-contents)

## **9. Sort a List of Dates in Java 8**  
💡 **Question:** Given a list of `LocalDate` objects, sort them in ascending order.  

🔹 **Input:**  
```java
List<LocalDate> dates = Arrays.asList(
    LocalDate.of(2023, 5, 20),
    LocalDate.of(2021, 8, 15),
    LocalDate.of(2022, 3, 10)
);
```
🔹 **Expected Output:**  
```
[2021-08-15, 2022-03-10, 2023-05-20]
```

---

[⬆ Back to top](#table-of-contents)

## **10. Sort a List Using Parallel Sorting (Efficient Sorting for Large Data)**  
💡 **Question:** Use Java 8's `Arrays.parallelSort()` for large data sorting.  

🔹 **Input:**  
```java
int[] numbers = {5, 2, 8, 1, 3};
```
🔹 **Expected Output:**  
```
[1, 2, 3, 5, 8]
```

---

[⬆ Back to top](#table-of-contents)

## **11. Custom Sorting Using a Comparator with Lambda**  
💡 **Question:** Sort a list of `Product` objects by **price** in **descending** order using a custom `Comparator`.  

🔹 **Class Definition:**  
```java
class Product {
    String name;
    double price;

    public Product(String name, double price) {
        this.name = name;
        this.price = price;
    }
}
```
🔹 **Input:**  
```java
List<Product> products = Arrays.asList(
    new Product("Laptop", 800),
    new Product("Phone", 500),
    new Product("Tablet", 300)
);
```
🔹 **Expected Output:**  
```
Laptop (800), Phone (500), Tablet (300)
```

---

[⬆ Back to top](#table-of-contents)

## **12. Sort a List Using Stream.sorted() with Custom Comparator**  
💡 **Question:** Sort a list of words by the last character of each word.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
```
🔹 **Expected Output:**  
```
banana, apple, cherry  // Sorted by last character
```

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 `Optional` Class - Coding Interview Questions** 🚀

Java 8 introduced `Optional` to handle **null values safely** and reduce `NullPointerException`. Here are some **coding interview questions** related to `Optional` with real-world scenarios.

---

[⬆ Back to top](#table-of-contents)

### **1. Convert a `String` to `Optional` and Handle Null Values**
💡 **Question:** Given a string, convert it into an `Optional<String>` and print its value. If the string is `null`, print `"Value is absent"`.

🔹 **Input:**  
```java
String input = "Hello, Java 8!";
```
🔹 **Expected Output:**  
```
Hello, Java 8!
```
(If `input = null`, output should be `"Value is absent"`)

---

[⬆ Back to top](#table-of-contents)

### **2. Use `Optional` to Avoid `NullPointerException`**
💡 **Question:** Given a `Person` object, retrieve the `address`. If the address is `null`, return `"Address not available"`.

```java
class Person {
    private String name;
    private String address;

    public Person(String name, String address) {
        this.name = name;
        this.address = address;
    }

    public String getAddress() {
        return address;
    }
}
```

🔹 **Input:**  
```java
Person person = new Person("Alice", null);
```
🔹 **Expected Output:**  
```
Address not available
```

---

[⬆ Back to top](#table-of-contents)

### **3. Get Default Value Using `orElse()` and `orElseGet()`**
💡 **Question:** Given an `Optional<String>`, return its value if present, otherwise return `"Default Value"`.

🔹 **Input:**  
```java
Optional<String> opt = Optional.empty();
```
🔹 **Expected Output:**  
```
Default Value
```

---

[⬆ Back to top](#table-of-contents)

### **4. Find Maximum Value in a List Using `Optional`**
💡 **Question:** Given a list of integers, find the **maximum** value using `Optional`. If the list is empty, return `-1`.

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 25, 30, 5, 15);
```
🔹 **Expected Output:**  
```
30
```
(If the list is empty, return `-1`)

---

[⬆ Back to top](#table-of-contents)

### **5. Check If a Value Exists Using `isPresent()`**
💡 **Question:** Given an `Optional<String>`, check if a value exists and print it.

🔹 **Input:**  
```java
Optional<String> opt = Optional.of("Java 8");
```
🔹 **Expected Output:**  
```
Value is: Java 8
```

---

[⬆ Back to top](#table-of-contents)

### **6. Use `Optional` with `filter()` to Check a Condition**
💡 **Question:** Given an `Optional<Integer>`, check if the value is even. If it is, print it; otherwise, print `"Odd number or not present"`.

🔹 **Input:**  
```java
Optional<Integer> opt = Optional.of(10);
```
🔹 **Expected Output:**  
```
Even number: 10
```
(If the value is `9`, output should be `"Odd number or not present"`)

---

[⬆ Back to top](#table-of-contents)

### **7. Use `Optional` with `map()` and `flatMap()` for Nested Objects**
💡 **Question:** Given a `Car` object, get its **engine type** safely using `Optional.map()`.

```java
class Engine {
    private String type;

    public Engine(String type) {
        this.type = type;
    }

    public String getType() {
        return type;
    }
}

class Car {
    private Optional<Engine> engine;

    public Car(Optional<Engine> engine) {
        this.engine = engine;
    }

    public Optional<Engine> getEngine() {
        return engine;
    }
}
```

🔹 **Input:**  
```java
Car car = new Car(Optional.of(new Engine("V8")));
```
🔹 **Expected Output:**  
```
Engine Type: V8
```
(If no engine is present, return `"No Engine"`)

---

[⬆ Back to top](#table-of-contents)

### **8. Use `orElseThrow()` to Throw an Exception if Value is Absent**
💡 **Question:** Given an `Optional<String>`, return its value. If it's empty, throw an exception.

🔹 **Input:**  
```java
Optional<String> opt = Optional.empty();
```
🔹 **Expected Output:**  
```
java.util.NoSuchElementException: No value present
```

---

[⬆ Back to top](#table-of-contents)

### **9. Find First Non-Empty `Optional` Using `Optional.ofNullable()`**
💡 **Question:** Given multiple `Optional<String>` values, return the **first non-empty value**.

🔹 **Input:**  
```java
Optional<String> opt1 = Optional.empty();
Optional<String> opt2 = Optional.of("Hello");
Optional<String> opt3 = Optional.of("World");
```
🔹 **Expected Output:**  
```
Hello
```

---

[⬆ Back to top](#table-of-contents)

### **10. Use `Optional` in Streams to Avoid `NullPointerException`**
💡 **Question:** Given a list of names, return the **first name that starts with "J"** using Java 8 Streams and `Optional`.

🔹 **Input:**  
```java
List<String> names = Arrays.asList("Alice", "Bob", "John", "Jack");
```
🔹 **Expected Output:**  
```
John
```
(If no name starts with "J", return `"No name found"`)

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 Lambda Expressions - Coding Interview Questions** 🚀

Java 8 introduced **lambda expressions** to provide a more concise and functional way to write code. Here are some **Lambda Expression** related **coding interview questions** with real-world scenarios.  

---

[⬆ Back to top](#table-of-contents)

## **1. Implement a Functional Interface Using Lambda**
💡 **Question:** Create a `Calculator` functional interface with a method `operate(int a, int b)`, and implement addition using a lambda expression.  

🔹 **Expected Output:**  
```
Sum: 30
```

---

[⬆ Back to top](#table-of-contents)

## **2. Sort a List Using Lambda**
💡 **Question:** Given a list of strings, sort them **alphabetically** using a lambda expression.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("banana", "apple", "cherry", "date");
```
🔹 **Expected Output:**  
```
[apple, banana, cherry, date]
```

---

[⬆ Back to top](#table-of-contents)

## **3. Find Even Numbers in a List Using Lambda & Streams**
💡 **Question:** Given a list of numbers, filter out only the **even numbers** using Java 8 lambda.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```
🔹 **Expected Output:**  
```
[2, 4, 6, 8, 10]
```

---

[⬆ Back to top](#table-of-contents)

## **4. Convert List of Strings to Uppercase Using Lambda**
💡 **Question:** Given a list of lowercase strings, convert them to **uppercase** using Java 8 lambda.  

🔹 **Input:**  
```java
List<String> names = Arrays.asList("java", "lambda", "stream");
```
🔹 **Expected Output:**  
```
[JAVA, LAMBDA, STREAM]
```

---

[⬆ Back to top](#table-of-contents)

## **5. Find the First Name That Starts with "A" Using Lambda**
💡 **Question:** Given a list of names, find the **first name that starts with "A"** using Java 8 Streams and lambda.  

🔹 **Input:**  
```java
List<String> names = Arrays.asList("Bob", "Alice", "Charlie", "Anna");
```
🔹 **Expected Output:**  
```
Alice
```
(If no name starts with "A", return `"No name found"`)

---

[⬆ Back to top](#table-of-contents)

## **6. Find the Sum of All Numbers in a List Using Lambda**
💡 **Question:** Given a list of numbers, find their **sum** using Java 8 lambda.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
```
🔹 **Expected Output:**  
```
150
```

---

[⬆ Back to top](#table-of-contents)

## **7. Implement Runnable Using Lambda**
💡 **Question:** Implement the `Runnable` interface using a lambda expression and start a thread.  

🔹 **Expected Output:**  
```
Thread is running...
```

---

[⬆ Back to top](#table-of-contents)

## **8. Remove Null Values from a List Using Lambda**
💡 **Question:** Given a list of names, remove all `null` values using Java 8 Streams and lambda.  

🔹 **Input:**  
```java
List<String> names = Arrays.asList("Alice", null, "Bob", "Charlie", null);
```
🔹 **Expected Output:**  
```
[Alice, Bob, Charlie]
```

---

[⬆ Back to top](#table-of-contents)

## **9. Count Names That Start with "J" Using Lambda**
💡 **Question:** Given a list of names, count how many names **start with "J"** using Java 8 lambda.  

🔹 **Input:**  
```java
List<String> names = Arrays.asList("John", "Jack", "Alice", "Bob", "James");
```
🔹 **Expected Output:**  
```
3
```

---

[⬆ Back to top](#table-of-contents)

## **10. Convert a List of Integers to a List of Strings Using Lambda**
💡 **Question:** Given a list of integers, convert them into **strings** using Java 8 lambda.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 20, 30);
```
🔹 **Expected Output:**  
```
["10", "20", "30"]
```

---

[⬆ Back to top](#table-of-contents)

## **11. Find the Maximum Value in a List Using Lambda**
💡 **Question:** Given a list of integers, find the **maximum value** using Java 8 lambda.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(5, 12, 8, 21, 3);
```
🔹 **Expected Output:**  
```
21
```

---

[⬆ Back to top](#table-of-contents)

## **12. Find the Length of Each String in a List Using Lambda**
💡 **Question:** Given a list of strings, return a list containing the **length of each string** using Java 8 lambda.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("Java", "Lambda", "Stream");
```
🔹 **Expected Output:**  
```
[4, 6, 6]
```

---

[⬆ Back to top](#table-of-contents)

## **13. Find Distinct Elements in a List Using Lambda**
💡 **Question:** Given a list of integers with duplicates, find the **distinct elements** using Java 8 lambda.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 4, 4, 5);
```
🔹 **Expected Output:**  
```
[1, 2, 3, 4, 5]
```

---

[⬆ Back to top](#table-of-contents)

## **14. Implement a Custom Comparator Using Lambda**
💡 **Question:** Sort a list of `Person` objects by **age** using a lambda comparator.  

🔹 **Class Definition:**  
```java
class Person {
    String name;
    int age;

    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```
🔹 **Input:**  
```java
List<Person> people = Arrays.asList(
    new Person("Alice", 30),
    new Person("Bob", 25),
    new Person("Charlie", 35)
);
```
🔹 **Expected Output:**  
```
Bob (25), Alice (30), Charlie (35)
```

---

[⬆ Back to top](#table-of-contents)

## **15. Convert a Map to a List Using Lambda**
💡 **Question:** Convert a `Map<String, Integer>` to a **list of values** using Java 8 lambda.  

🔹 **Input:**  
```java
Map<String, Integer> map = new HashMap<>();
map.put("A", 10);
map.put("B", 20);
map.put("C", 30);
```
🔹 **Expected Output:**  
```
[10, 20, 30]
```

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 Functional Interface - Coding Interview Questions** 🚀  

Java 8 introduced **Functional Interfaces** to support **Lambda Expressions** and enable functional programming in Java. Below are some **coding interview questions** on Java 8 **Functional Interfaces**.  

---

[⬆ Back to top](#table-of-contents)

## **1. Create a Custom Functional Interface**  
💡 **Question:** Create a functional interface `Calculator` with a method `calculate(int a, int b)`, and use a **lambda expression** to implement addition.  

🔹 **Expected Output:**  
```
Sum: 30
```

---

[⬆ Back to top](#table-of-contents)

## **2. Use `Predicate` to Check If a Number is Even**  
💡 **Question:** Use **`Predicate<Integer>`** to check if a number is even.  

🔹 **Input:**  
```java
int num = 10;
```
🔹 **Expected Output:**  
```
10 is even
```
(If `num = 9`, output should be `"9 is odd"`)

---

[⬆ Back to top](#table-of-contents)

## **3. Use `Function` to Convert String to Uppercase**  
💡 **Question:** Use **`Function<String, String>`** to convert a given string to **uppercase**.  

🔹 **Input:**  
```java
String input = "hello";
```
🔹 **Expected Output:**  
```
HELLO
```

---

[⬆ Back to top](#table-of-contents)

## **4. Use `Consumer` to Print a List of Names**  
💡 **Question:** Use **`Consumer<String>`** to print each name from a list.  

🔹 **Input:**  
```java
List<String> names = Arrays.asList("Alice", "Bob", "Charlie");
```
🔹 **Expected Output:**  
```
Alice  
Bob  
Charlie  
```

---

[⬆ Back to top](#table-of-contents)

## **5. Use `Supplier` to Generate a Random Number**  
💡 **Question:** Use **`Supplier<Integer>`** to generate a **random number**.  

🔹 **Expected Output:**  
```
Random number: 42  (Example output, varies each time)
```

---

[⬆ Back to top](#table-of-contents)

## **6. Use `BiFunction` to Multiply Two Numbers**  
💡 **Question:** Use **`BiFunction<Integer, Integer, Integer>`** to multiply two numbers.  

🔹 **Input:**  
```java
int a = 5, b = 6;
```
🔹 **Expected Output:**  
```
Product: 30
```

---

[⬆ Back to top](#table-of-contents)

## **7. Use `UnaryOperator` to Square a Number**  
💡 **Question:** Use **`UnaryOperator<Integer>`** to **square** a given number.  

🔹 **Input:**  
```java
int num = 4;
```
🔹 **Expected Output:**  
```
16
```

---

[⬆ Back to top](#table-of-contents)

## **8. Use `BinaryOperator` for String Concatenation**  
💡 **Question:** Use **`BinaryOperator<String>`** to concatenate two strings.  

🔹 **Input:**  
```java
String s1 = "Hello", s2 = "World";
```
🔹 **Expected Output:**  
```
HelloWorld
```

---

[⬆ Back to top](#table-of-contents)

## **9. Implement `Comparator` Using a Functional Interface**  
💡 **Question:** Use **`Comparator<Integer>`** to sort a list of numbers in **descending order**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(5, 2, 8, 1, 9);
```
🔹 **Expected Output:**  
```
[9, 8, 5, 2, 1]
```

---

[⬆ Back to top](#table-of-contents)

## **10. Find Names Starting with "A" Using `Predicate`**  
💡 **Question:** Use **`Predicate<String>`** to filter out names that **start with "A"** from a list.  

🔹 **Input:**  
```java
List<String> names = Arrays.asList("Alice", "Bob", "Anna", "Charlie");
```
🔹 **Expected Output:**  
```
[Alice, Anna]
```

---

[⬆ Back to top](#table-of-contents)

## **11. Chain `Predicate` Functions**  
💡 **Question:** Use **two `Predicate` functions** to check if a number is **greater than 10 and even**.  

🔹 **Input:**  
```java
int num = 12;
```
🔹 **Expected Output:**  
```
12 is greater than 10 and even
```

---

[⬆ Back to top](#table-of-contents)

## **12. Chain `Function` to Perform Two Operations**  
💡 **Question:** Use **`Function<Integer, Integer>`** to first **double** a number and then **add 10**.  

🔹 **Input:**  
```java
int num = 5;
```
🔹 **Expected Output:**  
```
20
```

---

[⬆ Back to top](#table-of-contents)

## **13. Use `Consumer` to Log a Message Before Execution**  
💡 **Question:** Use **`Consumer<String>`** to log a message **before** executing an action.  

🔹 **Expected Output:**  
```
Logging message: Processing request...
Processing request...
```

---

[⬆ Back to top](#table-of-contents)

## **14. Use `BiPredicate` to Compare Two Numbers**  
💡 **Question:** Use **`BiPredicate<Integer, Integer>`** to check if one number is a **multiple** of another.  

🔹 **Input:**  
```java
int a = 20, b = 5;
```
🔹 **Expected Output:**  
```
20 is a multiple of 5
```

---

[⬆ Back to top](#table-of-contents)

## **15. Implement Custom Functional Interface With Lambda**  
💡 **Question:** Create a **custom functional interface** `StringProcessor` that reverses a string using a **lambda expression**.  

🔹 **Input:**  
```java
String input = "Lambda";
```
🔹 **Expected Output:**  
```
adbmaL
```

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 Streams - Coding Interview Questions** 🚀  

Java 8 introduced **Streams API** to perform operations on collections efficiently using functional programming. Below are some **coding interview questions** on Java 8 **Streams** with real-world scenarios.  

---

[⬆ Back to top](#table-of-contents)

## **1. Find Even Numbers Using Streams**  
💡 **Question:** Given a list of numbers, use Java 8 **Streams** to filter and collect only the **even numbers**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```
🔹 **Expected Output:**  
```
[2, 4, 6, 8, 10]
```

---

[⬆ Back to top](#table-of-contents)

## **2. Find the First Element Greater Than 10**  
💡 **Question:** Use Java 8 **Streams** to find the **first number greater than 10** in a list.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(5, 8, 12, 3, 15);
```
🔹 **Expected Output:**  
```
12
```
(If no number is greater than 10, return `"Not Found"`)

---

[⬆ Back to top](#table-of-contents)

## **3. Find the Maximum Number in a List**  
💡 **Question:** Given a list of numbers, use Java 8 **Streams** to find the **maximum number**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(3, 7, 2, 8, 5);
```
🔹 **Expected Output:**  
```
8
```

---

[⬆ Back to top](#table-of-contents)

## **4. Convert a List of Strings to Uppercase**  
💡 **Question:** Use Java 8 **Streams** to convert a list of lowercase strings to **uppercase**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("java", "lambda", "stream");
```
🔹 **Expected Output:**  
```
[JAVA, LAMBDA, STREAM]
```

---

[⬆ Back to top](#table-of-contents)

## **5. Sort a List of Strings in Descending Order**  
💡 **Question:** Given a list of strings, use Java 8 **Streams** to **sort in descending order**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("banana", "apple", "cherry", "date");
```
🔹 **Expected Output:**  
```
[date, cherry, banana, apple]
```

---

[⬆ Back to top](#table-of-contents)

## **6. Count the Number of Strings with Length Greater Than 4**  
💡 **Question:** Use Java 8 **Streams** to count how many strings have a **length greater than 4**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("Java", "Python", "Go", "Rust", "Kotlin");
```
🔹 **Expected Output:**  
```
3
```

---

[⬆ Back to top](#table-of-contents)

## **7. Find the Sum of All Numbers in a List**  
💡 **Question:** Use Java 8 **Streams** to find the **sum of all numbers** in a list.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
```
🔹 **Expected Output:**  
```
150
```

---

[⬆ Back to top](#table-of-contents)

## **8. Find Distinct Elements in a List**  
💡 **Question:** Given a list of integers with duplicates, use Java 8 **Streams** to return **only unique elements**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 4, 4, 5);
```
🔹 **Expected Output:**  
```
[1, 2, 3, 4, 5]
```

---

[⬆ Back to top](#table-of-contents)

## **9. Find Names Starting with "J"**  
💡 **Question:** Use Java 8 **Streams** to filter out names that **start with "J"** from a list.  

🔹 **Input:**  
```java
List<String> names = Arrays.asList("John", "Jack", "Alice", "Bob", "James");
```
🔹 **Expected Output:**  
```
[John, Jack, James]
```

---

[⬆ Back to top](#table-of-contents)

## **10. Find the Average of a List of Numbers**  
💡 **Question:** Use Java 8 **Streams** to find the **average of a list of numbers**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
```
🔹 **Expected Output:**  
```
30.0
```

---

[⬆ Back to top](#table-of-contents)

## **11. Convert a List of Strings to a Single Comma-Separated String**  
💡 **Question:** Use Java 8 **Streams** to join a list of strings into a **single comma-separated string**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
```
🔹 **Expected Output:**  
```
"apple, banana, cherry"
```

---

[⬆ Back to top](#table-of-contents)

## **12. Find the Second Largest Number in a List**  
💡 **Question:** Use Java 8 **Streams** to find the **second largest number** in a list.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(3, 7, 2, 8, 5);
```
🔹 **Expected Output:**  
```
7
```

---

[⬆ Back to top](#table-of-contents)

## **13. Convert a List of Objects to a List of Strings Using Streams**  
💡 **Question:** Given a list of `Person` objects, use Java 8 **Streams** to extract only the names.  

🔹 **Class Definition:**  
```java
class Person {
    String name;
    int age;
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```
🔹 **Input:**  
```java
List<Person> people = Arrays.asList(
    new Person("Alice", 25),
    new Person("Bob", 30),
    new Person("Charlie", 35)
);
```
🔹 **Expected Output:**  
```
[Alice, Bob, Charlie]
```

---

[⬆ Back to top](#table-of-contents)

## **14. Find the First Non-Repeating Character in a String**  
💡 **Question:** Use Java 8 **Streams** to find the **first non-repeating character** in a given string.  

🔹 **Input:**  
```java
String input = "swiss";
```
🔹 **Expected Output:**  
```
w
```
(If all characters repeat, return `"No unique character"`)

---

[⬆ Back to top](#table-of-contents)

## **15. Convert a Map to a List of Keys Using Streams**  
💡 **Question:** Given a `Map<String, Integer>`, use Java 8 **Streams** to extract **all keys** into a list.  

🔹 **Input:**  
```java
Map<String, Integer> map = new HashMap<>();
map.put("A", 10);
map.put("B", 20);
map.put("C", 30);
```
🔹 **Expected Output:**  
```
[A, B, C]
```

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 Parallel Streams - Coding Interview Questions** 🚀  

Java 8 **Parallel Streams** help leverage multi-core processors to process large data sets in parallel, improving performance. Below are some **coding interview questions** on **Parallel Streams**.  

---

[⬆ Back to top](#table-of-contents)

## **1. Convert a List to Parallel Stream and Filter Even Numbers**  
💡 **Question:** Given a list of numbers, use **Parallel Stream** to filter only **even numbers**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```
🔹 **Expected Output (Order Not Guaranteed):**  
```
[2, 4, 6, 8, 10]
```

---

[⬆ Back to top](#table-of-contents)

## **2. Find the Maximum Number Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to find the **maximum number** in a list.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(3, 7, 2, 8, 5);
```
🔹 **Expected Output:**  
```
8
```

---

[⬆ Back to top](#table-of-contents)

## **3. Sum of All Elements Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to compute the **sum of all elements** in a list.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
```
🔹 **Expected Output:**  
```
150
```

---

[⬆ Back to top](#table-of-contents)

## **4. Convert a List of Strings to Uppercase Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to convert a list of **lowercase strings** to **uppercase**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("java", "parallel", "stream");
```
🔹 **Expected Output:**  
```
[JAVA, PARALLEL, STREAM]
```

---

[⬆ Back to top](#table-of-contents)

## **5. Sort a List in Parallel**  
💡 **Question:** Use **Parallel Stream** to sort a list of numbers **in ascending order**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(5, 3, 8, 1, 9);
```
🔹 **Expected Output:**  
```
[1, 3, 5, 8, 9]
```

---

[⬆ Back to top](#table-of-contents)

## **6. Find Distinct Elements Using Parallel Stream**  
💡 **Question:** Given a list with duplicate numbers, use **Parallel Stream** to return only **unique elements**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 4, 4, 5);
```
🔹 **Expected Output:**  
```
[1, 2, 3, 4, 5]
```

---

[⬆ Back to top](#table-of-contents)

## **7. Count Elements Greater Than 10 Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to count how many numbers are **greater than 10**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(5, 15, 20, 8, 25);
```
🔹 **Expected Output:**  
```
3
```

---

[⬆ Back to top](#table-of-contents)

## **8. Find the Average of a List of Numbers Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to find the **average** of a list of numbers.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
```
🔹 **Expected Output:**  
```
30.0
```

---

[⬆ Back to top](#table-of-contents)

## **9. Convert a List of Strings to a Single Comma-Separated String Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to join a list of strings into a **single comma-separated string**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
```
🔹 **Expected Output (Order Not Guaranteed):**  
```
"apple, banana, cherry"
```

---

[⬆ Back to top](#table-of-contents)

## **10. Find the First Element Greater Than 50 Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to find the **first number greater than 50**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(30, 20, 60, 80, 10);
```
🔹 **Expected Output:**  
```
60
```

---

[⬆ Back to top](#table-of-contents)

## **11. Convert a List of Objects to a List of Names Using Parallel Stream**  
💡 **Question:** Given a list of `Person` objects, use **Parallel Stream** to extract only the **names**.  

🔹 **Class Definition:**  
```java
class Person {
    String name;
    int age;
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```
🔹 **Input:**  
```java
List<Person> people = Arrays.asList(
    new Person("Alice", 25),
    new Person("Bob", 30),
    new Person("Charlie", 35)
);
```
🔹 **Expected Output:**  
```
[Alice, Bob, Charlie]
```

---

[⬆ Back to top](#table-of-contents)

## **12. Parallel Stream vs Sequential Stream Performance Test**  
💡 **Question:** Write a Java program to compare the **execution time** of **Parallel Stream** vs **Sequential Stream** for a large dataset.  

🔹 **Input:**  
```java
List<Integer> numbers = IntStream.range(1, 1000000).boxed().collect(Collectors.toList());
```
🔹 **Expected Output:**  
```
Time taken by Sequential Stream: X ms
Time taken by Parallel Stream: Y ms
```
(Where `Y` is expected to be **less** than `X` in most cases)

---

[⬆ Back to top](#table-of-contents)

## **13. Use `forEachOrdered` with Parallel Stream**  
💡 **Question:** Demonstrate how to use **`forEachOrdered()`** with **Parallel Stream** to maintain the order of elements.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
```
🔹 **Expected Output:**  
```
1 2 3 4 5
```
(Unlike `forEach()`, which may print in **random order**)

---

[⬆ Back to top](#table-of-contents)

## **14. Convert a Map to a List of Values Using Parallel Stream**  
💡 **Question:** Given a `Map<String, Integer>`, use **Parallel Stream** to extract **all values** into a list.  

🔹 **Input:**  
```java
Map<String, Integer> map = new HashMap<>();
map.put("A", 10);
map.put("B", 20);
map.put("C", 30);
```
🔹 **Expected Output:**  
```
[10, 20, 30]
```

---

[⬆ Back to top](#table-of-contents)

## **15. Apply a Function to Each Element and Collect Results Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to apply a **function** (e.g., multiply each number by 2) to all elements and collect the results.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
```
🔹 **Expected Output:**  
```
[2, 4, 6, 8, 10]
```

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 Parallel Streams - Coding Interview Questions** 🚀  

Java 8 **Parallel Streams** help leverage multi-core processors to process large data sets in parallel, improving performance. Below are some **coding interview questions** on **Parallel Streams**.  

---

[⬆ Back to top](#table-of-contents)

## **1. Convert a List to Parallel Stream and Filter Even Numbers**  
💡 **Question:** Given a list of numbers, use **Parallel Stream** to filter only **even numbers**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6, 7, 8, 9, 10);
```
🔹 **Expected Output (Order Not Guaranteed):**  
```
[2, 4, 6, 8, 10]
```

---

[⬆ Back to top](#table-of-contents)

## **2. Find the Maximum Number Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to find the **maximum number** in a list.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(3, 7, 2, 8, 5);
```
🔹 **Expected Output:**  
```
8
```

---

[⬆ Back to top](#table-of-contents)

## **3. Sum of All Elements Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to compute the **sum of all elements** in a list.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
```
🔹 **Expected Output:**  
```
150
```

---

[⬆ Back to top](#table-of-contents)

## **4. Convert a List of Strings to Uppercase Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to convert a list of **lowercase strings** to **uppercase**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("java", "parallel", "stream");
```
🔹 **Expected Output:**  
```
[JAVA, PARALLEL, STREAM]
```

---

[⬆ Back to top](#table-of-contents)

## **5. Sort a List in Parallel**  
💡 **Question:** Use **Parallel Stream** to sort a list of numbers **in ascending order**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(5, 3, 8, 1, 9);
```
🔹 **Expected Output:**  
```
[1, 3, 5, 8, 9]
```

---

[⬆ Back to top](#table-of-contents)

## **6. Find Distinct Elements Using Parallel Stream**  
💡 **Question:** Given a list with duplicate numbers, use **Parallel Stream** to return only **unique elements**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 2, 3, 4, 4, 5);
```
🔹 **Expected Output:**  
```
[1, 2, 3, 4, 5]
```

---

[⬆ Back to top](#table-of-contents)

## **7. Count Elements Greater Than 10 Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to count how many numbers are **greater than 10**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(5, 15, 20, 8, 25);
```
🔹 **Expected Output:**  
```
3
```

---

[⬆ Back to top](#table-of-contents)

## **8. Find the Average of a List of Numbers Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to find the **average** of a list of numbers.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);
```
🔹 **Expected Output:**  
```
30.0
```

---

[⬆ Back to top](#table-of-contents)

## **9. Convert a List of Strings to a Single Comma-Separated String Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to join a list of strings into a **single comma-separated string**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
```
🔹 **Expected Output (Order Not Guaranteed):**  
```
"apple, banana, cherry"
```

---

[⬆ Back to top](#table-of-contents)

## **10. Find the First Element Greater Than 50 Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to find the **first number greater than 50**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(30, 20, 60, 80, 10);
```
🔹 **Expected Output:**  
```
60
```

---

[⬆ Back to top](#table-of-contents)

## **11. Convert a List of Objects to a List of Names Using Parallel Stream**  
💡 **Question:** Given a list of `Person` objects, use **Parallel Stream** to extract only the **names**.  

🔹 **Class Definition:**  
```java
class Person {
    String name;
    int age;
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```
🔹 **Input:**  
```java
List<Person> people = Arrays.asList(
    new Person("Alice", 25),
    new Person("Bob", 30),
    new Person("Charlie", 35)
);
```
🔹 **Expected Output:**  
```
[Alice, Bob, Charlie]
```

---

[⬆ Back to top](#table-of-contents)

## **12. Parallel Stream vs Sequential Stream Performance Test**  
💡 **Question:** Write a Java program to compare the **execution time** of **Parallel Stream** vs **Sequential Stream** for a large dataset.  

🔹 **Input:**  
```java
List<Integer> numbers = IntStream.range(1, 1000000).boxed().collect(Collectors.toList());
```
🔹 **Expected Output:**  
```
Time taken by Sequential Stream: X ms
Time taken by Parallel Stream: Y ms
```
(Where `Y` is expected to be **less** than `X` in most cases)

---

[⬆ Back to top](#table-of-contents)

## **13. Use `forEachOrdered` with Parallel Stream**  
💡 **Question:** Demonstrate how to use **`forEachOrdered()`** with **Parallel Stream** to maintain the order of elements.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
```
🔹 **Expected Output:**  
```
1 2 3 4 5
```
(Unlike `forEach()`, which may print in **random order**)

---

[⬆ Back to top](#table-of-contents)

## **14. Convert a Map to a List of Values Using Parallel Stream**  
💡 **Question:** Given a `Map<String, Integer>`, use **Parallel Stream** to extract **all values** into a list.  

🔹 **Input:**  
```java
Map<String, Integer> map = new HashMap<>();
map.put("A", 10);
map.put("B", 20);
map.put("C", 30);
```
🔹 **Expected Output:**  
```
[10, 20, 30]
```

---

[⬆ Back to top](#table-of-contents)

## **15. Apply a Function to Each Element and Collect Results Using Parallel Stream**  
💡 **Question:** Use **Parallel Stream** to apply a **function** (e.g., multiply each number by 2) to all elements and collect the results.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
```
🔹 **Expected Output:**  
```
[2, 4, 6, 8, 10]
```

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 `map()` Method - Interview Questions** 🚀  

The `map()` method in Java 8 **Streams API** is used to **transform each element** of a stream into another form using a **Function**. Below are some **interview questions** related to the `map()` method, covering **basic to advanced** scenarios.  

---

[⬆ Back to top](#table-of-contents)

### **1. Convert a List of Integers to Their Squares**  
💡 **Question:** Given a list of integers, use the **`map()`** method to return a list of their squares.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
```
🔹 **Expected Output:**  
```
[1, 4, 9, 16, 25]
```

---

[⬆ Back to top](#table-of-contents)

### **2. Convert a List of Strings to Uppercase**  
💡 **Question:** Use **`map()`** to convert a list of **lowercase strings** to **uppercase**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("java", "stream", "map");
```
🔹 **Expected Output:**  
```
[JAVA, STREAM, MAP]
```

---

[⬆ Back to top](#table-of-contents)

### **3. Extract Name from a List of Objects**  
💡 **Question:** Given a list of `Person` objects, use **`map()`** to extract a list of names.  

🔹 **Class Definition:**  
```java
class Person {
    String name;
    int age;
    public Person(String name, int age) {
        this.name = name;
        this.age = age;
    }
}
```
🔹 **Input:**  
```java
List<Person> people = Arrays.asList(
    new Person("Alice", 25),
    new Person("Bob", 30),
    new Person("Charlie", 35)
);
```
🔹 **Expected Output:**  
```
[Alice, Bob, Charlie]
```

---

[⬆ Back to top](#table-of-contents)

### **4. Convert a List of Strings to Their Lengths**  
💡 **Question:** Use **`map()`** to convert a list of strings to a list of **their lengths**.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
```
🔹 **Expected Output:**  
```
[5, 6, 6]
```

---

[⬆ Back to top](#table-of-contents)

### **5. Convert a List of Integers to a List of Their Double Values**  
💡 **Question:** Given a list of integers, use **`map()`** to convert each number to its **double value**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
```
🔹 **Expected Output:**  
```
[2, 4, 6, 8]
```

---

[⬆ Back to top](#table-of-contents)

### **6. Convert a List of Prices from INR to USD (Assume 1 INR = 0.012 USD)**  
💡 **Question:** Use **`map()`** to convert a list of prices from **INR to USD**.  

🔹 **Input:**  
```java
List<Double> pricesInINR = Arrays.asList(100.0, 200.0, 300.0);
```
🔹 **Expected Output:**  
```
[1.2, 2.4, 3.6]
```

---

[⬆ Back to top](#table-of-contents)

### **7. Convert a List of Strings to a List of First Characters**  
💡 **Question:** Use **`map()`** to get the **first character** of each string in a list.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("apple", "banana", "cherry");
```
🔹 **Expected Output:**  
```
[a, b, c]
```

---

[⬆ Back to top](#table-of-contents)

### **8. Extract Domain Names from Email Addresses**  
💡 **Question:** Use **`map()`** to extract **domain names** from email addresses.  

🔹 **Input:**  
```java
List<String> emails = Arrays.asList("john@gmail.com", "alice@yahoo.com", "bob@outlook.com");
```
🔹 **Expected Output:**  
```
[gmail.com, yahoo.com, outlook.com]
```

---

[⬆ Back to top](#table-of-contents)

### **9. Convert a Map to a List of Values Using `map()`**  
💡 **Question:** Given a `Map<String, Integer>`, use **`map()`** to extract **only values** into a list.  

🔹 **Input:**  
```java
Map<String, Integer> map = new HashMap<>();
map.put("A", 10);
map.put("B", 20);
map.put("C", 30);
```
🔹 **Expected Output:**  
```
[10, 20, 30]
```

---

[⬆ Back to top](#table-of-contents)

### **10. Convert a List of Dates to a List of Formatted Strings**  
💡 **Question:** Use **`map()`** to format dates into `"dd-MM-yyyy"` format.  

🔹 **Input:**  
```java
List<LocalDate> dates = Arrays.asList(LocalDate.of(2023, 1, 1), LocalDate.of(2023, 2, 2));
```
🔹 **Expected Output:**  
```
["01-01-2023", "02-02-2023"]
```

---

[⬆ Back to top](#table-of-contents)

### **11. Find the Square Root of Numbers Using `map()`**  
💡 **Question:** Use **`map()`** to find the **square root** of numbers.  

🔹 **Input:**  
```java
List<Double> numbers = Arrays.asList(4.0, 9.0, 16.0);
```
🔹 **Expected Output:**  
```
[2.0, 3.0, 4.0]
```

---

[⬆ Back to top](#table-of-contents)

### **12. Convert a List of Strings to a List of Integers**  
💡 **Question:** Use **`map()`** to convert a list of **String numbers** to **Integer numbers**.  

🔹 **Input:**  
```java
List<String> numbers = Arrays.asList("1", "2", "3", "4");
```
🔹 **Expected Output:**  
```
[1, 2, 3, 4]
```

---

[⬆ Back to top](#table-of-contents)

### **13. Extract File Extensions from a List of Filenames**  
💡 **Question:** Use **`map()`** to extract file **extensions** from a list of filenames.  

🔹 **Input:**  
```java
List<String> files = Arrays.asList("data.txt", "image.jpg", "script.js");
```
🔹 **Expected Output:**  
```
[txt, jpg, js]
```

---

[⬆ Back to top](#table-of-contents)

### **14. Find the ASCII Values of Characters Using `map()`**  
💡 **Question:** Use **`map()`** to get the **ASCII values** of characters in a string.  

🔹 **Input:**  
```java
String input = "Java";
```
🔹 **Expected Output:**  
```
[74, 97, 118, 97]
```

---

[⬆ Back to top](#table-of-contents)

### **15. Handle Null Values Safely Using `Optional.map()`**  
💡 **Question:** Use **`Optional.map()`** to safely transform an `Optional<String>` to uppercase.  

🔹 **Input:**  
```java
Optional<String> name = Optional.of("java");
```
🔹 **Expected Output:**  
```
Optional[JAVA]
```
(If input is `Optional.empty()`, the output should also be `Optional.empty()`)

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 `flatMap()` - Interview Questions** 🚀  

The `flatMap()` method in Java 8 **Streams API** is used to **flatten** a **stream of collections** into a single stream. Below are **important interview questions** on `flatMap()` covering **basic to advanced** scenarios.  

---

[⬆ Back to top](#table-of-contents)

## **1. Difference Between `map()` and `flatMap()`**  
💡 **Question:** What is the difference between `map()` and `flatMap()` in Java 8?  

✅ **Answer:**  
- `map()` **transforms** each element into another object but keeps the structure **nested** (e.g., `Stream<List<T>>`).
- `flatMap()` **flattens** nested structures into a **single stream** (e.g., `Stream<T>`).  
📌 Example:  
```java
List<List<Integer>> nestedList = Arrays.asList(Arrays.asList(1, 2), Arrays.asList(3, 4));
List<Integer> flatList = nestedList.stream()
                                   .flatMap(List::stream)
                                   .collect(Collectors.toList());
// Output: [1, 2, 3, 4]
```

---

[⬆ Back to top](#table-of-contents)

## **2. Flatten a List of Lists Using `flatMap()`**  
💡 **Question:** Given a list of lists, use **`flatMap()`** to return a **flattened list**.  

🔹 **Input:**  
```java
List<List<Integer>> numbers = Arrays.asList(
    Arrays.asList(1, 2, 3),
    Arrays.asList(4, 5, 6),
    Arrays.asList(7, 8, 9)
);
```
🔹 **Expected Output:**  
```
[1, 2, 3, 4, 5, 6, 7, 8, 9]
```

---

[⬆ Back to top](#table-of-contents)

## **3. Convert a List of Strings to a List of Characters Using `flatMap()`**  
💡 **Question:** Given a list of words, return a **list of characters** using `flatMap()`.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("Java", "Stream", "FlatMap");
```
🔹 **Expected Output:**  
```
[J, a, v, a, S, t, r, e, a, m, F, l, a, t, M, a, p]
```

---

[⬆ Back to top](#table-of-contents)

## **4. Flatten a List of Sentences Into a List of Words**  
💡 **Question:** Given a list of **sentences**, return a **list of words** using `flatMap()`.  

🔹 **Input:**  
```java
List<String> sentences = Arrays.asList("Hello World", "Java 8 Streams", "FlatMap Example");
```
🔹 **Expected Output:**  
```
[Hello, World, Java, 8, Streams, FlatMap, Example]
```

---

[⬆ Back to top](#table-of-contents)

## **5. Extract All Unique Words from a List of Sentences Using `flatMap()`**  
💡 **Question:** Given a list of **sentences**, return a **set of unique words** using `flatMap()`.  

🔹 **Input:**  
```java
List<String> sentences = Arrays.asList("Java is fun", "Java is powerful", "Streams are great");
```
🔹 **Expected Output:**  
```
[Java, is, fun, powerful, Streams, are, great]
```

---

[⬆ Back to top](#table-of-contents)

## **6. Extract Phone Numbers from a List of Users Using `flatMap()`**  
💡 **Question:** Given a list of `User` objects, each containing multiple phone numbers, use `flatMap()` to get a **list of all phone numbers**.  

🔹 **Class Definition:**  
```java
class User {
    String name;
    List<String> phoneNumbers;
}
```
🔹 **Input:**  
```java
List<User> users = Arrays.asList(
    new User("Alice", Arrays.asList("123", "456")),
    new User("Bob", Arrays.asList("789", "101"))
);
```
🔹 **Expected Output:**  
```
[123, 456, 789, 101]
```

---

[⬆ Back to top](#table-of-contents)

## **7. Convert a List of `Optional<String>` to a List of Strings Using `flatMap()`**  
💡 **Question:** Convert a list of **`Optional<String>`** values to a **list of non-empty Strings**.  

🔹 **Input:**  
```java
List<Optional<String>> optionalStrings = Arrays.asList(
    Optional.of("Java"),
    Optional.empty(),
    Optional.of("Stream"),
    Optional.of("FlatMap")
);
```
🔹 **Expected Output:**  
```
[Java, Stream, FlatMap]
```

---

[⬆ Back to top](#table-of-contents)

## **8. Flatten a List of `Optional<Integer>` Values Using `flatMap()`**  
💡 **Question:** Given a list of **`Optional<Integer>`**, return a list of **non-empty integers**.  

🔹 **Input:**  
```java
List<Optional<Integer>> optionalNumbers = Arrays.asList(
    Optional.of(10),
    Optional.empty(),
    Optional.of(20),
    Optional.of(30)
);
```
🔹 **Expected Output:**  
```
[10, 20, 30]
```

---

[⬆ Back to top](#table-of-contents)

## **9. Flatten a List of Employee Departments into a Single List Using `flatMap()`**  
💡 **Question:** Given a list of `Employee` objects, where each employee has multiple departments, use `flatMap()` to return a **flat list of departments**.  

🔹 **Class Definition:**  
```java
class Employee {
    String name;
    List<String> departments;
}
```
🔹 **Input:**  
```java
List<Employee> employees = Arrays.asList(
    new Employee("John", Arrays.asList("HR", "Finance")),
    new Employee("Emma", Arrays.asList("IT", "Support"))
);
```
🔹 **Expected Output:**  
```
[HR, Finance, IT, Support]
```

---

[⬆ Back to top](#table-of-contents)

## **10. Flatten a Stream of Lists Using `flatMap()`**  
💡 **Question:** Given a stream of lists, return a **single stream of elements**.  

🔹 **Input:**  
```java
Stream<List<String>> streamOfLists = Stream.of(
    Arrays.asList("a", "b"),
    Arrays.asList("c", "d"),
    Arrays.asList("e", "f")
);
```
🔹 **Expected Output:**  
```
[a, b, c, d, e, f]
```

---

[⬆ Back to top](#table-of-contents)

## **11. Find All Unique Characters in a List of Words Using `flatMap()`**  
💡 **Question:** Given a list of words, return a **set of unique characters** using `flatMap()`.  

🔹 **Input:**  
```java
List<String> words = Arrays.asList("hello", "world");
```
🔹 **Expected Output:**  
```
[h, e, l, o, w, r, d]
```

---

[⬆ Back to top](#table-of-contents)

## **12. Convert a List of Arrays to a Single Flattened List Using `flatMap()`**  
💡 **Question:** Given a list of integer arrays, use `flatMap()` to return a **single list of integers**.  

🔹 **Input:**  
```java
List<int[]> listOfArrays = Arrays.asList(
    new int[]{1, 2, 3},
    new int[]{4, 5, 6}
);
```
🔹 **Expected Output:**  
```
[1, 2, 3, 4, 5, 6]
```

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 Functional Interfaces Supporting Primitive Types - Interview Questions** 🚀  

Java 8 introduced **specialized functional interfaces** for primitive types to **avoid unnecessary boxing/unboxing** and improve performance. These interfaces include:  

1. **`IntFunction<R>`**, **`LongFunction<R>`**, **`DoubleFunction<R>`**  
2. **`IntConsumer`**, **`LongConsumer`**, **`DoubleConsumer`**  
3. **`IntPredicate`**, **`LongPredicate`**, **`DoublePredicate`**  
4. **`IntSupplier`**, **`LongSupplier`**, **`DoubleSupplier`**  
5. **`IntUnaryOperator`**, **`LongUnaryOperator`**, **`DoubleUnaryOperator`**  
6. **`IntBinaryOperator`**, **`LongBinaryOperator`**, **`DoubleBinaryOperator`**  

Below are **Java 8 interview questions** covering these functional interfaces.  

---

[⬆ Back to top](#table-of-contents)

## **1. Find the Square of an Integer Using `IntFunction<R>`**  
💡 **Question:** Use `IntFunction<Integer>` to find the **square** of a number.  

🔹 **Expected Output:**  
```java
Square of 5 is 25
```

---

[⬆ Back to top](#table-of-contents)

## **2. Convert an Integer to a String Using `IntFunction<String>`**  
💡 **Question:** Use `IntFunction<String>` to convert an **integer** to a **string** representation.  

🔹 **Expected Output:**  
```java
Number 100 as a string: "100"
```

---

[⬆ Back to top](#table-of-contents)

## **3. Print a List of Integers Using `IntConsumer`**  
💡 **Question:** Use `IntConsumer` to **print** each number in a list.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);
```
🔹 **Expected Output:**  
```
1 2 3 4 5
```

---

[⬆ Back to top](#table-of-contents)

## **4. Check If a Number Is Even Using `IntPredicate`**  
💡 **Question:** Use `IntPredicate` to check if a number is **even**.  

🔹 **Expected Output:**  
```java
Number 10 is even: true
```

---

[⬆ Back to top](#table-of-contents)

## **5. Generate a Random Number Using `IntSupplier`**  
💡 **Question:** Use `IntSupplier` to generate a **random integer**.  

🔹 **Expected Output:**  
```java
Generated number: 42
```
*(Output may vary each time)*

---

[⬆ Back to top](#table-of-contents)

## **6. Double a Given Number Using `IntUnaryOperator`**  
💡 **Question:** Use `IntUnaryOperator` to **double** an integer.  

🔹 **Expected Output:**  
```java
Double of 5 is 10
```

---

[⬆ Back to top](#table-of-contents)

## **7. Find the Sum of Two Numbers Using `IntBinaryOperator`**  
💡 **Question:** Use `IntBinaryOperator` to **add two numbers**.  

🔹 **Expected Output:**  
```java
Sum of 4 and 6 is 10
```

---

[⬆ Back to top](#table-of-contents)

## **8. Find Maximum of Two Long Numbers Using `LongBinaryOperator`**  
💡 **Question:** Use `LongBinaryOperator` to find the **maximum** of two long numbers.  

🔹 **Expected Output:**  
```java
Max of 10000000000 and 5000000000 is 10000000000
```

---

[⬆ Back to top](#table-of-contents)

## **9. Convert a Double Value to a String Using `DoubleFunction<String>`**  
💡 **Question:** Use `DoubleFunction<String>` to convert a double to a string representation.  

🔹 **Expected Output:**  
```java
Converted double: "3.14159"
```

---

[⬆ Back to top](#table-of-contents)

## **10. Filter Even Numbers from a List Using `IntPredicate`**  
💡 **Question:** Given a list of integers, use `IntPredicate` to filter **even numbers**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);
```
🔹 **Expected Output:**  
```
[2, 4, 6]
```

---

[⬆ Back to top](#table-of-contents)

## **11. Find Factorial of a Number Using `IntUnaryOperator`**  
💡 **Question:** Use `IntUnaryOperator` to compute the **factorial** of a number.  

🔹 **Expected Output:**  
```java
Factorial of 5 is 120
```

---

[⬆ Back to top](#table-of-contents)

## **12. Check If a Number Is Prime Using `IntPredicate`**  
💡 **Question:** Use `IntPredicate` to check if a number is **prime**.  

🔹 **Expected Output:**  
```java
Is 7 prime? true
```

---

[⬆ Back to top](#table-of-contents)

## **13. Convert a List of Integers to Their Squares Using `IntFunction<List<Integer>>`**  
💡 **Question:** Given a list of integers, use `IntFunction` to return their **squares**.  

🔹 **Input:**  
```java
List<Integer> numbers = Arrays.asList(1, 2, 3, 4);
```
🔹 **Expected Output:**  
```
[1, 4, 9, 16]
```

---

[⬆ Back to top](#table-of-contents)

## **14. Find the Sum of an Array Using `IntBinaryOperator`**  
💡 **Question:** Given an array of integers, use `IntBinaryOperator` to compute the **sum**.  

🔹 **Input:**  
```java
int[] arr = {1, 2, 3, 4, 5};
```
🔹 **Expected Output:**  
```
Sum: 15
```

---

[⬆ Back to top](#table-of-contents)

## **15. Generate Fibonacci Sequence Using `IntSupplier`**  
💡 **Question:** Use `IntSupplier` to generate a **Fibonacci sequence**.  

🔹 **Expected Output (First 5 numbers):**  
```java
0 1 1 2 3
```

---

[⬆ Back to top](#table-of-contents)

## ### **Avoiding Boxing and Unboxing with Java 8 Functional Interfaces for Primitives** 🚀  

[⬆ Back to top](#table-of-contents)

#### 🔹 **What Is Boxing and Unboxing?**  
- **Boxing:** Converting a **primitive type** (e.g., `int`) into its corresponding **wrapper class** (`Integer`).  
  - Example: `Integer boxed = Integer.valueOf(10);`  
- **Unboxing:** Converting a **wrapper class** back into a **primitive type**.  
  - Example: `int unboxed = boxed.intValue();`  

[⬆ Back to top](#table-of-contents)

#### 🔹 **Why Is Boxing/Unboxing a Problem?**  
- **Performance overhead:** Each boxing operation involves creating an **object** in the heap.  
- **Garbage collection pressure:** More objects lead to **frequent GC cycles**.  
- **Unnecessary memory usage:** Wrapper objects use **more memory** than primitives.  

---

[⬆ Back to top](#table-of-contents)

## **💡 How Do Primitive Functional Interfaces Help?**  

Java 8 introduced **specialized functional interfaces** for **primitive types** (`int`, `long`, `double`).  
These avoid **auto-boxing/unboxing**, reducing memory usage and increasing performance.  

[⬆ Back to top](#table-of-contents)

### **🚀 Example: Without Primitive Functional Interface (Boxing & Unboxing Overhead)**  
[⬆ Back to top](#table-of-contents)

#### ❌ **Using `Function<Integer, Integer>` (Causes Boxing & Unboxing)**
```java
import java.util.function.Function;

public class BoxingExample {
    public static void main(String[] args) {
        Function<Integer, Integer> square = num -> num * num; // Auto-boxing & Unboxing

        int result = square.apply(5); // 5 is auto-boxed to Integer, then unboxed back
        System.out.println(result);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔴 Problem in Above Code**
- `5` (primitive `int`) is **boxed** into `Integer`
- `Integer` is **unboxed** back to `int` when multiplied (`num * num`)
- **Unnecessary performance overhead**  

---

[⬆ Back to top](#table-of-contents)

### **✅ Optimized Code Using `IntFunction<R>` (Avoids Boxing & Unboxing)**  
```java
import java.util.function.IntFunction;

public class PrimitiveFunctionExample {
    public static void main(String[] args) {
        IntFunction<Integer> square = num -> num * num; // No Boxing & Unboxing

        int result = square.apply(5); // No auto-boxing
        System.out.println(result);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔵 Why This Is Better?**
- **`IntFunction<R>` operates directly on `int` values** → No boxing/unboxing needed  
- **Avoids object creation** → Better performance  

---

[⬆ Back to top](#table-of-contents)

## **✅ Functional Interfaces for Primitives and Their Benefits**
| **Standard Interface**       | **Primitive Equivalent**       | **Avoids Boxing/Unboxing?** | **Example** |
|----------------------------|--------------------------------|-----------------------------|-------------|
| `Function<T, R>`           | `IntFunction<R>`, `LongFunction<R>`, `DoubleFunction<R>` | ✅ Yes | `IntFunction<String> intToString = String::valueOf;` |
| `Consumer<T>`              | `IntConsumer`, `LongConsumer`, `DoubleConsumer` | ✅ Yes | `IntConsumer print = System.out::println;` |
| `Predicate<T>`             | `IntPredicate`, `LongPredicate`, `DoublePredicate` | ✅ Yes | `IntPredicate isEven = n -> n % 2 == 0;` |
| `Supplier<T>`              | `IntSupplier`, `LongSupplier`, `DoubleSupplier` | ✅ Yes | `IntSupplier randomInt = () -> new Random().nextInt();` |
| `UnaryOperator<T>`         | `IntUnaryOperator`, `LongUnaryOperator`, `DoubleUnaryOperator` | ✅ Yes | `IntUnaryOperator square = n -> n * n;` |
| `BinaryOperator<T>`        | `IntBinaryOperator`, `LongBinaryOperator`, `DoubleBinaryOperator` | ✅ Yes | `IntBinaryOperator sum = (a, b) -> a + b;` |

---

[⬆ Back to top](#table-of-contents)

## **🚀 More Examples of Avoiding Boxing/Unboxing**

[⬆ Back to top](#table-of-contents)

### **1️⃣ Find Square of a Number Using `IntUnaryOperator` (No Boxing)**  
```java
import java.util.function.IntUnaryOperator;

public class IntUnaryOperatorExample {
    public static void main(String[] args) {
        IntUnaryOperator square = x -> x * x; // Direct int operation

        System.out.println(square.applyAsInt(6)); // Output: 36
    }
}
```
🔹 **`applyAsInt(6)` operates directly on `int` → No boxing/unboxing overhead!**  

---

[⬆ Back to top](#table-of-contents)

### **2️⃣ Print a List of Integers Using `IntConsumer` (No Boxing)**  
```java
import java.util.Arrays;
import java.util.List;
import java.util.function.IntConsumer;

public class IntConsumerExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        numbers.forEach((Integer num) -> System.out.println(num)); // Boxing happens ❌

        // ✅ Use IntConsumer to Avoid Boxing
        numbers.stream().mapToInt(Integer::intValue).forEach((IntConsumer) System.out::println);
    }
}
```
🔹 **Using `IntConsumer` eliminates unnecessary boxing of `Integer` values.**  

---

[⬆ Back to top](#table-of-contents)

### **3️⃣ Filter Even Numbers from a List Using `IntPredicate` (No Boxing)**  
```java
import java.util.Arrays;
import java.util.List;
import java.util.function.IntPredicate;
import java.util.stream.Collectors;

public class IntPredicateExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);

        // ✅ Use IntPredicate to Avoid Boxing
        IntPredicate isEven = num -> num % 2 == 0;
        
        List<Integer> evenNumbers = numbers.stream()
                                           .mapToInt(Integer::intValue) // Convert List<Integer> to IntStream
                                           .filter(isEven) // Use IntPredicate
                                           .boxed() // Convert back to List<Integer>
                                           .collect(Collectors.toList());

        System.out.println(evenNumbers); // Output: [2, 4, 6]
    }
}
```
🔹 **Here, `mapToInt(Integer::intValue)` avoids boxing, making filtering more efficient!**  

---

[⬆ Back to top](#table-of-contents)

## **🔥 Key Takeaways**  
✅ **Boxing & Unboxing increases memory usage and CPU overhead.**  
✅ **Primitive Functional Interfaces (`IntFunction`, `IntPredicate`, etc.) prevent boxing/unboxing.**  
✅ **Use `mapToInt()`, `mapToLong()`, `mapToDouble()` in Streams to work with primitives directly.**  
✅ **Prefer primitive functional interfaces for better performance and cleaner code.**  

---

[⬆ Back to top](#table-of-contents)

### **🔴 Without Primitive Functional Interface (Causes Boxing & Unboxing)**  
```java
Function<Integer, Integer> square = x -> x * x; // Boxing and Unboxing happens
```

[⬆ Back to top](#table-of-contents)

### **✅ Using `IntUnaryOperator` (Avoids Boxing & Unboxing)**  
```java
IntUnaryOperator square = x -> x * x; // No Boxing & Unboxing, direct int operation
```

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 Default Method - Coding Interview Questions** 🚀  

Java 8 introduced **default methods** in interfaces, allowing interfaces to have method implementations without breaking existing code. These methods help in extending functionality while maintaining backward compatibility.  

Here are some **coding interview questions** related to **default methods in Java 8**.  

---

[⬆ Back to top](#table-of-contents)

### **1️⃣ Define and Use a Default Method in an Interface**
💡 **Question:**  
Create an interface `Vehicle` with a default method `start()` that prints `"Vehicle is starting"`. Implement this interface in `Car` class and call the `start()` method.  

🔹 **Expected Output:**  
```java
Vehicle is starting
```

---

[⬆ Back to top](#table-of-contents)

### **2️⃣ Override a Default Method in a Class**
💡 **Question:**  
Create an interface `Device` with a default method `turnOn()`. Implement it in a `Phone` class but override `turnOn()` in `Phone` with a custom implementation.  

🔹 **Expected Output:**  
```java
Phone is turning on
```

---

[⬆ Back to top](#table-of-contents)

### **3️⃣ Multiple Interfaces with Same Default Method - How to Resolve Conflict?**  
💡 **Question:**  
What happens if two interfaces have a **default method with the same name**? How do you resolve the **diamond problem** in Java 8?  

**Example:**  
- `Interface A` and `Interface B` both have a default method `show()`.  
- A class `C` implements both interfaces.  
- How can class `C` resolve the method conflict?  

---

[⬆ Back to top](#table-of-contents)

### **4️⃣ Call a Default Method from a Subclass**
💡 **Question:**  
Modify the `Car` class to explicitly call the default method from the interface using `super`.  

🔹 **Expected Output:**  
```java
Car is starting
Vehicle is starting
```

---

[⬆ Back to top](#table-of-contents)

### **5️⃣ Use a Default Method in Functional Interface**
💡 **Question:**  
Java 8 allows functional interfaces to have **default methods**.  
- Define a functional interface `Calculator` with an abstract method `calculate(int a, int b)` and a default method `description()`.  

🔹 **Expected Output:**  
```java
Result: 10
This is a Calculator
```

---

[⬆ Back to top](#table-of-contents)

### **6️⃣ Modify a Default Method in a Sub-interface**
💡 **Question:**  
If interface `A` has a default method `display()`, and interface `B` extends `A`, can `B` modify `display()`?  

🔹 **Expected Output:**  
```java
Modified display from B
```

---

[⬆ Back to top](#table-of-contents)

### **7️⃣ Using Default Method in Java 8 Streams**
💡 **Question:**  
Can you use default methods inside Java 8 Streams?  
Example: Create an interface `MyList` with a default method that filters even numbers from a list using streams.  

🔹 **Expected Output:**  
```java
Filtered List: [2, 4, 6, 8, 10]
```

---

[⬆ Back to top](#table-of-contents)

### **8️⃣ Prevent a Class from Using a Default Method**
💡 **Question:**  
If a class implements an interface with a default method but doesn't want to inherit it, how can it **disable the default method**?  

---

[⬆ Back to top](#table-of-contents)

### **9️⃣ Default Methods in Multiple Inheritance**
💡 **Question:**  
If a class extends a superclass and implements an interface with the same method name as a default method, which method will be called?  

🔹 **Options:**  
1. The method from the superclass  
2. The default method from the interface  
3. Compiler error  

---

[⬆ Back to top](#table-of-contents)

### **🔟 Default Methods and Static Methods in an Interface**
💡 **Question:**  
What is the difference between **default methods** and **static methods** in an interface?  
- Implement a static method in an interface and call it from the main method.  

🔹 **Expected Output:**  
```java
This is a static method in Interface
```

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary of Java 8 Default Methods Concepts:**
✅ **Provide method implementation inside an interface**  
✅ **Can be overridden in implementing classes**  
✅ **Can use `super` to call the interface method explicitly**  
✅ **Solve multiple inheritance conflicts using explicit method override**  

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 Default Method - Scenario-Based Interview Questions** 🚀  

Java 8 **default methods** allow interfaces to have method implementations without breaking existing code. These **scenario-based interview questions** will test your understanding of default methods in **real-world applications**.  

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 1: Adding New Features to an Existing Interface Without Breaking Old Code**  
💡 **Question:**  
Suppose you have an interface `PaymentGateway` used by multiple payment providers. Now, you want to add a method `validateTransaction()`, but modifying all implementing classes is not feasible.  

🔹 **How would you add this new method without breaking existing implementations?**  
🔹 **Can implementing classes still override this method?**  

**Expected Output:**  
```java
Validating transaction using default implementation
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 2: Resolving Conflict When Implementing Multiple Interfaces with Same Default Method**  
💡 **Question:**  
You have two interfaces, `Printer` and `Scanner`, both containing a default method `connect()`. A class `MultiFunctionDevice` implements both.  

🔹 **What happens when you call `connect()` from `MultiFunctionDevice`?**  
🔹 **How will you resolve the conflict?**  

**Expected Output:**  
```java
MultiFunctionDevice: Resolving connect method conflict
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 3: Calling Default Methods from Implementing Class**  
💡 **Question:**  
You have an interface `Vehicle` with a default method `start()`, and a class `Car` implements it.  

🔹 **Modify `Car` to explicitly call `Vehicle`'s default method using `super`.**  

**Expected Output:**  
```java
Car is starting
Vehicle is starting
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 4: Default Method in a Functional Interface**  
💡 **Question:**  
Java 8 allows **functional interfaces** to have **default methods**.  

🔹 **Create a functional interface `Calculator` with:**  
   - An abstract method `calculate(int a, int b)`  
   - A default method `description()`  

🔹 **Can the default method be inherited in a lambda expression?**  

**Expected Output:**  
```java
Result: 15
This is a Calculator
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 5: Overriding a Default Method in a Sub-interface**  
💡 **Question:**  
You have an interface `ParentInterface` with a default method `show()`.  
Another interface `ChildInterface` extends `ParentInterface` but needs to modify `show()`.  

🔹 **Can the sub-interface change the behavior of the default method?**  
🔹 **How will an implementing class behave if it implements `ChildInterface`?**  

**Expected Output:**  
```java
Modified show method in ChildInterface
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 6: Preventing a Class from Using a Default Method**  
💡 **Question:**  
Suppose `InterfaceA` has a default method `logMessage()`.  
A class `MyClass` implements `InterfaceA` but doesn't want to inherit this method.  

🔹 **How can `MyClass` prevent itself from using `logMessage()`?**  

**Expected Output:**  
```java
MyClass: Overriding logMessage to avoid default method
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 7: Superclass vs. Interface Default Method Conflict**  
💡 **Question:**  
A class `SmartDevice` extends a superclass `ElectronicDevice` and implements an interface `ConfigurableDevice`.  
- `ElectronicDevice` has a method `setup()`  
- `ConfigurableDevice` has a default method `setup()`  

🔹 **Which method will `SmartDevice` inherit?**  
🔹 **Can `SmartDevice` explicitly call the interface’s default method?**  

**Expected Output:**  
```java
Setup method from ElectronicDevice
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 8: Using Default Methods in Java 8 Streams**  
💡 **Question:**  
Create an interface `NumberProcessor` with a default method that filters even numbers from a list using Java 8 **Streams**.  

🔹 **Can default methods use Streams inside interfaces?**  
🔹 **Can implementing classes override this behavior?**  

**Expected Output:**  
```java
Filtered List: [2, 4, 6, 8, 10]
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 9: Static vs. Default Methods in Interfaces**  
💡 **Question:**  
You have an interface `Utils` with a **static method** and a **default method**.  

🔹 **Can the static method be overridden?**  
🔹 **How is it different from a default method?**  
🔹 **How do you call a static method from an implementing class?**  

**Expected Output:**  
```java
This is a static method in Interface
This is a default method in Interface
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Scenario 10: Can Default Methods Call Other Abstract Methods?**  
💡 **Question:**  
You have an interface `Logger` with an **abstract method** `log(String message)` and a **default method** `logWithTimestamp()`.  

🔹 **Can the default method call the abstract method inside the interface?**  
🔹 **How does an implementing class handle this scenario?**  

**Expected Output:**  
```java
[2025-02-10] Log message: System started
```

---

[⬆ Back to top](#table-of-contents)

## **🔥 Key Takeaways on Java 8 Default Methods:**
✅ **Used to add new functionality without breaking existing code**  
✅ **Can be overridden in implementing classes**  
✅ **Multiple interfaces with the same default method require explicit resolution**  
✅ **Can be used with Streams and functional interfaces**  
✅ **A class always prefers a superclass method over an interface default method**  

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 `reduce()` - Counting, Average, Max & Min in Streams** 🚀  

The **`reduce()`** method in Java 8 **Streams API** is used for **aggregation operations** like:  
✅ **Counting elements**  
✅ **Calculating average**  
✅ **Finding maximum & minimum**  

---

[⬆ Back to top](#table-of-contents)

## **🔹 1. Counting Elements Using `reduce()`**
💡 **Question:**  
How can you use `reduce()` to count the number of elements in a list?

[⬆ Back to top](#table-of-contents)

### **✅ Solution:**
```java
import java.util.Arrays;
import java.util.List;

public class ReduceCountExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);

        // Counting elements using reduce()
        int count = numbers.stream()
                           .reduce(0, (subtotal, element) -> subtotal + 1);

        System.out.println("Count of elements: " + count);
    }
}
```
🔹 **Explanation:**  
- `reduce(0, (subtotal, element) -> subtotal + 1)` initializes the count as `0` and increments it for each element.  
- Output:  
  ```
  Count of elements: 5
  ```

📌 **Alternative:** Use `count()` for counting.
```java
long count = numbers.stream().count();
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 2. Calculating Average Using `reduce()`**
💡 **Question:**  
How can you calculate the **average** of numbers using `reduce()`?

[⬆ Back to top](#table-of-contents)

### **✅ Solution:**
```java
import java.util.Arrays;
import java.util.List;

public class ReduceAverageExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);

        // Calculate sum and count using reduce()
        int sum = numbers.stream().reduce(0, Integer::sum);
        long count = numbers.stream().count();

        double average = count == 0 ? 0 : (double) sum / count;
        
        System.out.println("Average: " + average);
    }
}
```
🔹 **Explanation:**  
- First, we use `reduce()` to calculate the **sum**.  
- Then, we use `count()` to count the elements.  
- Finally, we calculate **average = sum / count**.  
- Output:  
  ```
  Average: 30.0
  ```

📌 **Alternative:** Use `mapToInt().average()`
```java
double avg = numbers.stream().mapToInt(Integer::intValue).average().orElse(0);
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 3. Finding Maximum Using `reduce()`**
💡 **Question:**  
How can you find the **maximum number** using `reduce()`?

[⬆ Back to top](#table-of-contents)

### **✅ Solution:**
```java
import java.util.Arrays;
import java.util.List;

public class ReduceMaxExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 20, 5, 40, 50);

        // Finding max using reduce()
        int max = numbers.stream().reduce(Integer.MIN_VALUE, Integer::max);

        System.out.println("Maximum value: " + max);
    }
}
```
🔹 **Explanation:**  
- `reduce(Integer.MIN_VALUE, Integer::max)` initializes the minimum value and **compares each element** to find the **max**.  
- Output:  
  ```
  Maximum value: 50
  ```

📌 **Alternative:** Use `max()`
```java
int max = numbers.stream().mapToInt(Integer::intValue).max().orElse(Integer.MIN_VALUE);
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 4. Finding Minimum Using `reduce()`**
💡 **Question:**  
How can you find the **minimum number** using `reduce()`?

[⬆ Back to top](#table-of-contents)

### **✅ Solution:**
```java
import java.util.Arrays;
import java.util.List;

public class ReduceMinExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 20, 5, 40, 50);

        // Finding min using reduce()
        int min = numbers.stream().reduce(Integer.MAX_VALUE, Integer::min);

        System.out.println("Minimum value: " + min);
    }
}
```
🔹 **Explanation:**  
- `reduce(Integer.MAX_VALUE, Integer::min)` initializes **max value** and finds **min** by comparison.  
- Output:  
  ```
  Minimum value: 5
  ```

📌 **Alternative:** Use `min()`
```java
int min = numbers.stream().mapToInt(Integer::intValue).min().orElse(Integer.MAX_VALUE);
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 5. Sum of Numbers Using `reduce()`**
💡 **Question:**  
How can you calculate the **sum** of numbers using `reduce()`?

[⬆ Back to top](#table-of-contents)

### **✅ Solution:**
```java
import java.util.Arrays;
import java.util.List;

public class ReduceSumExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(10, 20, 30, 40, 50);

        // Calculate sum using reduce()
        int sum = numbers.stream().reduce(0, Integer::sum);

        System.out.println("Sum: " + sum);
    }
}
```
🔹 **Explanation:**  
- `reduce(0, Integer::sum)` starts from `0` and **adds each number**.  
- Output:  
  ```
  Sum: 150
  ```

📌 **Alternative:** Use `sum()`
```java
int sum = numbers.stream().mapToInt(Integer::intValue).sum();
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 6. Finding Product of Elements Using `reduce()`**
💡 **Question:**  
How can you find the **product of all numbers** using `reduce()`?

[⬆ Back to top](#table-of-contents)

### **✅ Solution:**
```java
import java.util.Arrays;
import java.util.List;

public class ReduceProductExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        // Calculate product using reduce()
        int product = numbers.stream().reduce(1, (a, b) -> a * b);

        System.out.println("Product: " + product);
    }
}
```
🔹 **Explanation:**  
- `reduce(1, (a, b) -> a * b)` starts from `1` and **multiplies all elements**.  
- Output:  
  ```
  Product: 120
  ```

---

[⬆ Back to top](#table-of-contents)

## **🔹 7. Concatenating Strings Using `reduce()`**
💡 **Question:**  
How can you **concatenate** a list of strings using `reduce()`?

[⬆ Back to top](#table-of-contents)

### **✅ Solution:**
```java
import java.util.Arrays;
import java.util.List;

public class ReduceStringConcatExample {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("Java", "8", "Reduce", "Example");

        // Concatenating strings using reduce()
        String result = words.stream().reduce("", (a, b) -> a + " " + b);

        System.out.println("Concatenated String:" + result.trim());
    }
}
```
🔹 **Explanation:**  
- `reduce("", (a, b) -> a + " " + b)` joins all words into a sentence.  
- Output:  
  ```
  Concatenated String: Java 8 Reduce Example
  ```

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary**
| **Operation** | **Code Using `reduce()`** |
|--------------|--------------------------|
| Count elements | `reduce(0, (subtotal, element) -> subtotal + 1)` |
| Average | `reduce(0, Integer::sum) / count()` |
| Maximum | `reduce(Integer.MIN_VALUE, Integer::max)` |
| Minimum | `reduce(Integer.MAX_VALUE, Integer::min)` |
| Sum | `reduce(0, Integer::sum)` |
| Product | `reduce(1, (a, b) -> a * b)` |
| Concatenate Strings | `reduce("", (a, b) -> a + " " + b)` |

---

[⬆ Back to top](#table-of-contents)

## ### **Java 8 `Collector` Interface – All Functions Explained with Examples** 🚀  

The `Collector<T, A, R>` interface in Java 8 is used to **accumulate input elements** into a **mutable result container**, such as a list, set, or map.  

[⬆ Back to top](#table-of-contents)

#### ✅ **Key Collector Functions:**  
1. **toList()** – Collects elements into a `List`.  
2. **toSet()** – Collects elements into a `Set`.  
3. **toMap()** – Collects elements into a `Map`.  
4. **joining()** – Concatenates strings.  
5. **summarizingInt(), summarizingDouble(), summarizingLong()** – Returns summary statistics.  
6. **partitioningBy()** – Splits data into two groups (true/false).  
7. **groupingBy()** – Groups elements based on a classifier.  
8. **counting()** – Counts the number of elements.  
9. **reducing()** – Performs a reduction operation.  

---

[⬆ Back to top](#table-of-contents)

## **1️⃣ Using `Collectors.toList()` – Convert Stream to List**
💡 **Example:** Convert a list of numbers into another list.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class CollectorExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5);

        List<Integer> result = numbers.stream()
                                      .filter(n -> n % 2 == 0) // Keep only even numbers
                                      .collect(Collectors.toList());

        System.out.println("Even Numbers: " + result);
    }
}
```
**🔹 Output:**  
```
Even Numbers: [2, 4]
```

---

[⬆ Back to top](#table-of-contents)

## **2️⃣ Using `Collectors.toSet()` – Convert Stream to Set**
💡 **Example:** Convert a list with duplicate elements into a `Set` (removes duplicates).

```java
import java.util.Arrays;
import java.util.Set;
import java.util.stream.Collectors;

public class CollectorExample {
    public static void main(String[] args) {
        Set<Integer> uniqueNumbers = Arrays.asList(1, 2, 2, 3, 4, 4, 5).stream()
                                          .collect(Collectors.toSet());

        System.out.println("Unique Numbers: " + uniqueNumbers);
    }
}
```
**🔹 Output:**  
```
Unique Numbers: [1, 2, 3, 4, 5]
```

---

[⬆ Back to top](#table-of-contents)

## **3️⃣ Using `Collectors.toMap()` – Convert Stream to Map**
💡 **Example:** Convert a list of strings into a `Map` where the key is the word, and the value is its length.

```java
import java.util.Arrays;
import java.util.Map;
import java.util.stream.Collectors;

public class CollectorExample {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "banana", "cherry");

        Map<String, Integer> wordLengthMap = words.stream()
                                                 .collect(Collectors.toMap(word -> word, String::length));

        System.out.println("Word Length Map: " + wordLengthMap);
    }
}
```
**🔹 Output:**  
```
Word Length Map: {apple=5, banana=6, cherry=6}
```

---

[⬆ Back to top](#table-of-contents)

## **4️⃣ Using `Collectors.joining()` – Concatenating Strings**
💡 **Example:** Join words into a single string with a separator.

```java
import java.util.Arrays;
import java.util.stream.Collectors;

public class CollectorExample {
    public static void main(String[] args) {
        String result = Arrays.asList("Java", "8", "Collectors", "Example").stream()
                              .collect(Collectors.joining(", "));

        System.out.println("Joined String: " + result);
    }
}
```
**🔹 Output:**  
```
Joined String: Java, 8, Collectors, Example
```

---

[⬆ Back to top](#table-of-contents)

## **5️⃣ Using `Collectors.summarizingInt()` – Summary Statistics**
💡 **Example:** Get count, sum, min, max, and average of numbers.

```java
import java.util.Arrays;
import java.util.IntSummaryStatistics;
import java.util.stream.Collectors;

public class CollectorExample {
    public static void main(String[] args) {
        IntSummaryStatistics stats = Arrays.asList(10, 20, 30, 40, 50).stream()
                                           .collect(Collectors.summarizingInt(Integer::intValue));

        System.out.println("Count: " + stats.getCount());
        System.out.println("Sum: " + stats.getSum());
        System.out.println("Min: " + stats.getMin());
        System.out.println("Max: " + stats.getMax());
        System.out.println("Average: " + stats.getAverage());
    }
}
```
**🔹 Output:**  
```
Count: 5
Sum: 150
Min: 10
Max: 50
Average: 30.0
```

---

[⬆ Back to top](#table-of-contents)

## **6️⃣ Using `Collectors.partitioningBy()` – Partition Data**
💡 **Example:** Split numbers into even and odd groups.

```java
import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

public class CollectorExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(1, 2, 3, 4, 5, 6);

        Map<Boolean, List<Integer>> partitioned = numbers.stream()
                                                         .collect(Collectors.partitioningBy(n -> n % 2 == 0));

        System.out.println("Even Numbers: " + partitioned.get(true));
        System.out.println("Odd Numbers: " + partitioned.get(false));
    }
}
```
**🔹 Output:**  
```
Even Numbers: [2, 4, 6]
Odd Numbers: [1, 3, 5]
```

---

[⬆ Back to top](#table-of-contents)

## **7️⃣ Using `Collectors.groupingBy()` – Group Data**
💡 **Example:** Group words by their lengths.

```java
import java.util.Arrays;
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;

public class CollectorExample {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "banana", "cherry", "dog", "elephant");

        Map<Integer, List<String>> groupedByLength = words.stream()
                                                          .collect(Collectors.groupingBy(String::length));

        System.out.println("Words Grouped by Length: " + groupedByLength);
    }
}
```
**🔹 Output:**  
```
Words Grouped by Length: {3=[dog], 5=[apple], 6=[banana, cherry], 8=[elephant]}
```

---

[⬆ Back to top](#table-of-contents)

## **8️⃣ Using `Collectors.counting()` – Count Elements**
💡 **Example:** Count how many words have more than 5 characters.

```java
import java.util.Arrays;
import java.util.List;
import java.util.stream.Collectors;

public class CollectorExample {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("apple", "banana", "cherry", "dog");

        long count = words.stream()
                          .filter(w -> w.length() > 5)
                          .collect(Collectors.counting());

        System.out.println("Words with more than 5 characters: " + count);
    }
}
```
**🔹 Output:**  
```
Words with more than 5 characters: 2
```

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary: Collectors Functions**
| **Collector Function** | **Purpose** |
|------------------|------------------------|
| `toList()` | Convert stream to List |
| `toSet()` | Convert stream to Set |
| `toMap()` | Convert stream to Map |
| `joining()` | Concatenate elements |
| `summarizingInt()` | Get summary stats (sum, avg, min, max) |
| `partitioningBy()` | Split elements into two groups |
| `groupingBy()` | Group elements based on a property |
| `counting()` | Count the number of elements |
| `reducing()` | Custom aggregation |

---

[⬆ Back to top](#table-of-contents)

## ### **Java `Collector` Interface - Four Core Functions Explained** 🚀  

The **`java.util.stream.Collector<T, A, R>`** interface is used in Java 8 **Streams API** for accumulating elements into a **mutable result container** (e.g., List, Set, Map).  

It has **four main functions**:  
1️⃣ **supplier()** – Provides a new result container (e.g., a new list).  
2️⃣ **accumulator()** – Adds elements to the result container.  
3️⃣ **combiner()** – Merges two partial results (used in parallel processing).  
4️⃣ **finisher()** – Converts the result into the desired final form.  

---

[⬆ Back to top](#table-of-contents)

## **1️⃣ `supplier()` – Creates a New Container**
🔹 This function returns a **supplier** (a factory method) that provides a **mutable container** for accumulating elements.  

[⬆ Back to top](#table-of-contents)

### **Example: Creating a `List`**
```java
Supplier<List<String>> supplier = ArrayList::new;
```
✅ **Explanation:** This **creates a new `ArrayList`** to store the collected elements.  

---

[⬆ Back to top](#table-of-contents)

## **2️⃣ `accumulator()` – Adds Elements to the Container**
🔹 This function returns a **BiConsumer<T, A>**, which takes two arguments:  
   - The **mutable container** (`A`)  
   - The **next element** from the stream (`T`)  

[⬆ Back to top](#table-of-contents)

### **Example: Adding Elements to a `List`**
```java
BiConsumer<List<String>, String> accumulator = List::add;
```
✅ **Explanation:** This function **adds each element from the stream** into the list.  

---

[⬆ Back to top](#table-of-contents)

## **3️⃣ `combiner()` – Merges Two Partial Results**
🔹 This function is used in **parallel streams** to merge two intermediate containers.  
🔹 Returns a **BinaryOperator<A>** that merges two accumulators.  

[⬆ Back to top](#table-of-contents)

### **Example: Merging Two Lists**
```java
BinaryOperator<List<String>> combiner = (list1, list2) -> {
    list1.addAll(list2);
    return list1;
};
```
✅ **Explanation:** This merges two lists when running **parallel streams**.  

---

[⬆ Back to top](#table-of-contents)

## **4️⃣ `finisher()` – Transforms the Result (Optional)**
🔹 This function returns a **Function<A, R>**, which converts the **mutable accumulator** (`A`) into a final **immutable result** (`R`).  
🔹 Often, this is **identity function** (`Function.identity()`) when no transformation is needed.  

[⬆ Back to top](#table-of-contents)

### **Example: Returning an Unmodifiable List**
```java
Function<List<String>, List<String>> finisher = Collections::unmodifiableList;
```
✅ **Explanation:** Converts the **mutable list** into an **immutable one** before returning.  

---

[⬆ Back to top](#table-of-contents)

## **📌 Example: Custom Collector Using All Four Functions**
💡 **Question:** Can you create a custom collector to collect strings into a `List`?

[⬆ Back to top](#table-of-contents)

### **✅ Solution:**
```java
import java.util.*;
import java.util.stream.Collector;
import java.util.stream.Collectors;
import java.util.function.*;
import java.util.stream.Stream;

public class CustomCollectorExample {
    public static void main(String[] args) {
        List<String> words = Arrays.asList("Java", "Streams", "Collector", "Example");

        // Using Custom Collector
        List<String> collectedWords = words.stream().collect(Collector.of(
            ArrayList::new,          // supplier: creates new ArrayList
            List::add,               // accumulator: adds elements
            (list1, list2) -> {      // combiner: merges lists (used in parallel)
                list1.addAll(list2);
                return list1;
            },
            Function.identity()      // finisher: returns the list as is
        ));

        System.out.println("Collected Words: " + collectedWords);
    }
}
```
✅ **Output:**  
```
Collected Words: [Java, Streams, Collector, Example]
```

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary Table**
| **Function**  | **Purpose** | **Example** |
|--------------|------------|------------|
| `supplier()`  | Creates a new container | `ArrayList::new` |
| `accumulator()`  | Adds elements to the container | `List::add` |
| `combiner()`  | Merges two intermediate results | `(list1, list2) -> { list1.addAll(list2); return list1; }` |
| `finisher()`  | Converts the mutable result into a final form | `Function.identity()` |

---

[⬆ Back to top](#table-of-contents)

## ### **`Stream.of(T t)` - Creating a Stream with a Single Element** 🚀  

The **`Stream.of(T t)`** method in Java 8 **creates a Stream containing only one element** of type `T`. This is useful when you need to process a **single element** in a functional way using Java Streams.

---

[⬆ Back to top](#table-of-contents)

## **📌 Syntax**
```java
Stream<T> singleElementStream = Stream.of(T t);
```
Here, `T` is the **type of the element**, and `Stream.of(T t)` creates a **Stream** with just that one element.

---

[⬆ Back to top](#table-of-contents)

## **✅ Example 1: Creating a Single-Element Stream**
```java
import java.util.stream.Stream;

public class StreamOfExample {
    public static void main(String[] args) {
        // Creating a Stream with a single element
        Stream<String> singleStream = Stream.of("Java 8");

        // Processing the single element in the stream
        singleStream.forEach(System.out::println);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **📝 Output:**
```
Java 8
```
✅ **Explanation:** `Stream.of("Java 8")` creates a **Stream** containing only one element (`"Java 8"`), which is then printed using `.forEach()`.

---

[⬆ Back to top](#table-of-contents)

## **✅ Example 2: Applying Stream Operations on a Single Element**
```java
import java.util.stream.Stream;

public class StreamOperations {
    public static void main(String[] args) {
        // Creating a Stream with a single Integer element
        Stream<Integer> singleNumber = Stream.of(10);

        // Doubling the number using map() and printing the result
        singleNumber.map(n -> n * 2).forEach(System.out::println);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **📝 Output:**
```
20
```
✅ **Explanation:**  
1. `Stream.of(10)` creates a **stream with one element (10)**.  
2. `.map(n -> n * 2)` applies a **transformation** (doubles the number).  
3. `.forEach(System.out::println)` prints the result.  

---

[⬆ Back to top](#table-of-contents)

## **✅ Example 3: Using `Stream.of()` with `Optional`**
```java
import java.util.Optional;
import java.util.stream.Stream;

public class OptionalToStream {
    public static void main(String[] args) {
        Optional<String> optionalValue = Optional.of("Hello Java");

        // Convert Optional to Stream
        Stream<String> stream = optionalValue.stream();

        // Print the element
        stream.forEach(System.out::println);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **📝 Output:**
```
Hello Java
```
✅ **Explanation:** The `.stream()` method of `Optional` internally **creates a single-element stream** if the value is present.

---

[⬆ Back to top](#table-of-contents)

## **🔥 Key Takeaways**
| **Method**  | **Description** |
|------------|---------------|
| `Stream.of(T t)`  | Creates a **Stream** containing a **single element** `t` |
| `Stream.of(null)` | Throws `NullPointerException` |
| `Stream.of(Optional<T>.get())` | Can be used with `Optional`, but must check if it's present |

---

[⬆ Back to top](#table-of-contents)

## ### **`Stream.of(Optional<T>.get())` - Explanation with Example** 🚀  

The method **`Optional<T>.get()`** retrieves the value inside an `Optional`, and **`Stream.of(T t)`** creates a **Stream containing that value**.  

[⬆ Back to top](#table-of-contents)

### **⚠️ Important Warning:**  
Using `Optional.get()` directly is **unsafe** because it throws a `NoSuchElementException` if the `Optional` is empty. Instead, **use `optional.stream()`**, which safely returns an **empty Stream if the Optional is empty**.

---

[⬆ Back to top](#table-of-contents)

## **❌ Incorrect Approach: Using `Optional.get()` Directly**
```java
import java.util.Optional;
import java.util.stream.Stream;

public class StreamOfOptionalGetExample {
    public static void main(String[] args) {
        Optional<String> optionalValue = Optional.empty(); // Empty Optional

        // ❌ This will throw NoSuchElementException if Optional is empty
        Stream<String> stream = Stream.of(optionalValue.get());

        // Process the stream
        stream.forEach(System.out::println);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🛑 Output (Exception)**
```
Exception in thread "main" java.util.NoSuchElementException: No value present
```
✅ **Fix:** Always check if `Optional` contains a value before calling `get()`.

---

[⬆ Back to top](#table-of-contents)

## **✅ Correct Approach: Using `Optional.orElse()`**
```java
import java.util.Optional;
import java.util.stream.Stream;

public class SafeStreamExample {
    public static void main(String[] args) {
        Optional<String> optionalValue = Optional.empty();

        // ✅ Avoid NoSuchElementException by using orElse()
        Stream<String> stream = Stream.of(optionalValue.orElse("Default Value"));

        // Print stream elements
        stream.forEach(System.out::println);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **📝 Output:**
```
Default Value
```
✅ **Explanation:** If `optionalValue` is empty, `orElse("Default Value")` returns `"Default Value"`, which is used inside `Stream.of()`.

---

[⬆ Back to top](#table-of-contents)

## **✅ Best Approach: Using `optional.stream()` (Preferred)**
💡 **Java 9 introduced `Optional.stream()`, which converts an `Optional<T>` into a Stream<T>** safely.

```java
import java.util.Optional;
import java.util.stream.Stream;

public class OptionalToStream {
    public static void main(String[] args) {
        Optional<String> optionalValue = Optional.of("Hello Java");

        // ✅ Safe approach: Converts Optional to Stream
        Stream<String> stream = optionalValue.stream();

        // Print elements
        stream.forEach(System.out::println);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **📝 Output:**
```
Hello Java
```
✅ **Why is this better?**
- **If Optional is empty** → `optional.stream()` returns an **empty stream (no exception)**.  
- **If Optional has a value** → Returns a **single-element stream**.  

---

[⬆ Back to top](#table-of-contents)

### **🔥 Key Takeaways**
| **Approach**  | **Safe?** | **Notes** |
|--------------|---------|------------|
| `Stream.of(optional.get())`  | ❌ No | Throws `NoSuchElementException` if empty |
| `Stream.of(optional.orElse("default"))`  | ✅ Yes | Provides a default value |
| `optional.stream()`  | ✅ ✅ Yes (Best) | Converts `Optional<T>` to `Stream<T>` safely |

---

[⬆ Back to top](#table-of-contents)

### **🚀 Final Recommendation:** **Always use `optional.stream()` instead of `Stream.of(optional.get())` for safe and functional programming in Java 8+!**

[⬆ Back to top](#table-of-contents)

## ### **`Collectors.toCollection()` - Explanation with Examples** 🚀  

The **`Collectors.toCollection()`** method in Java 8 allows us to **collect Stream elements** into a specific **mutable collection**, such as `ArrayList`, `HashSet`, `LinkedList`, `TreeSet`, etc. It is useful when you want **more control over the type of collection** than `Collectors.toList()` or `Collectors.toSet()`.  

---

[⬆ Back to top](#table-of-contents)

## **📌 Syntax**
```java
Collectors.toCollection(Supplier<C> collectionFactory)
```
- `collectionFactory`: A **supplier function** that creates the desired collection.

---

[⬆ Back to top](#table-of-contents)

## **✅ 1. Collecting Elements into an `ArrayList`**
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class ToCollectionExample {
    public static void main(String[] args) {
        List<String> names = Stream.of("Alice", "Bob", "Charlie")
            .collect(Collectors.toCollection(ArrayList::new));

        System.out.println(names); 
        // Output: [Alice, Bob, Charlie]
    }
}
```
✅ **Why use `toCollection(ArrayList::new)`?**  
Unlike `toList()`, this allows us to specify an `ArrayList` explicitly.

---

[⬆ Back to top](#table-of-contents)

## **✅ 2. Collecting Elements into a `LinkedList`**
```java
List<Integer> numbers = Stream.of(1, 2, 3, 4, 5)
    .collect(Collectors.toCollection(LinkedList::new));

System.out.println(numbers); 
// Output: [1, 2, 3, 4, 5]
```
✅ **Why `LinkedList`?**  
- Useful if **frequent insertions/deletions** are required.  

---

[⬆ Back to top](#table-of-contents)

## **✅ 3. Collecting Elements into a `HashSet`**
```java
Set<String> uniqueNames = Stream.of("Apple", "Banana", "Apple", "Cherry")
    .collect(Collectors.toCollection(HashSet::new));

System.out.println(uniqueNames); 
// Output: [Apple, Banana, Cherry] (No duplicates)
```
✅ **Why `HashSet`?**  
- Stores **unique elements** and offers **fast lookups**.

---

[⬆ Back to top](#table-of-contents)

## **✅ 4. Collecting Elements into a `TreeSet` (Sorted Order)**
```java
Set<Integer> sortedNumbers = Stream.of(5, 3, 8, 1, 2)
    .collect(Collectors.toCollection(TreeSet::new));

System.out.println(sortedNumbers); 
// Output: [1, 2, 3, 5, 8] (Sorted order)
```
✅ **Why `TreeSet`?**  
- Stores elements in **sorted order**.

---

[⬆ Back to top](#table-of-contents)

## **✅ 5. Collecting Elements into a `LinkedHashSet` (Maintains Insertion Order)**
```java
Set<String> orderedSet = Stream.of("Zebra", "Apple", "Mango", "Banana")
    .collect(Collectors.toCollection(LinkedHashSet::new));

System.out.println(orderedSet); 
// Output: [Zebra, Apple, Mango, Banana] (Insertion order maintained)
```
✅ **Why `LinkedHashSet`?**  
- **Maintains the insertion order**.

---

[⬆ Back to top](#table-of-contents)

## **✅ 6. Collecting Elements into a `PriorityQueue`**
```java
Queue<Integer> priorityQueue = Stream.of(7, 1, 4, 9, 2)
    .collect(Collectors.toCollection(PriorityQueue::new));

System.out.println(priorityQueue); 
// Output: [1, 2, 4, 9, 7] (Heap order)
```
✅ **Why `PriorityQueue`?**  
- Retrieves elements in **natural order**.

---

[⬆ Back to top](#table-of-contents)

## **⚠️ Can We Use `Collectors.toCollection()` to Collect into a `Map`?**
❌ **No**, because `Collectors.toCollection()` works with **collection types (List, Set, Queue, etc.)**, not `Map`.  
✅ Instead, use **`Collectors.toMap()`** to collect elements into a `Map`:

```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class ToMapExample {
    public static void main(String[] args) {
        Map<String, Integer> nameLengthMap = Stream.of("Alice", "Bob", "Charlie")
            .collect(Collectors.toMap(name -> name, String::length));

        System.out.println(nameLengthMap);
        // Output: {Alice=5, Bob=3, Charlie=7}
    }
}
```

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary Table of `Collectors.toCollection()` Usage**
| **Collection Type**  | **Example Code** | **Purpose** |
|------------|---------------|------------|
| `ArrayList` | `Collectors.toCollection(ArrayList::new)` | Default `List` implementation |
| `LinkedList` | `Collectors.toCollection(LinkedList::new)` | Efficient insertions & deletions |
| `HashSet` | `Collectors.toCollection(HashSet::new)` | Removes duplicates, fast lookup |
| `TreeSet` | `Collectors.toCollection(TreeSet::new)` | Sorted set |
| `LinkedHashSet` | `Collectors.toCollection(LinkedHashSet::new)` | Maintains insertion order |
| `PriorityQueue` | `Collectors.toCollection(PriorityQueue::new)` | Elements are retrieved in natural order |

---

[⬆ Back to top](#table-of-contents)

## **🎯 Key Takeaways**
✅ `Collectors.toCollection()` lets you **control the type of collection** used.  
✅ Use it **when `Collectors.toList()` or `Collectors.toSet()` isn't enough**.  
✅ If you need a `Map`, **use `Collectors.toMap()` instead**.  

---

[⬆ Back to top](#table-of-contents)

## **`Comparator` Class Utility Methods in Java (Up to Java 8)** 🚀  

The `Comparator` interface in Java **provides several utility methods** to help with custom sorting. Starting from **Java 8**, new **default and static methods** were added to make comparisons more powerful and flexible.

---

[⬆ Back to top](#table-of-contents)

## **✅ 1. `comparing()` - Creates a Comparator for an Object Field**
**📌 Syntax:**  
```java
Comparator<T> comparing(Function<T, U> keyExtractor)
```
**🔹 Example: Sorting a list of Strings by length**
```java
import java.util.*;
import java.util.stream.Collectors;

public class ComparatorExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Alice", "Bob", "Charlie");

        // Sort by length using Comparator.comparing()
        List<String> sortedNames = names.stream()
            .sorted(Comparator.comparing(String::length))
            .collect(Collectors.toList());

        System.out.println(sortedNames);
        // Output: [Bob, Alice, Charlie] (Sorted by string length)
    }
}
```
✅ **Why Use `comparing()`?**  
- Helps create **custom comparators** using method references (`String::length`).
- Makes sorting more **readable and concise**.

---

[⬆ Back to top](#table-of-contents)

## **✅ 2. `comparingInt()`, `comparingLong()`, `comparingDouble()` - Primitive Comparisons**
Java 8 introduced specialized comparators for **primitive types** to avoid unnecessary boxing/unboxing.

**📌 Syntax:**  
```java
Comparator<T> comparingInt(ToIntFunction<T> keyExtractor)
Comparator<T> comparingLong(ToLongFunction<T> keyExtractor)
Comparator<T> comparingDouble(ToDoubleFunction<T> keyExtractor)
```
**🔹 Example: Sorting Employees by Salary (Primitive `int`)**
```java
import java.util.*;

class Employee {
    String name;
    int salary;

    Employee(String name, int salary) {
        this.name = name;
        this.salary = salary;
    }
}

public class ComparatorPrimitiveExample {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("Alice", 5000),
            new Employee("Bob", 7000),
            new Employee("Charlie", 4000)
        );

        // Sorting by salary
        employees.sort(Comparator.comparingInt(emp -> emp.salary));

        // Print sorted employees
        employees.forEach(emp -> System.out.println(emp.name + ": " + emp.salary));
        // Output: Charlie: 4000, Alice: 5000, Bob: 7000
    }
}
```
✅ **Why Use `comparingInt()`?**  
- Avoids **unnecessary boxing/unboxing** when working with primitives.
- **More efficient** than `Comparator.comparing()` with wrapper types.

---

[⬆ Back to top](#table-of-contents)

## **✅ 3. `thenComparing()` - Secondary Sorting**
Used for **chained comparisons**, allowing sorting by multiple fields.

**📌 Syntax:**  
```java
Comparator<T> thenComparing(Comparator<? super T> other)
Comparator<T> thenComparing(Function<? super T, ? extends U> keyExtractor)
Comparator<T> thenComparingInt(ToIntFunction<? super T> keyExtractor)
Comparator<T> thenComparingLong(ToLongFunction<? super T> keyExtractor)
Comparator<T> thenComparingDouble(ToDoubleFunction<? super T> keyExtractor)
```
**🔹 Example: Sorting Employees by Salary, then by Name**
```java
import java.util.*;

class Employee {
    String name;
    int salary;

    Employee(String name, int salary) {
        this.name = name;
        this.salary = salary;
    }
}

public class ThenComparingExample {
    public static void main(String[] args) {
        List<Employee> employees = Arrays.asList(
            new Employee("Alice", 5000),
            new Employee("Bob", 5000),
            new Employee("Charlie", 4000)
        );

        // Sorting by salary, then by name
        employees.sort(
            Comparator.comparingInt(emp -> emp.salary)
                      .thenComparing(emp -> emp.name)
        );

        employees.forEach(emp -> System.out.println(emp.name + ": " + emp.salary));
        // Output:
        // Charlie: 4000
        // Alice: 5000
        // Bob: 5000
    }
}
```
✅ **Why Use `thenComparing()`?**  
- Allows **sorting by multiple fields** in a clean, readable way.

---

[⬆ Back to top](#table-of-contents)

## **✅ 4. `reverseOrder()` - Reverse Natural Ordering**
Used to **sort in descending order** based on natural ordering.

**📌 Syntax:**  
```java
Comparator<T> reverseOrder()
```
**🔹 Example: Sorting Numbers in Descending Order**
```java
import java.util.*;

public class ReverseOrderExample {
    public static void main(String[] args) {
        List<Integer> numbers = Arrays.asList(5, 2, 9, 1);

        // Sort in reverse order
        numbers.sort(Comparator.reverseOrder());

        System.out.println(numbers);
        // Output: [9, 5, 2, 1]
    }
}
```
✅ **Why Use `reverseOrder()`?**  
- Simplifies **sorting in descending order**.

---

[⬆ Back to top](#table-of-contents)

## **✅ 5. `naturalOrder()` - Sorting in Ascending Order**
Explicitly sorts elements in **natural order**.

**📌 Syntax:**  
```java
Comparator<T> naturalOrder()
```
**🔹 Example: Sorting Strings Alphabetically**
```java
import java.util.*;

public class NaturalOrderExample {
    public static void main(String[] args) {
        List<String> fruits = Arrays.asList("Mango", "Banana", "Apple");

        // Sort in natural order (A-Z)
        fruits.sort(Comparator.naturalOrder());

        System.out.println(fruits);
        // Output: [Apple, Banana, Mango]
    }
}
```
✅ **Why Use `naturalOrder()`?**  
- Explicitly enforces **default sorting order**.

---

[⬆ Back to top](#table-of-contents)

## **✅ 6. `nullsFirst()` & `nullsLast()` - Handling `null` Values**
- `nullsFirst()` → **Null values come first**
- `nullsLast()` → **Null values come last**

**📌 Syntax:**  
```java
Comparator<T> nullsFirst(Comparator<? super T> comparator)
Comparator<T> nullsLast(Comparator<? super T> comparator)
```
**🔹 Example: Sorting with `null` Values**
```java
import java.util.*;

public class NullHandlingExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Charlie", null, "Alice", "Bob");

        // Sort with nulls first
        names.sort(Comparator.nullsFirst(Comparator.naturalOrder()));

        System.out.println(names);
        // Output: [null, Alice, Bob, Charlie]
    }
}
```
✅ **Why Use `nullsFirst()` or `nullsLast()`?**  
- Prevents `NullPointerException` when sorting.

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary Table**
| **Method**          | **Purpose** |
|---------------------|------------|
| `comparing()`       | Sorts using an object's field |
| `comparingInt()`    | Efficient sorting for `int` fields |
| `comparingLong()`   | Efficient sorting for `long` fields |
| `comparingDouble()` | Efficient sorting for `double` fields |
| `thenComparing()`   | Adds secondary sorting |
| `reverseOrder()`    | Sorts in descending order |
| `naturalOrder()`    | Sorts in ascending order |
| `nullsFirst()`      | Places `null` values first |
| `nullsLast()`       | Places `null` values last |

---

[⬆ Back to top](#table-of-contents)

## **🎯 Key Takeaways**
✅ Java 8 added **powerful default and static methods** to `Comparator`.  
✅ Use `comparing()` for **custom sorting** and `thenComparing()` for **multi-level sorting**.  
✅ `nullsFirst()` and `nullsLast()` **avoid `NullPointerException`**.  
✅ `comparingInt()`, `comparingLong()`, and `comparingDouble()` are **more efficient for primitives**.  

---

[⬆ Back to top](#table-of-contents)

## **`Comparator.naturalOrder()`**
- Returns a **Comparator** that sorts elements in their **natural order** (ascending for numbers, lexicographical for strings).
- Requires elements to implement `Comparable<T>`.
- Equivalent to **"ascending order" sorting**.

**✅ Example: Sorting Strings in Natural Order**
```java
import java.util.*;

public class NaturalOrderExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Charlie", "Alice", "Bob");

        // Sort in natural order (A-Z)
        names.sort(Comparator.naturalOrder());

        System.out.println(names);
        // Output: [Alice, Bob, Charlie]
    }
}
```

---

[⬆ Back to top](#table-of-contents)

## **`Comparator.reverseOrder()`**
- Returns a **Comparator** that sorts elements in **reverse of their natural order**.
- Equivalent to **"descending order" sorting**.

**✅ Example: Sorting Strings in Reverse Order**
```java
import java.util.*;

public class ReverseOrderExample {
    public static void main(String[] args) {
        List<String> names = Arrays.asList("Charlie", "Alice", "Bob");

        // Sort in reverse order (Z-A)
        names.sort(Comparator.reverseOrder());

        System.out.println(names);
        // Output: [Charlie, Bob, Alice]
    }
}
```

---

[⬆ Back to top](#table-of-contents)

## **🚀 Key Differences**
| **Feature**               | **Comparator.naturalOrder()** | **Comparator.reverseOrder()** |
|---------------------------|------------------------------|------------------------------|
| **Sorting Order**         | Ascending (A-Z, 1-9)        | Descending (Z-A, 9-1)       |
| **Example Output (Strings)** | `[Alice, Bob, Charlie]`  | `[Charlie, Bob, Alice]`  |
| **Example Output (Numbers)** | `[1, 2, 3, 4, 5]`      | `[5, 4, 3, 2, 1]`       |

---

[⬆ Back to top](#table-of-contents)

## **🎯 Key Takeaways**
✅ **Use `naturalOrder()`** when you need **default (ascending) sorting**.  
✅ **Use `reverseOrder()`** when you need **descending sorting**.  

---

[⬆ Back to top](#table-of-contents)

### **Java 8 `Collectors` Class - All Utility Methods with Examples** 🚀  

The `java.util.stream.Collectors` class provides **static factory methods** for reducing, grouping, and collecting Stream elements. These methods are primarily used with the `.collect()` terminal operation in Java Streams.

---

[⬆ Back to top](#table-of-contents)

## **📌 1. Collecting into a List, Set, or Map**
[⬆ Back to top](#table-of-contents)

### **✅ `toList()` - Collects Elements into a List**
```java
List<String> names = Stream.of("Alice", "Bob", "Charlie")
    .collect(Collectors.toList());

System.out.println(names);
// Output: [Alice, Bob, Charlie]
```
- **Returns an `ArrayList` by default.**

---

[⬆ Back to top](#table-of-contents)

### **✅ `toSet()` - Collects Elements into a Set**
```java
Set<Integer> numbers = Stream.of(1, 2, 2, 3, 4)
    .collect(Collectors.toSet());

System.out.println(numbers);
// Output: [1, 2, 3, 4] (Removes duplicates)
```
- **Returns a `HashSet` by default.**

---

[⬆ Back to top](#table-of-contents)

### **✅ `toMap()` - Collects Elements into a Map**
```java
Map<String, Integer> nameLengthMap = Stream.of("Alice", "Bob", "Charlie")
    .collect(Collectors.toMap(name -> name, String::length));

System.out.println(nameLengthMap);
// Output: {Alice=5, Bob=3, Charlie=7}
```
- **Requires key and value mapping functions.**
- **Throws an exception if duplicate keys exist!** Use `(key1, key2) -> key1` to resolve conflicts.

---

[⬆ Back to top](#table-of-contents)

## **📌 2. Grouping and Partitioning**
[⬆ Back to top](#table-of-contents)

### **✅ `groupingBy()` - Groups Elements by a Key**
```java
Map<Integer, List<String>> groupedByLength = Stream.of("one", "two", "three", "four", "five")
    .collect(Collectors.groupingBy(String::length));

System.out.println(groupedByLength);
// Output: {3=[one, two], 4=[four, five], 5=[three]}
```
- **Groups elements into a `Map<K, List<V>>`.**
- You can also specify a downstream collector.

---

[⬆ Back to top](#table-of-contents)

### **✅ `partitioningBy()` - Splits Data into Two Groups (Boolean Predicate)**
```java
Map<Boolean, List<Integer>> evenOddPartition = Stream.of(1, 2, 3, 4, 5, 6)
    .collect(Collectors.partitioningBy(num -> num % 2 == 0));

System.out.println(evenOddPartition);
// Output: {false=[1, 3, 5], true=[2, 4, 6]}
```
- **Partitions elements into `true` (match) and `false` (no match).**
- Always returns a **Map<Boolean, List<T>>**.

---

[⬆ Back to top](#table-of-contents)

## **📌 3. Reducing and Summarizing**
[⬆ Back to top](#table-of-contents)

### **✅ `counting()` - Counts the Number of Elements**
```java
long count = Stream.of("A", "B", "C").collect(Collectors.counting());

System.out.println(count); // Output: 3
```
- **Equivalent to `stream.count()` but inside `collect()`**.

---

[⬆ Back to top](#table-of-contents)

### **✅ `summarizingInt()` / `summarizingDouble()` / `summarizingLong()` - Summary Statistics**
```java
IntSummaryStatistics stats = Stream.of(5, 10, 15, 20)
    .collect(Collectors.summarizingInt(Integer::intValue));

System.out.println(stats);
// Output: IntSummaryStatistics{count=4, sum=50, min=5, average=12.5, max=20}
```
- Provides **count, sum, min, max, and average**.

---

[⬆ Back to top](#table-of-contents)

### **✅ `reducing()` - Custom Reduction**
```java
Optional<Integer> sum = Stream.of(1, 2, 3, 4)
    .collect(Collectors.reducing((a, b) -> a + b));

System.out.println(sum.get()); // Output: 10
```
- **Similar to `reduce()` but used inside `collect()`**.

---

[⬆ Back to top](#table-of-contents)

## **📌 4. Joining Strings**
[⬆ Back to top](#table-of-contents)

### **✅ `joining()` - Concatenates Strings**
```java
String result = Stream.of("Apple", "Banana", "Cherry")
    .collect(Collectors.joining(", "));

System.out.println(result);
// Output: Apple, Banana, Cherry
```
- **By default, no delimiter, but you can add one (`", "`)**.
- **Also supports prefix and suffix.**

---

[⬆ Back to top](#table-of-contents)

## **📌 5. Mapping & Collecting**
[⬆ Back to top](#table-of-contents)

### **✅ `mapping()` - Transforms Elements Before Collecting**
```java
List<Integer> nameLengths = Stream.of("Alice", "Bob", "Charlie")
    .collect(Collectors.mapping(String::length, Collectors.toList()));

System.out.println(nameLengths);
// Output: [5, 3, 7]
```
- **Transforms data before collecting into another collection**.

---

[⬆ Back to top](#table-of-contents)

## **📌 6. Collecting into Custom Collections**
[⬆ Back to top](#table-of-contents)

### **✅ `toCollection()` - Collecting into a Specific Collection Type**
```java
LinkedList<String> names = Stream.of("A", "B", "C")
    .collect(Collectors.toCollection(LinkedList::new));

System.out.println(names);
// Output: [A, B, C]
```
- **Lets you specify the type of collection (e.g., `LinkedList`, `TreeSet`)**.

---

[⬆ Back to top](#table-of-contents)

## **📌 Summary Table**
| **Method**              | **Description** | **Returns** |
|------------------------|-----------------|-------------|
| `toList()`             | Collects elements into a `List` | `List<T>` |
| `toSet()`              | Collects elements into a `Set` | `Set<T>` |
| `toMap()`              | Collects elements into a `Map` | `Map<K, V>` |
| `groupingBy()`         | Groups elements based on a function | `Map<K, List<T>>` |
| `partitioningBy()`     | Splits elements into two groups | `Map<Boolean, List<T>>` |
| `counting()`           | Counts elements in the stream | `Long` |
| `summarizingInt()`     | Provides summary statistics for `int` values | `IntSummaryStatistics` |
| `summarizingDouble()`  | Provides summary statistics for `double` values | `DoubleSummaryStatistics` |
| `summarizingLong()`    | Provides summary statistics for `long` values | `LongSummaryStatistics` |
| `reducing()`           | Performs custom reduction | `Optional<T>` or `T` |
| `joining()`            | Concatenates Strings | `String` |
| `mapping()`            | Applies a function before collecting | Custom Collection |
| `toCollection()`       | Collects elements into a specific collection | Custom Collection |

---

[⬆ Back to top](#table-of-contents)

## **🔥 Key Takeaways**
✅ **`Collectors.toList()` and `Collectors.toSet()`** are the most commonly used.  
✅ **`groupingBy()` and `partitioningBy()`** are powerful for categorizing data.  
✅ **`reducing()` is similar to `reduce()`, but used inside `collect()`**.  
✅ **`joining()` is great for concatenating strings in a list**.  
✅ **`toCollection()` allows you to collect into a `LinkedList`, `TreeSet`, etc.**  

---

[⬆ Back to top](#table-of-contents)

## **`Collectors.collectingAndThen()` - Java 8 Explained with Examples** 🚀

[⬆ Back to top](#table-of-contents)

### **📌 What is `collectingAndThen()`?**
`Collectors.collectingAndThen()` is a **wrapper collector** that **modifies** the result of another collector using a **finishing function**.

[⬆ Back to top](#table-of-contents)

### **📌 Method Signature:**
```java
public static <T, A, R, RR> Collector<T, A, RR> collectingAndThen(
        Collector<T, A, R> downstream,
        Function<R, RR> finisher
)
```
[⬆ Back to top](#table-of-contents)

### **📌 Key Points:**
1. **First Collector (`downstream`)** - Collects stream elements (e.g., `toList()`, `toSet()`, etc.).
2. **Finishing Function (`finisher`)** - Applies transformation on the collected result.
3. **Immutable Wrapping** - Often used to **make collections immutable**.

---

[⬆ Back to top](#table-of-contents)

## **1️⃣ Example: Collect List and Make it Immutable**
[⬆ Back to top](#table-of-contents)

### ✅ **Use Case: Prevent Modification After Collection**
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectingAndThenExample1 {
    public static void main(String[] args) {
        List<String> names = Stream.of("Alice", "Bob", "Charlie")
            .collect(Collectors.collectingAndThen(
                Collectors.toList(),  // Step 1: Collect into a List
                Collections::unmodifiableList // Step 2: Make it Immutable
            ));

        System.out.println(names);  // Output: [Alice, Bob, Charlie]

        // Trying to modify the list will throw an exception
        names.add("David");  // Throws UnsupportedOperationException
    }
}
```
✔ **Why?**  
- `toList()` collects elements into a `List<String>`.  
- `Collections.unmodifiableList()` **makes it immutable**.

---

[⬆ Back to top](#table-of-contents)

## **2️⃣ Example: Get Maximum Value Using CollectingAndThen**
[⬆ Back to top](#table-of-contents)

### ✅ **Use Case: Find Maximum Element Using a Comparator**
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectingAndThenExample2 {
    public static void main(String[] args) {
        Integer maxNumber = Stream.of(10, 20, 30, 40, 50)
            .collect(Collectors.collectingAndThen(
                Collectors.maxBy(Comparator.naturalOrder()),  // Step 1: Find Max
                Optional::get // Step 2: Extract value from Optional
            ));

        System.out.println(maxNumber);  // Output: 50
    }
}
```
✔ **Why?**  
- `Collectors.maxBy(Comparator.naturalOrder())` **returns an Optional**.
- `Optional.get()` extracts the value.

---

[⬆ Back to top](#table-of-contents)

## **3️⃣ Example: Counting Elements and Converting to String**
[⬆ Back to top](#table-of-contents)

### ✅ **Use Case: Get Number of Elements as String**
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectingAndThenExample3 {
    public static void main(String[] args) {
        String countString = Stream.of("A", "B", "C", "D")
            .collect(Collectors.collectingAndThen(
                Collectors.counting(),  // Step 1: Count elements
                count -> "Total Elements: " + count // Step 2: Convert to String
            ));

        System.out.println(countString);  
        // Output: Total Elements: 4
    }
}
```
✔ **Why?**  
- `counting()` **counts the elements** in the stream.
- The finisher function **converts count to a formatted string**.

---

[⬆ Back to top](#table-of-contents)

## **4️⃣ Example: Collect into a Custom Collection**
[⬆ Back to top](#table-of-contents)

### ✅ **Use Case: Collect as `TreeSet` (Sorted Order)**
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectingAndThenExample4 {
    public static void main(String[] args) {
        Set<String> sortedSet = Stream.of("Banana", "Apple", "Cherry", "Mango")
            .collect(Collectors.collectingAndThen(
                Collectors.toCollection(TreeSet::new),  // Step 1: Collect as TreeSet
                Collections::unmodifiableSet // Step 2: Make Immutable
            ));

        System.out.println(sortedSet);  
        // Output: [Apple, Banana, Cherry, Mango]

        sortedSet.add("Orange"); // Throws UnsupportedOperationException
    }
}
```
✔ **Why?**  
- `toCollection(TreeSet::new)` ensures elements are **sorted**.
- `unmodifiableSet()` **makes it immutable**.

---

[⬆ Back to top](#table-of-contents)

## **5️⃣ Example: Convert List to Comma-Separated String**
[⬆ Back to top](#table-of-contents)

### ✅ **Use Case: Format List as a String**
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectingAndThenExample5 {
    public static void main(String[] args) {
        String result = Stream.of("Red", "Green", "Blue")
            .collect(Collectors.collectingAndThen(
                Collectors.joining(", "),  // Step 1: Join as "Red, Green, Blue"
                str -> "Colors: [" + str + "]" // Step 2: Format the String
            ));

        System.out.println(result);  
        // Output: Colors: [Red, Green, Blue]
    }
}
```
✔ **Why?**  
- `joining(", ")` joins elements with a comma separator.
- The finisher function **adds square brackets for formatting**.

---

[⬆ Back to top](#table-of-contents)

## **6️⃣ Example: Convert List to Uppercase After Collection**
[⬆ Back to top](#table-of-contents)

### ✅ **Use Case: Modify List After Collection**
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectingAndThenExample6 {
    public static void main(String[] args) {
        List<String> upperCaseNames = Stream.of("john", "jane", "jack")
            .collect(Collectors.collectingAndThen(
                Collectors.toList(),  // Step 1: Collect into List
                list -> list.stream().map(String::toUpperCase).collect(Collectors.toList()) // Step 2: Convert to Uppercase
            ));

        System.out.println(upperCaseNames);  
        // Output: [JOHN, JANE, JACK]
    }
}
```
✔ **Why?**  
- Collects into a `List<String>`.  
- Finisher function **converts all names to uppercase**.

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary of Use Cases**
| **Use Case** | **Code Example** |
|-------------|----------------|
| Make List Immutable | `collectingAndThen(toList(), unmodifiableList())` |
| Get Maximum Element | `collectingAndThen(maxBy(), Optional::get)` |
| Convert Count to String | `collectingAndThen(counting(), count -> "Total: " + count)` |
| Collect as `TreeSet` | `collectingAndThen(toCollection(TreeSet::new), unmodifiableSet())` |
| Join as String | `collectingAndThen(joining(", "), str -> "List: " + str)` |
| Convert List to Uppercase | `collectingAndThen(toList(), list -> list.stream().map(String::toUpperCase).toList())` |

---

[⬆ Back to top](#table-of-contents)

### **🚀 Key Takeaways**
✅ `collectingAndThen()` is useful for **post-processing collected data**.  
✅ Often used to **make collections immutable** (`unmodifiableList()`, `unmodifiableSet()`).  
✅ Can **unwrap Optionals**, **format output**, **apply transformations**, and **convert types**.  

---

[⬆ Back to top](#table-of-contents)

## **🎯 Interview Question**
**Q:** "How would you collect a stream into a sorted, immutable `Set` using Java 8?"  
**A:**  
```java
Set<Integer> numbers = Stream.of(5, 3, 8, 1)
    .collect(Collectors.collectingAndThen(
        Collectors.toCollection(TreeSet::new),
        Collections::unmodifiableSet
    ));
```
---

[⬆ Back to top](#table-of-contents)

## ## **📌 Complete List of Utility Methods in `Collectors` Class (Java 8+)**  

The `Collectors` class in Java **(java.util.stream.Collectors)** provides **static factory methods** to generate `Collector` instances for reducing and accumulating elements in a `Stream`.

---

[⬆ Back to top](#table-of-contents)

## **🔹 List of All Utility Methods in `Collectors`**

[⬆ Back to top](#table-of-contents)

### **1️⃣ Basic Collection Methods**
| **Method** | **Description** |
|------------|----------------|
| `toList()` | Collects elements into a `List<T>`. |
| `toSet()` | Collects elements into a `Set<T>`. |
| `toMap(Function keyMapper, Function valueMapper)` | Collects elements into a `Map<K, V>`. |
| `toMap(Function keyMapper, Function valueMapper, BinaryOperator<V> mergeFunction)` | Collects elements into a `Map<K, V>` and resolves key conflicts. |
| `toUnmodifiableList()` | Collects elements into an **immutable List**. *(Java 10+)* |
| `toUnmodifiableSet()` | Collects elements into an **immutable Set**. *(Java 10+)* |
| `toUnmodifiableMap(Function keyMapper, Function valueMapper)` | Collects elements into an **immutable Map**. *(Java 10+)* |

---

[⬆ Back to top](#table-of-contents)

### **2️⃣ Counting and Summarization**
| **Method** | **Description** |
|------------|----------------|
| `counting()` | Counts the number of elements in a stream. |
| `summingInt(ToIntFunction<T>)` | Computes the sum of `int` values. |
| `summingLong(ToLongFunction<T>)` | Computes the sum of `long` values. |
| `summingDouble(ToDoubleFunction<T>)` | Computes the sum of `double` values. |
| `averagingInt(ToIntFunction<T>)` | Computes the average of `int` values. |
| `averagingLong(ToLongFunction<T>)` | Computes the average of `long` values. |
| `averagingDouble(ToDoubleFunction<T>)` | Computes the average of `double` values. |

---

[⬆ Back to top](#table-of-contents)

### **3️⃣ Finding Min & Max**
| **Method** | **Description** |
|------------|----------------|
| `maxBy(Comparator<T>)` | Finds the **maximum** element using a comparator. |
| `minBy(Comparator<T>)` | Finds the **minimum** element using a comparator. |

---

[⬆ Back to top](#table-of-contents)

### **4️⃣ String Joining**
| **Method** | **Description** |
|------------|----------------|
| `joining()` | Concatenates elements into a single `String`. |
| `joining(CharSequence delimiter)` | Concatenates elements with a **delimiter** (e.g., `", "`). |
| `joining(CharSequence delimiter, CharSequence prefix, CharSequence suffix)` | Concatenates elements with a **delimiter, prefix, and suffix**. |

---

[⬆ Back to top](#table-of-contents)

### **5️⃣ Grouping and Partitioning**
| **Method** | **Description** |
|------------|----------------|
| `groupingBy(Function classifier)` | Groups elements into a `Map<K, List<T>>`. |
| `groupingBy(Function classifier, Collector downstream)` | Groups elements and applies another collector (e.g., `counting()`). |
| `groupingBy(Function classifier, Supplier mapFactory, Collector downstream)` | Groups elements into a **custom `Map` type**. |
| `partitioningBy(Predicate<T> predicate)` | Splits elements into **two groups (`true` and `false`)**. |
| `partitioningBy(Predicate<T> predicate, Collector downstream)` | Splits elements into **two groups** and applies another collector. |

---

[⬆ Back to top](#table-of-contents)

### **6️⃣ Custom Collection Transformation**
| **Method** | **Description** |
|------------|----------------|
| `collectingAndThen(Collector<T, A, R>, Function<R, RR>)` | Applies a transformation after collecting. |
| `reducing(BinaryOperator<T>)` | Performs **reduction** using a binary operation. |
| `reducing(T identity, BinaryOperator<T>)` | Performs reduction with an **initial value**. |
| `reducing(U identity, Function<T, U> mapper, BinaryOperator<U>)` | Maps and reduces elements to a **single value**. |

---

[⬆ Back to top](#table-of-contents)

## **🚀 Example Usage of Each Method**

[⬆ Back to top](#table-of-contents)

### **1️⃣ Collecting into List, Set, and Map**
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectExample {
    public static void main(String[] args) {
        // toList()
        List<String> names = Stream.of("Alice", "Bob", "Charlie")
                .collect(Collectors.toList());
        System.out.println(names);  // [Alice, Bob, Charlie]

        // toSet()
        Set<Integer> uniqueNumbers = Stream.of(1, 2, 3, 3, 2, 1)
                .collect(Collectors.toSet());
        System.out.println(uniqueNumbers);  // [1, 2, 3]

        // toMap()
        Map<Integer, String> nameMap = Stream.of("Alice", "Bob", "Charlie")
                .collect(Collectors.toMap(String::length, name -> name, (existing, replacement) -> existing));
        System.out.println(nameMap);  // {5=Alice, 3=Bob, 7=Charlie}
    }
}
```

---

[⬆ Back to top](#table-of-contents)

### **2️⃣ Counting and Summing**
```java
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CountingExample {
    public static void main(String[] args) {
        long count = Stream.of("Apple", "Banana", "Cherry")
                .collect(Collectors.counting());
        System.out.println(count);  // 3

        int sum = Stream.of(1, 2, 3, 4, 5)
                .collect(Collectors.summingInt(Integer::intValue));
        System.out.println(sum);  // 15
    }
}
```

---

[⬆ Back to top](#table-of-contents)

### **3️⃣ Grouping and Partitioning**
```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class GroupingPartitioningExample {
    public static void main(String[] args) {
        // Grouping by string length
        Map<Integer, List<String>> groupedByLength = Stream.of("one", "two", "three", "four", "five")
                .collect(Collectors.groupingBy(String::length));
        System.out.println(groupedByLength);  // {3=[one, two], 4=[four, five], 5=[three]}

        // Partitioning into even and odd numbers
        Map<Boolean, List<Integer>> partitioned = Stream.of(1, 2, 3, 4, 5)
                .collect(Collectors.partitioningBy(num -> num % 2 == 0));
        System.out.println(partitioned);  // {false=[1, 3, 5], true=[2, 4]}
    }
}
```

---

[⬆ Back to top](#table-of-contents)

### **4️⃣ `collectingAndThen()` - Convert List to Unmodifiable List**
```java
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectingAndThenExample {
    public static void main(String[] args) {
        List<String> names = Stream.of("Alice", "Bob", "Charlie")
                .collect(Collectors.collectingAndThen(Collectors.toList(), Collections::unmodifiableList));

        System.out.println(names);  // [Alice, Bob, Charlie]
        names.add("David");  // Throws UnsupportedOperationException
    }
}
```

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary Table**
| **Method Group** | **Methods** |
|----------------|------------|
| **Basic Collection** | `toList()`, `toSet()`, `toMap()` |
| **Counting & Summing** | `counting()`, `summingInt()`, `averagingInt()` |
| **Min & Max** | `maxBy()`, `minBy()` |
| **Joining Strings** | `joining()` |
| **Grouping & Partitioning** | `groupingBy()`, `partitioningBy()` |
| **Custom Collection** | `collectingAndThen()`, `reducing()` |

---

[⬆ Back to top](#table-of-contents)

## # **📌 `Stream.collect()` Variations Based on Supplied Collector in Java 8+**

The `collect()` method in Java **streams** is a **terminal operation** used to **accumulate elements** into a result container (like `List`, `Set`, `Map`, or even a custom object). It works by **accepting a `Collector`**, which defines how the stream elements are collected.

[⬆ Back to top](#table-of-contents)

## **🚀 Syntax of `collect()`**
```java
<R, A> R collect(Collector<? super T, A, R> collector)
```
- `T` → The type of elements in the stream.
- `A` → The intermediate accumulation type.
- `R` → The final result type.
- `collector` → A `Collector` implementation that defines how to collect elements.

---

[⬆ Back to top](#table-of-contents)

## **🔹 Different `collect()` Variations Based on Supplied `Collector`**
Java provides **`Collectors` utility methods** to supply various predefined collectors.

[⬆ Back to top](#table-of-contents)

### **1️⃣ Collect Elements into a `List`**
```java
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectToList {
    public static void main(String[] args) {
        List<String> names = Stream.of("Alice", "Bob", "Charlie")
                .collect(Collectors.toList());  // Collecting into List

        System.out.println(names);  // Output: [Alice, Bob, Charlie]
    }
}
```
✔ **`toList()`** → Collects elements into a `List<T>`.

---

[⬆ Back to top](#table-of-contents)

### **2️⃣ Collect Elements into a `Set`**
```java
import java.util.Set;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectToSet {
    public static void main(String[] args) {
        Set<Integer> numbers = Stream.of(1, 2, 3, 2, 1)
                .collect(Collectors.toSet());  // Collecting into Set

        System.out.println(numbers);  // Output: [1, 2, 3] (Duplicates removed)
    }
}
```
✔ **`toSet()`** → Collects elements into a `Set<T>` (removes duplicates).

---

[⬆ Back to top](#table-of-contents)

### **3️⃣ Collect Elements into a `Map`**
```java
import java.util.Map;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectToMap {
    public static void main(String[] args) {
        Map<Integer, String> map = Stream.of("Alice", "Bob", "Charlie")
                .collect(Collectors.toMap(
                        String::length, // Key: Length of the string
                        name -> name,   // Value: Name itself
                        (existing, replacement) -> existing // Merge function
                ));

        System.out.println(map);  // Output: {5=Alice, 3=Bob, 7=Charlie}
    }
}
```
✔ **`toMap()`** → Collects elements into a `Map<K, V>`, resolving duplicate keys using a merge function.

---

[⬆ Back to top](#table-of-contents)

### **4️⃣ Collect Elements into an Immutable List**
```java
import java.util.List;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectUnmodifiableList {
    public static void main(String[] args) {
        List<String> names = Stream.of("Alice", "Bob", "Charlie")
                .collect(Collectors.toUnmodifiableList());

        System.out.println(names);  // Output: [Alice, Bob, Charlie]
        names.add("David");  // Throws UnsupportedOperationException
    }
}
```
✔ **`toUnmodifiableList()`** → Creates an immutable `List`.

---

[⬆ Back to top](#table-of-contents)

### **5️⃣ Counting Elements in a Stream**
```java
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectCounting {
    public static void main(String[] args) {
        long count = Stream.of("Apple", "Banana", "Cherry")
                .collect(Collectors.counting());

        System.out.println(count);  // Output: 3
    }
}
```
✔ **`counting()`** → Counts the number of elements in the stream.

---

[⬆ Back to top](#table-of-contents)

### **6️⃣ Joining Strings with a Delimiter**
```java
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectJoining {
    public static void main(String[] args) {
        String result = Stream.of("Red", "Green", "Blue")
                .collect(Collectors.joining(", "));

        System.out.println(result);  // Output: Red, Green, Blue
    }
}
```
✔ **`joining()`** → Concatenates stream elements into a single string.

---

[⬆ Back to top](#table-of-contents)

### **7️⃣ Finding the Maximum or Minimum Element**
```java
import java.util.Comparator;
import java.util.Optional;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectMaxMin {
    public static void main(String[] args) {
        Optional<Integer> maxNumber = Stream.of(5, 10, 15, 20)
                .collect(Collectors.maxBy(Comparator.naturalOrder()));

        System.out.println(maxNumber.get());  // Output: 20
    }
}
```
✔ **`maxBy()` and `minBy()`** → Finds the maximum/minimum element based on a comparator.

---

[⬆ Back to top](#table-of-contents)

### **8️⃣ Summing or Averaging Numbers**
```java
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectSummingAveraging {
    public static void main(String[] args) {
        int sum = Stream.of(1, 2, 3, 4, 5)
                .collect(Collectors.summingInt(Integer::intValue));

        double average = Stream.of(1, 2, 3, 4, 5)
                .collect(Collectors.averagingInt(Integer::intValue));

        System.out.println("Sum: " + sum);       // Output: Sum: 15
        System.out.println("Average: " + average); // Output: Average: 3.0
    }
}
```
✔ **`summingInt()` and `averagingInt()`** → Calculate the sum and average of stream elements.

---

[⬆ Back to top](#table-of-contents)

### **9️⃣ Grouping Elements Using `groupingBy()`**
```java
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectGroupingBy {
    public static void main(String[] args) {
        Map<Integer, List<String>> groupedByLength = Stream.of("one", "two", "three", "four", "five")
                .collect(Collectors.groupingBy(String::length));

        System.out.println(groupedByLength);  
        // Output: {3=[one, two], 4=[four, five], 5=[three]}
    }
}
```
✔ **`groupingBy()`** → Groups elements based on a classification function.

---

[⬆ Back to top](#table-of-contents)

### **🔟 Partitioning Elements Using `partitioningBy()`**
```java
import java.util.List;
import java.util.Map;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class CollectPartitioningBy {
    public static void main(String[] args) {
        Map<Boolean, List<Integer>> partitioned = Stream.of(10, 15, 20, 25, 30)
                .collect(Collectors.partitioningBy(num -> num % 2 == 0));

        System.out.println(partitioned);  
        // Output: {false=[15, 25], true=[10, 20, 30]}
    }
}
```
✔ **`partitioningBy()`** → Splits elements into two groups (true/false).

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary of `collect()` Variations**
| **Collector** | **Functionality** |
|-------------|----------------|
| `toList()` | Collect elements into a `List` |
| `toSet()` | Collect elements into a `Set` |
| `toMap()` | Collect elements into a `Map` |
| `counting()` | Count elements |
| `joining(delimiter)` | Join elements into a string |
| `maxBy(Comparator)` | Find the maximum element |
| `minBy(Comparator)` | Find the minimum element |
| `summingInt()` | Sum values |
| `averagingInt()` | Calculate the average |
| `groupingBy(Function)` | Group elements by a key |
| `partitioningBy(Predicate)` | Partition elements into two groups |

---

[⬆ Back to top](#table-of-contents)

## ## **📌 Complete List of Methods in `Stream` Class (Java 8+)**  

The `Stream<T>` interface in Java **(java.util.stream.Stream)** provides numerous methods for **processing collections** in a functional style.

---

[⬆ Back to top](#table-of-contents)

## **🔹 List of All Methods in `Stream` Interface**

[⬆ Back to top](#table-of-contents)

### **1️⃣ Stream Creation**
| **Method** | **Description** |
|------------|----------------|
| `of(T... values)` | Creates a stream from multiple values. |
| `ofNullable(T t)` | Creates a stream with a single element or an empty stream if `null`. |
| `empty()` | Returns an empty stream. |
| `generate(Supplier<T> s)` | Generates an infinite stream using a `Supplier`. |
| `iterate(T seed, UnaryOperator<T> f)` | Creates an infinite stream starting with a seed and applying a function. |
| `concat(Stream<T> a, Stream<T> b)` | Concatenates two streams. |
| `builder()` | Returns a mutable builder for creating a stream. |

---

[⬆ Back to top](#table-of-contents)

### **2️⃣ Filtering & Matching**
| **Method** | **Description** |
|------------|----------------|
| `filter(Predicate<T> predicate)` | Filters elements based on a condition. |
| `distinct()` | Removes duplicate elements. |
| `allMatch(Predicate<T> predicate)` | Checks if **all** elements match a condition. |
| `anyMatch(Predicate<T> predicate)` | Checks if **any** element matches a condition. |
| `noneMatch(Predicate<T> predicate)` | Checks if **none** of the elements match a condition. |
| `findFirst()` | Retrieves the **first** element in the stream. |
| `findAny()` | Retrieves **any** element (useful in parallel streams). |

---

[⬆ Back to top](#table-of-contents)

### **3️⃣ Transforming Elements**
| **Method** | **Description** |
|------------|----------------|
| `map(Function<T, R> mapper)` | Transforms elements using a function. |
| `flatMap(Function<T, Stream<R>> mapper)` | Flattens nested streams into a single stream. |
| `mapToInt(ToIntFunction<T> mapper)` | Converts stream elements into an `IntStream`. |
| `mapToLong(ToLongFunction<T> mapper)` | Converts stream elements into a `LongStream`. |
| `mapToDouble(ToDoubleFunction<T> mapper)` | Converts stream elements into a `DoubleStream`. |

---

[⬆ Back to top](#table-of-contents)

### **4️⃣ Sorting & Limiting**
| **Method** | **Description** |
|------------|----------------|
| `sorted()` | Sorts elements in natural order (`Comparable`). |
| `sorted(Comparator<T> comparator)` | Sorts elements using a custom comparator. |
| `limit(long maxSize)` | Returns only the first `maxSize` elements. |
| `skip(long n)` | Skips the first `n` elements. |

---

[⬆ Back to top](#table-of-contents)

### **5️⃣ Reducing & Collecting**
| **Method** | **Description** |
|------------|----------------|
| `collect(Collector<T, A, R> collector)` | Reduces elements into a collection (List, Set, Map). |
| `reduce(BinaryOperator<T> accumulator)` | Reduces elements using a binary operation. |
| `reduce(T identity, BinaryOperator<T> accumulator)` | Reduces elements using an **identity value**. |
| `reduce(U identity, BiFunction<U, T, U> accumulator, BinaryOperator<U> combiner)` | Reduces elements with a combiner function. |
| `count()` | Counts the number of elements. |
| `min(Comparator<T> comparator)` | Finds the minimum element. |
| `max(Comparator<T> comparator)` | Finds the maximum element. |

---

[⬆ Back to top](#table-of-contents)

### **6️⃣ Parallel Processing**
| **Method** | **Description** |
|------------|----------------|
| `parallel()` | Converts a stream into a **parallel stream**. |
| `sequential()` | Converts a stream into a **sequential stream**. |
| `isParallel()` | Checks if the stream is parallel. |
| `unordered()` | Removes ordering constraints for better parallel processing. |

---

[⬆ Back to top](#table-of-contents)

### **7️⃣ Terminal Operations (ForEach & Iteration)**
| **Method** | **Description** |
|------------|----------------|
| `forEach(Consumer<T> action)` | Iterates over elements (unordered). |
| `forEachOrdered(Consumer<T> action)` | Iterates over elements in the original order. |

---

[⬆ Back to top](#table-of-contents)

### **8️⃣ Converting Stream to an Array**
| **Method** | **Description** |
|------------|----------------|
| `toArray()` | Converts the stream into an `Object[]`. |
| `toArray(IntFunction<A[]> generator)` | Converts the stream into a **custom array type**. |

---

[⬆ Back to top](#table-of-contents)

### **9️⃣ Short-Circuiting Methods**
| **Method** | **Description** |
|------------|----------------|
| `limit(long maxSize)` | Returns only the **first `maxSize` elements**. |
| `findFirst()` | Retrieves the **first element**, if present. |
| `findAny()` | Retrieves **any element** (useful in parallel streams). |
| `anyMatch(Predicate<T> predicate)` | Stops when **any** element matches. |
| `allMatch(Predicate<T> predicate)` | Stops when an element **doesn't match**. |
| `noneMatch(Predicate<T> predicate)` | Stops when an element **matches**. |

---

[⬆ Back to top](#table-of-contents)

## **🚀 Examples for Each Type of Method**

[⬆ Back to top](#table-of-contents)

### **1️⃣ Creating Streams**
```java
Stream<String> stream1 = Stream.of("Apple", "Banana", "Cherry");
Stream<Integer> stream2 = Stream.iterate(1, n -> n + 2).limit(5);
Stream<Double> stream3 = Stream.generate(Math::random).limit(3);
```

---

[⬆ Back to top](#table-of-contents)

### **2️⃣ Filtering & Matching**
```java
Stream.of("John", "Jane", "Jack")
    .filter(name -> name.startsWith("J"))
    .forEach(System.out::println);
```

---

[⬆ Back to top](#table-of-contents)

### **3️⃣ Transforming with `map()`**
```java
Stream.of("hello", "world")
    .map(String::toUpperCase)
    .forEach(System.out::println);
```

---

[⬆ Back to top](#table-of-contents)

### **4️⃣ Sorting & Limiting**
```java
Stream.of(5, 3, 9, 1, 7)
    .sorted()
    .limit(3)
    .forEach(System.out::println);
```

---

[⬆ Back to top](#table-of-contents)

### **5️⃣ Reducing Elements**
```java
int sum = Stream.of(1, 2, 3, 4, 5)
    .reduce(0, Integer::sum);
System.out.println(sum);  // Output: 15
```

---

[⬆ Back to top](#table-of-contents)

### **6️⃣ Collecting into a List**
```java
List<String> list = Stream.of("A", "B", "C")
    .collect(Collectors.toList());
```

---

[⬆ Back to top](#table-of-contents)

### **7️⃣ Parallel Processing**
```java
Stream.of("A", "B", "C", "D")
    .parallel()
    .forEach(System.out::println);
```

---

[⬆ Back to top](#table-of-contents)

## **🔥 Summary Table of `Stream` Methods**
| **Category** | **Methods** |
|-------------|------------|
| **Stream Creation** | `of()`, `empty()`, `generate()`, `iterate()`, `concat()` |
| **Filtering & Matching** | `filter()`, `distinct()`, `allMatch()`, `anyMatch()`, `noneMatch()`, `findFirst()`, `findAny()` |
| **Transforming Elements** | `map()`, `flatMap()`, `mapToInt()`, `mapToLong()`, `mapToDouble()` |
| **Sorting & Limiting** | `sorted()`, `limit()`, `skip()` |
| **Reducing & Collecting** | `collect()`, `reduce()`, `count()`, `min()`, `max()` |
| **Parallel Processing** | `parallel()`, `sequential()`, `isParallel()`, `unordered()` |
| **Iteration & ForEach** | `forEach()`, `forEachOrdered()` |
| **Converting to Array** | `toArray()` |
| **Short-Circuiting** | `findFirst()`, `findAny()`, `limit()`, `anyMatch()`, `allMatch()`, `noneMatch()` |

---

[⬆ Back to top](#table-of-contents)

## **Merging Two Maps Using `Map.merge()` and Anonymous Inner Class in Java 8**

In Java 8, the `Map.merge()` method is useful for merging two maps by handling key conflicts with a **custom merging function**.

---

[⬆ Back to top](#table-of-contents)

## **📌 Syntax of `merge()`**
```java
V merge(K key, V value, BiFunction<? super V, ? super V, ? extends V> remappingFunction)
```
- **If the key is absent**, it inserts the new value.
- **If the key is present**, it applies the `remappingFunction` to merge values.

---

[⬆ Back to top](#table-of-contents)

## **🚀 Example: Merging Two Maps with `Map.merge()` and Anonymous Inner Class**
```java
import java.util.HashMap;
import java.util.Map;
import java.util.function.BiFunction;

public class MergeMapsExample {
    public static void main(String[] args) {
        // First Map
        Map<String, Integer> map1 = new HashMap<>();
        map1.put("A", 10);
        map1.put("B", 20);
        map1.put("C", 30);

        // Second Map
        Map<String, Integer> map2 = new HashMap<>();
        map2.put("B", 5);
        map2.put("C", 15);
        map2.put("D", 25);

        // Merging map2 into map1 using Map.merge() and Anonymous Inner Class
        for (Map.Entry<String, Integer> entry : map2.entrySet()) {
            map1.merge(entry.getKey(), entry.getValue(), new BiFunction<Integer, Integer, Integer>() {
                @Override
                public Integer apply(Integer val1, Integer val2) {
                    return val1 + val2;  // Merging by summing values
                }
            });
        }

        // Output merged map
        System.out.println(map1);
    }
}
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Explanation**
1. **`map1.put()` and `map2.put()`** - Two maps are created with overlapping keys.
2. **Looping through `map2.entrySet()`**:
   - The `merge()` method checks if the key exists in `map1`.
   - If **not present**, it inserts the key-value pair.
   - If **present**, it applies the merging function (`BiFunction<Integer, Integer, Integer>`).
   - The **anonymous inner class** implements `apply(val1, val2)`, where `val1 + val2` sums the values.
3. **Final Merged Map Output**:
   ```
   {A=10, B=25, C=45, D=25}
   ```
   - `B`: `20 + 5 = 25`
   - `C`: `30 + 15 = 45`
   - `D` (new key) is added as `25`.

---

[⬆ Back to top](#table-of-contents)

## **💡 Alternative: Using Lambda Expression**
If you don’t need an anonymous inner class, you can simplify it with a **lambda function**:
```java
map1.merge(entry.getKey(), entry.getValue(), (val1, val2) -> val1 + val2);
```
This is **shorter and more readable**.

---

[⬆ Back to top](#table-of-contents)

## ## **📌 `Collectors.toMap()` - All Variants and Examples in Java 8**

The `Collectors.toMap()` method is used to collect elements from a Stream into a **Map**. It has **four overloaded variations**, allowing different levels of customization.

---

[⬆ Back to top](#table-of-contents)

## **📌 1️⃣ Basic Syntax: `toMap(KeyMapper, ValueMapper)`**
```java
Map<K, V> toMap(Function<? super T, ? extends K> keyMapper,
                Function<? super T, ? extends V> valueMapper)
```
- **KeyMapper**: Function to extract keys.
- **ValueMapper**: Function to extract values.

[⬆ Back to top](#table-of-contents)

### **🚀 Example**
```java
import java.util.*;
import java.util.stream.Collectors;

public class ToMapExample1 {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("A", "B", "C");

        Map<String, Integer> map = list.stream()
            .collect(Collectors.toMap(s -> s, s -> s.length()));

        System.out.println(map);  // Output: {A=1, B=1, C=1}
    }
}
```
- **Keys** → `"A"`, `"B"`, `"C"`
- **Values** → Their lengths (`1`).

---

[⬆ Back to top](#table-of-contents)

## **📌 2️⃣ Handling Duplicate Keys: `toMap(KeyMapper, ValueMapper, MergeFunction)`**
```java
Map<K, V> toMap(Function<? super T, ? extends K> keyMapper,
                Function<? super T, ? extends V> valueMapper,
                BinaryOperator<V> mergeFunction)
```
- **KeyMapper**: Function to extract keys.
- **ValueMapper**: Function to extract values.
- **MergeFunction**: Defines how to handle duplicate keys.

[⬆ Back to top](#table-of-contents)

### **🚀 Example (Handling Duplicate Keys)**
```java
import java.util.*;
import java.util.stream.Collectors;

public class ToMapExample2 {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("Apple", "Avocado", "Banana");

        Map<Character, String> map = list.stream()
            .collect(Collectors.toMap(
                s -> s.charAt(0), // Key: First letter
                s -> s,           // Value: Full word
                (existing, replacement) -> existing + ", " + replacement  // Merge duplicates
            ));

        System.out.println(map);  // Output: {A=Apple, Avocado, B=Banana}
    }
}
```
- **Keys** → First letter of each word.
- **Values** → Words.
- **Merge Strategy** → Concatenation.

---

[⬆ Back to top](#table-of-contents)

## **📌 3️⃣ Using a Specific `Map` Type: `toMap(KeyMapper, ValueMapper, MergeFunction, MapSupplier)`**
```java
Map<K, V> toMap(Function<? super T, ? extends K> keyMapper,
                Function<? super T, ? extends V> valueMapper,
                BinaryOperator<V> mergeFunction,
                Supplier<M> mapSupplier)
```
- **KeyMapper**: Extracts keys.
- **ValueMapper**: Extracts values.
- **MergeFunction**: Handles duplicate keys.
- **MapSupplier**: Defines the specific `Map` implementation (e.g., `TreeMap`, `LinkedHashMap`).

[⬆ Back to top](#table-of-contents)

### **🚀 Example (Using `LinkedHashMap` for Order)**
```java
import java.util.*;
import java.util.stream.Collectors;

public class ToMapExample3 {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("Dog", "Cat", "Deer", "Cheetah");

        Map<Character, String> map = list.stream()
            .collect(Collectors.toMap(
                s -> s.charAt(0),   // Key: First character
                s -> s,             // Value: Full word
                (existing, replacement) -> existing,  // Keep first value (ignore duplicates)
                LinkedHashMap::new  // Preserve insertion order
            ));

        System.out.println(map);  // Output: {D=Dog, C=Cat}
    }
}
```
- **Keys** → First character.
- **Values** → Words.
- **Duplicate Handling** → Keeps first value.
- **Map Type** → `LinkedHashMap` (preserves insertion order).

---

[⬆ Back to top](#table-of-contents)

## **📌 4️⃣ Handling Null Values in `toMap()`**
`toMap()` does not allow `null` **keys** or **values**. It throws a `NullPointerException`.

[⬆ Back to top](#table-of-contents)

### **🚀 Example (Handling Nulls)**
```java
import java.util.*;
import java.util.stream.Collectors;

public class ToMapExample4 {
    public static void main(String[] args) {
        List<String> list = Arrays.asList("Apple", null, "Banana");

        Map<Character, String> map = list.stream()
            .filter(Objects::nonNull) // Remove nulls before collecting
            .collect(Collectors.toMap(
                s -> s.charAt(0),
                s -> s
            ));

        System.out.println(map);  // Output: {A=Apple, B=Banana}
    }
}
```
- **Filters out `null` values** before collecting.

---

[⬆ Back to top](#table-of-contents)

## **🔹 Summary Table of `toMap()` Variants**

| **Syntax** | **Purpose** |
|------------|------------|
| `toMap(KeyMapper, ValueMapper)` | Simple conversion to `Map`. |
| `toMap(KeyMapper, ValueMapper, MergeFunction)` | Handles duplicate keys. |
| `toMap(KeyMapper, ValueMapper, MergeFunction, MapSupplier)` | Specifies a custom `Map` type. |

---

[⬆ Back to top](#table-of-contents)

## **🔥 Key Takeaways**
✔ `Collectors.toMap()` is **immutable** by default.  
✔ Handles **duplicate keys** using a merge function.  
✔ Use `LinkedHashMap::new` to **preserve insertion order**.  
✔ **No null values** allowed (use `.filter(Objects::nonNull)`).  

---

[⬆ Back to top](#table-of-contents)

## ## **📌 `Stream.concat()` in Java 8**  

The `Stream.concat()` method is used to **merge two streams** into a **single continuous stream**. It **does not modify** the original streams but creates a **new combined stream**.  

---

[⬆ Back to top](#table-of-contents)

## **📌 Syntax**  
```java
public static <T> Stream<T> concat(Stream<? extends T> a, Stream<? extends T> b)
```
[⬆ Back to top](#table-of-contents)

### **🔹 Parameters**  
- `a` → The first stream  
- `b` → The second stream  

[⬆ Back to top](#table-of-contents)

### **🔹 Returns**  
- A new **concatenated** stream consisting of all elements from `a`, followed by all elements from `b`.  

[⬆ Back to top](#table-of-contents)

### **🔹 Important Notes**
✔ Streams passed to `Stream.concat()` **must not be reused** after concatenation.  
✔ If either `a` or `b` is **null**, it will throw `NullPointerException`.  

---

[⬆ Back to top](#table-of-contents)

## **📌 Example 1: Merging Two Streams of Strings**
```java
import java.util.stream.Stream;

public class StreamConcatExample {
    public static void main(String[] args) {
        Stream<String> stream1 = Stream.of("Apple", "Banana");
        Stream<String> stream2 = Stream.of("Cherry", "Date");

        Stream<String> mergedStream = Stream.concat(stream1, stream2);

        mergedStream.forEach(System.out::println);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔹 Output**
```
Apple
Banana
Cherry
Date
```

---

[⬆ Back to top](#table-of-contents)

## **📌 Example 2: Concatenating Streams with Different Data Types**
You can concatenate streams of **subtypes** if they share a common **superclass**.

```java
import java.util.stream.Stream;

public class StreamConcatExample2 {
    public static void main(String[] args) {
        Stream<Number> intStream = Stream.of(1, 2, 3);
        Stream<Number> doubleStream = Stream.of(4.5, 5.5, 6.5);

        Stream<Number> mergedStream = Stream.concat(intStream, doubleStream);

        mergedStream.forEach(System.out::println);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔹 Output**
```
1
2
3
4.5
5.5
6.5
```
✔ Since `Integer` and `Double` both extend `Number`, `Stream<Number>` can hold both.  

---

[⬆ Back to top](#table-of-contents)

## **📌 Example 3: Handling Empty Streams**
```java
import java.util.stream.Stream;

public class StreamConcatExample3 {
    public static void main(String[] args) {
        Stream<String> emptyStream = Stream.empty();
        Stream<String> nonEmptyStream = Stream.of("Hello", "World");

        Stream<String> result = Stream.concat(emptyStream, nonEmptyStream);

        result.forEach(System.out::println);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔹 Output**
```
Hello
World
```
✔ If one of the streams is **empty**, `Stream.concat()` simply returns the non-empty stream.  

---

[⬆ Back to top](#table-of-contents)

## **📌 Example 4: Using `Stream.concat()` Multiple Times**
You can **chain `Stream.concat()` calls** to merge multiple streams.

```java
import java.util.stream.Stream;

public class StreamConcatExample4 {
    public static void main(String[] args) {
        Stream<String> stream1 = Stream.of("A", "B");
        Stream<String> stream2 = Stream.of("C", "D");
        Stream<String> stream3 = Stream.of("E", "F");

        Stream<String> finalStream = Stream.concat(Stream.concat(stream1, stream2), stream3);

        finalStream.forEach(System.out::print);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔹 Output**
```
ABCDEF
```
✔ **Nesting** `Stream.concat()` calls allows you to merge multiple streams.  

---

[⬆ Back to top](#table-of-contents)

## **📌 Example 5: Avoiding `IllegalStateException`**
> ⚠ **Once a stream is consumed, it cannot be reused**.  
The following **incorrect** code will throw `IllegalStateException`:
```java
Stream<String> stream = Stream.of("X", "Y");

Stream<String> merged1 = Stream.concat(stream, Stream.of("Z"));
Stream<String> merged2 = Stream.concat(stream, Stream.of("W")); // ERROR!
```
✔ **Solution**: Use `.supplier()` or **create a new stream every time**.

```java
import java.util.function.Supplier;
import java.util.stream.Stream;

public class StreamConcatExample5 {
    public static void main(String[] args) {
        Supplier<Stream<String>> streamSupplier = () -> Stream.of("X", "Y");

        Stream<String> merged1 = Stream.concat(streamSupplier.get(), Stream.of("Z"));
        Stream<String> merged2 = Stream.concat(streamSupplier.get(), Stream.of("W"));

        merged1.forEach(System.out::print);  // XYZ
        System.out.println();
        merged2.forEach(System.out::print);  // XYW
    }
}
```
✔ **Using `Supplier<Stream<T>>` allows multiple stream creations.**  

---

[⬆ Back to top](#table-of-contents)

## **📌 Alternative to `Stream.concat()`**
- You can also use `Stream.of()` to merge multiple streams.

```java
Stream<String> combinedStream = Stream.of(stream1, stream2, stream3).flatMap(s -> s);
```
✔ **This is more flexible** when merging multiple streams.  

---

[⬆ Back to top](#table-of-contents)

## **✅ Summary of `Stream.concat()`**
| **Feature**      | **Details** |
|-----------------|------------|
| **Purpose** | Merges two streams into one. |
| **Modifies Original Streams?** | ❌ No |
| **Reusable Streams?** | ❌ No, unless recreated (e.g., using `Supplier<Stream<T>>`). |
| **Handles Empty Streams?** | ✅ Yes |
| **Handles Nulls?** | ❌ No (`NullPointerException` for `null` streams). |
| **Alternative** | `Stream.of(stream1, stream2).flatMap(s -> s)` |

---

[⬆ Back to top](#table-of-contents)

## ## **Merging Two Maps Using `Stream.concat()` and Anonymous Inner Class in Java 8**  

You can use **`Stream.concat()`** to merge two maps by converting their entries into a **Stream**, then collecting them back into a `Map`. If there are duplicate keys, we handle them using a **merge function** inside an **anonymous inner class**.

---

[⬆ Back to top](#table-of-contents)

## **📌 Example: Merging Two Maps with `Stream.concat()` and Anonymous Inner Class**
```java
import java.util.*;
import java.util.function.BinaryOperator;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class MergeMapsWithStreamConcat {
    public static void main(String[] args) {
        // First Map
        Map<String, Integer> map1 = new HashMap<>();
        map1.put("A", 10);
        map1.put("B", 20);
        map1.put("C", 30);

        // Second Map
        Map<String, Integer> map2 = new HashMap<>();
        map2.put("B", 5);
        map2.put("C", 15);
        map2.put("D", 25);

        // Merging using Stream.concat() and Anonymous Inner Class
        Map<String, Integer> mergedMap = Stream.concat(map1.entrySet().stream(), map2.entrySet().stream())
            .collect(Collectors.toMap(
                Map.Entry::getKey,
                Map.Entry::getValue,
                new BinaryOperator<Integer>() {  // Anonymous inner class
                    @Override
                    public Integer apply(Integer v1, Integer v2) {
                        return v1 + v2; // Merging by summing values
                    }
                }
            ));

        // Output merged map
        System.out.println(mergedMap);
    }
}
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Explanation**
1. **Convert Both Maps into Streams**  
   - `map1.entrySet().stream()` → Converts `map1` into a stream of key-value pairs.
   - `map2.entrySet().stream()` → Converts `map2` into a stream of key-value pairs.

2. **Merge Using `Stream.concat()`**  
   - Combines the two streams into one.

3. **Collect Back to a Map Using `Collectors.toMap()`**  
   - `Map.Entry::getKey` → Extracts the key.
   - `Map.Entry::getValue` → Extracts the value.
   - **Anonymous Inner Class (BinaryOperator)** handles duplicate keys:
     ```java
     new BinaryOperator<Integer>() {
         @Override
         public Integer apply(Integer v1, Integer v2) {
             return v1 + v2;
         }
     }
     ```
     - If a key exists in both maps, it sums the values.

---

[⬆ Back to top](#table-of-contents)

## **🔹 Output**
```
{A=10, B=25, C=45, D=25}
```
- `"B"`: `20 + 5 = 25`
- `"C"`: `30 + 15 = 45`
- `"D"` is added as `25`.

---

[⬆ Back to top](#table-of-contents)

## **✅ Alternative Using Lambda (More Concise)**
Instead of an anonymous inner class, use a **lambda function**:
```java
.collect(Collectors.toMap(
    Map.Entry::getKey,
    Map.Entry::getValue,
    (v1, v2) -> v1 + v2  // Merging duplicate keys
));
```

---

[⬆ Back to top](#table-of-contents)

## **🚀 Key Takeaways**
✔ **`Stream.concat()` merges streams of key-value pairs.**  
✔ **`Collectors.toMap()` collects them back into a Map.**  
✔ **Anonymous Inner Class helps in handling key conflicts.**  
✔ **Alternative:** Use a lambda function for conciseness.  

---

[⬆ Back to top](#table-of-contents)

## ## **Merging Two Maps Using `Stream.concat()`, `toMap()` with `MapSupplier`, and an Anonymous Inner Class in Java 8**  

We will use:  
✔ **`Stream.concat()`** → To merge two streams of `Map.Entry<K, V>`.  
✔ **`Collectors.toMap(KeyMapper, ValueMapper, MergeFunction, MapSupplier)`** → To merge entries into a custom `Map` type.  
✔ **Anonymous Inner Class (`BinaryOperator`)** → To handle key conflicts when merging duplicate keys.  

---

[⬆ Back to top](#table-of-contents)

### **📌 Example: Merging Two Maps into a `LinkedHashMap` (Maintaining Order)**
```java
import java.util.*;
import java.util.function.BinaryOperator;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class MergeMapsExample {
    public static void main(String[] args) {
        // First Map
        Map<String, Integer> map1 = new HashMap<>();
        map1.put("A", 10);
        map1.put("B", 20);
        map1.put("C", 30);

        // Second Map
        Map<String, Integer> map2 = new HashMap<>();
        map2.put("B", 5);
        map2.put("C", 15);
        map2.put("D", 25);

        // Merging using Stream.concat() and Anonymous Inner Class
        Map<String, Integer> mergedMap = Stream.concat(map1.entrySet().stream(), map2.entrySet().stream())
            .collect(Collectors.toMap(
                Map.Entry::getKey,   // KeyMapper: Extracts the key
                Map.Entry::getValue, // ValueMapper: Extracts the value
                new BinaryOperator<Integer>() {  // MergeFunction: Handles duplicate keys
                    @Override
                    public Integer apply(Integer v1, Integer v2) {
                        return v1 + v2; // Merge values by summing them
                    }
                },
                LinkedHashMap::new   // MapSupplier: Uses LinkedHashMap to maintain order
            ));

        // Output merged map
        System.out.println(mergedMap);
    }
}
```

---

[⬆ Back to top](#table-of-contents)

## **🔹 Explanation**
1. **Convert Both Maps to Streams**  
   - `map1.entrySet().stream()` → Converts `map1` into a stream of key-value pairs.  
   - `map2.entrySet().stream()` → Converts `map2` into a stream of key-value pairs.  

2. **Merge the Two Streams Using `Stream.concat()`**  
   - Combines both `Stream<Map.Entry<K, V>>` into one unified stream.  

3. **Collect Merged Stream into a `LinkedHashMap` Using `Collectors.toMap()`**  
   - `Map.Entry::getKey` → Extracts the key from the entry.  
   - `Map.Entry::getValue` → Extracts the value from the entry.  
   - **Anonymous Inner Class (`BinaryOperator`)**:
     ```java
     new BinaryOperator<Integer>() {
         @Override
         public Integer apply(Integer v1, Integer v2) {
             return v1 + v2;
         }
     }
     ```
     - If a key appears in both maps, sum their values.  
   - **Custom Map Type (`LinkedHashMap::new`)**:
     - Ensures that the insertion order is preserved.  

---

[⬆ Back to top](#table-of-contents)

## **🔹 Output**
```
{A=10, B=25, C=45, D=25}
```
- `"B"`: `20 + 5 = 25`
- `"C"`: `30 + 15 = 45`
- `"D"`: Added as `25` since it is only in `map2`.

---

[⬆ Back to top](#table-of-contents)

## **✅ Alternative Using Lambda for Merge Function**
Instead of an anonymous inner class, you can use a **lambda function**:
```java
.collect(Collectors.toMap(
    Map.Entry::getKey,
    Map.Entry::getValue,
    (v1, v2) -> v1 + v2,  // Merge duplicate keys by summing values
    LinkedHashMap::new     // Use LinkedHashMap
));
```
✔ **Lambdas make the code more concise!**  

---

[⬆ Back to top](#table-of-contents)

## **🔥 Key Takeaways**
✔ **Use `Stream.concat()`** to merge two `Stream<Map.Entry<K, V>>`.  
✔ **Use `Collectors.toMap()`** to collect entries into a custom `Map`.  
✔ **Use `BinaryOperator` (Anonymous Inner Class)** to handle duplicate keys.  
✔ **Use `MapSupplier` (`LinkedHashMap::new`)** to maintain insertion order.  

---

[⬆ Back to top](#table-of-contents)

## ## **Merging Two Maps with Same Keys in Java 8**  

When merging two maps that **share common keys**, we need to decide how to handle the duplicate keys. Java 8 provides multiple approaches using **Streams and Collectors**.

---

[⬆ Back to top](#table-of-contents)

## **📌 Approach 1: Using `Stream.concat()` and `Collectors.toMap()`**
✔ **Concatenates both maps into a single stream**  
✔ **Handles duplicate keys using a merge function**  

```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class MergeMapsUsingStream {
    public static void main(String[] args) {
        // First Map
        Map<String, Integer> map1 = new HashMap<>();
        map1.put("A", 10);
        map1.put("B", 20);
        map1.put("C", 30);

        // Second Map
        Map<String, Integer> map2 = new HashMap<>();
        map2.put("B", 5);
        map2.put("C", 15);
        map2.put("D", 25);

        // Merging maps
        Map<String, Integer> mergedMap = Stream.concat(map1.entrySet().stream(), map2.entrySet().stream())
            .collect(Collectors.toMap(
                Map.Entry::getKey, 
                Map.Entry::getValue, 
                (v1, v2) -> v1 + v2 // Merge function: sum values of duplicate keys
            ));

        System.out.println(mergedMap);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔹 Output**
```
{A=10, B=25, C=45, D=25}
```
✔ `"B"` → `20 + 5 = 25`  
✔ `"C"` → `30 + 15 = 45`  
✔ `"D"` is added as `25`  

---

[⬆ Back to top](#table-of-contents)

## **📌 Approach 2: Using `Map.merge()`**
✔ **Iterates through one map and merges with another**  
✔ **Avoids creating extra streams**  

```java
import java.util.*;

public class MergeMapsUsingMergeMethod {
    public static void main(String[] args) {
        // First Map
        Map<String, Integer> map1 = new HashMap<>();
        map1.put("A", 10);
        map1.put("B", 20);
        map1.put("C", 30);

        // Second Map
        Map<String, Integer> map2 = new HashMap<>();
        map2.put("B", 5);
        map2.put("C", 15);
        map2.put("D", 25);

        // Merge two maps using Map.merge()
        map2.forEach((key, value) -> 
            map1.merge(key, value, (v1, v2) -> v1 + v2)); // Merge function: sum values

        System.out.println(map1);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔹 Output**
```
{A=10, B=25, C=45, D=25}
```
✔ `"B"` → `20 + 5 = 25`  
✔ `"C"` → `30 + 15 = 45`  
✔ `"D"` is added as `25`  

🔹 **Efficient**, as it modifies `map1` directly instead of creating a new map.

---

[⬆ Back to top](#table-of-contents)

## **📌 Approach 3: Using `Collectors.toMap()` with a Custom Map (LinkedHashMap)**
✔ **Maintains insertion order**  
✔ **Uses a custom map supplier (`LinkedHashMap::new`)**  

```java
import java.util.*;
import java.util.stream.Collectors;
import java.util.stream.Stream;

public class MergeMapsUsingLinkedHashMap {
    public static void main(String[] args) {
        // First Map
        Map<String, Integer> map1 = new LinkedHashMap<>();
        map1.put("A", 10);
        map1.put("B", 20);
        map1.put("C", 30);

        // Second Map
        Map<String, Integer> map2 = new LinkedHashMap<>();
        map2.put("B", 5);
        map2.put("C", 15);
        map2.put("D", 25);

        // Merging maps while maintaining order
        Map<String, Integer> mergedMap = Stream.concat(map1.entrySet().stream(), map2.entrySet().stream())
            .collect(Collectors.toMap(
                Map.Entry::getKey, 
                Map.Entry::getValue, 
                Integer::sum, // Merge function: sum values of duplicate keys
                LinkedHashMap::new // Use LinkedHashMap to preserve order
            ));

        System.out.println(mergedMap);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔹 Output**
```
{A=10, B=25, C=45, D=25}
```
✔ `"B"` → `20 + 5 = 25`  
✔ `"C"` → `30 + 15 = 45`  
✔ `"D"` is added as `25`  

🔹 **Maintains order** because of `LinkedHashMap::new`.

---

[⬆ Back to top](#table-of-contents)

## **📌 Approach 4: Using Java 8 `reduce()`**
✔ **Merges multiple maps into one using `reduce()`**  
✔ **More functional approach**  

```java
import java.util.*;
import java.util.stream.Stream;

public class MergeMapsUsingReduce {
    public static void main(String[] args) {
        // First Map
        Map<String, Integer> map1 = new HashMap<>();
        map1.put("A", 10);
        map1.put("B", 20);
        map1.put("C", 30);

        // Second Map
        Map<String, Integer> map2 = new HashMap<>();
        map2.put("B", 5);
        map2.put("C", 15);
        map2.put("D", 25);

        // Merging using reduce()
        Map<String, Integer> mergedMap = Stream.of(map1, map2)
            .map(Map::entrySet)
            .flatMap(Set::stream)
            .reduce(new HashMap<>(), (acc, entry) -> {
                acc.merge(entry.getKey(), entry.getValue(), Integer::sum);
                return acc;
            }, (m1, m2) -> {
                m1.putAll(m2);
                return m1;
            });

        System.out.println(mergedMap);
    }
}
```
[⬆ Back to top](#table-of-contents)

### **🔹 Output**
```
{A=10, B=25, C=45, D=25}
```
✔ Uses `reduce()` to accumulate values efficiently.  
✔ **Good for merging multiple maps dynamically.**  

---

[⬆ Back to top](#table-of-contents)

## **🔥 Comparison of Methods**
| **Approach**                 | **Pros** | **Cons** |
|------------------------------|---------|----------|
| `Stream.concat() + toMap()`  | Simple, Functional | Creates extra stream overhead |
| `Map.merge()`                | Efficient, No extra memory | Modifies original map |
| `Collectors.toMap()` + `LinkedHashMap` | Maintains order | Extra overhead |
| `reduce()`                   | Works with multiple maps | Verbose |

---

[⬆ Back to top](#table-of-contents)

## **✅ Best Choice Based on Use Case**
| **Scenario** | **Best Approach** |
|-------------|----------------|
| Merge two maps (simple case) | `Stream.concat()` + `toMap()` |
| Modify one of the maps directly | `Map.merge()` |
| Maintain insertion order | `Collectors.toMap()` with `LinkedHashMap::new` |
| Merge multiple maps dynamically | `reduce()` |

---

[⬆ Back to top](#table-of-contents)

## **🚀 Summary**
✔ **If modifying an existing map** → Use `Map.merge()`  
✔ **If creating a new map and maintaining order** → Use `LinkedHashMap`  
✔ **If handling multiple maps dynamically** → Use `reduce()`  

---







[⬆ Back to top](#table-of-contents)
