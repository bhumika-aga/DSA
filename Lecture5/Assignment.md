# 🧠 Assignment 5 — Java Memory Management

> **Lecture:** 5 of 45 — Java Memory Management
> **Phase:** 1 — Foundations
> **Estimated Time:** 4 days · **Total Problems:** 35 (20 Easy · 14 Medium · 1 Hard)
> **Goal:** Build a rock-solid mental model of JVM memory and master the trade-offs of the Collections Framework.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                   | Pattern              | Move                                                  |
| --------------------------------------- | -------------------- | ----------------------------------------------------- |
| "have I seen this before?"              | HashSet              | `add` / `contains` in O(1) average                    |
| "how many times does x appear"          | HashMap Counting     | `map.merge(x, 1, Integer::sum)`                       |
| "same group / same key"                 | HashMap Grouping     | build a canonical key, map it to a list               |
| "closest smaller / larger key", "range" | TreeMap / TreeSet    | `floorKey`, `ceilingKey`, `subMap` in O(log n)        |
| "predict the output" with objects       | Stack vs Heap Model  | primitives copy the value, objects copy the reference |
| "why is this slow?"                     | Collection Internals | ArrayList shifts, LinkedList walks, HashMap hashes    |

---

## 🟢 Easy Tier (20 Problems)

_Memory & Collection Basics._

### E1 · Stack vs Heap Logic

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** JVM Memory & References | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Explain which memory area (Stack or Heap) stores the following variables in a method call:

- An `int` primitive locally declared.
- An `int[]` array reference.
- The actual integers inside the `int[]` array.
- A `String` object.

---

### E2 · String Literal vs Object

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** JVM Memory & References | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Predict the output and explain **WHY**:

```java
String s1 = "DSA";
String s2 = "DSA";
String s3 = new String("DSA");
System.out.println(s1 == s2);
System.out.println(s1 == s3);
System.out.println(s1.equals(s3));
```

---

### E3 · Memory Leak 101

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** JVM Memory & References | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Identify why this code might lead to an `OutOfMemoryError` over time:

```java
List<byte[]> data = new ArrayList<>();
while (true) {
    data.add(new byte[1024 * 1024]); // Adds 1MB every loop
}
```

---

### E4 · StackOverflow Simulation

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** JVM Memory & References | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Write the simplest recursive function that triggers a `StackOverflowError`. What is the default stack size in a standard JVM?

---

### E5 · Pass-by-Value "Trap"

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** JVM Memory & References | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Predict the output of `a` after `modify(a)`:

```java
void modify(int x) {
    x = 100;
}

int a = 5;
modify(a);
System.out.println(a);
```

---

### E6 · Reference Modification

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** JVM Memory & References | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Predict the output of `arr[0]` after `modify(arr)`:

```java
void modify(int[] x) {
    x[0] = 100;
}

int[] arr = {5, 10};
modify(arr);
System.out.println(arr[0]);
```

---

### E7 · ArrayList: Insert at Front

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** List Internals | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Write a function to insert 10,000 elements at index 0 of an `ArrayList`. Measure time. Why is it slow? What is the Time Complexity of `add(0, val)`?

---

### E8 · ArrayList vs LinkedList Lookup

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** List Internals | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Initialise both with 10⁵ elements. Compare `list.get(50000)` performance. State the complexity for each.

---

### E9 · Unique Morse Code Words

