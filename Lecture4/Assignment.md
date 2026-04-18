# 📝 Assignment 04 — Java 8+ Modern Features

> **Topic:** Java 8+ Modern Features (Phase 1 — Foundations)
> **Topic Count:** 4 of 30 — Phase 1 Foundations
> **Duration:** 3 Days
> **Core Problems:** 25 (10 Easy · 10 Medium · 5 Hard) + 8 Challenge + 6 Complexity Exercises
> **Goal:** Leverage the power of Lambdas, Streams, and Optional to write cleaner, more declarative, and FAANG-ready Java code.

---

## 🗺️ Problem Map by Pattern

| Pattern / Topic         | Problems           |
| ----------------------- | ------------------ |
| Lambda Basic Sorting    | 01, 02, 03         |
| Functional Interfaces   | 04, 05, 06         |
| IntStream / Ranges      | 07, 08             |
| Stream Filtering & Map  | 09, 10, 11         |
| Method References       | 12, 13             |
| Optional Patterns       | 14, 15, 16         |
| Grouping & Partitioning | 17, 18, 19, 20     |
| FlatMap & Reduction     | 21, 22, 23         |
| Parallel Streams        | 24, 25             |
| Challenge Zone (FAANG)  | 26, 27, 28, 29, 30 |

---

## 🟢 Easy Tier — 10 Problems (Syntax & Basics)

### Problem 01 — Lambda One-Liner

> 🔗 **Practice:** Rewrite an anonymous inner class for `Runnable` into a concise Lambda. Also rewrite `Comparator<Integer> comp = (a, b) -> a - b;` into a method reference `Integer::compare`.

### Problem 02 — Sorting a List of Strings

> 🔗 **Practice:** Create a `List<String> names = Arrays.asList("Apple", "Banana", "Cherry");` and use `names.sort(...)` with a Lambda to sort by **string length** instead of alphabetical order.

### Problem 03 — List to UpperCase

> 🔗 **Practice:** Given a list of strings, use `list.replaceAll(...)` with a Lambda to convert all elements to uppercase.

### Problem 04 — Custom Functional Interface

Create a `@FunctionalInterface` called `MathOp` with one method `double operate(double a, double b)`. Implement `Add`, `Subtract`, `Multiply`, and `Divide` using only Lambda variables.

### Problem 05 — Predicate Filtering

> 🔗 **Practice:** Use `Predicate<Integer> isEven = n -> n % 2 == 0;` and use `list.removeIf(isEven)` to filter a list of numbers.

### Problem 06 — Supplier & Consumer

Write a `Supplier<Double>` that returns a random number and a `Consumer<Double>` that prints "Random: " followed by that number. Execute them 5 times.

### Problem 07 — IntStream Ranges

> 🔗 **Practice:** Use `IntStream.rangeClosed(1, 100)` to find the sum of all odd numbers between 1 and 100.

### Problem 08 — Array to Stream

Convert `int[] nums = {1, 2, 3, 4, 5}` into a stream. Use `.map(n -> n * n)` to square each number and collect it into a `List<Integer>`.

### Problem 09 — AnyMatch / AllMatch

> 🔗 **Practice:** Given a list of students, check if **all** students have `gpa > 2.0` and if **any** student has `gpa == 4.0` using Streams.

### Problem 10 — Distinct & Sort

> 🔗 **Practice:** Join unique names from a list, sorted alphabetically, into a single comma-separated string using `.distinct().sorted().collect(Collectors.joining(", "))`.

---

## 🟡 Medium Tier — 10 Problems (Pipeline Mastery)

### Problem 11 — The `Optional` Rescue

> 🔗 **Practice:** Create a method `String getUpperName(Employee e)` that returns `Optional.ofNullable(e.getName()).map(String::toUpperCase).orElse("UNKNOWN")`. Test it with a null employee name.

### Problem 12 — Mapping to Object

> 🔗 **Practice:** Given a `List<String> titles`, use a Stream to convert them into a `List<Book>` objects where the title is passed to the constructor.

### Problem 13 — Grouping By Category

> 🔗 **Practice:** Given `List<Item>` (each with `name` and `category`), create a `Map<String, List<Item>>` grouped by category using `Collectors.groupingBy`.

### Problem 14 — Partitioning By Predicate

> 🔗 **Practice:** Partition a list of integers into two lists: `primes` and `non-primes` using `Collectors.partitioningBy(n -> isPrime(n))`.

### Problem 15 — FlatMap (List of Lists)

> 🔗 **Practice:** Given `List<List<Integer>>`, use `.flatMap(List::stream)` to flatten it into a single `List<Integer>` of all numbers.

### Problem 16 — Count Word Frequencies

> 🔗 **Practice:** Given a list of words, use `Collectors.groupingBy(Function.identity(), Collectors.counting())` to find the frequency of each word.

