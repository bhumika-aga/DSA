# 📐 Assignment 28 — Intervals & Sweep Line

> **Lecture:** 28 of 45 — Intervals & Sweep Line
> **Phase:** 3 — Core Patterns
> **Estimated Time:** 4 days · **Total Problems:** 18 (5 Easy · 10 Medium · 3 Hard)
> **Goal:** Decide what to sort by, or stop sorting intervals altogether and sweep their start and end events instead.

---

## 🗺️ Pattern Recognition — Read Before Starting

Before writing any code, match the problem to a shape. Aim to do it **within 30 seconds**:

| Signal in the Problem                 | Pattern                | Move                                  |
| ------------------------------------- | ---------------------- | ------------------------------------- |
| "merge", "combine overlapping"        | Sort by Start          | extend with `max(end, iv.end)`        |
| "how many can I keep / attend"        | Greedy by End          | earliest finish leaves the most room  |
| "minimum rooms", "maximum at once"    | Event Sweep            | `+1` on start, `-1` on end, then sort |
| "add v to a range", small coordinates | Difference Array       | Lecture 26, indexed by position       |
| "skyline", "area covered once"        | Sweep + Active Set     | multiset or heap of what is open      |
| huge or sparse coordinates            | Coordinate Compression | rank the endpoints, then sweep        |

---

## 🟢 Easy Tier (5 Problems)

_Build intervals, test overlap, and count what covers a point._

### E1 · Summary Ranges

