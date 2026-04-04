# 📝 Assignment 03 — OOP & Java Collections Deep Dive

> **Topic:** OOP & Java Collections (Phase 1 — Foundations)
> **Topic Count:** 3 of 30 — Phase 1 Foundations
> **Duration:** 4 Days
> **Core Problems:** 35 (15 Easy · 15 Medium · 5 Hard) + 8 Challenge + 8 Complexity Exercises
> **Goal:** Master the abstractions of Java and the high-performance implementation of the Collections Framework.

---

## 🗺️ Problem Map by Pattern

| Pattern / Topic             | Problems           |
| --------------------------- | ------------------ |
| Encapsulation & Access      | 01, 02, 03, 04     |
| Inheritance & Overriding    | 05, 06, 07         |
| Polymorphism (Method)       | 08, 09, 10         |
| Interfaces & Abstraction    | 11, 12, 13, 14, 15 |
| Abstract Classes            | 16, 17, 18         |
| Generics (Basic)            | 19, 20             |
| Bounded Wildcards           | 21, 22, 23         |
| Design Problems (LC)        | 24, 25, 26, 27, 28 |
| Sorting (Comparators)       | 29, 30, 31         |
| Collection Interoperability | 32, 33, 34, 35     |

---

## 🟢 Easy Tier — 15 Problems (OOP Foundations)

### Problem 01 — Encapsulation Audit

Create a `BankAccount` class with a `private` balance. Provide a `deposit()` method that validates the amount is positive. Why is `private balance` better than `public balance`?

### Problem 02 — Data Hiding

Implement a `Person` class where the `age` can only be set between 0 and 150. If an invalid age is passed, print an error or throw an exception. This is the core of "Internal State Protection".

### Problem 03 — Primitive vs Reference Packaging

Create a `WrapperTest` class. Pass a `StringBuilder` to a method and append text. Does the original `StringBuilder` change? Now pass an `Integer` and increment it. Does the original change? Explain.

### Problem 04 — Default vs Private Constructors

When would you make a constructor `private`? (Hint: Utility classes or Singleton pattern). Implement a `MathUtils` class with a private constructor that only has static methods.

### Problem 05 — Simple Inheritance

Create a `Shape` class with a `draw()` method. Create `Circle` and `Square` subclasses that override `draw()`. Use a `Shape` reference to call `draw()` on a `Circle` object.

### Problem 06 — The `super` Keyword

In a `Dog` class extending `Animal`, use `super()` to call the parent's constructor and `super.makeSound()` to call the parent's method before the dog's bark.

### Problem 07 — Static vs Instance variables

Create a `Employee` class where `id` is instance-based and `companyName` is `static`. Create 3 employees. Change `companyName` for one. Check if it changed for others.

### Problem 08 — Method Overloading

Implement `calculateArea(int side)`, `calculateArea(int length, int width)`, and `calculateArea(double radius)`. How does the compiler know which one to call? (Static Polymorphism).

### Problem 09 — Final Keyword

What happens if you try to extend a `final class`? What happens if you try to override a `final method`? Implement a `ConstantManager` class to test this.

### Problem 10 — Overriding `toString()`

Override the `toString()` method for a `Book` class (`title`, `author`). Print the object directly. Why is this better than calling `book.getTitle()`?

### Problem 11 — Interface Basics

Define a `Switchable` interface with `turnOn()` and `turnOff()`. Implement it in `LightBulb` and `Fan`. Why is an interface more flexible than an abstract class here?

### Problem 12 — Multiple Interface Implementation

Implement `Readable` and `Writable` interfaces in a `SmartDocument` class.

### Problem 13 — Default Methods in Interfaces

Can an interface have a method body? Since Java 8, yes. Add a `logActivity()` default method to an interface. Does the implementing class _have_ to override it?

### Problem 14 — Comparable Basics

> 🔗 **Practice:** Make a `Student` class implement `Comparable<Student>` to sort by `gpa` descending. Use `Collections.sort(students)`.

### Problem 15 — ArrayList vs Raw Arrays

Convert an `int[]` array to an `ArrayList<Integer>`. Practice `add()`, `remove(index)`, `set(index, val)`, and `contains()`. Why does `remove(0)` take O(n) time?

---

## 🟡 Medium Tier — 15 Problems (Interview Staples)

### Problem 16 — Abstract Class Design

Create an abstract `PaymentMethod` class with an abstract `processPayment(double amount)` and a concrete `printReceipt()` method. Why can't you instantiate `PaymentMethod`?

### Problem 17 — Nested Classes

Explain the difference between a `static nested class` and an `inner class`. When would you use a `Local Inner Class` inside a method?

### Problem 18 — Interface vs Abstract Class (The Table)

Write a 5-point comparison table for your notes. Key points: Constructor, Multi-inheritance, State (variables), Method visibility, Use cases.

### Problem 19 — Generic Class Implementation

> 🔗 **Practice:** Implement a generic `Box<T>` class that can hold any type. Add `set(T item)` and `T get()`.

### Problem 20 — Generic Methods

Write a generic method `printArray(T[] array)` that prints any array type (Integer, String, Double). Why won't it work for primitives like `int[]`? (Hint: Type Erasure).

### Problem 21 — Bounded Wildcards (UL/LL)

Explain `List<? extends Shape>` (Upper Bound) and `List<? super Circle>` (Lower Bound). Which one allows adding elements? Why? (PECS: Producer Extends, Consumer Super).

### Problem 22 — Design a Stack using ArrayList

Implement a class `MyStack` that uses an internal `ArrayList`. Methods: `push(T)`, `pop()`, `peek()`, `isEmpty()`.

