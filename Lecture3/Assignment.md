# 🏗️ Assignment 3 — OOP & Java Collections Deep Dive

> **Lecture:** 3 of 38 — OOP & Java Collections Deep Dive
> **Phase:** 1 — Foundations
> **Estimated Time:** 4 days · **Total Problems:** 35 (15 Easy · 15 Medium · 5 Hard)
> **Goal:** Master the abstractions of Java and the high-performance implementation of the Collections Framework.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                           | Pattern          | Move                                                  |
| ----------------------------------------------- | ---------------- | ----------------------------------------------------- |
| "only valid values allowed"                     | Encapsulation    | private fields + validating methods                   |
| "is-a" relationship                             | Inheritance      | extend, override, call `super`                        |
| "can-do" capability shared by unrelated classes | Interface        | program to the interface, not the class               |
| "design a class that supports …"                | Class Design     | pick the backing structure first, then the invariants |
| "sort objects by several fields"                | Comparator Chain | `comparing(...).thenComparing(...)`                   |
| "iterate over my custom collection"             | Iterator Pattern | implement `Iterable<T>` / wrap an `Iterator`          |

---

## 🟢 Easy Tier (15 Problems)

_OOP Foundations._

### E1 · Encapsulation Audit

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Encapsulation & Constructors | **Companies:** Amazon, Microsoft, Oracle

**Task:** Create a `BankAccount` class with a `private` balance. Provide a `deposit()` method that validates the amount is positive. Why is `private balance` better than `public balance`?

---

### E2 · Data Hiding

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Encapsulation & Constructors | **Companies:** Amazon, Microsoft, Oracle

**Task:** Implement a `Person` class where the `age` can only be set between 0 and 150. If an invalid age is passed, print an error or throw an exception. This is the core of "Internal State Protection".

---

### E3 · Primitive vs Reference Packaging

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Encapsulation & Constructors | **Companies:** Amazon, Microsoft, Oracle

**Task:** Create a `WrapperTest` class. Pass a `StringBuilder` to a method and append text. Does the original `StringBuilder` change? Now pass an `Integer` and increment it. Does the original change? Explain.

---

### E4 · Default vs Private Constructors

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Encapsulation & Constructors | **Companies:** Amazon, Microsoft, Oracle

**Task:** When would you make a constructor `private`? (Hint: Utility classes or Singleton pattern). Implement a `MathUtils` class with a private constructor that only has static methods.

---

### E5 · Simple Inheritance

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Inheritance & static | **Companies:** Amazon, Microsoft, Oracle

**Task:** Create a `Shape` class with a `draw()` method. Create `Circle` and `Square` subclasses that override `draw()`. Use a `Shape` reference to call `draw()` on a `Circle` object.

---

### E6 · The `super` Keyword

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Inheritance & static | **Companies:** Amazon, Microsoft, Oracle

**Task:** In a `Dog` class extending `Animal`, use `super()` to call the parent's constructor and `super.makeSound()` to call the parent's method before the dog's bark.

---

### E7 · Static vs Instance variables

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Inheritance & static | **Companies:** Amazon, Microsoft, Oracle

**Task:** Create a `Employee` class where `id` is instance-based and `companyName` is `static`. Create 3 employees. Change `companyName` for one. Check if it changed for others.

---

### E8 · Method Overloading

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Polymorphism & Object Methods | **Companies:** Amazon, Microsoft, Oracle

**Task:** Implement `calculateArea(int side)`, `calculateArea(int length, int width)`, and `calculateArea(double radius)`. How does the compiler know which one to call? (Static Polymorphism).

---

### E9 · Final Keyword

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Polymorphism & Object Methods | **Companies:** Amazon, Microsoft, Oracle

**Task:** What happens if you try to extend a `final class`? What happens if you try to override a `final method`? Implement a `ConstantManager` class to test this.

---

### E10 · Overriding `toString()`

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Polymorphism & Object Methods | **Companies:** Amazon, Microsoft, Oracle

**Task:** Override the `toString()` method for a `Book` class (`title`, `author`). Print the object directly. Why is this better than calling `book.getTitle()`?

---

### E11 · Interface Basics

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Interfaces & Comparable | **Companies:** Amazon, Microsoft, Oracle

**Task:** Define a `Switchable` interface with `turnOn()` and `turnOff()`. Implement it in `LightBulb` and `Fan`. Why is an interface more flexible than an abstract class here?

---

### E12 · Multiple Interface Implementation

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Interfaces & Comparable | **Companies:** Amazon, Microsoft, Oracle

**Task:** Implement `Readable` and `Writable` interfaces in a `SmartDocument` class.

---

