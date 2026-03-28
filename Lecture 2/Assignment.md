# 📝 Assignment 02 — Recursion & Backtracking

> **Lecture:** Recursion & Backtracking  
> **Builds on:** Lecture 1 (Java Fundamentals, Big-O)  
> **Complete before:** Lecture 3 (Bit Manipulation)  
> **Rule:** Write brute recursion first → identify repeated subproblems → memoize if possible → state complexity for every solution.

---

## 🗺️ Problem Map by Pattern

| Pattern                      | Problems           |
| ---------------------------- | ------------------ |
| Linear Recursion             | 01, 02, 03, 04     |
| Tree Recursion + Memoization | 05, 06, 07         |
| Include / Exclude (Subsets)  | 08, 09, 10         |
| Permutations                 | 11, 12             |
| Backtracking + Pruning       | 13, 14, 15, 16, 17 |
| Hard / FAANG-level           | 18, 19, 20, 21, 22 |
| Complexity Analysis          | 23, 24, 25         |
| Bonus Practice               | B1–B7              |

---

## 🟢 Easy — Pattern Builders (Do ALL)

---

### Problem 01 — Print 1 to N, then N to 1 (no loop, no second function)
> 🔗 **Practice:** [Print 1 to N (GFG)](https://www.geeksforgeeks.org/problems/print-1-to-n-without-using-loops-1587115620/1)

**`[Amazon] [TCS] [Easy]`**  
**Pattern: Linear Recursion · Parameterized**

Print numbers 1 to N and then N back to 1, using only a single recursive function. You may NOT use any loop or a second helper function.

```
Input:  N = 5
Output: 1 2 3 4 5 4 3 2 1
```

**Key insight:** Print the number once before the recursive call and once after — the "coming back" phase prints in reverse.  
**Expected:** Time O(n), Space O(n)

---

### Problem 02 — Check if String is Palindrome (Recursive)
> 🔗 **LeetCode:** [125. Valid Palindrome](https://leetcode.com/problems/valid-palindrome/)

**`[Amazon] [Microsoft] [Adobe] [Easy]`**  
**Pattern: Linear Recursion · Two Pointers via recursion**

Check if a string is a palindrome using recursion. No loops, no built-in reverse.

```
Input:  "racecar"  → true
Input:  "hello"    → false
Input:  "a"        → true
Input:  ""         → true
```

**Think:** Compare first and last characters. If they match, recurse on the substring between them.  
**Expected:** Time O(n), Space O(n)  
**Bonus:** How would you do this iteratively in O(1) space?

---

### Problem 03 — Power of a Number (Fast Exponentiation)
> 🔗 **LeetCode:** [50. Pow(x, n)](https://leetcode.com/problems/powx-n/)

**`[Google] [Amazon] [Microsoft] [Medium-Easy]`**  
**Pattern: Functional Recursion · Divide & Conquer seed**  
**LeetCode #50**

Implement `pow(x, n)` — compute x raised to the power n. Handle negative exponents.

```
Input:  x = 2.0,  n = 10   → Output: 1024.0
Input:  x = 2.1,  n = 3    → Output: 9.261
Input:  x = 2.0,  n = -2   → Output: 0.25
```

**Brute force:** Multiply x, n times → O(n)  
**Optimal:** Binary exponentiation — halve the exponent each time → O(log n)  
**Careful:** n can be Integer.MIN_VALUE — negate it carefully using long!  
**Expected:** Time O(log n), Space O(log n)

---

### Problem 04 — Reverse a Linked List (Recursive)
> 🔗 **LeetCode:** [206. Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

**`[Amazon] [Microsoft] [Facebook] [Easy]`**  
**Pattern: Linear Recursion on Linked List**

Reverse a singly linked list using recursion. (Define a basic ListNode class if needed.)

```
Input:  1 → 2 → 3 → 4 → 5
Output: 5 → 4 → 3 → 2 → 1
```

**Think first:** What's the base case? (null or single node)  
**Trust:** Assume reverseList(head.next) correctly reverses the tail.  
**Induct:** After reversal, head.next.next = head; head.next = null.  
**Expected:** Time O(n), Space O(n) — can you convert to O(1) space iteratively?

---

### Problem 05 — Count Occurrences in Array (Recursive)
> 🔗 **Practice:** [Count Occurrences (GFG)](https://www.geeksforgeeks.org/problems/number-of-occurrence2259/1)

**`[Infosys] [Wipro] [Easy]`**  
**Pattern: Linear Recursion**

Given a sorted array and a target, count how many times target appears using recursion.

```
Input:  arr = [1, 1, 2, 2, 2, 3, 4], target = 2  → Output: 3
Input:  arr = [5, 5, 5, 5], target = 5            → Output: 4
```

**Expected:** Time O(n) recursive, Space O(n). Bonus: O(log n) using binary search recursion.

---

### Problem 06 — Rope Cutting Problem
> 🔗 **Practice:** [Rope Cutting (GFG)](https://www.geeksforgeeks.org/problems/cutted-segments1642/1)

**`[Amazon] [Flipkart] [Easy-Medium]`**  
**Pattern: Functional Recursion · Greedy seed**

Given a rope of length `n` and cut sizes `a`, `b`, `c`, find the maximum number of pieces you can cut. If no valid cut exists, return -1.

```
Input:  n=5, a=2, b=5, c=1  → Output: 5  (five 1-length cuts)
Input:  n=23, a=11, b=9, c=12 → Output: 2
Input:  n=5, a=4, b=2, c=6   → Output: -1
```

**Think:** At each step, try cutting `a`, `b`, or `c` lengths and recurse on the remainder.  
**Base:** n=0 → 0 cuts (valid). n<0 → -1 (invalid).  
**Induct:** result = 1 + max(cut_a, cut_b, cut_c), taking -1 into account.

---

## 🟡 Medium — Core Pattern Mastery

---

### Problem 07 — Climbing Stairs (Fibonacci Disguise)
> 🔗 **LeetCode:** [70. Climbing Stairs](https://leetcode.com/problems/climbing-stairs/)

**`[Google] [Amazon] [Microsoft] [Apple] [Medium]`**  
**Pattern: Tree Recursion · Memoization**  
**LeetCode #70**

You can climb 1 or 2 stairs at a time. In how many distinct ways can you reach the top (n stairs)?

```
Input:  n = 2  → Output: 2   (1+1, 2)
Input:  n = 3  → Output: 3   (1+1+1, 1+2, 2+1)
Input:  n = 5  → Output: 8
```

**Notice:** ways(n) = ways(n-1) + ways(n-2) — it's Fibonacci!  
**Required:** Implement all 3 approaches: naive recursion, memoization, and iterative DP.  
**Expected:** Time O(n), Space O(1) for optimal

---

### Problem 08 — Generate All Subsets with Duplicate Elements
> 🔗 **LeetCode:** [90. Subsets II](https://leetcode.com/problems/subsets-ii/)

**`[Google] [Facebook] [Amazon] [Medium]`**  
**Pattern: Include/Exclude + Deduplication**  
**LeetCode #90**

Given an integer array that may contain duplicates, return all possible subsets (no duplicate subsets in result).

```
Input:  [1, 2, 2]
Output: [[], [1], [1,2], [1,2,2], [2], [2,2]]
```

**Key difference from Problem 08 in Lecture (no duplicates):**  
Sort first! Then at each recursion level, skip elements equal to the previous one.  
`if (i > start && nums[i] == nums[i-1]) continue;`  
**Expected:** Time O(2ⁿ × n), Space O(n)

---

### Problem 09 — Combination Sum II (each element used once)
> 🔗 **LeetCode:** [40. Combination Sum II](https://leetcode.com/problems/combination-sum-ii/)

**`[Google] [Amazon] [Microsoft] [Medium]`**  
**Pattern: Backtracking + Deduplication**  
**LeetCode #40**

Given candidates (may contain duplicates) and a target, find all unique combinations summing to target. Each number may only be used once.

```
Input:  candidates=[10,1,2,7,6,1,5], target=8
Output: [[1,1,6],[1,2,5],[1,7],[2,6]]
```

**Differs from Combination Sum I:** Pass `i+1` (not `i`) to prevent reuse. Skip duplicates at same level.

---

### Problem 10 — Letter Combinations of Phone Number
> 🔗 **LeetCode:** [17. Letter Combinations of a Phone Number](https://leetcode.com/problems/letter-combinations-of-a-phone-number/)

**`[Google] [Amazon] [Facebook] [Microsoft] [Medium]`**  
**Pattern: Backtracking · State building**  
**LeetCode #17**

Given a string containing digits 2-9, return all possible letter combinations the number could represent (like a phone keypad).

```
Input:  "23"
Output: ["ad","ae","af","bd","be","bf","cd","ce","cf"]
```

**Map:** 2→abc, 3→def, 4→ghi, 5→jkl, 6→mno, 7→pqrs, 8→tuv, 9→wxyz  
**Hint:** For each digit, try each of its letters, recurse on the next digit.  
**Expected:** Time O(4ⁿ × n), Space O(n) where n = number of digits

---

### Problem 11 — Permutations of Array
> 🔗 **LeetCode:** [46. Permutations](https://leetcode.com/problems/permutations/)

**`[Google] [Amazon] [Facebook] [Microsoft] [Medium]`**  
**Pattern: Backtracking · Swap**  
**LeetCode #46**

Given an array of distinct integers, return all possible permutations.

```
Input:  [1, 2, 3]
Output: [[1,2,3],[1,3,2],[2,1,3],[2,3,1],[3,1,2],[3,2,1]]
```

**Implement both approaches:**

1. String-based (remove chosen character from remaining pool)
2. Swap-based in-place (more efficient, no extra space for the string pool)  
   **Expected:** Time O(n! × n), Space O(n)

---

### Problem 12 — Permutations II (with duplicates)
> 🔗 **LeetCode:** [47. Permutations II](https://leetcode.com/problems/permutations-ii/)

**`[Amazon] [Google] [Microsoft] [Medium]`**  
**Pattern: Backtracking · Deduplication**  
**LeetCode #47**

Given a collection that might contain duplicates, return all unique permutations.

```
Input:  [1, 1, 2]
Output: [[1,1,2],[1,2,1],[2,1,1]]
```

**Deduplication trick:** Sort + use a `used[]` boolean array. Skip `nums[i] == nums[i-1]` when `used[i-1]` is false (sibling-level duplicate).

---

### Problem 13 — Generate Parentheses
> 🔗 **LeetCode:** [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)

**`[Google] [Amazon] [Facebook] [Microsoft] [Medium]`**  
**Pattern: Backtracking · Constraint-based pruning**  
**LeetCode #22**

Given n pairs of parentheses, generate all combinations of well-formed parentheses.

```
Input:  n = 3
Output: ["((()))","(()())","(())()","()(())","()()()"]
```

**Constraints (pruning rules):**

- Can add `(` only if open count < n
- Can add `)` only if close count < open count

**Expected:** Time O(4ⁿ / √n) — Catalan number, Space O(n)

---

### Problem 14 — Flood Fill (Paint Bucket)
> 🔗 **LeetCode:** [733. Flood Fill](https://leetcode.com/problems/flood-fill/)

**`[Facebook] [Amazon] [Microsoft] [Medium]`**  
**Pattern: Grid DFS Recursion**  
**LeetCode #733**

Given a 2D image grid, a starting pixel, and a new color, fill all connected pixels of the same original color with the new color. (Like the paint bucket in MS Paint.)

```
Input:  image = [[1,1,1],[1,1,0],[1,0,1]], sr=1, sc=1, color=2
Output: [[2,2,2],[2,2,0],[2,0,1]]
```

**This is DFS on a grid — the precursor to number of islands, BFS shortest path, etc.**  
**Base cases:** Out of bounds. Current cell ≠ original color. Already filled.

---

### Problem 15 — Count All Paths in a Grid (Top-Left to Bottom-Right)
> 🔗 **LeetCode:** [62. Unique Paths](https://leetcode.com/problems/unique-paths/)

**`[Amazon] [Google] [Microsoft] [Medium]`**  
**Pattern: Tree Recursion on Grid · DP Precursor**

Count distinct paths from (0,0) to (m-1, n-1) moving only right or down.

```
Input:  m=3, n=3  → Output: 6
Input:  m=3, n=7  → Output: 28
```

**Recursive:** paths(r,c) = paths(r+1,c) + paths(r,c+1)  
**With memoization:** O(m×n) time, O(m×n) space  
**Bonus:** Can you derive the closed-form formula? C(m+n-2, m-1)

---

## 🔴 Hard — FAANG Level

---

### Problem 16 — N-Queens Problem
> 🔗 **LeetCode:** [51. N-Queens](https://leetcode.com/problems/n-queens/)

**`[Google] [Amazon] [Facebook] [Hard]`**  
**Pattern: Backtracking + O(1) safety check optimization**  
**LeetCode #51**

Place N queens on an N×N chessboard such that no two attack each other. Return all distinct solutions.

```
Input:  n = 4
Output: [[".Q..","...Q","Q...","..Q."],["..Q.","Q...","...Q",".Q.."]]
```

**Full implementation required:**

1. Naive O(n) safety check (as shown in lecture)
2. Optimized O(1) safety using three sets: `cols`, `diag1 (r-c)`, `diag2 (r+c)`  
   **Compare the runtime of both approaches empirically.**

---

### Problem 17 — Rat in a Maze
> 🔗 **Practice:** [Rat in a Maze (GFG)](https://www.geeksforgeeks.org/problems/rat-in-a-maze-problem/1)

**`[Amazon] [Google] [Flipkart] [Hard]`**  
**Pattern: Grid Backtracking · Path recording**

Given an N×N binary matrix where 1=open and 0=blocked, find all paths from (0,0) to (N-1,N-1) moving in all 4 directions. Return all path strings (L/R/U/D).

```
Input:  [[1,0,0,0],
          [1,1,0,1],
          [1,1,0,0],
          [0,1,1,1]]
Output: ["DDRDRR","DRDDRR"]
```

**Key:** Mark cell visited while exploring, unmark on backtrack.

---

### Problem 18 — Decode Ways
> 🔗 **LeetCode:** [91. Decode Ways](https://leetcode.com/problems/decode-ways/)

**`[Amazon] [Google] [Facebook] [Microsoft] [Hard]`**  
**Pattern: Tree Recursion + Memoization → DP**  
**LeetCode #91**

A message encoded as digits (A=1, B=2, ..., Z=26). Count the number of ways to decode it.

```
Input:  "12"   → Output: 2   ("AB" or "L")
Input:  "226"  → Output: 3   ("BZ","VF","BBF")
Input:  "06"   → Output: 0   (invalid: leading zero)
```

**This is Fibonacci with extra conditions!**  
At each position, try a 1-digit decode (if valid) and a 2-digit decode (if valid).  
Use memoization to avoid O(2ⁿ) → O(n).

---

### Problem 19 — Expression Add Operators
> 🔗 **LeetCode:** [282. Expression Add Operators](https://leetcode.com/problems/expression-add-operators/)

**`[Google] [Facebook] [Amazon] [Hard]`**  
**Pattern: Backtracking · String building**  
**LeetCode #282**

Given a string of digits and a target, add `+`, `-`, or `*` between digits to reach the target. Return all valid expressions.

```
Input:  num = "123", target = 6
Output: ["1+2+3", "1*2*3"]

Input:  num = "232", target = 8
Output: ["2+3*2", "2*3+2"]
```

**Hardest part:** Multiplication requires tracking the `prevOperand` to correctly handle operator precedence without parentheses.

---

### Problem 20 — Palindrome Partitioning
> 🔗 **LeetCode:** [131. Palindrome Partitioning](https://leetcode.com/problems/palindrome-partitioning/)

**`[Google] [Facebook] [Amazon] [Hard]`**  
**Pattern: Backtracking + Palindrome Check**  
**LeetCode #131**

Given a string, partition it such that every substring is a palindrome. Return all possible partitions.

```
Input:  "aab"
Output: [["a","a","b"],["aa","b"]]
```

**Steps:**

1. At each position, try all substrings starting here
2. If the substring is a palindrome → include it and recurse on the rest
3. Backtrack

**Optimization:** Pre-compute `isPalin[i][j]` using DP in O(n²) before backtracking.

---

### Problem 21 — Sudoku Solver
> 🔗 **LeetCode:** [37. Sudoku Solver](https://leetcode.com/problems/sudoku-solver/)

**`[Google] [Amazon] [Microsoft] [Hard]`**  
**Pattern: Backtracking + Constraint propagation**  
**LeetCode #37**

Solve a given Sudoku puzzle. Fill in the empty cells ('.' characters).

**Full implementation:** Use the approach from lecture notes. Test with multiple valid Sudoku boards.  
**Optimization:** Try the cell with fewest valid choices first (constraint propagation — this is how real Sudoku solvers work).

---

### Problem 22 — K-th Symbol in Grammar
> 🔗 **LeetCode:** [779. K-th Symbol in Grammar](https://leetcode.com/problems/k-th-symbol-in-grammar/)

**`[Amazon] [Google] [Medium-Hard]`**  
**Pattern: Pure Recursion · Binary tree insight**  
**LeetCode #779**

Row 1: "0". Each subsequent row: replace 0→01, 1→10. Find the kth symbol (1-indexed) in the nth row.

```
Row 1:  0
Row 2:  01
Row 3:  0110
Row 4:  01101001
Input:  n=4, k=5  → Output: 1
```

**Key insight:** The nth row has 2^(n-1) characters. The kth character in row n is derived from the ceil(k/2)th character in row n-1.  
This is a pure recursion problem — no iteration needed at all.

---


## 🎁 Bonus — Extra Practice (Build Speed & Confidence)

---

### Problem B1 — Tower of Hanoi

> 🔗 **Practice:** [Tower of Hanoi (GFG)](https://www.geeksforgeeks.org/problems/tower-of-hanoi-1587115621/1)

**`[Amazon] [Microsoft] [Easy]`**  
**Pattern: Linear Recursion · Classic**

Move N disks from source to destination using an auxiliary rod. Rules: move one disk at a time, never place a larger disk on a smaller one.

```
Input:  N = 3
Output: Move disk 1 from A to C
        Move disk 2 from A to B
        Move disk 1 from C to B
        Move disk 3 from A to C
        Move disk 1 from B to A
        Move disk 2 from B to C
        Move disk 1 from A to C
```

**This is THE classic recursion problem.** Total moves = 2ⁿ - 1.  
**Expected:** Time O(2ⁿ), Space O(n) — cannot be optimized.

---

### Problem B2 — Sort an Array Using Recursion Only

> 🔗 **Practice:** [Sort a Stack (GFG)](https://www.geeksforgeeks.org/problems/sort-a-stack/1) *(same concept)*

**`[Amazon] [Medium]`**  
**Pattern: Recursion on reduced input**

Sort an array using recursion only. No loops, no built-in sort.

**Approach:** Remove last element → recursively sort remaining → insert the removed element at its correct position (also recursively).  
**Expected:** Time O(n²), Space O(n)

---

### Problem B3 — Subset Sum Problem

> 🔗 **LeetCode:** [416. Partition Equal Subset Sum](https://leetcode.com/problems/partition-equal-subset-sum/) *(related)*

**`[Amazon] [Google] [Medium]`**  
**Pattern: Include/Exclude**

Given an array and a target sum, determine if any subset sums to exactly the target.

```
Input:  arr = [3, 34, 4, 12, 5, 2], target = 9
Output: true (subset [4, 3, 2] or [4, 5])
```

**Expected:** Brute O(2ⁿ), Memoized O(n × target)  
**This is a gateway to DP! You'll revisit this exact pattern in Lecture 18.**

---

### Problem B4 — Unique Paths with Obstacles

> 🔗 **LeetCode:** [63. Unique Paths II](https://leetcode.com/problems/unique-paths-ii/)

**`[Amazon] [Google] [Medium]`**  
**Pattern: Grid Recursion with constraints**

Same as grid paths but some cells are blocked (value 1). Count paths from top-left to bottom-right.

```
Input:  [[0,0,0],[0,1,0],[0,0,0]]
Output: 2
```

**Key difference:** If `grid[r][c] == 1`, return 0 (blocked cell).  
**Expected:** Time O(m×n) with memoization

---

### Problem B5 — Word Break Problem

> 🔗 **LeetCode:** [139. Word Break](https://leetcode.com/problems/word-break/)

**`[Google] [Amazon] [Facebook] [Medium]`**  
**Pattern: Backtracking + Memoization → DP**

Given a string and a dictionary, determine if the string can be segmented into dictionary words.

```
Input:  s = "leetcode", wordDict = ["leet", "code"]
Output: true (leet + code)

Input:  s = "catsandog", wordDict = ["cats","dog","sand","and","cat"]
Output: false
```

**Expected:** Brute O(2ⁿ), Memoized O(n² × m)

---

### Problem B6 — Restore IP Addresses

> 🔗 **LeetCode:** [93. Restore IP Addresses](https://leetcode.com/problems/restore-ip-addresses/)

**`[Amazon] [Google] [Medium]`**  
**Pattern: Backtracking with numeric constraints**

Given a string of digits, return all valid IP addresses formed by inserting dots.

```
Input:  "25525511135"
Output: ["255.255.11.135", "255.255.111.35"]
```

**Constraints:** Each segment 0–255, no leading zeros (except "0" itself), exactly 4 segments.  
**Expected:** Time O(3⁴ × n), Space O(n)

---

### Problem B7 — Combination Sum III

> 🔗 **LeetCode:** [216. Combination Sum III](https://leetcode.com/problems/combination-sum-iii/)

**`[Medium]`**  
**Pattern: Backtracking with count constraint**

Find all combinations of k numbers (from 1-9, each used once) that sum to n.

```
Input:  k = 3, n = 7
Output: [[1,2,4]]

Input:  k = 3, n = 9
Output: [[1,2,6],[1,3,5],[2,3,4]]
```

**This combines the sum constraint (Combo Sum) with a count constraint (exactly k numbers).**

## 📊 Complexity Analysis — Spot the Recursion

For each, identify the recurrence relation and solve for Time and Space:

### Problem 23 — What is the complexity?

```java
// Code A
int mystery(int n) {
    if (n <= 0) return 0;
    return mystery(n/3) + mystery(n/3) + mystery(n/3);
}
```

> **Recurrence:** T(n) = \_\_\_\_  
> **Time:** \_\_\_\_  
> **Hint:** Think Master Theorem with a=3, b=3

```java
// Code B
void mystery2(int n) {
    if (n <= 1) return;
    for (int i = 0; i < n; i++) System.out.println(i);
    mystery2(n/2);
    mystery2(n/2);
}
```

> **Recurrence:** T(n) = \_\_\_\_  
> **Time:** \_\_\_\_

```java
// Code C — what EXTRA space does this use?
List<List<Integer>> subsets(int[] arr, int idx, List<Integer> cur) {
    if (idx == arr.length) { result.add(new ArrayList<>(cur)); return; }
    cur.add(arr[idx]);   subsets(arr, idx+1, cur);
    cur.remove(...);     subsets(arr, idx+1, cur);
}
```

> **Space (call stack only, not result):** \_\_\_\_

---

### Problem 24 — Recursion Tree Drawing

Draw the complete recursion tree for `fib(5)`. Count:

- Total number of nodes in the tree: \_\_\_\_
- Number of times `fib(2)` is called: \_\_\_\_
- Number of times `fib(1)` is called: \_\_\_\_
- With memoization, how many unique calls are made? \_\_\_\_

---

### Problem 25 — Convert Recursion to Iteration

For each recursive function, write the equivalent iterative version:

**25a.** Convert recursive binary search to iterative (O(1) space)

**25b.** Convert recursive `printNto1` to iterative using an explicit Stack

**25c.** Convert recursive `subsets` (include/exclude) to iterative using bit manipulation  
(Hint: For n elements, iterate i from 0 to 2ⁿ-1. The jth bit of i tells you whether to include arr[j].)

---

## 🏁 Self-Assessment Checklist

Before moving to Lecture 3:

- [ ] I solved all 6 Easy problems without looking at solutions
- [ ] I implemented the universal backtracking template from memory
- [ ] I can explain the difference between subsets and permutations clearly
- [ ] I solved N-Queens with BOTH O(n) and O(1) safety check
- [ ] I correctly identified the complexity for all 3 Code Snippets in Problem 23
- [ ] I understand why memoization turns O(2ⁿ) → O(n) for Fibonacci
- [ ] I can explain why we add a COPY (`new ArrayList<>(cur)`) not the list itself
- [ ] I solved at least 3 of the 7 Hard problems

---

## 📋 Answers — Complexity Problems

<details>
<summary>Click only after attempting</summary>

**Code A:** T(n) = 3T(n/3) + O(1) → a=3, b=3, d=0 → log_b(a)=1 > d=0 → **O(n)**  
**Code B:** T(n) = 2T(n/2) + O(n) → a=2, b=2, d=1 → log_b(a)=1 = d=1 → **O(n log n)**  
**Code C:** Stack depth = n levels → each frame holds idx (int) + pointer to cur list → **O(n)**

**fib(5) tree:**  
Total nodes = 15 | fib(2) called 3 times | fib(1) called 5 times  
With memoization: only 5 unique calls (fib(1) through fib(5)) — everything else is cache hit!

</details>

---

_Next: Lecture 3 — Bit Manipulation. Short but powerful: XOR, masking, and number theory tricks used constantly in optimized solutions._
