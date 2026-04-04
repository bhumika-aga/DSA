# 🎯 DSA Mastery — Complete Study Plan

> **Inspired by Kunal Kushwaha's DSA in Java Lectures**
> Pattern-first · Intuition-before-code · Company-tagged problems

---

## 📊 Overview

| Metric             | Value                    |
| ------------------ | ------------------------ |
| **Total Topics**   | 30 (Updated)             |
| **Phases**         | 4                        |
| **Duration**       | 22–26 Weeks              |
| **Total Problems** | 600+                     |
| **Approach**       | Pattern-based, bottom-up |

### How to Use This Plan

1. **Follow the phases in order** — each builds on the previous
2. **Master patterns, not problems** — recognize the pattern, then solve any variant
3. **Think before you code** — Mantra: understand the intuition first
4. **Practice daily** — consistency beats intensity
5. **Tag your solves** — track which patterns and companies you've covered

---

## 🟣 Phase 1 — Foundations (Weeks 1–5)

> Build the mental models. Learn to think recursively. Understand how the computer thinks.

---

### Topic 1: ⚙️ Java & Programming Fundamentals

| Detail               | Value              |
| -------------------- | ------------------ |
| **Duration**         | 5 days             |
| **Problems**         | 20                 |
| **Difficulty Split** | 15 Easy · 5 Medium |
| **Prerequisites**    | None               |

#### 🎓 Learning Objectives

- Understand variables, data types, operators, and control flow
- Master loops (for, while, do-while) and when to use each
- Grasp methods, scope, and the call stack
- Learn OOP pillars: Encapsulation, Inheritance, Polymorphism, Abstraction
- Introduction to time and space complexity (Big-O notation)

#### 🔑 Key Patterns

| Pattern                | Description                                | Example Problem                 |
| ---------------------- | ------------------------------------------ | ------------------------------- |
| **Iteration**          | Using loops to traverse/process data       | Print all elements of an array  |
| **Base case thinking** | Identifying when to stop a process         | Factorial calculation           |
| **Big-O analysis**     | Counting operations relative to input size | Compare O(n) vs O(n²) solutions |
| **Digit extraction**   | Use `% 10` and `/ 10` to process digits    | Reverse a number, digit sum     |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Variables, data types (int, long, double, char, boolean), type casting, integer overflow
2. **Day 2:** Operators, control flow (if/else, switch), loops (for, while, do-while, enhanced-for)
3. **Day 3:** Methods, parameter passing (by value vs reference), scope, the call stack, overloading
4. **Day 4:** OOP — Classes, objects, constructors, `this` keyword, `static` vs instance, inheritance, polymorphism
5. **Day 5:** Introduction to Big-O — O(1), O(log n), O(n), O(n log n), O(n²), O(2ⁿ), O(n!), space complexity

#### 🏢 Companies That Ask These

`Google` `Amazon` `Microsoft`

---

### Topic 2: 🧠 Java Memory Management

| Detail               | Value              |
| -------------------- | ------------------ |
| **Duration**         | 2 days             |
| **Problems**         | 5 (Conceptual)     |
| **Difficulty Split** | 5 Easy             |
| **Prerequisites**    | Programming Basics |

#### 🎓 Learning Objectives

- Master the difference between Stack (static) and Heap (dynamic) memory
- Understand how Java handles primitive vs. object references
- Grasp Garbage Collection as a background process and why it matters
- Identify and prevent common memory leaks in Java applications

#### 🔑 Key Patterns

| Pattern                 | Description                                | Example Problem                   |
| ----------------------- | ------------------------------------------ | --------------------------------- |
| **Pass-by-value/ref**   | Understand what exactly is copied in Java  | Value vs Object reference swap    |
| **Scope understanding** | Visualize stack frames during method calls | Method call stack visualization   |
| **GC trigger thinking** | Recognize when objects become GC-eligible  | Object dereferencing scenarios    |
| **Object lifecycle**    | Track instantiation to destruction         | Visualize object creation in heap |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Stack vs. Heap architecture, stack frames, primitive vs. reference types, pass-by-value in Java
2. **Day 2:** Garbage Collection algorithms (basics), Young vs. Old gen, finalization, detecting memory leaks

#### 🏢 Companies That Ask These

`Google` `Oracle` `Goldman Sachs`

---

### Topic 3: 🏗️ OOP & Java Collections Deep Dive

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 4 days                     |
| **Problems**         | 15                         |
| **Difficulty Split** | 8 Easy · 5 Medium · 2 Hard |
| **Prerequisites**    | Java Fundamentals          |

#### 🎓 Learning Objectives

- Understand interfaces, abstract classes, generics
- Master Java Collections Framework: ArrayList, LinkedList, Stack, Queue, Deque, PriorityQueue
- Learn HashMap, TreeMap, LinkedHashMap and when to use each
- Understand Comparable vs Comparator for custom sorting
- Learn Iterator pattern and for-each internals

#### 🔑 Key Patterns

| Pattern                    | Description                                    | Example Problem                   |
| -------------------------- | ---------------------------------------------- | --------------------------------- |
| **Custom Comparator**      | Sort objects by derived key                    | Sort employees by salary          |
| **Collections.sort()**     | Leverage built-in sort with lambda comparators | Sort arrays by second element     |
| **Map as frequency store** | getOrDefault, merge, putIfAbsent patterns      | Character frequency count         |
| **Deque as stack & queue** | Use ArrayDeque for both LIFO and FIFO          | Implement stack using ArrayDeque  |
| **PriorityQueue reversal** | Pass custom comparator to reverse heap order   | K largest elements using min-heap |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Interfaces, abstract classes, generics (`List<T>`, `Comparable<T>`), wildcards, type erasure
2. **Day 2:** ArrayList vs LinkedList, Stack, Queue, Deque — when to use which. ArrayDeque internals.
3. **Day 3:** HashMap, TreeMap, LinkedHashMap — hashing internals, red-black trees, insertion-order maps
4. **Day 4:** Comparable vs Comparator, Collections utility methods, Iterator pattern, streams intro

#### 🏢 Companies That Ask These

`Amazon` `Microsoft` `Adobe` `Goldman Sachs`

---

### Topic 4: ⚡ Java 8+ Modern Features

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 3 days                     |
| **Problems**         | 10                         |
| **Difficulty Split** | 4 Easy · 4 Medium · 2 Hard |
| **Prerequisites**    | OOP & Collections          |

#### 🎓 Learning Objectives

- Master Lambda expressions for concise and readable interview code
- Understand functional interfaces (Predicate, Consumer, Supplier, Function)
- Use the Streams API to process collections like a pro (filter, map, reduce)
- Learn Optional<T> to handle null-safety without bulky if-statements

#### 🔑 Key Patterns

| Pattern                  | Description                              | Example Problem                    |
| ------------------------ | ---------------------------------------- | ---------------------------------- |
| **Stream Filtering**     | Filter collections using Predicate       | Filter strings by length or starts |
| **Map-Reduce**           | Transform then aggregate data            | Sum squares of even numbers        |
| **Lambda Sorting**       | Use lambda as Comparator in sort()       | Sort objects by multiple fields    |
| **Functional Interface** | Pass behavior as data to generic methods | Custom functional processor        |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Lambda expressions syntax, functional interfaces Basics, `@FunctionalInterface` annotation
2. **Day 2:** Streams API deep dive — filter, map, flatMap, findFirst, collectors (toList, groupingBy)
3. **Day 3:** Advanced Streams — reduce, parallel streams, Optional<T> for null safety, method references

#### 🏢 Companies That Ask These

