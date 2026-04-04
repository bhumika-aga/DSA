# 📝 Assignment 02 — Memory Management & JCF Deep Dive

> **Lecture:** Topic 2 — Memory Management & Java Collections Framework
> **Topic Count:** 2 of 30 — Phase 1 Foundations
> **Duration:** 5 Days
> **Core Problems:** 35 (15 Easy · 15 Medium · 5 Hard) + 10 Challenge + 10 Complexity Exercises
> **Goal:** Build a rock-solid mental model of JVM memory and master the trade-offs of the Collections Framework.

---

## 🗺️ Problem Map by Pattern

| Pattern / Topic          | Problems                   |
| ------------------------ | -------------------------- |
| JVM Memory Architecture  | 01, 02, 03, 04, 05         |
| String Pool & Constants  | 06, 07, 08, 09             |
| Pass-by-Value Primitives | 10, 11                     |
| ArrayList & Resizing     | 12, 13, 14, 15             |
| HashMap (Hash Counting)  | 16, 17, 18, 19, 20, 21, 22 |
| Two Pointers / Lookup    | 23, 24, 25                 |
| TreeMap (Range Queries)  | 26, 27, 28                 |
| HashSet (Uniqueness)     | 29, 30                     |
| Challenge Zone (FAANG)   | 31, 32, 33, 34, 35         |

---

## 🟢 Easy Tier — 15 Problems (Memory & Collection Basics)

### Problem 01 — Stack vs Heap Logic

Explain which memory area (Stack or Heap) stores the following variables in a method call:

- An `int` primitive locally declared.
- An `int[]` array reference.
- The actual integers inside the `int[]` array.
- A `String` object.

### Problem 02 — String Literal vs Object

Predict the output and explain **WHY**:

```java
String s1 = "DSA";
String s2 = "DSA";
String s3 = new String("DSA");
System.out.println(s1 == s2);
System.out.println(s1 == s3);
System.out.println(s1.equals(s3));
```

### Problem 03 — Memory Leak 101

Identify why this code might lead to an `OutOfMemoryError` over time:

```java
List<byte[]> data = new ArrayList<>();
while (true) {
    data.add(new byte[1024 * 1024]); // Adds 1MB every loop
}
```

### Problem 04 — StackOverflow Simulation

Write the simplest recursive function that triggers a `StackOverflowError`. What is the default stack size in a standard JVM?

### Problem 05 — Pass-by-Value "Trap"

Predict the output of `a` after `modify(a)`:

```java
void modify(int x) { x = 100; }
int a = 5;
modify(a);
System.out.println(a);
```

### Problem 06 — Reference Modification

Predict the output of `arr[0]` after `modify(arr)`:

```java
void modify(int[] x) { x[0] = 100; }
int[] arr = {5, 10};
modify(arr);
System.out.println(arr[0]);
```

### Problem 07 — ArrayList: Insert at Front

> 🔗 **Practice:** Write a function to insert 10,000 elements at index 0 of an `ArrayList`. Measure time. Why is it slow? What is the Time Complexity of `add(0, val)`?

### Problem 08 — ArrayList vs LinkedList Lookup

> 🔗 **Practice:** Initialize both with 10⁵ elements. Compare `list.get(50000)` performance. State the complexity for each.

### Problem 09 — HashSet: Remove Duplicates