### Problem 17 — Max/Min with Streams

> 🔗 **Practice:** Find the oldest `User` in a list using `.max(Comparator.comparingInt(User::getAge))`. Return as an `Optional<User>`.

### Problem 18 — Parallel Stream Performance

> 🔗 **Practice:** Perform a complex calculation (e.g., sum of prime factors) on a list of 1,000,000 numbers. Compare the time taken by `.stream()` vs `.parallelStream()`.

### Problem 19 — Reduce (Custom Accumulation)

> 🔗 **Practice:** Use `.reduce(1, (a, b) -> a * b)` to find the factorial of a small number list. Explain the "Identity" parameter.

### Problem 20 — Stream-based Filtering ([LC 438](https://leetcode.com/problems/find-all-anagrams-in-a-string/))

> 🔗 **LeetCode:** [438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)
> **`[Pattern: Sliding Window + Stream (optional)]` `[Medium]`**
> Use an array freq map to find anagrams. (Hint: Java 8 `Arrays.equals(arr1, arr2)` is the most efficient way to compare the maps inside the loop).

---

## 🔴 Challenge Zone — 10 Advanced Problems

### P21-30: Real-World Scenarios

- **P21: Top K Frequent Words** ([LC 692](https://leetcode.com/problems/top-k-frequent-words/)) - Use `Collectors.groupingBy` and then sort by `Entry.getValue()` DESC and `Entry.getKey()` ASC.
- **P22: Custom Collector**: Implement a custom collector that computes the **standard deviation** of a stream of doubles.
- **P23: Stream of Files**: Use `Files.lines(Path)` to process a 100MB log file. Filter lines starting with "ERROR" and count them without loading the whole file into RAM.
- **P24: Optionals in Serialization**: Explain why putting `Optional<T>` as a field in a class is considered "bad practice" (it's not Serializable).
- **P25: Infinite Stream**: Use `Stream.generate(Math::random).limit(10)` to produce random numbers.

---

## 📊 Complexity Analysis Exercises — 6 Snippets

Wait, are Streams efficient? Let's check.

```java
// Snippet 1
long count = IntStream.range(0, n).filter(x -> x % 2 == 0).count();

// Snippet 2
List<Integer> list = list.stream().sorted().collect(Collectors.toList());

// Snippet 3
Map<Integer, List<String>> map = list.stream().collect(Collectors.groupingBy(String::length));

// Snippet 4
Optional<String> first = list.parallelStream().filter(s -> s.startsWith("A")).findAny();

// Snippet 5
int result = list.stream().reduce(0, Integer::sum);

// Snippet 6
list.stream().flatMap(sublist -> sublist.stream()).distinct().count();
```

**Complexity Answers:**

1. **O(n)** Time, O(1) Space. Pipeline lazy evaluation.
2. **O(n log n)** Time, O(n) Space for sorting result.
3. **O(n)** Time, O(n) Space for the HashMap.
4. **O(n/k)** Time where k is CPU cores, O(log n) overhead.
5. **O(n)** Time, O(1) Space.
6. **O(Total Elements)** Time, O(Distinct Elements) Space.

---

## ✅ Self-Assessment — True / False

1. Lambdas can modify local variables from the outer scope if they are not `final`. → **False** (must be effectively final).
2. `stream().map()` is a terminal operation. → **False** (intermediate operation).
3. `optional.get()` will throw an exception if the value is null. → **True** (Always use `orElse` or `isPresent` first).
4. `Collectors.toMap()` throws an exception if keys collide. → **True** (unless a merge function is provided).
5. A Stream can be reused multiple times once closed. → **False**.
6. `filter()` reduces the elements in a stream, but `map()` keeps the count same. → **True**.
7. Method references like `String::toUpperCase` are faster than Lambdas. → **False** (compiled to same bytecode).
8. Functional Interfaces can have multiple default methods. → **True** (only ONE abstract method allowed).

---

## 🧠 Conceptual Mastery Questions

1. **Lazy Evaluation**: Explain what it means that Java Streams are "lazy". How does it affect performance in a `.filter().map().findFirst()` pipeline?
2. **Lambda Internals**: How are Lambdas represented in memory? Are they just anonymous inner classes under the hood? (Hint: `invokedynamic`).
3. **Optional Choice**: Why was `Optional` added to Java if we already had null? (Hint: API intent vs pointer safety).
4. **Intermediate vs Terminal**: What happens if you call `.filter().map()` but never call a terminal operation like `.toList()` or `.count()`?
5. **Parallel Streams Trap**: When is `parallelStream()` actually SLOWER than a serial stream? (Hint: Small datasets, expensive merge steps).

---

Next: [Topic 5 — Recursion & Backtracking](../Lecture5/Assignment.md)
