# ⚡ Assignment 7 — Java 8+ Modern Features

> **Lecture:** 7 of 45 — Java 8+ Modern Features
> **Phase:** 1 — Foundations
> **Estimated Time:** 3 days · **Total Problems:** 25 (12 Easy · 9 Medium · 4 Hard)
> **Goal:** Leverage the power of Lambdas, Streams, and Optional to write cleaner, more declarative, and FAANG-ready
> Java code.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem               | Pattern               | Move                                    |
| ----------------------------------- | --------------------- | --------------------------------------- |
| "transform every element"           | map                   | `stream().map(f)`                       |
| "keep only elements that …"         | filter                | `filter(predicate)`                     |
| "group by / count by"               | Collectors.groupingBy | `groupingBy(key, counting())`           |
| "list of lists"                     | flatMap               | `flatMap(List::stream)`                 |
| "combine everything into one value" | reduce                | identity + associative accumulator      |
| "value might be missing"            | Optional              | `map` / `orElse` instead of null checks |

---

## 🟢 Easy Tier (12 Problems)

_Syntax & Basics._

### E1 · Lambda One-Liner

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Lambda Basics | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Rewrite an anonymous inner class for `Runnable` into a concise Lambda. Also rewrite `Comparator<Integer> comp = (a, b) -> a - b;` into a method reference `Integer::compare`.

---

### E2 · Sorting a List of Strings

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Lambda Basics | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Create a `List<String> names = Arrays.asList("Apple", "Banana", "Cherry");` and use `names.sort(...)` with a Lambda to sort by **string length** instead of alphabetical order.

---

### E3 · List to UpperCase

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Lambda Basics | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Given a list of strings, use `list.replaceAll(...)` with a Lambda to convert all elements to uppercase.

---

### E4 · Custom Functional Interface

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Functional Interfaces | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Create a `@FunctionalInterface` called `MathOp` with one method `double operate(double a, double b)`. Implement `Add`, `Subtract`, `Multiply`, and `Divide` using only Lambda variables.

---

### E5 · Predicate Filtering

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Functional Interfaces | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Use `Predicate<Integer> isEven = n -> n % 2 == 0;` and use `list.removeIf(isEven)` to filter a list of numbers.

---

### E6 · Supplier & Consumer

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Functional Interfaces | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Write a `Supplier<Double>` that returns a random number and a `Consumer<Double>` that prints "Random: " followed by that number. Execute them 5 times.

---

### E7 · IntStream Ranges

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Stream Sources | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Use `IntStream.rangeClosed(1, 100)` to find the sum of all odd numbers between 1 and 100.

---

### E8 · Array to Stream

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Stream Sources | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Convert `int[] nums = {1, 2, 3, 4, 5}` into a stream. Use `.map(n -> n * n)` to square each number and collect it into a `List<Integer>`.

---

### E9 · AnyMatch / AllMatch

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Filter, Match & Map | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Given a list of students, check if **all** students have `gpa > 2.0` and if **any** student has `gpa == 4.0` using Streams.

---

### E10 · Distinct & Sort

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Filter, Match & Map | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Join unique names from a list, sorted alphabetically, into a single comma-separated string using `.distinct().sorted().collect(Collectors.joining(", "))`.

---

### E11 · Uncommon Words from Two Sentences