### E13 · Default Methods in Interfaces

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Interfaces & Comparable | **Companies:** Amazon, Microsoft, Oracle

**Task:** Can an interface have a method body? Since Java 8, yes. Add a `logActivity()` default method to an interface. Does the implementing class _have_ to override it?

---

### E14 · Comparable Basics

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Interfaces & Comparable | **Companies:** Amazon, Microsoft, Oracle

**Task:** Make a `Student` class implement `Comparable<Student>` to sort by `gpa` descending. Use `Collections.sort(students)`.

---

### E15 · ArrayList vs Raw Arrays

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Arrays vs Collections | **Companies:** Amazon, Microsoft, Oracle

**Task:** Convert an `int[]` array to an `ArrayList<Integer>`. Practice `add()`, `remove(index)`, `set(index, val)`, and `contains()`. Why does `remove(0)` take O(n) time?

---

## 🟡 Medium Tier (15 Problems)

_Interview Staples._

### M1 · Abstract Class Design

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Abstraction & Nested Classes | **Companies:** Amazon, Microsoft, Oracle

**Task:** Create an abstract `PaymentMethod` class with an abstract `processPayment(double amount)` and a concrete `printReceipt()` method. Why can't you instantiate `PaymentMethod`?

---

### M2 · Nested Classes

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Abstraction & Nested Classes | **Companies:** Amazon, Microsoft, Oracle

**Task:** Explain the difference between a `static nested class` and an `inner class`. When would you use a `Local Inner Class` inside a method?

---

### M3 · Interface vs Abstract Class (The Table)

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Abstraction & Nested Classes | **Companies:** Amazon, Microsoft, Oracle

**Task:** Write a 5-point comparison table for your notes. Key points: Constructor, Multi-inheritance, State (variables), Method visibility, Use cases.

---

### M4 · Generic Class Implementation

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Generics & Wildcards | **Companies:** Amazon, Microsoft, Oracle

**Task:** Implement a generic `Box<T>` class that can hold any type. Add `set(T item)` and `T get()`.

---

### M5 · Generic Methods

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Generics & Wildcards | **Companies:** Amazon, Microsoft, Oracle

**Task:** Write a generic method `printArray(T[] array)` that prints any array type (Integer, String, Double). Why won't it work for primitives like `int[]`? (Hint: Type Erasure).

---

### M6 · Bounded Wildcards (UL/LL)

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Generics & Wildcards | **Companies:** Amazon, Microsoft, Oracle

**Task:** Explain `List<? extends Shape>` (Upper Bound) and `List<? super Circle>` (Lower Bound). Which one allows adding elements? Why? (PECS: Producer Extends, Consumer Super).

---

### M7 · Design a Stack With Increment Operation

