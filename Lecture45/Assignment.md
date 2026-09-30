# 🎓 Assignment 45 — Mock Interviews & System Thinking

> **Lecture:** 45 of 45 — Mock Interviews & System Thinking
> **Phase:** 6 — Interview Mastery
> **Estimated Time:** 7 days · **Total Problems:** 15 (3 Easy · 7 Medium · 5 Hard)
> **Goal:** Run complete mock interviews end to end, catch edge cases before the interviewer does, sketch a simple system design, and tell your own stories clearly.

---

## 🗺️ Pattern Recognition — Read Before Starting

Every problem here is a **mock round**, not an exercise. Use a partner if you can; otherwise record yourself talking. Follow the same framework every time:

| Stage (UMPIRE) | What you do                                              | Signal you are ready to move on              |
| -------------- | -------------------------------------------------------- | -------------------------------------------- |
| **U**nderstand | Restate the problem; ask about sizes and odd inputs      | You and the interviewer agree on one example |
| **M**atch      | Name the pattern from the constraints and question words | You can say why that pattern fits            |
| **P**lan       | Brute force, then the better idea, in plain words        | The interviewer agrees with the plan         |
| **I**mplement  | Write the code, narrating the non-obvious lines          | It compiles in your head                     |
| **R**eview     | Trace one normal case and two edge cases by hand         | Every variable holds what you expected       |
| **E**valuate   | State time and space; name one improvement or trade-off  | The interviewer has no open questions        |

**Round lengths:** Easy 20 minutes · Medium 35 minutes · Hard 45 minutes, talking the whole time.

---

## 🟢 Easy Tier (3 Problems)

_Openers. The code is short, so the whole score is in how clearly you clarify, test and explain._

### E1 · Detect Capital