**🔗 [LC 884 — Uncommon Words from Two Sentences](https://leetcode.com/problems/uncommon-words-from-two-sentences/)** · Easy
**Pattern:** Collectors.groupingBy + counting | **Companies:** Amazon, Microsoft

**Hint:** Stream the words of both sentences: `Arrays.stream((s1 + " " + s2).split(" "))`, group with `Collectors.groupingBy(Function.identity(), Collectors.counting())`, then filter entries with count 1 and map to keys.

---

### E12 · Find Resultant Array After Removing Anagrams

**🔗 [LC 2273 — Find Resultant Array After Removing Anagrams](https://leetcode.com/problems/find-resultant-array-after-removing-anagrams/)** · Easy
**Pattern:** Stream Filtering with State | **Companies:** Amazon, Google

**Hint:** Two words are anagrams when their sorted characters match. A plain `filter` has no memory of the previous word, so compare against the last kept word — use `IntStream.range` over indices, or a loop, and explain why stateful lambdas are unsafe in parallel streams.

---

## 🟡 Medium Tier (9 Problems)

_Pipeline Mastery._

### M1 · The `Optional` Rescue

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Optional | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Create a method `String getUpperName(Employee e)` that returns `Optional.ofNullable(e.getName()).map(String::toUpperCase).orElse("UNKNOWN")`. Test it with a null employee name.

---

### M2 · Mapping to Object

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Filter, Match & Map | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Given a `List<String> titles`, use a Stream to convert them into a `List<Book>` objects where the title is passed to the constructor.

---

### M3 · Grouping By Category

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Grouping & Partitioning | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Given `List<Item>` (each with `name` and `category`), create a `Map<String, List<Item>>` grouped by category using `Collectors.groupingBy`.

---

### M4 · Partitioning By Predicate

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Grouping & Partitioning | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Partition a list of integers into two lists: `primes` and `non-primes` using `Collectors.partitioningBy(n -> isPrime(n))`.

---

### M5 · FlatMap (List of Lists)

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** FlatMap & Reduction | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Given `List<List<Integer>>`, use `.flatMap(List::stream)` to flatten it into a single `List<Integer>` of all numbers.

---

### M6 · Max/Min with Streams

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** FlatMap & Reduction | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Find the oldest `User` in a list using `.max(Comparator.comparingInt(User::getAge))`. Return as an `Optional<User>`.

---

### M7 · Parallel Stream Performance

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Parallel Streams | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Perform a complex calculation (e.g., sum of prime factors) on a list of 1,000,000 numbers. Compare the time taken by `.stream()` vs `.parallelStream()`.

---

### M8 · Reduce (Custom Accumulation)

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** FlatMap & Reduction | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Use `.reduce(1, (a, b) -> a * b)` to find the factorial of a small number list. Explain the "Identity" parameter.

---

### M9 · Top K Frequent Words

**🔗 [LC 692 — Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/)** · Medium
**Pattern:** groupingBy + Custom Comparator | **Companies:** Amazon, Google, Uber

**Hint:** Use `Collectors.groupingBy` and then sort by `Entry.getValue()` DESC and `Entry.getKey()` ASC.

---

## 🔴 Hard Tier (4 Problems)

_5 Advanced Problems._

### H1 · Custom Collector

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Custom Collector | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Implement a custom collector that computes the **standard deviation** of a stream of doubles.

---

### H2 · Stream of Files

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Lazy Streams over Files | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Use `Files.lines(Path)` to process a 100MB log file. Filter lines starting with "ERROR" and count them without loading the whole file into RAM.

---

### H3 · Optionals in Serialization

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Optional Best Practices | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Explain why putting `Optional<T>` as a field in a class is considered "bad practice" (it's not Serializable).

---

### H4 · Infinite Stream

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Infinite Streams + limit | **Companies:** Amazon, LinkedIn, Goldman Sachs

**Task:** Use `Stream.generate(Math::random).limit(10)` to produce random numbers.

---

## 📊 Complexity Analysis Exercises

Wait, are Streams efficient? Let's check.

```java
// Snippet 1
long count = IntStream.range(0, n).filter(x -> x % 2 == 0).count();

// Snippet 2
List<Integer> sorted = list.stream().sorted().collect(Collectors.toList());

// Snippet 3
Map<Integer, List<String>> byLength = words.stream().collect(Collectors.groupingBy(String::length));

// Snippet 4
Optional<String> first = words.parallelStream().filter(s -> s.startsWith("A")).findAny();

// Snippet 5
int result = list.stream().reduce(0, Integer::sum);

// Snippet 6
long distinct = lists.stream()
        .flatMap(sublist -> sublist.stream())
        .distinct()
        .count();
```

**Complexity Answers:**

1. **O(n)** Time, O(1) Space. Pipeline lazy evaluation.
2. **O(n log n)** Time, O(n) Space for sorting result.
3. **O(n)** Time, O(n) Space for the HashMap.
4. **O(n)** Time. Running in parallel can divide the wall-clock time by up to the number of cores, but the total
   work — and so the Big-O — is unchanged.
5. **O(n)** Time, O(1) Space.
6. **O(Total Elements)** Time, O(Distinct Elements) Space.

---

## 🔍 Self-Assessment — True / False

1. Lambdas can modify local variables from the outer scope if they are not `final`. → **False** (must be effectively
   final).
2. `stream().map()` is a terminal operation. → **False** (intermediate operation).
3. `optional.get()` will throw an exception if the value is null. → **True** (Always use `orElse` or `isPresent` first).
4. `Collectors.toMap()` throws an exception if keys collide. → **True** (unless a merge function is provided).
5. A Stream can be reused multiple times once closed. → **False**.
6. `filter()` reduces the elements in a stream, but `map()` keeps the count same. → **True**.
7. Method references like `String::toUpperCase` are faster than Lambdas. → **False** (compiled to same bytecode).
8. Functional Interfaces can have multiple default methods. → **True** (only ONE abstract method allowed).

---

## 🧠 Conceptual Check

1. **Lazy Evaluation**: Explain what it means that Java Streams are "lazy". How does it affect performance in a
   `.filter().map().findFirst()` pipeline?
2. **Lambda Internals**: How are Lambdas represented in memory? Are they just anonymous inner classes under the hood?
   (Hint: `invokedynamic`).
3. **Optional Choice**: Why was `Optional` added to Java if we already had null? (Hint: API intent vs pointer safety).
4. **Intermediate vs Terminal**: What happens if you call `.filter().map()` but never call a terminal operation like
   `.toList()` or `.count()`?
5. **Parallel Streams Trap**: When is `parallelStream()` actually SLOWER than a serial stream? (Hint: Small datasets,
   expensive merge steps).

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                          |
| ------------- | --------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Find Resultant Array After Removing Anagrams](https://leetcode.com/problems/find-resultant-array-after-removing-anagrams/), [Uncommon Words from Two Sentences](https://leetcode.com/problems/uncommon-words-from-two-sentences/), [Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/) |
| **Google**    | [Find Resultant Array After Removing Anagrams](https://leetcode.com/problems/find-resultant-array-after-removing-anagrams/), [Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/)                                                                                                        |
| **Microsoft** | [Uncommon Words from Two Sentences](https://leetcode.com/problems/uncommon-words-from-two-sentences/)                                                                                                                                                                                                           |
| **Uber**      | [Top K Frequent Words](https://leetcode.com/problems/top-k-frequent-words/)                                                                                                                                                                                                                                     |

---

## ✅ Completion Checklist

- [ ] All 12 Easy problems solved
- [ ] All 9 Medium problems solved
- [ ] All 4 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 5 conceptual questions answered out loud
- [ ] I can rewrite an anonymous class as a lambda or method reference
- [ ] I can explain when a parallel stream is slower than a sequential one

---

**← [Lecture 6 · OOP & Java Collections Deep Dive](../Lecture6/Assignment.md)** &nbsp;·&nbsp; **[Lecture 8 · Recursion — The Mental Model](../Lecture8/Assignment.md) →**