### Problem 23 — Comparator Chain

> 🔗 **Practice:** Sort a `List<Product>` by `category` first (ASC), then by `price` (DESC) within the same category. Use `Comparator.comparing(...).thenComparing(...)`.

### Problem 24 — Design HashMap

> 🔗 **LeetCode:** [706. Design HashMap](https://leetcode.com/problems/design-hashmap/)
> **`[Pattern: Hashing + Collision Handling]` `[Medium]`**
> Implement `put`, `get`, and `remove` without using built-in HashMaps. Use an array of buckets (LinkedLists).

### Problem 25 — Design Linked List

> 🔗 **LeetCode:** [707. Design Linked List](https://leetcode.com/problems/design-linked-list/)
> **`[Pattern: Pointer Manipulation]` `[Medium]`**
> Implement a singly linked list. This cements your understanding of node-based data structures.

### Problem 26 — Implement Stack using Queues

> 🔗 **LeetCode:** [225. Implement Stack using Queues](https://leetcode.com/problems/implement-stack-using-queues/)
> **`[Pattern: Data Structure Interoperability]` `[Medium]`**
> Use two `Queue` objects to simulate a `Last-In-First-Out` stack.

### Problem 27 — Implement Queue using Stacks

> 🔗 **LeetCode:** [232. Implement Queue using Stacks](https://leetcode.com/problems/implement-queue-using-stacks/)
> **`[Pattern: Data Structure Interoperability]` `[Medium]`**
> Use two stacks. Amortized O(1) for `enqueue` and `dequeue`.

### Problem 28 — Min Stack (O(1) time)

> 🔗 **LeetCode:** [155. Min Stack](https://leetcode.com/problems/min-stack/)
> **`[Pattern: Auxiliary State Storage]` `[Amazon] [Google]` `[Medium]`**
> Design a stack that supports `push`, `pop`, `top`, and retrieving the minimum element in constant time. Use an auxiliary "min-stack".

### Problem 29 — Iterator Pattern

Implement the `Iterable` interface on a custom `BookCollection` class. Allow users to use `for(Book b : collection)` to iterate through the books.

### Problem 30 — Deep Copy vs Shallow Copy

Implement `Cloneable` on an `Engine` and a `Car` (which contains an `Engine`). Perform a shallow copy and a deep copy. Change the engine details in the clone. Does it affect the original?

---

## 🔴 Challenge Zone — 5 Advanced Problems

### P31-35: Design Architectures

- **P31: Design an LRU Cache** ([LC 146](https://leetcode.com/problems/lru-cache/)) - The ultimate JCF + OOP test. O(1) time complexity requirement.
- **P32: Generic MyLinkedList<T>**: Implement a doubly linked list with Generics. Support `Iterator`, `Generic types`, and `O(1) size access`.
- **P33: Frequency Stack** ([LC 895](https://leetcode.com/problems/maximum-frequency-stack/)) - A stack that pops the most frequent element.
- **P34: Design Browser History** ([LC 1470](https://leetcode.com/problems/design-browser-history/)) - Using two stacks or a doubly linked list.
- **P35: Dependency Injection Preview**: Write a `EngineInterface` and two implementations: `ElectricEngine` and `GasEngine`. Write a `Car` class that accepts a `EngineInterface` in its constructor. Explain why this is better than "newing" up an engine inside the car.

---

## 📊 Complexity Analysis Exercises — 8 Snippets

Analyze the Time and Space complexity for these OOP/Collection patterns.

```java
// Snippet A: Adding N elements to a LinkedList (at the end) vs ArrayList
List<Integer> list = new LinkedList<>();
for(int i=0; i<n; i++) list.add(i);

// Snippet B: Recursive Fibonacci (Object-based for some reason)
Integer fib(int n) {
    if(n <= 1) return n;
    return fib(n-1) + fib(n-2);
}

// Snippet C: ArrayList clear()
// If list has N elements, what is the complexity of list.clear()? (Hint: it sets elements to null for GC)

// Snippet D: Custom Hash Function
// If hashCode() always returns 1, what is the complexity of HashMap.get()?

// Snippet E: PriorityQueue (O?)
PriorityQueue<Integer> pq = new PriorityQueue<>();
for(int x : nums) pq.offer(x); // N insertions

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

## ✅ Self-Assessment — True / False

1. You can create an instance of an Abstract Class using `new`. → **False**.
2. Private attributes are accessible within the same package. → **False** (only within same class).
3. `Interface` methods are `public abstract` by default. → **True**.
4. A class can extend multiple parent classes in Java. → **False** (Single inheritance for classes).
5. `Generics` info is removed at runtime (Type Erasure). → **True**.
6. `ArrayList` size is fixed once initialized. → **False** (it is dynamic).
7. `HashSet` relies on `hashCode()` to find the correct bucket. → **True**.
8. `static` methods can call non-static instance methods directly. → **False** (needs an object reference).

---

## 🧠 Conceptual Mastery Questions

1. **Composition vs Inheritance**: Why do senior engineers say "Favor composition over inheritance"? Give a real-world scenario.
2. **Type Erasure**: Why can't we use `instanceof T` or `new T()` in a generic class?
3. **Internal Logic**: How does `ArrayList.add()` handle capacity? Explain the "doubling" amortized cost proof.
4. **Abstract vs Interface**: If both allow abstract methods, when precisely do you choose an `Abstract Class` over an `Interface`? (Hint: State vs Behavior).
5. **Polymorphism in Production**: How does the JVM choose which overridden method to call at runtime? (Virtual Method Table lookup).

---

Next: [Topic 4 — Java 8+ Modern Features](../Lecture4/Assignment.md)