**🔗 [LC 804 — Unique Morse Code Words](https://leetcode.com/problems/unique-morse-code-words/)** · Easy
**Pattern:** HashSet — Uniqueness | **Companies:** Amazon, Google

**Hint:** Translate each word into its Morse string with a `StringBuilder`, add it to a `HashSet<String>`, and return the set's size. `String` works as a key because its `equals`/`hashCode` compare content.

---

### E10 · Sum of Unique Elements

**🔗 [LC 1748 — Sum of Unique Elements](https://leetcode.com/problems/sum-of-unique-elements/)** · Easy
**Pattern:** HashMap — Counting | **Companies:** Amazon, Microsoft

**Hint:** Count with `map.merge(x, 1, Integer::sum)`, then sum the keys whose count is 1. Note how `Integer` values are boxed on the heap.

---

### E11 · Intersection of Two Arrays

**🔗 [LC 349 — Intersection of Two Arrays](https://leetcode.com/problems/intersection-of-two-arrays/)** · Easy
**Pattern:** Two Sets | **Companies:** Amazon, Google, Meta

**Hint:** Return an array of unique elements present in both arrays. Use two `HashSet`s.

---

### E12 · Find Words That Can Be Formed by Characters

**🔗 [LC 1160 — Find Words That Can Be Formed by Characters](https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/)** · Easy
**Pattern:** Frequency Array | **Companies:** Amazon, Microsoft

**Hint:** Count the letters of `chars` once in `int[26]`. For each word, count its letters and check every count fits. Copying the base array per word is O(26) — cheap.

---

### E13 · Check if All Characters Have Equal Number of Occurrences

**🔗 [LC 1941 — Check if All Characters Have Equal Number of Occurrences](https://leetcode.com/problems/check-if-all-characters-have-equal-number-of-occurrences/)** · Easy
**Pattern:** HashMap — Counting | **Companies:** Amazon, Adobe

**Hint:** Count characters, then put all the counts into a `HashSet<Integer>`; the answer is `set.size() == 1`.

---

### E14 · Unique Number of Occurrences

**🔗 [LC 1207 — Unique Number of Occurrences](https://leetcode.com/problems/unique-number-of-occurrences/)** · Easy
**Pattern:** HashMap + HashSet | **Companies:** Amazon, Google

**Hint:** Count occurrences in a `HashMap`, then check that `new HashSet<>(map.values()).size() == map.size()`.

---

### E15 · Intersection of Multiple Arrays

**🔗 [LC 2248 — Intersection of Multiple Arrays](https://leetcode.com/problems/intersection-of-multiple-arrays/)** · Easy
**Pattern:** Counting Across Lists | **Companies:** Amazon, Google

**Hint:** Each inner array has distinct values, so a value is in every array exactly when its total count equals `nums.length`. Count, collect, sort.

---

### E16 · Contains Duplicate II

**🔗 [LC 219 — Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/)** · Easy
**Pattern:** HashMap — Last Index | **Companies:** Amazon, Google, Meta

**Hint:** Store `value → last index seen`. At index `i`, if the value is already in the map and `i - map.get(v) <= k`, return true; either way update the stored index to `i`.

---

### E17 · Sort Array by Increasing Frequency

**🔗 [LC 1636 — Sort Array by Increasing Frequency](https://leetcode.com/problems/sort-array-by-increasing-frequency/)** · Easy
**Pattern:** Map + Custom Comparator | **Companies:** Amazon, Google, eBay

**Hint:** Count frequencies, box the array into `Integer[]`, and sort with a comparator: lower frequency first, and for equal frequency, larger value first.

---

### E18 · Sort the People

**🔗 [LC 2418 — Sort the People](https://leetcode.com/problems/sort-the-people/)** · Easy
**Pattern:** Sort by Key | **Companies:** Amazon, Microsoft

**Hint:** Heights are distinct, so pair each name with its height (a `TreeMap<Integer, String>` with reverse order, or an index array sorted by height) and read the names in descending height.

---

### E19 · Check If N and Its Double Exist

**🔗 [LC 1346 — Check If N and Its Double Exist](https://leetcode.com/problems/check-if-n-and-its-double-exist/)** · Easy
**Pattern:** HashSet Lookup | **Companies:** Amazon, Google

**Hint:** Walk the array once. Before adding `x` to a `HashSet`, check whether `2 * x` is in it, or (for even `x`) whether `x / 2` is. The zero case is handled because you check before adding.

---

### E20 · Find the Difference of Two Arrays

**🔗 [LC 2215 — Find the Difference of Two Arrays](https://leetcode.com/problems/find-the-difference-of-two-arrays/)** · Easy
**Pattern:** Set Difference | **Companies:** Amazon, Microsoft

**Hint:** Load both arrays into `HashSet`s, then keep the values of set1 not in set2 and vice versa. `removeAll` on copies works too — understand why its cost depends on the set type.

---

## 🟡 Medium Tier (14 Problems)

_Interview Staples._

### M1 · Find Duplicate File in System

**🔗 [LC 609 — Find Duplicate File in System](https://leetcode.com/problems/find-duplicate-file-in-system/)** · Medium
**Pattern:** HashMap — Group by Key | **Companies:** Amazon, Google, Dropbox

**Hint:** Parse each path string, split out `name(content)`, and group full paths in `Map<String, List<String>>` keyed by content. Return only the groups with 2 or more files.

---

### M2 · Count Number of Nice Subarrays

**🔗 [LC 1248 — Count Number of Nice Subarrays](https://leetcode.com/problems/count-number-of-nice-subarrays/)** · Medium
**Pattern:** Prefix Count + HashMap | **Companies:** Amazon, Google, Meta

**Hint:** Turn each number into 1 if odd and 0 if even; now you need subarrays with sum exactly `k`. Keep a running count of odds and a map of how many prefixes had each count; add `map.get(count - k)` at every step.

---

### M3 · Pairs of Songs With Total Durations Divisible by 60

**🔗 [LC 1010 — Pairs of Songs With Total Durations Divisible by 60](https://leetcode.com/problems/pairs-of-songs-with-total-durations-divisible-by-60/)** · Medium
**Pattern:** Complement Counting | **Companies:** Amazon, Google

**Hint:** Only `time % 60` matters. For remainder `r`, its partner is `(60 - r) % 60`. Keep `int[60]` counts and add `count[partner]` before recording `r`.

---

### M4 · Equal Row and Column Pairs

**🔗 [LC 2352 — Equal Row and Column Pairs](https://leetcode.com/problems/equal-row-and-column-pairs/)** · Medium
**Pattern:** HashMap — Row as Key | **Companies:** Amazon, Google

**Hint:** Turn each row into a key (e.g. `Arrays.toString(row)` or a `List<Integer>`) and count it in a map. Then build each column's key and add the map's count for it.

---

### M5 · Design Authentication Manager

**🔗 [LC 1797 — Design Authentication Manager](https://leetcode.com/problems/design-authentication-manager/)** · Medium
**Pattern:** HashMap with Expiry | **Companies:** Twitter, Amazon

**Hint:** Store `tokenId → expiryTime`. `renew` only works if the token exists and hasn't expired. `countUnexpiredTokens` counts entries with `expiry > currentTime` — or prune expired entries as you go.

---

### M6 · My Calendar I

**🔗 [LC 729 — My Calendar I](https://leetcode.com/problems/my-calendar-i/)** · Medium
**Pattern:** TreeMap — floor / ceiling | **Companies:** Google, Amazon, Uber

**Hint:** Keep booked intervals in a `TreeMap<start, end>`. A new `[s, e)` conflicts if `floorEntry(s)` ends after `s`, or `ceilingKey(s)` starts before `e`. Otherwise insert. Each booking is O(log n).

---

### M7 · Custom Class as HashMap Key

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** hashCode / equals & Set Checks | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Implement a `Student` class with `id` and `name`. Override `hashCode()` and `equals()`. Explain why `equals()` must be consistent with `hashCode()`. What happens if you modify the `name` of a Student already inside a `HashSet`?

---

### M8 · Valid Sudoku

**🔗 [LC 36 — Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)** · Medium
**Pattern:** HashSet / Grid Logic | **Companies:** Amazon, Google, Uber, Apple

**Hint:** Check if a 9x9 board is valid. Use one HashSet with string keys: `"row"+i+val`, `"col"+j+val`, `"box"+(i/3)+"-"+(j/3)+val`.

---

### M9 · Continuous Subarray Sum

**🔗 [LC 523 — Continuous Subarray Sum](https://leetcode.com/problems/continuous-subarray-sum/)** · Medium
**Pattern:** Prefix Sum Modulo | **Companies:** Meta, Amazon, Google

**Hint:** Find a subarray of at least size 2 summing to a multiple of k. Store `sum % k → firstIndex` in a HashMap.

---

### M10 · Find and Replace Pattern

**🔗 [LC 890 — Find and Replace Pattern](https://leetcode.com/problems/find-and-replace-pattern/)** · Medium
**Pattern:** Bijection — Two Maps | **Companies:** Amazon, Google

**Hint:** A word matches when there is a one-to-one mapping between pattern letters and word letters. Use two maps (pattern→word and word→pattern) and reject on any conflict.

---

### M11 · Insert Delete GetRandom O(1)

**🔗 [LC 380 — Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o1/)** · Medium
**Pattern:** HashMap + Dynamic Array | **Companies:** Amazon, Google, Meta, Bloomberg

**Hint:** Add, remove, and get a random element, all in O(1). (Hint: HashMap of value → index + a dynamic array; delete by swapping with the last element.)

---

### M12 · Smallest Number in Infinite Set

**🔗 [LC 2336 — Smallest Number in Infinite Set](https://leetcode.com/problems/smallest-number-in-infinite-set/)** · Medium
**Pattern:** TreeSet + Counter | **Companies:** Amazon, Google

**Hint:** Everything at or above a pointer `next` is still present. Numbers added back below `next` go into a `TreeSet`. `popSmallest` takes the set's first element if there is one, otherwise returns `next++`.

---

### M13 · Time Based Key-Value Store

**🔗 [LC 981 — Time Based Key-Value Store](https://leetcode.com/problems/time-based-key-value-store/)** · Medium
**Pattern:** TreeMap — floorKey | **Companies:** Google, Amazon, Netflix

**Hint:** Store `key → TreeMap<timestamp, value>`. `get(key, t)` is `floorEntry(t)` on that inner map. (Timestamps arrive increasing, so binary search on a list works too.)

---

### M14 · Smallest String With Swaps

**🔗 [LC 1202 — Smallest String With Swaps](https://leetcode.com/problems/smallest-string-with-swaps/)** · Medium
**Pattern:** Union-Find / DFS + Sorting per Group | **Companies:** Amazon, Google, Meta

**Hint:** Swaps are transitive, so indices in the same connected component can be arranged in any order. Group indices with DFS or Union-Find, sort each group's characters, and write them back into the group's sorted indices.

---

## 🔴 Hard Tier (1 Problem)

_Final Prep._

### H1 · Custom Object Collision

**🔗 Concept exercise — no LeetCode equivalent**
**Pattern:** hashCode Collisions | **Companies:** Amazon, Oracle, Goldman Sachs

**Task:** Write a `BadHashCode` object where `hashCode()` always returns `1`. Measure `HashMap.put()` performance as N grows. See the degradation from O(1) to O(N).

---

## 📊 Complexity Analysis Exercises

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
7. **O(n)** Time. Amortised O(1) per append.
8. **O(2ⁿ \* n)** Space. There are 2ⁿ subsets, each of size up to n.
9. **O(log n)** Time. It's a Red-Black tree.
10. **O(n²)** Space. Total space = n + (n-1) + (n-2)... = n (n+1)/2.

---

## 🔍 Self-Assessment — True / False

1. `HashMap` order is guaranteed to be same as insertion order. → **False** (Use `LinkedHashMap`).
2. `HashSet` uses a `HashMap` internally with a dummy value. → **True**.
3. Primitives like `int` are stored on the Heap if they are part of an Object. → **True**.
4. Garbage Collection collects objects immediately when their reference count hits 0. → **False** (Java does not
   count references; the collector frees objects that are no longer reachable, at a time of its choosing).
5. `Arrays.asList(arr)` creates a deep copy of the array. → **False** (Fixed-size view of the original).
6. Recursive calls never use Heap space. → **False** (Local variables go to Stack, but `new` objects go to Heap).
7. `TreeMap` operations take O(1) constant time. → **False** (O(log n)).
8. `ArrayList` growth factor is typically 1.5x. → **True**.

---

## 🧠 Conceptual Check

1. **The "Why" of Hashing**: Why must `hashCode()` be overridden if `equals()` is overridden? Explain the "lost element"
   problem if it's not.
2. **Collection Selection**: You need to store 1 billion elements, but only care about the last 100 inserted. Which
   collection? Why?
3. **String Pool Rationale**: Why did Java designers introduce the String Pool? What are the trade-offs regarding memory
   vs computation?
4. **Resizing Cost**: If `ArrayList` doubles its size, isn't that `O(n)` move operation bad? Prove that it's `O(1)`
   amortised.
5. **Memory Leak Protection**: How can you prevent a `Static Map` from causing a memory leak in a long-running server?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                                                                         |
| ------------- | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Design Authentication Manager](https://leetcode.com/problems/design-authentication-manager/), [Check if All Characters Have Equal Number of Occurrences](https://leetcode.com/problems/check-if-all-characters-have-equal-number-of-occurrences/), [Smallest Number in Infinite Set](https://leetcode.com/problems/smallest-number-in-infinite-set/), [Time Based Key-Value Store](https://leetcode.com/problems/time-based-key-value-store/) |
| **Google**    | [Check If N and Its Double Exist](https://leetcode.com/problems/check-if-n-and-its-double-exist/), [Equal Row and Column Pairs](https://leetcode.com/problems/equal-row-and-column-pairs/), [Find Duplicate File in System](https://leetcode.com/problems/find-duplicate-file-in-system/), [Find and Replace Pattern](https://leetcode.com/problems/find-and-replace-pattern/)                                                                 |
| **Meta**      | [Insert Delete GetRandom O(1)](https://leetcode.com/problems/insert-delete-getrandom-o1/), [Smallest String With Swaps](https://leetcode.com/problems/smallest-string-with-swaps/), [Contains Duplicate II](https://leetcode.com/problems/contains-duplicate-ii/), [Continuous Subarray Sum](https://leetcode.com/problems/continuous-subarray-sum/)                                                                                           |
| **Microsoft** | [Find the Difference of Two Arrays](https://leetcode.com/problems/find-the-difference-of-two-arrays/), [Sort the People](https://leetcode.com/problems/sort-the-people/), [Find Words That Can Be Formed by Characters](https://leetcode.com/problems/find-words-that-can-be-formed-by-characters/), [Sum of Unique Elements](https://leetcode.com/problems/sum-of-unique-elements/)                                                           |
| **Uber**      | [My Calendar I](https://leetcode.com/problems/my-calendar-i/), [Valid Sudoku](https://leetcode.com/problems/valid-sudoku/)                                                                                                                                                                                                                                                                                                                     |

---

## ✅ Completion Checklist

- [ ] All 20 Easy problems solved
- [ ] All 14 Medium problems solved
- [ ] All 1 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 5 conceptual questions answered out loud
- [ ] I can draw the stack and heap for a method call that creates objects
- [ ] I can pick HashMap vs TreeMap vs LinkedHashMap from the requirements alone

---

**← [Lecture 4 · Java & Programming Fundamentals](../Lecture4/Assignment.md)** &nbsp;·&nbsp; **[Lecture 6 · OOP & Java Collections Deep Dive](../Lecture6/Assignment.md) →**