**🔗 [LC 520 — Detect Capital](https://leetcode.com/problems/detect-capital/)** · Easy
**Pattern:** Count, then check three cases | **Companies:** Google

**Hint:** Count the capitals. Valid if the count is 0, equals the length, or is 1 with the first letter capital. Before coding, ask about single-letter words.

---

### E2 · Path Crossing

**🔗 [LC 1496 — Path Crossing](https://leetcode.com/problems/path-crossing/)** · Easy
**Pattern:** HashSet of visited points | **Companies:** Amazon

**Hint:** Start at (0, 0) and store every point you reach; the path crosses itself the moment you reach a stored point. Include the origin in the set.

---

### E3 · Minimum Time Visiting All Points

**🔗 [LC 1266 — Minimum Time Visiting All Points](https://leetcode.com/problems/minimum-time-visiting-all-points/)** · Easy
**Pattern:** Geometry insight | **Companies:** Amazon

**Hint:** A diagonal step moves both coordinates at once, so going from one point to the next takes max(|dx|, |dy|) seconds. Sum over consecutive points.

---

## 🟡 Medium Tier (7 Problems)

_Standard 35-minute rounds. Say the brute force first, every time._

### M1 · Encode and Decode TinyURL

**🔗 [LC 535 — Encode and Decode TinyURL](https://leetcode.com/problems/encode-and-decode-tinyurl/)** · Medium
**Pattern:** Id → base-62 code + two maps | **Companies:** Amazon, Google, Uber

**Hint:** Give each new URL the next integer id and write it in base 62. Keep code → URL for decoding and URL → code so the same URL is not stored twice. Then discuss how this would scale — the system-design half of the lecture.

---

### M2 · Count Good Nodes in Binary Tree

**🔗 [LC 1448 — Count Good Nodes in Binary Tree](https://leetcode.com/problems/count-good-nodes-in-binary-tree/)** · Medium
**Pattern:** DFS carrying the path maximum | **Companies:** Microsoft, Amazon

**Hint:** Pass down the largest value seen on the path from the root. A node is good if its value is at least that maximum.

---

### M3 · Lowest Common Ancestor of Deepest Leaves

**🔗 [LC 1123 — Lowest Common Ancestor of Deepest Leaves](https://leetcode.com/problems/lowest-common-ancestor-of-deepest-leaves/)** · Medium
**Pattern:** Post-order returning (depth, node) | **Companies:** Meta, Google

**Hint:** Each call returns the depth of its deepest leaf and the answer for its subtree. If both children are equally deep, the current node is the answer; otherwise pass up the deeper side's answer.

---

### M4 · Score of Parentheses

**🔗 [LC 856 — Score of Parentheses](https://leetcode.com/problems/score-of-parentheses/)** · Medium
**Pattern:** Stack, or count depth | **Companies:** Google

**Hint:** Only the innermost "()" pairs create points: each is worth 2 to the power of its depth. Track the depth and add 2^depth whenever ")" directly follows "(".

---

### M5 · Expressive Words

**🔗 [LC 809 — Expressive Words](https://leetcode.com/problems/expressive-words/)** · Medium
**Pattern:** Compare run-length groups | **Companies:** Google

**Hint:** Split both strings into (letter, run length) groups. The groups must match letter by letter, and each run in s must equal the word's run, or be at least 3 and no shorter than the word's.

---

### M6 · Find And Replace in String

**🔗 [LC 833 — Find And Replace in String](https://leetcode.com/problems/find-and-replace-in-string/)** · Medium
**Pattern:** Decide first, then build once | **Companies:** Google

**Hint:** All replacements refer to the original string. Record, for each valid index, which replacement starts there; then build the answer in one left-to-right pass.

---

### M7 · Minimum Genetic Mutation

**🔗 [LC 433 — Minimum Genetic Mutation](https://leetcode.com/problems/minimum-genetic-mutation/)** · Medium
**Pattern:** BFS over strings | **Companies:** Google, Amazon

**Hint:** Each gene is a node; neighbours differ in one position and must be in the bank. BFS from the start gives the fewest mutations. Ask early: what if the end gene is not in the bank?

---

## 🔴 Hard Tier (5 Problems)

_45-minute rounds where the edge cases, not the idea, decide the result._

### H1 · Max Points on a Line

**🔗 [LC 149 — Max Points on a Line](https://leetcode.com/problems/max-points-on-a-line/)** · Hard
**Pattern:** Slopes as reduced fractions | **Companies:** Google, Apple

**Hint:** For each point, count the other points by direction (dx, dy) divided by their gcd, with one fixed sign. Never use floating-point slopes, and do not forget vertical lines.

---

### H2 · Number of Atoms

**🔗 [LC 726 — Number of Atoms](https://leetcode.com/problems/number-of-atoms/)** · Hard
**Pattern:** Stack of count maps | **Companies:** Google

**Hint:** Push a new map on "("; on ")" read the multiplier, multiply the top map and merge it into the one below. Parse element names as one capital plus lowercase letters.

---

### H3 · Reaching Points

**🔗 [LC 780 — Reaching Points](https://leetcode.com/problems/reaching-points/)** · Hard
**Pattern:** Work backwards with modulo | **Companies:** Google, Amazon

**Hint:** Going backwards, the larger coordinate must have been produced from the smaller, so there is only one move. Replace repeated subtraction by modulo, and handle the case where one coordinate has already reached its start.

---

### H4 · Robot Collisions

**🔗 [LC 2751 — Robot Collisions](https://leetcode.com/problems/robot-collisions/)** · Hard
**Pattern:** Stack after sorting by position | **Companies:** Amazon

**Hint:** Sort by position. Right-movers wait on a stack; each left-mover fights the top of the stack until one of them is destroyed. Return survivors in the original input order.

---

### H5 · Concatenated Words

**🔗 [LC 472 — Concatenated Words](https://leetcode.com/problems/concatenated-words/)** · Hard
**Pattern:** Word-break DP per word | **Companies:** Amazon

**Hint:** Sort words by length. For each word, run Word Break against the set of shorter words, requiring at least two pieces; then add the word to the set.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — Max Points on a Line: for each point, a map of reduced slopes to every other point

// Snippet 2 — Reaching Points: the backwards modulo loop on (tx, ty)

// Snippet 3 — Robot Collisions: sort, then one pass with a stack

// Snippet 4 — TinyURL: encode and decode with a counter and two HashMaps

// Snippet 5 — Concatenated Words: n words of length up to L, Word Break DP for each

// Snippet 6 — Minimum Genetic Mutation: BFS over a bank of b genes of length 8, 4 letters
```

**Complexity Answers:**

1. **O(n² log C)** — n² pairs, a gcd each (C is the coordinate range).
2. **O(log(max(tx, ty)))** — like the Euclidean algorithm.
3. **O(n log n)** — the sort; every robot is pushed and popped at most once.
4. **O(L)** per call for a URL of length L (hashing it); O(1) otherwise.
5. **O(n log n + n · L²)** — or O(n · L³) if substrings are copied.
6. **O(b · 8 · 4)** states and moves, each with an O(8) string check.

---

## 🔍 Self-Assessment — True / False

1. It is fine to start coding as soon as you recognise the pattern. → **False** — agree the plan and the edge cases first
2. Saying a correct brute force out loud earns credit, even if you later improve it. → **True**
3. Comparing slopes as doubles is safe for integer points. → **False** — rounding makes different slopes equal; use reduced (dy, dx) pairs
4. In a system design round, you should fix the requirements and rough numbers before drawing boxes. → **True**
5. A cache in front of a database always makes reads correct and faster. → **False** — faster, but cached data can be stale; you must choose an invalidation rule
6. A behavioural answer should describe what the team did. → **False** — say what _you_ did, and the result

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **UMPIRE**: Walk through all six stages for Path Crossing in under three minutes.
2. **Edge cases**: List six edge cases you check on every array problem.
3. **TinyURL at scale**: How would you store the mapping, make ids unique across many servers, and keep popular links fast?
4. **Trade-offs**: SQL or NoSQL for the TinyURL mapping? Give one reason for each.
5. **Load balancing**: What does a load balancer do, and why must the web servers then be stateless?
6. **STAR**: Tell a two-minute story about a bug you fixed, using Situation, Task, Action, Result.

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                             |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Google**    | [Max Points on a Line](https://leetcode.com/problems/max-points-on-a-line/), [Reaching Points](https://leetcode.com/problems/reaching-points/), [Number of Atoms](https://leetcode.com/problems/number-of-atoms/), [Expressive Words](https://leetcode.com/problems/expressive-words/)             |
| **Amazon**    | [Robot Collisions](https://leetcode.com/problems/robot-collisions/), [Concatenated Words](https://leetcode.com/problems/concatenated-words/), [Encode and Decode TinyURL](https://leetcode.com/problems/encode-and-decode-tinyurl/), [Path Crossing](https://leetcode.com/problems/path-crossing/) |
| **Meta**      | [Lowest Common Ancestor of Deepest Leaves](https://leetcode.com/problems/lowest-common-ancestor-of-deepest-leaves/)                                                                                                                                                                                |
| **Microsoft** | [Count Good Nodes in Binary Tree](https://leetcode.com/problems/count-good-nodes-in-binary-tree/)                                                                                                                                                                                                  |
| **Apple**     | [Max Points on a Line](https://leetcode.com/problems/max-points-on-a-line/)                                                                                                                                                                                                                        |
| **Uber**      | [Encode and Decode TinyURL](https://leetcode.com/problems/encode-and-decode-tinyurl/)                                                                                                                                                                                                              |

---

## ✅ Completion Checklist

- [ ] All 3 Easy problems done as full mock rounds, out loud
- [ ] All 7 Medium problems done as 35-minute rounds
- [ ] All 5 Hard problems attempted as 45-minute rounds
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I sketched the TinyURL system design on paper, with numbers
- [ ] I have four STAR stories written and rehearsed

---

**← [Lecture 44 · Company Pattern Drills](../Lecture44/Assignment.md)** &nbsp;·&nbsp; **🎉 Course complete — [back to the study plan](../README.md)**