> 🔗 **LeetCode:** [Contains Duplicate](https://leetcode.com/problems/contains-duplicate/)
> **`[Pattern: Hashing Fundamentals]` `[Easy]`**
> Given an array, return true if any value appears at least twice. Use `HashSet` for O(1) average lookup/insert.

### Problem 10 — Find All Unique Numbers

> 🔗 **LeetCode:** [Single Number](https://leetcode.com/problems/single-number/)
> **`[Pattern: Uniqueness / XOR]` `[Easy]`**
> Use a `HashSet` to store numbers. If number already exists, remove it. Final remaining number is the answer. (Then think: how to do this in O(1) space with XOR?)

### Problem 11 — Intersection of Two Arrays

> 🔗 **LeetCode:** [349. Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)
> **`[Pattern: Two Sets]` `[Easy]`**
> Return an array of unique elements present in both arrays. Use two `HashSet`s.

### Problem 12 — Valid Anagram (HashMap Version)

> 🔗 **LeetCode:** [242. Valid Anagram](https://leetcode.com/problems/valid-anagram/)
> **`[Pattern: Frequency Count]` `[Easy]`**
> Use a `HashMap<Character, Integer>` to count frequencies of characters in `s`, then decrement for `t`.

### Problem 13 — First Unique Character

> 🔗 **LeetCode:** [387. First Unique Character](https://leetcode.com/problems/first-unique-character-in-a-string/)
> **`[Pattern: Frequency Count]` `[Easy]`**
> Find the first character that does not repeat. Two passes: first to count, second to find first char with count == 1.

### Problem 14 — Find Pivot Index

> 🔗 **LeetCode:** [724. Find Pivot Index](https://leetcode.com/problems/find-pivot-index/)
> **`[Pattern: Prefix Sum]` `[Easy]`**
> Return the index where sum of elements to the left equals sum to the right. Use a single loop after precompute total sum.

### Problem 15 — Majority Element

> 🔗 **LeetCode:** [169. Majority Element](https://leetcode.com/problems/majority-element/)
> **`[Pattern: Counting]` `[Easy]`**
> Find the element appearing more than `n/2` times. Use `HashMap<Integer, Integer>` to track counts.

---

## 🟡 Medium Tier — 15 Problems (Interview Staples)

### Problem 16 — Two Sum (The King of Patterns)

> 🔗 **LeetCode:** [1. Two Sum](https://leetcode.com/problems/two-sum/)
> **`[Pattern: Complement Lookup]` `[Must Know]` `[Medium on intuition]`**
> Return indices of two numbers summing to target. One-pass: check if `target - nums[i]` exists in HashMap before putting `nums[i]`. O(n).

### Problem 17 — Group Anagrams

> 🔗 **LeetCode:** [49. Group Anagrams](https://leetcode.com/problems/group-anagrams/)
> **`[Pattern: Hashed Key]` `[Amazon] [Microsoft]` `[Medium]`**
> Group strings that are anagrams. Map `Sorted String → List of Strings`. Or use a frequency string (e.g., "a1b2c1") as key to achieve O(N\*K).

### Problem 18 — Top K Frequent Elements

> 🔗 **LeetCode:** [347. Top K Frequent Elements](https://leetcode.com/problems/top-k-frequent-elements/)
> **`[Pattern: Min-Heap / Bucket Sort]` `[Google]` `[Medium]`**
> Find the k most frequent elements. HashMap for counts + `PriorityQueue` of size K to keep the top elements.

### Problem 19 — Subarray Sum Equals K

> 🔗 **LeetCode:** [560. Subarray Sum Equals K](https://leetcode.com/problems/subarray-sum-equals-k/)
> **`[Pattern: Prefix Sum + HashMap]` `[Facebook/Meta]` `[Medium]`**
> Count total continuous subarrays summing to k. Maintain `runningSum → count` in HashMap. If `runningSum - k` exists, add its count to result. Core pattern for range queries.

### Problem 20 — 4Sum II

> 🔗 **LeetCode:** [454. 4Sum II](https://leetcode.com/problems/4sum-ii/)
> **`[Pattern: HashMap Partitioning]` `[Apple]` `[Medium]`**
> Four arrays A, B, C, D. Find how many tuples sum to zero. Compute sum(A+B) and store in Map, then check sum(C+D) against map. O(n²) instead of O(n⁴).

### Problem 21 — Longest Substring Without Repeating Characters

> 🔗 **LeetCode:** [3. Longest Substring](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
> **`[Pattern: Sliding Window + HashMap]` `[Google] [Amazon]` `[Medium]`**
> Maintenance a window. If char at right pointer already in Map, move left pointer to `max(left, map.get(char) + 1)`.

### Problem 22 — LRU Cache (Design Baseline)

> 🔗 **LeetCode:** [146. LRU Cache](https://leetcode.com/problems/lru-cache/)
> **`[Pattern: LinkedHashMap / DLL + Map]` `[Tier 1 High Frequency]` `[Medium/Hard]`**
> Implement Get and Put in O(1). Use a `HashMap` for O(1) lookup and a `Doubly Linked List` for O(1) ordering.

### Problem 23 — Sort Characters By Frequency

> 🔗 **LeetCode:** [451. Sort Characters By Frequency](https://leetcode.com/problems/sort-characters-by-frequency/)
> **`[Pattern: Map + Sorting]` `[Microsoft]` `[Medium]`**
> Build frequency map, then sort keys based on values. Use a `PriorityQueue` or bucket array.

### Problem 24 — TreeMap Range Queries

> 🔗 **Practice:** Find all keys in range [10, 50].
> **`[Pattern: Binary Search Tree Property]` `[Medium]`**
> Use `treeMap.subMap(10, true, 50, true)`. Key insight: TreeMap maintains sorted order, allowing O(log n) searches and O(k) range traversals.

### Problem 25 — Custom Class as HashMap Key

Implement a `Student` class with `id` and `name`. Override `hashCode()` and `equals()`. Explain why `equals()` must be consistent with `hashCode()`. What happens if you modify the `name` of a Student already inside a `HashSet`?

### Problem 26 — Valid Sudoku

> 🔗 **LeetCode:** [36. Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)
> **`[Pattern: HashSet / Grid Logic]` `[Medium]`**
> Check if a 9x9 board is valid. Use one HashSet with string keys: `"row"+i+val`, `"col"+j+val`, `"box"+(i/3)+"-"+(j/3)+val`.

### Problem 27 — Continuous Subarray Sum

> 🔗 **LeetCode:** [523. Continuous Subarray Sum](https://leetcode.com/problems/continuous-subarray-sum/)
> **`[Pattern: Prefix Sum Modulo]` `[Facebook]` `[Medium]`**
> Find a subarray of at least size 2 summing to a multiple of k. Store `sum % k → firstIndex` in a HashMap.

### Problem 28 — Linked List Cycle Detection (Map Version)

> 🔗 **LeetCode:** [141. Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)
> **`[Pattern: Node Hashing]` `[Medium]`**
> Use a `HashSet<ListNode>` to store visited nodes. If you see a node again, there is a cycle. (Hint for L9: How to do this with Two Pointers instead?)

### Problem 29 — Find All Numbers Disappeared

> 🔗 **LeetCode:** [448. Find All Numbers Disappeared in an Array](https://leetcode.com/problems/find-all-numbers-disappeared-in-an-array/)
> **`[Pattern: Index Marking / Hash-in-place]` `[Google]` `[Easy/Medium]`**
> Given array of [1, n], return list of missing numbers. Use a HashSet to track seen numbers. **Challenge:** Solve in O(1) space by negating values at indices.

### Problem 30 — Word Pattern

> 🔗 **LeetCode:** [290. Word Pattern](https://leetcode.com/problems/word-pattern/)
> **`[Pattern: Bijections / Dual Map]` `[Easy/Medium]`**
> Map characters to words. E.g., "abba" → "dog cat cat dog". Use two maps or one map with a special value proxy.

---

## 🔴 Challenge Zone — 10 Advanced Problems (Final Prep)

### P31-40: Real-World System Scenarios

- **P31: Design Task Scheduler O(1)**: Implement a system that can add task, remove random task, and get random task all in O(1). (Hint: Map + Dynamic Array).
- **P32: K-th Smallest in Matrix** ([LC 378](https://leetcode.com/problems/kth-smallest-element-in-a-sorted-matrix/)) - Use `PriorityQueue` vs Binary Search.
- **P33: Merge K Sorted Lists** ([LC 23](https://leetcode.com/problems/merge-k-sorted-lists/)) - The classic HEAP problem.
- **P34: Smallest String With Swaps** ([LC 1202](https://leetcode.com/problems/smallest-string-with-swaps/)) - DFS + Map grouping.
- **P35: Custom Object Collision**: Write a `BadHashCode` object where `hashCode()` always returns `1`. Measure `HashMap.put()` performance as N grows. See the degradation from O(1) to O(N).

---

## 📊 Complexity Analysis Exercises — 10 Snippets

Determine **Time** and **Space** complexity.

```java
// Snippet 1
List<Integer> list = new ArrayList<>();
for (int i = 0; i < n; i++) list.add(0, i);

// Snippet 2
Map<Integer, Integer> map = new HashMap<>();
for (int x : nums) map.put(x, map.getOrDefault(x, 0) + 1);

// Snippet 3
PriorityQueue<Integer> pq = new PriorityQueue<>();
for (int x : nums) {
    pq.add(x);
    if (pq.size() > k) pq.poll();
}

// Snippet 4
Set<Integer> set = new TreeSet<>();
for (int x : nums) set.add(x);

// Snippet 5
int[][] matrix = new int[n][n]; // Space?

// Snippet 6
String s = "";
for (int i = 0; i < n; i++) s += i; // Time? (Warning: String is immutable)

// Snippet 7
StringBuilder sb = new StringBuilder();
for (int i = 0; i < n; i++) sb.append(i); // Time?

// Snippet 8
List<List<Integer>> result = new ArrayList<>();
// Result of generating all subsets of size n... (Space?)

// Snippet 9
// Binary search on TreeMap entrySet (O?)

// Snippet 10
void recurse(int n) {
    if (n <= 0) return;
    int[] arr = new int[n]; // Space?
    recurse(n - 1);
}
```

**Complexity Answers:**

1. **O(n²)** Time, O(n) Space. Shifting array for every insert.
2. **O(n)** Time, O(n) Space. Standard hash map counting.
3. **O(n log k)** Time, O(k) Space. The "Top-K" heap pattern.
4. **O(n log n)** Time, O(n) Space. Balanced BST insertion.
5. **O(n²)** Space.
6. **O(n²)** Time. Each `+=` creates a new String, copying all previous chars.
7. **O(n)** Time. Amortized O(1) per append.
8. **O(2ⁿ \* n)** Space. There are 2ⁿ subsets, each of size up to n.
9. **O(log n)** Time. It's a Red-Black tree.
10. **O(n²)** Space. Total space = n + (n-1) + (n-2)... = n(n+1)/2.

---

## ✅ Self-Assessment — True / False

1. `HashMap` order is guaranteed to be same as insertion order. → **False** (Use `LinkedHashMap`).
2. `HashSet` uses a `HashMap` internally with a dummy value. → **True**.
3. Primitives like `int` are stored on the Heap if they are part of an Object. → **True**.
4. Garbage Collection collects objects immediately when their reference count hits 0. → **False** (Non-deterministic timing).
5. `Arrays.asList(arr)` creates a deep copy of the array. → **False** (Fixed-size view of the original).
6. Recursive calls never use Heap space. → **False** (Local variables go to Stack, but `new` objects go to Heap).
7. `TreeMap` operations take O(1) constant time. → **False** (O(log n)).
8. `ArrayList` growth factor is typically 1.5x. → **True**.

---

## 🧠 Conceptual Mastery Questions

1. **The "Why" of Hashing**: Why must `hashCode()` be overridden if `equals()` is overridden? Explain the "lost element" problem if it's not.
2. **Collection Selection**: You need to store 1 billion elements, but only care about the last 100 inserted. Which collection? Why?
3. **String Pool Rationale**: Why did Java designers introduce the String Pool? What are the trade-offs regarding memory vs computation?
4. **Resizing Cost**: If `ArrayList` doubles its size, isn't that `O(n)` move operation bad? Prove that it's `O(1)` amortized.
5. **Memory Leak Protection**: How can you prevent a `Static Map` from causing a memory leak in a long-running server?

---

Next: [Topic 3 — OOP & Collections Deep Dive](../Lecture3/Assignment.md)