`Amazon` `LinkedIn` `Salesforce`

---

### Topic 5: 🔁 Recursion & Backtracking

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 7 days                      |
| **Problems**         | 30                          |
| **Difficulty Split** | 8 Easy · 15 Medium · 7 Hard |
| **Prerequisites**    | Java Fundamentals           |

#### 🎓 Learning Objectives

- Understand the recursive leap of faith — trust the function
- Visualize recursion as a tree of calls
- Master the 3 steps: base case, recursive relation, combine results
- Learn backtracking as "recursion + undo"
- Identify when to use memoization to avoid recomputation

#### 🔑 Key Patterns

| Pattern                   | Description                                           | Example Problem          |
| ------------------------- | ----------------------------------------------------- | ------------------------ |
| **Recursive Tree**        | Visualize all branches of recursive calls             | Fibonacci, Power Set     |
| **Backtracking**          | Try → Explore → Undo (for constraint satisfaction)    | N-Queens, Sudoku Solver  |
| **Divide & Conquer seed** | Split problem, solve halves, combine                  | Merge Sort (intro)       |
| **Memoization intro**     | Cache results of overlapping subproblems              | Fibonacci with memo      |
| **Include/Exclude**       | At each step, choose to include or exclude an element | Subsets, Combination Sum |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** What is recursion? Stack frames, call stack visualization, simple examples (factorial, sum of N)
2. **Day 2:** Recursion on arrays — print array, find max, check sorted, linear search recursively
3. **Day 3:** Recursion on strings — palindrome check, reverse string, count occurrences recursively
4. **Day 4:** Subsets & Subsequences — power set, subsets with duplicates, subsequence generation
5. **Day 5:** Permutations — all permutations, permutations with duplicates, letter combinations of phone number
6. **Day 6:** Backtracking — N-Queens, Sudoku Solver, Word Search, Rat in a Maze
7. **Day 7:** Advanced backtracking — Knight's Tour, Combination Sum I/II/III, Palindrome Partitioning

#### 🏢 Companies That Ask These

`Google` `Facebook/Meta` `Amazon` `Uber`

---

### Topic 6: 📊 Bit Manipulation

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 3 days                     |
| **Problems**         | 15                         |
| **Difficulty Split** | 8 Easy · 5 Medium · 2 Hard |
| **Prerequisites**    | Java Fundamentals          |

#### 🎓 Learning Objectives

- Understand binary representation and bitwise operators (AND, OR, XOR, NOT, shifts)
- Learn bit tricks that appear in interviews
- Solve problems in O(1) space using bit manipulation
- Understand bitmask DP setup (used in Phase 3)

#### 🔑 Key Patterns

| Pattern               | Description                                   | Example Problem       |
| --------------------- | --------------------------------------------- | --------------------- |
| **XOR cancellation**  | a ⊕ a = 0, useful for finding unique elements | Single Number         |
| **Bit masking**       | Use bits as boolean flags for subsets         | Subsets using bitmask |
| **Power of 2 check**  | n & (n-1) == 0                                | Power of Two          |
| **Brian Kernighan's** | Count set bits by clearing lowest set bit     | Count Set Bits        |
| **Set/Clear/Toggle**  | Manipulate individual bits                    | Set/Clear kth bit     |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Binary number system, AND, OR, XOR, NOT, left/right shift, 2's complement, signed integers
2. **Day 2:** Bit tricks — check odd/even, swap without temp, find sign, absolute value, check power of 2
3. **Day 3:** Interview problems — Single Number I/II/III, Missing Number, Counting Bits, Reverse Bits, Hamming Distance

#### 🏢 Companies That Ask These

`Amazon` `Microsoft` `Apple`

---

### Topic 7: 🏆 Math & Number Theory

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 4 days                     |
| **Problems**         | 15                         |
| **Difficulty Split** | 6 Easy · 6 Medium · 3 Hard |
| **Prerequisites**    | Java Fundamentals          |

#### 🎓 Learning Objectives

- Master GCD, LCM, prime factorization, and sieve algorithms
- Apply modular arithmetic for large number problems
- Use fast exponentiation to replace brute-force powers
- Understand combinatorics: nCr, Pascal's triangle, Catalan numbers

#### 🔑 Key Patterns