**🔗 [LC 228 — Summary Ranges](https://leetcode.com/problems/summary-ranges/)** · Easy
**Pattern:** Interval Building | **Companies:** Amazon, Google, Meta

**Hint:** Walk the sorted array keeping the start of the current run. Close the run when `nums[i] + 1 != nums[i+1]`, and format as `a` or `a->b`.

---

### E2 · Determine if Two Events Have Conflict

**🔗 [LC 2446 — Determine if Two Events Have Conflict](https://leetcode.com/problems/determine-if-two-events-have-conflict/)** · Easy
**Pattern:** Overlap Test | **Companies:** Amazon

**Hint:** Two half-open events clash unless one finishes before the other starts: `startA < endB and startB < endA`. Times are `"HH:MM"` strings, so compare them directly or convert to minutes.

---

### E3 · Number of Students Doing Homework at a Given Time

**🔗 [LC 1450 — Number of Students Doing Homework at a Given Time](https://leetcode.com/problems/number-of-students-doing-homework-at-a-given-time/)** · Easy
**Pattern:** Count Covering Intervals | **Companies:** Amazon, Adobe

**Hint:** Each student is the interval `[startTime[i], endTime[i]]`. Count how many contain `queryTime` — a single pass, since the intervals are given, not built.

---

### E4 · Teemo Attacking

**🔗 [LC 495 — Teemo Attacking](https://leetcode.com/problems/teemo-attacking/)** · Easy
**Pattern:** Overlapping Ranges | **Companies:** Amazon, Google

**Hint:** Each attack covers `[t, t + duration)`. Add the full duration, unless the next attack starts sooner — then add only the gap. One pass over the sorted times.

---

### E5 · Range Addition II

**🔗 [LC 598 — Range Addition II](https://leetcode.com/problems/range-addition-ii/)** · Easy
**Pattern:** Range Intersection | **Companies:** Amazon

**Hint:** Every operation covers a rectangle anchored at the origin, so the most-incremented cells are the intersection of them all: the product of the minimum width and the minimum height.

---

## 🟡 Medium Tier (10 Problems)

_The two sort orders, the greedy proof, and the first real sweeps._

### M1 · Non-overlapping Intervals

**🔗 [LC 435 — Non-overlapping Intervals](https://leetcode.com/problems/non-overlapping-intervals/)** · Medium
**Pattern:** Greedy by End Time | **Companies:** Amazon, Google, Meta

**Hint:** Sort by end and keep an interval whenever its start is at least the last kept end. The answer is the total minus the number kept.

---

### M2 · Minimum Number of Arrows to Burst Balloons

**🔗 [LC 452 — Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/)** · Medium
**Pattern:** Greedy by End Time | **Companies:** Amazon, Google, Meta

**Hint:** Same loop as non-overlapping intervals, but touching balloons burst together, so the test is `start > lastEnd`. Sort by end and count the arrows.

---

### M3 · Partition Labels

**🔗 [LC 763 — Partition Labels](https://leetcode.com/problems/partition-labels/)** · Medium
**Pattern:** Intervals from Last Occurrence | **Companies:** Amazon, Google, Meta

**Hint:** Record each letter's last index, then sweep: extend the current part to the furthest last-occurrence seen, and cut when the index reaches it.

---

### M4 · Remove Covered Intervals

**🔗 [LC 1288 — Remove Covered Intervals](https://leetcode.com/problems/remove-covered-intervals/)** · Medium
**Pattern:** Sort with a Tie-Break | **Companies:** Amazon, Google

**Hint:** Sort by start ascending and end descending, then keep a running `maxEnd`. An interval is covered exactly when its end is at most `maxEnd`.

---

### M5 · My Calendar II

**🔗 [LC 731 — My Calendar II](https://leetcode.com/problems/my-calendar-ii/)** · Medium
**Pattern:** Two Booking Layers | **Companies:** Google, Amazon

**Hint:** Keep the booked intervals and the already-double-booked intervals in two lists. A new booking is rejected if it overlaps the doubles; otherwise add its overlaps with the singles to the doubles.

---

### M6 · Video Stitching

**🔗 [LC 1024 — Video Stitching](https://leetcode.com/problems/video-stitching/)** · Medium
**Pattern:** Greedy Reach | **Companies:** Amazon, Google

**Hint:** Sort by start. Scan forward tracking the furthest reach from clips that begin at or before the current end; when the current end is reached, take a clip and increment the count. It is Jump Game on intervals.

---

### M7 · Maximum Length of Pair Chain

**🔗 [LC 646 — Maximum Length of Pair Chain](https://leetcode.com/problems/maximum-length-of-pair-chain/)** · Medium
**Pattern:** Greedy by End Time | **Companies:** Amazon, Google

**Hint:** The same chain rule as non-overlapping intervals: sort by the second value and extend the chain whenever the next pair starts strictly after the last kept end.

---

### M8 · Maximum Number of Events That Can Be Attended

**🔗 [LC 1353 — Maximum Number of Events That Can Be Attended](https://leetcode.com/problems/maximum-number-of-events-that-can-be-attended/)** · Medium
**Pattern:** Day Sweep + Min-Heap | **Companies:** Amazon, Google, Microsoft

**Hint:** Advance day by day. Push every event that has started into a min-heap keyed on end day, discard expired tops, and attend the event that ends soonest.

---

### M9 · Two Best Non-Overlapping Events

**🔗 [LC 2054 — Two Best Non-Overlapping Events](https://leetcode.com/problems/two-best-non-overlapping-events/)** · Medium
**Pattern:** Sort + Suffix Maximum | **Companies:** Amazon, Google

**Hint:** Sort by start and precompute the best value among events starting at or after each index. For each event, binary search the first non-overlapping event and add that suffix maximum.

---

### M10 · Exclusive Time of Functions

**🔗 [LC 636 — Exclusive Time of Functions](https://leetcode.com/problems/exclusive-time-of-functions/)** · Medium
**Pattern:** Stack of Active Calls | **Companies:** Amazon, Microsoft, Meta

**Hint:** A stack holds the currently running function ids. On every log entry, add the elapsed time to whatever is on top, then push (start) or pop (end). Remember that an end timestamp is inclusive.

---

## 🔴 Hard Tier (3 Problems)

_Sweeps that carry a structure: a multiset, a merge, or a DP table._

### H1 · The Skyline Problem

**🔗 [LC 218 — The Skyline Problem](https://leetcode.com/problems/the-skyline-problem/)** · Hard
**Pattern:** Event Sweep + Multiset | **Companies:** Google, Amazon, Meta

**Hint:** Turn each building into a start and an end event, sort with starts before ends and taller first, and keep the open heights in a multiset. Emit a point whenever the maximum changes.

---

### H2 · Rectangle Area II

**🔗 [LC 850 — Rectangle Area II](https://leetcode.com/problems/rectangle-area-ii/)** · Hard
**Pattern:** Sweep + Coordinate Compression | **Companies:** Google, Amazon

**Hint:** Sweep the distinct x-coordinates. Within a strip, the covered height is fixed: merge the y-intervals of the rectangles spanning it and multiply by the strip width.

---

### H3 · Maximum Profit in Job Scheduling

**🔗 [LC 1235 — Maximum Profit in Job Scheduling](https://leetcode.com/problems/maximum-profit-in-job-scheduling/)** · Hard
**Pattern:** Sort + DP + Binary Search | **Companies:** Google, Amazon, Meta

**Hint:** Sort jobs by end time. `dp[i] = max(dp[i-1], profit[i] + dp[j])`, where `j` is the last job ending at or before this job's start — found by binary search.

---

## 📊 Complexity Analysis Exercises

Work out the time and space complexity of each snippet before checking the answers.

```pseudocode
// Snippet 1 — merge overlapping intervals (sort first)

// Snippet 2 — check if a new interval overlaps each of n others

// Snippet 3 — minimum meeting rooms with a sweep of 2n events

// Snippet 4 — minimum meeting rooms with a min-heap of end times

// Snippet 5 — insert one interval into a sorted, non-overlapping list

// Snippet 6 — maximum non-overlapping intervals (sort by end, greedy)
```

**Complexity Answers:**

1. **O(n log n)**.
2. **O(n)**.
3. **O(n log n)** — sorting the events.
4. **O(n log n)**.
5. **O(n)**.
6. **O(n log n)**.

---

## 🔍 Self-Assessment — True / False

1. Two intervals [a, b] and [c, d] overlap exactly when a ≤ d and c ≤ b. → **True** — for closed intervals
2. Merging intervals works without sorting them first. → **False** — sort by start first
3. For the most non-overlapping intervals, sort by end time. → **True** — finishing earliest leaves the most room
4. A sweep line processes events in time order. → **True**
5. At equal times, the order of start and end events never matters. → **False** — it decides whether touching intervals count as overlapping
6. Meeting rooms can be solved with a heap of end times. → **True**

---

## 🧠 Conceptual Check

Answer these out loud, without looking at the notes:

1. **Endpoints:** Write the overlap test for half-open intervals, then for closed ones. Which does a meeting-room problem use?
2. **Sort choice:** Give a concrete input where sorting by start gives the wrong answer to "keep the most non-overlapping intervals".
3. **The max:** Why must merging use `max(end, iv.end)`? Give an input that exposes the bug.
4. **Tie-break:** At the same timestamp, when should an end event be processed before a start event, and what is the symptom of getting it backwards?
5. **Sweep vs difference array:** Both count concurrency. State the input that makes each one the wrong choice.
6. **Skyline removal:** Why can a plain binary heap not be used directly, and what are the two standard fixes?

---

## 🏢 Company Focus

The companies that ask this lecture's problems most often, with the problems to start from:

| Company       | Problems to Prioritise                                                                                                                                                                                                                                                                                                                                                                             |
| ------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| **Amazon**    | [Determine if Two Events Have Conflict](https://leetcode.com/problems/determine-if-two-events-have-conflict/), [Range Addition II](https://leetcode.com/problems/range-addition-ii/), [Rectangle Area II](https://leetcode.com/problems/rectangle-area-ii/), [Maximum Length of Pair Chain](https://leetcode.com/problems/maximum-length-of-pair-chain/)                                           |
| **Google**    | [My Calendar II](https://leetcode.com/problems/my-calendar-ii/), [Remove Covered Intervals](https://leetcode.com/problems/remove-covered-intervals/), [Two Best Non-Overlapping Events](https://leetcode.com/problems/two-best-non-overlapping-events/), [Video Stitching](https://leetcode.com/problems/video-stitching/)                                                                         |
| **Meta**      | [Maximum Profit in Job Scheduling](https://leetcode.com/problems/maximum-profit-in-job-scheduling/), [The Skyline Problem](https://leetcode.com/problems/the-skyline-problem/), [Exclusive Time of Functions](https://leetcode.com/problems/exclusive-time-of-functions/), [Minimum Number of Arrows to Burst Balloons](https://leetcode.com/problems/minimum-number-of-arrows-to-burst-balloons/) |
| **Microsoft** | [Maximum Number of Events That Can Be Attended](https://leetcode.com/problems/maximum-number-of-events-that-can-be-attended/), [Exclusive Time of Functions](https://leetcode.com/problems/exclusive-time-of-functions/)                                                                                                                                                                           |
| **Adobe**     | [Number of Students Doing Homework at a Given Time](https://leetcode.com/problems/number-of-students-doing-homework-at-a-given-time/)                                                                                                                                                                                                                                                              |

---

## ✅ Completion Checklist

- [ ] All 5 Easy problems solved
- [ ] All 10 Medium problems solved
- [ ] All 3 Hard problems attempted
- [ ] Every complexity exercise answered before checking
- [ ] Self-assessment completed without looking at the notes
- [ ] All 6 conceptual questions answered out loud
- [ ] I can convert any interval problem into events and sweep them
- [ ] I can say which of sort-by-start, sort-by-end and event-sweep a new problem needs

---

**← [Lecture 27 · Monotonic Stack & Queue](../Lecture27/Assignment.md)** &nbsp;·&nbsp; **[Lecture 29 · Greedy Algorithms](../Lecture29/Assignment.md) →**