**🔗 [LC 1381 — Design a Stack With Increment Operation](https://leetcode.com/problems/design-a-stack-with-increment-operation/)** · Medium
**Pattern:** Class Design — Array-backed Stack | **Companies:** Amazon, Microsoft

**Hint:** Back the stack with an array and a `top` index. For O(1) `increment`, keep a lazy `inc[]` array: add `val` at index `min(k, size) - 1`, and when popping index `i`, carry `inc[i]` down to `inc[i - 1]`.

---

### M8 · Comparator Chain

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Comparators, Iterators & Copying | **Companies:** Amazon, Microsoft, Oracle

**Task:** Sort a `List<Product>` by `category` first (ASC), then by `price` (DESC) within the same category. Use `Comparator.comparing(...).thenComparing(...)`.

---

### M9 · Design HashMap

**🔗 [LC 706 — Design HashMap](https://leetcode.com/problems/design-hashmap/)** · Easy
**Pattern:** Hashing + Collision Handling | **Companies:** Amazon, Google, Microsoft

**Hint:** Implement `put`, `get`, and `remove` without using built-in HashMaps. Use an array of buckets (LinkedLists).

---

### M10 · Design Linked List

**🔗 [LC 707 — Design Linked List](https://leetcode.com/problems/design-linked-list/)** · Medium
**Pattern:** Pointer Manipulation | **Companies:** Amazon, Microsoft, Adobe

**Hint:** Implement a singly linked list. This cements your understanding of node-based data structures.

---

### M11 · Design Parking System

**🔗 [LC 1603 — Design Parking System](https://leetcode.com/problems/design-parking-system/)** · Easy
**Pattern:** Class Design — Encapsulation | **Companies:** Amazon, Microsoft

**Hint:** Hold the three remaining capacities in a `private` array indexed by car type. `addCar` checks and decrements. Nothing outside the class can change the counts directly — that's encapsulation.

---

### M12 · Design an Ordered Stream

**🔗 [LC 1656 — Design an Ordered Stream](https://leetcode.com/problems/design-an-ordered-stream/)** · Easy
**Pattern:** Class Design — State | **Companies:** Bloomberg, Amazon

**Hint:** Keep a `String[]` of size n+1 and a `ptr` starting at 1. `insert` stores the value, then collects values while `arr[ptr]` is filled, moving `ptr` forward.

---

### M13 · Simple Bank System

**🔗 [LC 2043 — Simple Bank System](https://leetcode.com/problems/simple-bank-system/)** · Medium
**Pattern:** Class Design — Validation | **Companies:** Amazon, Microsoft

**Hint:** Wrap the balances in a class with one private helper `valid(account)`. Each operation validates the accounts and balances first and only then mutates — no half-finished transfers.

---

### M14 · Peeking Iterator

**🔗 [LC 284 — Peeking Iterator](https://leetcode.com/problems/peeking-iterator/)** · Medium
**Pattern:** Iterator Pattern — Decorator | **Companies:** Google, Apple, Amazon

**Hint:** Wrap the given `Iterator` and cache one element ahead (`nextVal`, `hasPeeked`). `peek` fills the cache without consuming; `next` returns the cache if filled. Make it generic: `PeekingIterator<T>`.

---

### M15 · Deep Copy vs Shallow Copy

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Comparators, Iterators & Copying | **Companies:** Amazon, Microsoft, Oracle

**Task:** Implement `Cloneable` on an `Engine` and a `Car` (which contains an `Engine`). Perform a shallow copy and a deep copy. Change the engine details in the clone. Does it affect the original?

---

## 🔴 Hard Tier (5 Problems)

_5 Advanced Problems._

### H1 · Design a Text Editor

**🔗 [LC 2296 — Design a Text Editor](https://leetcode.com/problems/design-a-text-editor/)** · Hard
**Pattern:** Class Design — Two Stacks | **Companies:** Amazon, Google

**Hint:** Model the cursor as the gap between two stacks (text left of the cursor, text right of it). Moving the cursor pops from one and pushes onto the other; add and delete touch only the left stack. Use `StringBuilder`s for O(1) pushes and pops at the end.

---

### H2 · Generic `MyLinkedList<T>`

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Generics + Iterator | **Companies:** Amazon, Microsoft, Oracle

**Task:** Implement a doubly linked list with Generics. Support `Iterator`, `Generic types`, and `O(1) size access`.

---

### H3 · Maximum Frequency Stack

**🔗 [LC 895 — Maximum Frequency Stack](https://leetcode.com/problems/maximum-frequency-stack/)** · Hard
**Pattern:** Map of Stacks by Frequency | **Companies:** Amazon, Google, Meta

**Hint:** Keep `freq: value → count` and `group: count → stack of values`, plus `maxFreq`. `push` increments the value's count and pushes it onto that count's stack. `pop` pops from `group[maxFreq]`, decrements the count, and lowers `maxFreq` when that stack empties.

---

### H4 · Design Browser History

**🔗 [LC 1472 — Design Browser History](https://leetcode.com/problems/design-browser-history/)** · Medium
**Pattern:** Two Stacks / Doubly Linked List | **Companies:** Amazon, Google, Bloomberg

**Hint:** Hold the history in an `ArrayList<String>` with a `cur` index and a `last` index. `visit` overwrites at `cur + 1` and sets `last = cur`; `back` and `forward` just clamp `cur` between 0 and `last`. Every operation is O(1).

---

### H5 · Dependency Injection Preview

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** Interfaces & Dependency Injection | **Companies:** Amazon, Microsoft, Oracle

**Task:** Write a `EngineInterface` and two implementations: `ElectricEngine` and `GasEngine`. Write a `Car` class that accepts a `EngineInterface` in its constructor. Explain why this is better than

"newing" up an engine inside the car.

---

## 📊 Complexity Analysis Exercises

Analyze the Time and Space complexity for these OOP/Collection patterns.

```java
// Snippet A: Adding N elements to a LinkedList (at the end) vs ArrayList
List<Integer> list = new LinkedList<>();
for (int i = 0; i < n; i++) list.add(i);

// Snippet B: Recursive Fibonacci (Object-based for some reason)
Integer fib(int n) {
    if (n <= 1) return n;
    return fib(n - 1) + fib(n - 2);
}

// Snippet C: ArrayList clear()
// If list has N elements, what is the complexity of list.clear()? (Hint: it sets elements to null for GC)

// Snippet D: Custom Hash Function
// If hashCode() always returns 1, what is the complexity of HashMap.get()?

// Snippet E: PriorityQueue (O?)
PriorityQueue<Integer> pq = new PriorityQueue<>();
for (int x : nums) pq.offer(x); // N insertions

// Snippet F: Binary Search in Sorted ArrayList
Collections.binarySearch(myArrayList, target);

// Snippet G: Binary Search in Sorted LinkedList
Collections.binarySearch(myLinkedList, target); // Warning: Think about random access!

// Snippet H: Deep copy of a nested structure (N nodes, depth D)
```

**Answers:**

| Snippet | Time       | Space | Explanation                                                           |
| :------ | :--------- | :---- | :-------------------------------------------------------------------- |
| **A**   | O(n)       | O(n)  | Both are O(n) total if adding to end.                                 |
| **B**   | O(2ⁿ)      | O(n)  | Binary tree of depth N.                                               |
| **C**   | O(n)       | O(1)  | Must nullify each element pointer for GC.                             |
| **D**   | O(n)       | O(1)  | Degradation to a singly linked list.                                  |
| **E**   | O(n log n) | O(n)  | n separate O(log n) heap adjustments.                                 |
| **F**   | O(log n)   | O(1)  | ArrayList has RandomAccess (Direct index logic).                      |
| **G**   | O(n)       | O(1)  | LinkedList lacks RandomAccess; binary search defaults to linear walk. |
| **H**   | O(n)       | O(n)  | Must visit every node to copy.                                        |

---

## 🔍 Self-Assessment — True / False

1. You can create an instance of an Abstract Class using `new`. → **False**.
2. Private attributes are accessible within the same package. → **False** (only within same class).
3. `Interface` methods are `public abstract` by default. → **True**.
4. A class can extend multiple parent classes in Java. → **False** (Single inheritance for classes).
5. `Generics` info is removed at runtime (Type Erasure). → **True**.
6. `ArrayList` size is fixed once initialized. → **False** (it is dynamic).
7. `HashSet` relies on `hashCode()` to find the correct bucket. → **True**.
8. `static` methods can call non-static instance methods directly. → **False** (needs an object reference).

---

## 🧠 Conceptual Check

1. **Composition vs Inheritance**: Why do senior engineers say "Favor composition over inheritance"? Give a real-world
   scenario.
2. **Type Erasure**: Why can't we use `instanceof T` or `new T()` in a generic class?
3. **Internal Logic**: How does `ArrayList.add()` handle capacity? Explain the "doubling" amortized cost proof.
4. **Abstract vs Interface**: If both allow abstract methods, when precisely do you choose an `Abstract Class` over an
   `Interface`? (Hint: State vs Behavior).
5. **Polymorphism in Production**: How does the JVM choose which overridden method to call at runtime? (Virtual Method
   Table lookup).

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                             |
| ------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| **Amazon**    | [Design a Text Editor](https://leetcode.com/problems/design-a-text-editor/), [Maximum Frequency Stack](https://leetcode.com/problems/maximum-frequency-stack/), [Design Browser History](https://leetcode.com/problems/design-browser-history/), [Design a Stack With Increment Operation](https://leetcode.com/problems/design-a-stack-with-increment-operation/) |
| **Google**    | [Design a Text Editor](https://leetcode.com/problems/design-a-text-editor/), [Maximum Frequency Stack](https://leetcode.com/problems/maximum-frequency-stack/), [Design Browser History](https://leetcode.com/problems/design-browser-history/), [Design HashMap](https://leetcode.com/problems/design-hashmap/)                                                   |
| **Microsoft** | [Design a Stack With Increment Operation](https://leetcode.com/problems/design-a-stack-with-increment-operation/), [Design HashMap](https://leetcode.com/problems/design-hashmap/), [Design Linked List](https://leetcode.com/problems/design-linked-list/), [Design Parking System](https://leetcode.com/problems/design-parking-system/)                         |
| **Bloomberg** | [Design Browser History](https://leetcode.com/problems/design-browser-history/), [Design an Ordered Stream](https://leetcode.com/problems/design-an-ordered-stream/)                                                                                                                                                                                               |
| **Adobe**     | [Design Linked List](https://leetcode.com/problems/design-linked-list/)                                                                                                                                                                                                                                                                                            |

---

## ✅ Completion Checklist

- [ ] All 15 Easy problems solved
- [ ] All 15 Medium problems solved
- [ ] All 5 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 5 conceptual questions answered out loud
- [ ] I can explain when to choose an abstract class over an interface
- [ ] I can override `equals` and `hashCode` correctly together

---

**← [Lecture 2 · Java Memory Management](../Lecture2/Assignment.md)** &nbsp;·&nbsp; **[Lecture 4 · Java 8+ Modern Features](../Lecture4/Assignment.md) →**