| Pattern                   | Description                              | Example Problem     |
| ------------------------- | ---------------------------------------- | ------------------- |
| **Sieve of Eratosthenes** | All primes up to N in O(N log log N)     | Count Primes        |
| **Fast Exponentiation**   | Compute pow(x, n) in O(log n)            | Pow(x, n)           |
| **Modular Arithmetic**    | (a + b) % m = ((a % m) + (b % m)) % m    | Large Fibonacci     |
| **GCD/LCM**               | Euclidean algorithm: gcd(a,b)=gcd(b,a%b) | Fraction simplify   |
| **Combinatorics nCr**     | Pascal's triangle, permutations          | Unique Paths (math) |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** GCD (Euclidean), LCM, prime factorization, Sieve of Eratosthenes, prime test O(√n)
2. **Day 2:** Fast exponentiation, modular arithmetic, modular inverse (Fermat's little theorem), Pow(x, n), Sqrt(x)
3. **Day 3:** Number theory problems — Count Primes, Happy Number, Excel Sheet Column, Ugly Number I/II
4. **Day 4:** Combinatorics — Pascal's Triangle, Unique Paths (math), Catalan Numbers, nCr mod p

#### 🏢 Companies That Ask These

`Google` `Amazon` `Apple` `Microsoft`

---

## 🟢 Phase 2 — Core Data Structures (Weeks 6–13)

> The bread and butter. These topics make up 60–70% of coding interviews.

---

### Topic 8: 📋 Arrays & Strings

| Detail               | Value                        |
| -------------------- | ---------------------------- |
| **Duration**         | 8 days                       |
| **Problems**         | 40                           |
| **Difficulty Split** | 10 Easy · 22 Medium · 8 Hard |
| **Prerequisites**    | Recursion basics, Big-O      |

#### 🎓 Learning Objectives

- Master in-place array manipulation techniques
- Learn two-pointer technique for sorted/unsorted arrays
- Understand sliding window for subarray/substring problems
- Use prefix sums for O(1) range query optimization
- Apply Kadane's algorithm for maximum subarray problems

#### 🔑 Key Patterns

| Pattern                 | Description                                     | Example Problem                              |
| ----------------------- | ----------------------------------------------- | -------------------------------------------- |
| **Two Pointers**        | Converge from both ends or chase pointers       | Two Sum (sorted), 3Sum, Container with Water |
| **Sliding Window**      | Fixed or variable-size window over array/string | Longest Substring Without Repeating          |
| **Prefix Sum**          | Precompute cumulative sums for O(1) queries     | Subarray Sum Equals K, Range Sum Query       |
| **Kadane's Algorithm**  | Track max subarray sum ending at each index     | Maximum Subarray, Max Product Subarray       |
| **Dutch National Flag** | 3-way partition in single pass                  | Sort Colors                                  |
| **In-place reversal**   | Reverse portions of array without extra space   | Rotate Array, Reverse Words in String        |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Array basics — traversal, insertion, deletion. String basics — immutability, StringBuilder vs String
2. **Day 2:** Two pointers — Two Sum II, Remove Duplicates, Move Zeroes, Container with Most Water
3. **Day 3:** Two pointers advanced — 3Sum, 3Sum Closest, Trapping Rain Water (two-pointer approach)
4. **Day 4:** Sliding window (fixed) — Max Sum Subarray of Size K, first negative, Permutation in String
5. **Day 5:** Sliding window (variable) — Longest Substring Without Repeating, Minimum Window Substring
6. **Day 6:** Prefix sum — Range Sum Query, Subarray Sum Equals K, Product of Array Except Self
7. **Day 7:** Kadane's — Maximum Subarray, Maximum Product Subarray, Circular Subarray Sum
8. **Day 8:** Mixed mastery — Rotate Array, Next Permutation, Majority Element (Boyer-Moore), Longest Consecutive Sequence

#### 🏢 Companies That Ask These

`Google` `Amazon` `Facebook/Meta` `Microsoft` `Uber`

---

### Topic 9: ⚡ Sorting Algorithms

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 4 days                      |
| **Problems**         | 20                          |
| **Difficulty Split** | 5 Easy · 10 Medium · 5 Hard |
| **Prerequisites**    | Arrays, Recursion           |

#### 🎓 Learning Objectives

- Implement all major sorting algorithms from scratch
- Know stability, in-place, and worst-case trade-offs for each sort
- Apply sort as preprocessing to unlock faster algorithms
- Understand counting/radix sort for O(n) on bounded-range inputs

#### 🔑 Key Patterns

| Pattern                  | Description                                   | Example Problem                   |
| ------------------------ | --------------------------------------------- | --------------------------------- |
| **Merge Sort D&C**       | Split, sort halves, merge — stable O(n log n) | Merge Sort, Count Inversions      |
| **Quick Sort Partition** | Partition around pivot — avg O(n log n)       | Quick Sort, Dutch National Flag   |
| **Counting/Radix Sort**  | Non-comparison sort for bounded integer range | Maximum Gap, Sort Colors          |
| **Sort as preprocess**   | Sort first, then apply linear algorithm       | Meeting Rooms, 3Sum               |
| **Custom sort (lambda)** | Sort by derived key using Comparator          | Sort by frequency, Sort by parity |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** O(n²) sorts — Bubble Sort (stable), Selection Sort (unstable), Insertion Sort (adaptive, stable)
2. **Day 2:** O(n log n) sorts — Merge Sort (stable, D&C), Quick Sort (partition, pivot selection, unstable)
3. **Day 3:** Special sorts — Heap Sort, Counting Sort, Radix Sort, Bucket Sort — when and why each
4. **Day 4:** Interview problems — Custom Comparator, Largest Number, Wiggle Sort, Maximum Gap

#### 🏢 Companies That Ask These

`Google` `Amazon` `Microsoft` `Apple`

---

### Topic 10: 🔎 Binary Search (Deep Dive)

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 5 days                      |
| **Problems**         | 25                          |
| **Difficulty Split** | 6 Easy · 12 Medium · 7 Hard |
| **Prerequisites**    | Arrays, Sorting             |

#### 🎓 Learning Objectives

- Implement binary search perfectly — get boundaries right every single time
- Recognize disguised binary search problems that aren't obviously binary search
- Apply "binary search on answer" for monotonic optimization problems
- Search in rotated arrays, 2D matrices, and infinite streams
- Understand the loop invariant: what is always true in every iteration

#### 🔑 Key Patterns

| Pattern                     | Description                                  | Example Problem                              |
| --------------------------- | -------------------------------------------- | -------------------------------------------- |
| **Classic Binary Search**   | lo/hi/mid framework, left vs right bias      | Search Insert Position, Find Peak Element    |
| **Binary Search on Answer** | Search the optimal answer in monotonic space | Koko Eating Bananas, Split Array Largest Sum |
| **Rotated Array Search**    | Identify which half is sorted, binary search | Search in Rotated Sorted Array I/II          |
| **First/Last Occurrence**   | Leftmost or rightmost index of target        | Find First and Last Position in Array        |
| **2D Matrix Binary Search** | Treat 2D matrix as flat sorted array         | Search a 2D Matrix I/II                      |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Classic template — lo/hi/mid, off-by-one bugs, when to use `<` vs `<=`, left vs right bias
2. **Day 2:** Variants — first/last occurrence, count of target, search insert position, find peak element
3. **Day 3:** Rotated array — Search in Rotated Sorted Array I/II, Find Minimum in Rotated Array
4. **Day 4:** Binary search on answer — Koko Eating Bananas, Capacity to Ship, Min Days for Bouquets, Aggressive Cows
5. **Day 5:** Hard — Median of Two Sorted Arrays, Split Array Largest Sum, Search a 2D Matrix II

#### 🏢 Companies That Ask These

`Google` `Amazon` `Microsoft` `Facebook/Meta` `Apple`

---

### Topic 11: 🗂️ Linked Lists

| Detail               | Value                        |
| -------------------- | ---------------------------- |
| **Duration**         | 6 days                       |
| **Problems**         | 28                           |
| **Difficulty Split** | 10 Easy · 13 Medium · 5 Hard |
| **Prerequisites**    | Arrays, Pointers/References  |

#### 🎓 Learning Objectives

- Understand linked list as a recursive data structure
- Master pointer manipulation (next, prev, dummy head sentinel)
- Learn fast & slow pointer technique (Floyd's Cycle Detection algorithm)
- Implement reversal in-place (iterative and recursive forms)
- Handle edge cases: empty list, single node, circular list

#### 🔑 Key Patterns

| Pattern                  | Description                                  | Example Problem                          |
| ------------------------ | -------------------------------------------- | ---------------------------------------- |
| **Fast & Slow Pointers** | Detect cycle, find middle, find nth from end | Linked List Cycle, Middle of LL          |
| **Reverse In-Place**     | Reverse entire list or k-groups iteratively  | Reverse Linked List, Reverse in K-Groups |
| **Merge Two Lists**      | Merge sorted lists using dummy head node     | Merge Two Sorted Lists, Merge K Sorted   |
| **Cycle Detection**      | Floyd's tortoise and hare algorithm          | Linked List Cycle II (find cycle start)  |
| **Dummy Head**           | Sentinel node simplifies all edge cases      | Remove Nth Node from End                 |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Singly LL — implementation, insertion (head/tail/middle), deletion, traversal
2. **Day 2:** Doubly LL, circular LL — implementation and real-world use cases
3. **Day 3:** Fast & slow pointers — find middle, detect cycle, find cycle start, nth from end
4. **Day 4:** Reversal — reverse entire (iterative + recursive), between positions, in k-groups
5. **Day 5:** Merge — merge two sorted lists, merge k sorted lists, sort list (merge sort on LL)
6. **Day 6:** Advanced — LRU Cache, copy list with random pointer, intersection, palindrome LL

#### 🏢 Companies That Ask These

`Amazon` `Microsoft` `Facebook/Meta` `Uber`

---

### Topic 12: 📚 Stacks & Queues

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 5 days                      |
| **Problems**         | 25                          |
| **Difficulty Split** | 8 Easy · 12 Medium · 5 Hard |
| **Prerequisites**    | Arrays, Linked Lists        |

#### 🎓 Learning Objectives

- Understand LIFO (stack) and FIFO (queue) principles and their implementations
- Master monotonic stack for next greater/smaller element problems
- Use queues for BFS and level-order traversals
- Master deque for O(n) sliding window min/max problems

#### 🔑 Key Patterns

| Pattern                   | Description                                         | Example Problem                   |
| ------------------------- | --------------------------------------------------- | --------------------------------- |
| **Monotonic Stack**       | Maintain increasing/decreasing stack for span probs | Next Greater Element, Daily Temps |
| **Histogram Stack**       | Track left/right boundaries for area calculation    | Largest Rectangle in Histogram    |
| **Deque Sliding Window**  | O(n) sliding window max/min using deque             | Sliding Window Maximum            |
| **BFS via Queue**         | Level-by-level graph/tree traversal                 | Binary Tree Level Order           |
| **Expression Evaluation** | Stack for infix/postfix/calculator problems         | Basic Calculator, Evaluate RPN    |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Stack fundamentals — array/LL implementation, balanced parentheses, all parentheses variants
2. **Day 2:** Monotonic stack — Next Greater Element I/II, Daily Temperatures, Stock Span Problem
3. **Day 3:** Stack applications — Largest Rectangle in Histogram, Trapping Rain Water (stack), Min Stack
4. **Day 4:** Queue fundamentals — circular queue, ArrayDeque, priority queue intro
5. **Day 5:** Advanced — Sliding Window Maximum (deque), implement stack using queues, queue using stacks

#### 🏢 Companies That Ask These

`Google` `Amazon` `Microsoft` `Facebook/Meta`

---

### Topic 13: 🗃️ HashMap & HashSet

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 4 days                      |
| **Problems**         | 20                          |
| **Difficulty Split** | 6 Easy · 10 Medium · 4 Hard |
| **Prerequisites**    | Arrays, Strings             |

#### 🎓 Learning Objectives

- Understand hashing, hash functions, and collision resolution internals
- Use frequency maps for counting, grouping, and top-K problems
- Apply complement lookup for pair-sum patterns in O(1)
- Know when to use TreeMap (sorted), LinkedHashMap (ordered), vs HashMap (fastest)

#### 🔑 Key Patterns

| Pattern                | Description                                     | Example Problem                            |
| ---------------------- | ----------------------------------------------- | ------------------------------------------ |
| **Frequency Counting** | Count occurrences for duplicates/majority/top-K | Top K Frequent Elements                    |
| **Complement Lookup**  | Store complements for O(1) pair finding         | Two Sum                                    |
| **Grouping by Key**    | Group elements by a derived computed key        | Group Anagrams                             |
| **Prefix Sum + Map**   | Store prefix sums in map for subarray problems  | Subarray Sum Equals K                      |
| **Seen Set**           | Track visited elements for cycle/dup detection  | Happy Number, Longest Consecutive Sequence |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Hashing internals — hash functions, chaining vs open addressing, load factor, Java HashMap
2. **Day 2:** HashMap problems — Two Sum, Roman to Integer, Isomorphic Strings, Word Pattern
3. **Day 3:** Frequency maps — Top K Frequent Elements, Group Anagrams, Sort Characters by Frequency
4. **Day 4:** Advanced — Subarray Sum Equals K, Longest Consecutive Sequence, LRU Cache

#### 🏢 Companies That Ask These

`Google` `Amazon` `Facebook/Meta` `Uber`

---

### Topic 14: 🧮 Matrix Problems

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 4 days                      |
| **Problems**         | 20                          |
| **Difficulty Split** | 5 Easy · 10 Medium · 5 Hard |
| **Prerequisites**    | Arrays, BFS/DFS basics      |

#### 🎓 Learning Objectives

- Traverse 2D grids efficiently (spiral, diagonal, layer-by-layer)
- Apply in-place matrix transformations without extra space
- Use multi-source BFS for grid distance and region problems
- Use DFS for flood fill and connected component labelling

#### 🔑 Key Patterns

| Pattern                   | Description                                  | Example Problem                    |
| ------------------------- | -------------------------------------------- | ---------------------------------- |
| **Spiral Traversal**      | Peel outer ring: right → down → left → up    | Spiral Matrix I/II                 |
| **In-place Rotation**     | Transpose then reverse rows for 90° rotation | Rotate Image                       |
| **Multi-source BFS**      | Start BFS simultaneously from multiple cells | 01 Matrix, Rotting Oranges         |
| **Grid DFS (Flood Fill)** | DFS to explore/mark connected regions        | Number of Islands, Max Area Island |
| **Row/Col Walk**          | O(m+n) walk from corner for sorted 2D matrix | Search a 2D Matrix II              |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Matrix traversal — row-major, anti-diagonal, spiral, zigzag. Spiral Matrix I/II
2. **Day 2:** In-place transforms — Rotate Image, Set Matrix Zeroes, Game of Life (state machine trick)
3. **Day 3:** Grid BFS — 01 Matrix, Rotting Oranges, Walls and Gates, Pacific Atlantic Water Flow
4. **Day 4:** Grid DFS — Number of Islands, Max Area of Island, Flood Fill, Surrounded Regions

#### 🏢 Companies That Ask These

`Google` `Amazon` `Facebook/Meta` `Microsoft`

---

### Topic 15: 🌳 Trees (Binary Trees & BST)

| Detail               | Value                         |
| -------------------- | ----------------------------- |
| **Duration**         | 10 days                       |
| **Problems**         | 45                            |
| **Difficulty Split** | 12 Easy · 23 Medium · 10 Hard |
| **Prerequisites**    | Recursion, Stacks & Queues    |

#### 🎓 Learning Objectives

- Master all traversals (pre, in, post, level-order, Morris traversal)
- Think recursively — every tree problem is root + left sub-problem + right sub-problem
- Leverage BST property for O(log n) operations
- Solve path-sum, ancestor, construction, and serialization problems

#### 🔑 Key Patterns

| Pattern               | Description                                     | Example Problem                 |
| --------------------- | ----------------------------------------------- | ------------------------------- |
| **DFS (Pre/In/Post)** | Recursive or stack-based depth-first traversal  | All traversal variants          |
| **BFS Level-Order**   | Queue-based, level-by-level processing          | Level Order, Zigzag, Right View |
| **Height Recursion**  | height = 1 + max(height(left), height(right))   | Max Depth, Balanced Tree        |
| **Global via Local**  | Update global answer inside each recursive call | Diameter, Max Path Sum          |
| **BST Property**      | left < root < right at every node               | Validate BST, Kth Smallest      |
| **LCA**               | Lowest common ancestor — find split point       | LCA of Binary Tree/BST          |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Terminology, node class, tree types (full/complete/perfect/balanced/degenerate)
2. **Day 2:** DFS — preorder, inorder, postorder (recursive + iterative using explicit stack)
3. **Day 3:** BFS — level order, zigzag, right side view, average of levels, max width of tree
4. **Day 4:** Height & depth — max depth, min depth, balanced check, diameter of binary tree
5. **Day 5:** Paths — path sum I/II/III, root-to-leaf paths, binary tree max path sum
6. **Day 6:** Construction — build from preorder+inorder, from sorted array → BST, BST to sorted DLL
7. **Day 7:** BST ops — search, insert, delete, validate BST, kth smallest, successor/predecessor
8. **Day 8:** LCA — LCA of binary tree, LCA of BST, distance between two nodes
9. **Day 9:** Views — serialize/deserialize BT, vertical/top/bottom/boundary view
10. **Day 10:** Advanced — flatten BT to LL, Morris traversal O(1) space, count complete tree nodes

#### 🏢 Companies That Ask These

`Google` `Amazon` `Facebook/Meta` `Microsoft` `Apple`

---

### Topic 16: ⛰️ Heaps & Priority Queues

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 5 days                      |
| **Problems**         | 20                          |
| **Difficulty Split** | 5 Easy · 10 Medium · 5 Hard |
| **Prerequisites**    | Arrays, Trees (concepts)    |

#### 🎓 Learning Objectives

- Understand heap property (min-heap, max-heap) and heapify operation
- Implement a heap from scratch using array representation
- Solve Top-K problems efficiently with a size-K min-heap
- Use two heaps for dynamic median computation in O(log n) per element

#### 🔑 Key Patterns

| Pattern                | Description                               | Example Problem                  |
| ---------------------- | ----------------------------------------- | -------------------------------- |
| **Min/Max Heap**       | Maintain smallest/largest at root         | Kth Largest Element              |
| **Two Heaps (Median)** | Max-heap lower half, min-heap upper half  | Find Median from Data Stream     |
| **Top K Elements**     | Size-K min-heap to maintain top-K results | Top K Frequent, K Closest Points |
| **K-way Merge**        | Merge K sorted lists using min-heap       | Merge K Sorted Lists             |
| **Heap Sort**          | Build heap O(n) + repeated extractions    | Heap Sort implementation         |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Heap property, array representation (parent=i, left=2i+1, right=2i+2), sift-up, sift-down, build heap O(n)
2. **Day 2:** Heap sort O(n log n), PriorityQueue in Java — custom comparators, objects in heap
3. **Day 3:** Top K — Kth Largest Element, K Closest Points, Top K Frequent, Sort K Sorted Array
4. **Day 4:** Two heaps — Find Median from Data Stream, Sliding Window Median
5. **Day 5:** K-way merge — Merge K Sorted Lists, Smallest Range Covering Elements, Task Scheduler, Reorganize String

#### 🏢 Companies That Ask These

`Google` `Amazon` `Microsoft`

---

## 🟠 Phase 3 — Advanced Structures & Algorithms (Weeks 14–20)

> The differentiators. These topics separate good from great in interviews.

---

### Topic 17: 🕸️ Graphs

| Detail               | Value                                  |
| -------------------- | -------------------------------------- |
| **Duration**         | 12 days                                |
| **Problems**         | 45                                     |
| **Difficulty Split** | 8 Easy · 25 Medium · 12 Hard           |
| **Prerequisites**    | Recursion, BFS/DFS from Trees, HashMap |

#### 🎓 Learning Objectives

- Understand graph representations (adjacency list, matrix, edge list) and trade-offs
- Master BFS for shortest path in unweighted graphs
- Master DFS for connectivity, cycle detection, and topological sort
- Apply Dijkstra's and Bellman-Ford for weighted shortest paths
- Build minimum spanning trees with Kruskal's and Prim's

#### 🔑 Key Patterns

| Pattern                      | Description                                       | Example Problem                        |
| ---------------------------- | ------------------------------------------------- | -------------------------------------- |
| **BFS Shortest Path**        | Level-by-level, shortest path in unweighted graph | Word Ladder, Shortest Path in Grid     |
| **DFS Connected Components** | Explore all reachable nodes, label components     | Number of Islands, Number of Provinces |
| **Topological Sort**         | Order DAG nodes respecting all edge directions    | Course Schedule I/II, Alien Dictionary |
| **Dijkstra**                 | Weighted shortest path via min-heap               | Network Delay Time, Path Min Effort    |
| **Bellman-Ford**             | Handles negative weights, detect negative cycle   | Cheapest Flights Within K Stops        |
| **Cycle Detection**          | Back edge (directed), parent skip (undirected)    | Course Schedule, Redundant Connection  |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Graph basics — terminology, directed/undirected, weighted, adjacency list vs matrix
2. **Day 2:** BFS — unweighted shortest path, single-source, multi-source (01 Matrix, Rotting Oranges)
3. **Day 3:** DFS — traversal, connected components, Number of Islands, clone graph
4. **Day 4:** Cycle detection — directed graph (3-color DFS), undirected (parent-skip DFS)
5. **Day 5:** Topological sort — Kahn's BFS algorithm, DFS-based, Course Schedule II, Alien Dictionary
6. **Day 6:** Dijkstra's — min-heap approach, Network Delay Time, Path With Minimum Effort
7. **Day 7:** Bellman-Ford — negative weights / K-stops constraint, Cheapest Flights Within K Stops
8. **Day 8:** MST — Kruskal's (sort edges + Union-Find), Prim's (min-heap), Min Cost Connect All Points
9. **Day 9:** Advanced BFS — Word Ladder I/II, Open the Lock, Bidirectional BFS
10. **Day 10:** Bipartite graphs — Is Graph Bipartite?, Possible Bipartition
11. **Day 11:** Bridges & articulation points — Tarjan's algorithm, Critical Connections in a Network
12. **Day 12:** Floyd-Warshall (all-pairs), Eulerian path, review & hard problems

#### 🏢 Companies That Ask These

`Google` `Facebook/Meta` `Amazon` `Microsoft` `Uber`

---

### Topic 18: 🔗 Union-Find (Disjoint Set Union)

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 3 days                     |
| **Problems**         | 15                         |
| **Difficulty Split** | 3 Easy · 8 Medium · 4 Hard |
| **Prerequisites**    | Arrays, Graphs basics      |

#### 🎓 Learning Objectives

- Understand DSU as a data structure for tracking dynamic connectivity
- Implement with path compression + union by rank for near-O(1) per operation
- Apply to connected components, cycle detection, and set-merging problems
- Know when DSU is better than BFS/DFS (online queries, dynamic edges)

#### 🔑 Key Patterns

| Pattern                  | Description                                   | Example Problem                      |
| ------------------------ | --------------------------------------------- | ------------------------------------ |
| **Path Compression**     | Flatten the find() tree — near O(1) amortized | Standard DSU find()                  |
| **Union by Rank/Size**   | Always attach smaller tree to larger          | Standard DSU union()                 |
| **Connected Components** | Count or query connectivity dynamically       | Number of Provinces, Friend Circles  |
| **Cycle Detection**      | If both nodes already in same set → cycle     | Redundant Connection                 |
| **Dynamic Merging**      | Merge sets over time, query connectivity      | Accounts Merge, Number of Islands II |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** DSU fundamentals — naive, path compression, union by rank, Inverse Ackermann O(α) proof
2. **Day 2:** Classic problems — Number of Provinces, Redundant Connection, Graph Valid Tree, Connecting Cities
3. **Day 3:** Advanced — Accounts Merge, Number of Islands II (online), Largest Color Value in a DAG

#### 🏢 Companies That Ask These

`Google` `Facebook/Meta` `Amazon` `Microsoft`

---

### Topic 19: 💡 Greedy Algorithms

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 5 days                      |
| **Problems**         | 20                          |
| **Difficulty Split** | 5 Easy · 10 Medium · 5 Hard |
| **Prerequisites**    | Sorting, Arrays             |

#### 🎓 Learning Objectives

- Understand the greedy choice property and the exchange argument proof technique
- Identify problems where local optimal reliably leads to global optimal
- Distinguish greedy from DP (greedy makes irreversible choices)
- Master interval scheduling as the most important greedy pattern

#### 🔑 Key Patterns

| Pattern                 | Description                                     | Example Problem           |
| ----------------------- | ----------------------------------------------- | ------------------------- |
| **Interval Scheduling** | Sort by end time, greedily pick non-overlapping | Non-Overlapping Intervals |
| **Activity Selection**  | Select max non-conflicting activities           | Meeting Rooms I/II        |
| **Jump Greedy**         | Track max reachable index, expand as you go     | Jump Game I/II            |
| **Gas Station**         | Net surplus greedy — start from valley          | Gas Station               |
| **Assignment**          | Sort both arrays, match greedily                | Assign Cookies            |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Greedy fundamentals — greedy choice property, exchange argument, when greedy fails
2. **Day 2:** Interval problems — Merge Intervals, Non-Overlapping Intervals, Meeting Rooms I/II, Insert Interval
3. **Day 3:** Sequence greedy — Jump Game I/II, Gas Station, Candy, Assign Cookies
4. **Day 4:** Partitioning — Partition Labels, Queue Reconstruction by Height, Task Scheduler
5. **Day 5:** Advanced — Minimum Number of Platforms, Job Sequencing, Fractional Knapsack, Huffman Encoding

#### 🏢 Companies That Ask These

`Amazon` `Google` `Microsoft`

---

### Topic 20: 📐 Intervals & Sweep Line

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 3 days                     |
| **Problems**         | 12                         |
| **Difficulty Split** | 3 Easy · 6 Medium · 3 Hard |
| **Prerequisites**    | Arrays, Sorting, Greedy    |

#### 🎓 Learning Objectives

- Recognize intervals as a distinct pattern family beyond basic merge/overlap
- Apply sweep line algorithm for event-processing problems
- Use difference arrays for O(1) per range update
- Handle Skyline Problem and rectangle area union

#### 🔑 Key Patterns

| Pattern                 | Description                                  | Example Problem                        |
| ----------------------- | -------------------------------------------- | -------------------------------------- |
| **Event Sweep**         | Convert intervals to events, sort, process   | Meeting Rooms II (minimum rooms)       |
| **Difference Array**    | Range increment O(1), reconstruct in O(n)    | Car Pooling, Corporate Flight Bookings |
| **Interval Merging**    | Sort by start, merge overlapping intervals   | Merge Intervals, Insert Interval       |
| **Sweep Line**          | Sweep a vertical line, track active segments | Skyline Problem, Rectangle Area Union  |
| **Coordinate Compress** | Map large sparse coordinates to dense range  | Count Smaller Numbers After Self       |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Interval fundamentals — overlap check (a.end > b.start), merge, insert, min meeting rooms
2. **Day 2:** Difference array — range increment/decrement O(1), car pooling, corporate flight bookings
3. **Day 3:** Sweep line — Skyline Problem, Rectangle Area Union, Employee Free Time

#### 🏢 Companies That Ask These

`Google` `Amazon` `Microsoft` `Uber`

---

### Topic 21: 🧩 Dynamic Programming

| Detail               | Value                                 |
| -------------------- | ------------------------------------- |
| **Duration**         | 15 days                               |
| **Problems**         | 55                                    |
| **Difficulty Split** | 8 Easy · 30 Medium · 17 Hard          |
| **Prerequisites**    | Recursion & Backtracking, Memoization |

#### 🎓 Learning Objectives

- Transform recursive solution → memoization → tabulation systematically
- Recognize DP: choices at each step + overlapping subproblems + optimal substructure
- Master the "state → transition → base case" framework for any DP problem
- Space-optimize 2D DP to 1D using rolling arrays

#### 🔑 Key Patterns

| Pattern                | Description                                      | Example Problem                                  |
| ---------------------- | ------------------------------------------------ | ------------------------------------------------ |
| **0/1 Knapsack**       | Include or exclude each item exactly once        | 0/1 Knapsack, Subset Sum, Partition Equal Subset |
| **Unbounded Knapsack** | Item can be used unlimited times                 | Coin Change I/II, Rod Cutting                    |
| **LCS / LIS**          | Longest common / increasing subsequence          | LCS, Edit Distance, LIS, Russian Doll Envelopes  |
| **Matrix DP**          | Fill 2D table cell by cell with transitions      | Unique Paths, Min Path Sum, Maximal Square       |
| **Interval DP**        | Optimize over subranges [i..j]                   | Burst Balloons, Palindrome Partitioning II       |
| **DP on Trees**        | State transitions follow tree parent→child edges | House Robber III, Max Path Sum                   |
| **Bitmask DP**         | Represent subset as bitmask in DP state          | TSP, Minimum XOR Sum of Two Arrays               |
| **Stock DP**           | State = day × holding status × transactions left | Buy & Sell Stock I/II/III/IV with Cooldown/Fee   |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Fundamentals — recursion → memoization → tabulation. Fibonacci comparison, Climbing Stairs
2. **Day 2:** 1D DP — House Robber I/II, Decode Ways, Word Break, Min Cost Climbing Stairs
3. **Day 3:** 0/1 Knapsack family — 0/1 Knapsack, Subset Sum, Partition Equal Subset, Target Sum
4. **Day 4:** Unbounded Knapsack — Coin Change I (min coins), Coin Change II (ways), Rod Cutting
5. **Day 5:** LIS family — O(n²) DP, O(n log n) patience sort, Russian Doll Envelopes
6. **Day 6:** LCS family — LCS, Shortest Common Supersequence, Edit Distance, Print LCS
7. **Day 7:** String DP — Longest Palindromic Subsequence, Distinct Subsequences, Palindrome Partitioning
8. **Day 8:** Matrix / Grid DP — Unique Paths I/II, Min Path Sum, Maximal Square, Dungeon Game
9. **Day 9:** Interval DP — Matrix Chain Multiplication, Burst Balloons, Min Cost Tree From Leaf Values
10. **Day 10:** Stock problems — Buy & Sell I/II/III/IV, with Cooldown, with Transaction Fee
11. **Day 11:** More subsequences — Longest Common Substring, Count Distinct Subsequences
12. **Day 12:** DP on trees — House Robber III, Maximum Path Sum (DP view), Diameter
13. **Day 13:** Bitmask DP — Traveling Salesman intro, Minimum XOR Sum of Two Arrays, Assign Tasks
14. **Day 14:** Space optimization — rolling array, reduce 2D DP to O(n) or O(1) space
15. **Day 15:** Hard problems — Regular Expression Matching, Wildcard Matching, Interleaving String

#### 🏢 Companies That Ask These

`Google` `Amazon` `Facebook/Meta` `Microsoft` `Apple` `Uber`

---

### Topic 22: 🔤 Tries

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 4 days                      |
| **Problems**         | 15                          |
| **Difficulty Split** | 3 Easy · 8 Medium · 4 Hard  |
| **Prerequisites**    | Strings, HashMap, Recursion |

#### 🎓 Learning Objectives

- Understand prefix trees as a specialized string search structure
- Implement insert, search, startsWith from scratch in O(L) time
- Apply tries for autocomplete, dictionary, and multi-word grid search
- Learn XOR tries for efficient maximum XOR queries

#### 🔑 Key Patterns

| Pattern             | Description                                   | Example Problem                     |
| ------------------- | --------------------------------------------- | ----------------------------------- |
| **Prefix Lookup**   | Check if any inserted word starts with prefix | Implement Trie (Prefix Tree)        |
| **Auto-complete**   | Return all words sharing a given prefix       | Search Suggestions System           |
| **XOR Max Trie**    | Bit-by-bit trie to find maximum XOR pair      | Maximum XOR of Two Numbers in Array |
| **Trie + DFS**      | DFS on board guided by trie for multi-word    | Word Search II                      |
| **Wildcard Search** | TrieNode + DFS handles '.' wildcards          | Design Add and Search Words         |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Trie fundamentals — TrieNode class, insert, search, startsWith, memory layout
2. **Day 2:** Applications — Word Break (trie-based), Replace Words, Map Sum Pairs
3. **Day 3:** Trie + DFS — Word Search II (Boggle), Design Add and Search Words (wildcards)
4. **Day 4:** XOR Trie — Maximum XOR of Two Numbers in Array, Maximum XOR With Element From Array

#### 🏢 Companies That Ask These

`Google` `Facebook/Meta` `Amazon`

---

### Topic 23: 📐 Segment Trees & Binary Indexed Trees

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 5 days                     |
| **Problems**         | 15                         |
| **Difficulty Split** | 2 Easy · 8 Medium · 5 Hard |
| **Prerequisites**    | Arrays, Trees, Recursion   |

#### 🎓 Learning Objectives

- Understand why static prefix sums fail when elements can be updated
- Build segment trees for O(log n) range query and point update
- Learn lazy propagation to batch range updates efficiently
- Implement Fenwick Tree (BIT) — simpler and cache-friendly for prefix sums

#### 🔑 Key Patterns

| Pattern              | Description                                   | Example Problem             |
| -------------------- | --------------------------------------------- | --------------------------- |
| **Range Sum Query**  | Query sum of [l, r] after point updates       | Range Sum Query - Mutable   |
| **Point Update**     | Update single element, propagate through tree | All segment tree problems   |
| **Lazy Propagation** | Defer range updates until children queried    | Range Update + Range Query  |
| **Fenwick BIT**      | Simpler structure: prefix sum + point update  | BIT implementation          |
| **Count Inversions** | Merge sort variant or BIT counting            | Count of Smaller After Self |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Motivation — static prefix sum breaks on updates; square-root decomposition as bridge
2. **Day 2:** Segment tree — build O(n), range query O(log n), point update O(log n)
3. **Day 3:** Lazy propagation — range update + range query in O(log n) each
4. **Day 4:** Fenwick Tree (BIT) — build, prefix sum query, point update — all O(log n)
5. **Day 5:** Problems — Range Sum Query Mutable, Count of Smaller Numbers After Self, Reverse Pairs

#### 🏢 Companies That Ask These

`Google` `Amazon` `Microsoft`

### Topic 24: 🪵 Square Root Decomposition (NEW)

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 3 days                     |
| **Problems**         | 10                         |
| **Difficulty Split** | 2 Easy · 5 Medium · 3 Hard |
| **Prerequisites**    | Segment Trees, Arrays      |

#### 🎓 Learning Objectives

- Understand the "block-based" strategy to optimize range queries when full trees are overkill
- Master the O(√N) query and O(1) or O(√N) update trade-offs
- Learn Mo’s Algorithm for offline range queries
- Handle problems involving frequency counting in specific ranges

#### 🔑 Key Patterns

| Pattern                 | Description                                      | Example Problem                        |
| ----------------------- | ------------------------------------------------ | -------------------------------------- |
| **Mo's Algorithm**      | Sort queries by block to reach O((N+Q)√N)        | Range Distinct Elements                |
| **Block Decomposition** | Precompute values for blocks of size √N          | Range Sum Query (SQRT)                 |
| **Block-based Updates** | Update element and its corresponding block value | SQRT Point Update                      |
| **Frequency Frequency** | Use two arrays to track freq of freqs with Mo's  | Mo's on most frequent element problems |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** SQRT fundamentals — partitioning array into blocks, Range Sum/Min query in O(√N)
2. **Day 2:** Update operations — point update O(1) vs. range query O(√N), block-based optimizations
3. **Day 3:** Mo’s Algorithm — query sorting basics, offline range processing, solving Range Distinct Elements

#### 🏢 Companies That Ask These

`CodeChef` `HackerRank` `Directi` `Uber`

---

## 🔴 Phase 4 — Interview Patterns & Mock Prep (Weeks 21–26)

> Consolidate, speed up, and simulate real FAANG-style interviews.

---

### Topic 25: 🔍 Advanced Recursion & Divide and Conquer

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 4 days                     |
| **Problems**         | 15                         |
| **Difficulty Split** | 3 Easy · 7 Medium · 5 Hard |
| **Prerequisites**    | Recursion, Sorting         |

#### 🎓 Learning Objectives

- Formally analyze recursive algorithms using the Master Theorem
- Apply QuickSelect for O(n) average-case selection
- Identify when divide-and-conquer beats brute force
- Solve hard problems by splitting the problem space

#### 🔑 Key Patterns

| Pattern                  | Description                               | Example Problem              |
| ------------------------ | ----------------------------------------- | ---------------------------- |
| **D&C on Sorted Arrays** | Divide sorted structure, combine results  | Median of Two Sorted Arrays  |
| **QuickSelect**          | Partition-based O(n) average selection    | Kth Largest Element in Array |
| **Fast Exponentiation**  | Compute pow(x, n) by squaring — O(log n)  | Pow(x, n)                    |
| **Merge Sort Variants**  | Count useful properties during merge step | Count Inversions             |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Master Theorem, recurrence relations, analyzing T(n) = aT(n/b) + f(n)
2. **Day 2:** QuickSelect — Kth Largest/Smallest, worst case O(n²) vs average O(n)
3. **Day 3:** Merge sort variants — Count Inversions, Count of Smaller Numbers After Self
4. **Day 4:** Median of Two Sorted Arrays, different ways to add parentheses, expression evaluation

#### 🏢 Companies That Ask These

`Google` `Facebook/Meta` `Amazon`

---

### Topic 26: 🎯 Two Pointers & Sliding Window (Deep Dive)

| Detail               | Value                       |
| -------------------- | --------------------------- |
| **Duration**         | 3 days                      |
| **Problems**         | 20                          |
| **Difficulty Split** | 4 Easy · 12 Medium · 4 Hard |
| **Prerequisites**    | Arrays & Strings, HashMap   |

#### 🎓 Learning Objectives

- Consolidate all two-pointer and sliding window patterns in a single mental model
- Shift from "which algorithm?" to _instantly recognizing_ the pattern to use
- Master the general expand/shrink template for variable window problems
- Handle all multi-pointer cases: 3-sum, 4-sum, and beyond

#### 🔑 Key Patterns

| Pattern             | Description                                      | Example Problem                         |
| ------------------- | ------------------------------------------------ | --------------------------------------- |
| **Fixed Window**    | Window of constant size K                        | Max Sum Subarray of Size K              |
| **Variable Window** | Expand until condition breaks, shrink to restore | Minimum Window Substring                |
| **Opposite Ends**   | Left + right converge for sorted-array problems  | 3Sum, Trapping Rain Water               |
| **Same Direction**  | Slow + fast in same direction                    | Longest Repeating Character Replacement |
| **At-Most Trick**   | f(exactly K) = f(at most K) - f(at most K-1)     | Subarrays with K Different Integers     |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Opposite-ends patterns — Two Sum II, 3Sum, 4Sum, Container with Most Water, Trapping Rain Water
2. **Day 2:** Variable window — Min Window Substring, Longest Repeating Char Replacement, Fruit Into Baskets
3. **Day 3:** Advanced — Subarrays with K Different Integers (at-most trick), Count of Substrings

#### 🏢 Companies That Ask These

`Google` `Amazon` `Facebook/Meta` `Uber`

---

### Topic 27: 🔗 String Algorithms (KMP/Z-Algo)

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 4 days                     |
| **Problems**         | 15                         |
| **Difficulty Split** | 2 Easy · 8 Medium · 5 Hard |
| **Prerequisites**    | Strings, HashMap           |

#### 🎓 Learning Objectives

- Implement KMP for O(n+m) guaranteed pattern matching
- Use Rabin-Karp rolling hash for average O(n) matching
- Apply Z-algorithm for linear prefix-matching queries
- Use Manacher's for O(n) palindromic substring discovery

#### 🔑 Key Patterns

| Pattern                       | Description                              | Example Problem               |
| ----------------------------- | ---------------------------------------- | ----------------------------- |
| **KMP Failure Function**      | O(n+m) pattern matching, no backtracking | Implement strStr()            |
| **Rolling Hash (Rabin-Karp)** | O(n) average matching via hash           | Repeated String Match         |
| **Z-algorithm**               | Z-array for O(n) prefix matching         | String matching applications  |
| **Manacher's Algorithm**      | All palindromic substrings in O(n)       | Longest Palindromic Substring |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** KMP — prefix function / failure function construction, pattern matching, Repeated Substring Pattern
2. **Day 2:** Rabin-Karp — polynomial rolling hash, modular arithmetic, collision handling
3. **Day 3:** Z-algorithm — Z-array construction and applications for pattern matching
4. **Day 4:** Palindromes — expand around center O(n²), Manacher's O(n), Shortest Palindrome

#### 🏢 Companies That Ask These

`Google` `Microsoft` `Amazon`

---

### Topic 28: 📊 Monotonic Patterns (Deep Dive)

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 3 days                     |
| **Problems**         | 15                         |
| **Difficulty Split** | 2 Easy · 8 Medium · 5 Hard |
| **Prerequisites**    | Stacks & Queues            |

#### 🎓 Learning Objectives

- Internalize all 4 monotonic stack variants as a single unified template
- Apply the contribution technique to solve range min/max sum problems
- Use monotone deque for O(n) sliding window extremes
- Recognize problems solvable only with monotonic structures

#### 🔑 Key Patterns

| Pattern                      | Description                                  | Example Problem                |
| ---------------------------- | -------------------------------------------- | ------------------------------ |
| **Next Greater Element**     | Pop when current > top; stack stores indices | Daily Temperatures, NGE I/II   |
| **Previous Greater Element** | Same stack, different traversal direction    | Stock Span Problem             |
| **Next Smaller Element**     | Pop when current < top                       | Largest Rectangle in Histogram |
| **Contribution Technique**   | Each element as min/max of some subarray     | Sum of Subarray Minimums       |
| **Monotone Deque**           | Sliding window min/max in O(n)               | Sliding Window Maximum         |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** Unified template for all 4 variants — NGE, NSE, PGE, PSE — with direction analysis
2. **Day 2:** Area problems — Largest Rectangle in Histogram, Maximal Rectangle in Binary Matrix
3. **Day 3:** Contribution technique — Sum of Subarray Minimums, Sum of Subarray Maximums, Subarray Ranges

#### 🏢 Companies That Ask These

`Google` `Amazon` `Facebook/Meta`

---

### Topic 29: 🏗️ Design Data Structures

| Detail               | Value                      |
| -------------------- | -------------------------- |
| **Duration**         | 5 days                     |
| **Problems**         | 15                         |
| **Difficulty Split** | 3 Easy · 7 Medium · 5 Hard |
| **Prerequisites**    | All Core DS Topics         |

#### 🎓 Learning Objectives

- Design custom data structures by combining primitive structures
- Understand trade-offs: O(1) read vs O(1) write, space vs time
- Implement LRU and LFU cache eviction policies
- Design for O(1) get/put/delete/random simultaneously

#### 🔑 Key Patterns

| Pattern             | Description                                  | Example Problem                         |
| ------------------- | -------------------------------------------- | --------------------------------------- |
| **HashMap + DLL**   | O(1) access + O(1) ordered eviction          | LRU Cache, LFU Cache                    |
| **HashMap + Array** | O(1) lookup + O(1) random access             | RandomizedSet (insert/remove/getRandom) |
| **Two DS Trick**    | Combine two structures to get O(1) from both | Min Stack, Max Stack                    |
| **Augmented BST**   | BST with extra size/count per node           | Order Statistics Tree                   |
| **Lazy Cleaning**   | Mark deleted instead of actually removing    | Design Twitter (lazy operations)        |

#### 📝 Sub-Topics & Lecture Flow

1. **Day 1:** LRU Cache — HashMap + Doubly Linked List. Why this pair achieves O(1) get/put/evict
2. **Day 2:** LFU Cache — two HashMaps + DLL per frequency. O(1) all operations analysis
3. **Day 3:** Min Stack, Max Stack (two-stack trick), Median Stream (two heaps), RandomizedSet
4. **Day 4:** Design Search Autocomplete System, Time-Based Key-Value Store, Snapshot Array
5. **Day 5:** Advanced — Design Twitter (heap + lists), In-Memory File System, Skip List

#### 🏢 Companies That Ask These

`Google` `Amazon` `Facebook/Meta` `Microsoft` `Uber`

---

### Topic 30: 🧠 Mock Interviews & System Thinking

| Detail            | Value               |
| ----------------- | ------------------- |
| **Duration**      | 7 days              |
| **Problems**      | Mixed review        |
| **Prerequisites** | All previous topics |

#### 🎓 Learning Objectives

- Simulate real FAANG-style interviews end-to-end under timed pressure
- Practice the UMPIRE framework: Understand, Match, Plan, Implement, Review, Evaluate
- Build the discipline of clarifying requirements _before_ touching code
- Develop the verbal articulation and dry-run habits of a senior engineer

#### 📝 Sub-Topics & Lecture Flow

1. **Days 1–2:** Mock Round 1 — Easy/Medium mix, 45-min timer, full verbal walkthrough, code review
2. **Days 3–4:** Mock Round 2 — Medium/Hard, brute → optimal progression, time-box optimization
3. **Day 5:** Edge-case drills — empty/null input, single element, integer overflow, negative numbers
4. **Day 6:** System design foundations — REST APIs, caching, databases, load balancing (SDE-1 level)
5. **Day 7:** Behavioral prep — STAR method, project walkthrough, conflict/leadership stories

#### 🏢 Companies That Ask These

`Google` `Facebook/Meta` `Amazon` `Microsoft` `Apple` `Uber`

---

## 📅 Weekly Schedule Template

| Day          | Activity                                      | Time    |
| ------------ | --------------------------------------------- | ------- |
| **Mon–Fri**  | Lecture notes + 3–5 focused practice problems | 3–4 hrs |
| **Saturday** | Weekly assignment (10–12 problems, timed)     | 4–5 hrs |
| **Sunday**   | Review weak areas, update cheat sheet, rest   | 2–3 hrs |

## 🎯 Our Learning Principles

1. **Don't memorize — understand.** Explain it like you'd teach a 5-year-old.
2. **Draw it out.** Every recursion tree, every pointer move, every state transition.
3. **Brute force first.** Start simple, then optimize one step at a time.
4. **Identify the pattern.** 95% of interview problems are variants of ~20 patterns.
5. **Teach it.** The deepest learning comes from explaining to others.
6. **Consistency > intensity.** 2 hours daily beats 14 hours on Saturday.
7. **Track everything.** Note which patterns you struggle with; revisit weekly.

## 📊 Complete Phase Summary

| Phase                   | Topics                                                                   | Weeks           | Key Focus               | Problems          |
| ----------------------- | ------------------------------------------------------------------------ | --------------- | ----------------------- | ----------------- |
| **1 — Foundations**     | Java, OOP, Recursion, Bit Manipulation, Math                             | 1–5             | Build thinking patterns | ~110              |
| **2 — Core DS**         | Arrays, Sorting, Binary Search, LL, Stack, HashMap, Matrix, Trees, Heaps | 6–13            | Core interview topics   | ~243              |
| **3 — Advanced**        | Graphs, Union-Find, Greedy, Intervals, DP, Tries, Segment Trees, SQRT    | 14–20           | Differentiators         | ~187              |
| **4 — Patterns & Prep** | D&C, Two Pointers, String Algos, Monotonic, Design DS, Mocks             | 21–26           | Speed + Polish          | ~80               |
| **Total**               | **30 topics**                                                            | **21–26 weeks** |                         | **620+ problems** |
