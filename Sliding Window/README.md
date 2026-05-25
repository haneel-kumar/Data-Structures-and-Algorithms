# Pattern 01 · Sliding Window

> **Interactive visualizations** for every problem in the Sliding Window pattern.  
> Each link opens a step-by-step animated page — use **Play / Step** controls to watch the algorithm run.

---

## What is the Sliding Window pattern?

Instead of re-computing a result from scratch for every sub-array or sub-string, a sliding window **reuses** the previous result by adding one element on the right and removing one on the left. This reduces many O(N·K) brute-force solutions down to **O(N)**.

Two variants appear below:

| Variant | Window size | Typical trigger |
|---|---|---|
| **Fixed** | Constant (= K or pattern length) | "subarray / substring of size K" |
| **Variable** | Expands & shrinks dynamically | "smallest / longest … satisfying condition" |

---

## Problems

### 🔷 Fixed Window

#### 1. Find Averages of Sub Arrays
Given an array, find the **average of each subarray of size K**.  
Brute force recomputes each sum from scratch — sliding window carries the running sum forward.

- 🔗 [LeetCode 643 – Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/maximum-average-subarray-i.html)

---

#### 2. Maximum Sum Subarray of Size K
Given an array of positive numbers and a positive number K, find the **maximum sum of any contiguous subarray of size K**.

- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/largest-subarray-length-k.html)

---

### 🔶 Variable Window — Sum / Count

#### 3. Smallest Subarray with a Given Sum
Given an array of positive numbers and a positive number S, find the **length of the smallest contiguous subarray whose sum is ≥ S**.

- 🔗 [LeetCode 209 – Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/minimum-size-subarray-sum.html)

---

### 🔶 Variable Window — Character Frequency

#### 4. Longest Substring with K Distinct Characters
Given a string, find the **length of the longest substring with no more than K distinct characters**.

- 🔗 [LeetCode 340 – Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/longest-substring-with-at-most-k-distinct-characters.html)

---

#### 5. Fruits into Baskets
Given a row of fruit trees where each tree produces one type of fruit, find the **length of the longest subarray you can pick with only 2 baskets** (one fruit type per basket). This is identical to K Distinct Characters with K = 2.

- 🔗 [LeetCode 904 – Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/fruit-into-baskets.html)

---

#### 6. Longest Substring with at Most 2 Distinct Characters
Given a string, find the **length of the longest substring with at most 2 distinct characters**. A focused look at the K = 2 case using an index map for O(1) jumps.

- 🔗 [LeetCode 159 – Longest Substring with At Most Two Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-two-distinct-characters/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/longest-substring-with-at-most-two-distinct-characters.html)

---

#### 7. No-repeat Substring
Given a string, find the **length of the longest substring with no repeating characters**.  
Key insight: use a character → last-seen-index map to **jump** the window start instead of shrinking it one step at a time.

- 🔗 [LeetCode 3 – Longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/longest-substring-without-repeating-characters.html)

---

#### 8. Longest Substring with Same Letters after Replacement
Given a string and a number K, find the **length of the longest substring containing the same letter after replacing at most K characters**.  
Key insight: `windowSize − maxRepeatLetterCount ≤ K`. The `maxRepeatLetterCount` high-water mark never decrements.

- 🔗 [LeetCode 424 – Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/longest-repeating-character-replacement.html)

---

#### 9. Longest Subarray of 1s after Replacement
Given a binary array and a number K, find the **length of the longest subarray of 1s after replacing at most K 0s**.  
Same formula as above but `maxOnesCount` *does* decrement when a 1 leaves — unlike the char-replacement variant.

- 🔗 [LeetCode 1004 – Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/max-consecutive-ones-iii.html)

---

### 🔷 Fixed Window — Anagram / Permutation

#### 10. Permutation in a String
Given a string and a pattern, find out if the string **contains any permutation of the pattern**.  
Window size is fixed at `pattern.length`. An `isMatch` counter tracks how many distinct pattern characters have been fully satisfied.

- 🔗 [LeetCode 567 – Permutation in String](https://leetcode.com/problems/permutation-in-string/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/permutation-in-string.html)

---

#### 11. String Anagrams
Given a string and a pattern, find **all starting indices of substrings that are anagrams of the pattern**.  
Same algorithm as Permutation in String, but instead of returning `true` on the first match, every match position is pushed to a results list.

- 🔗 [LeetCode 438 – Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/find-all-anagrams-in-a-string.html)

---

### 🔴 Advanced Variable Window

#### 12. Smallest Window containing Substring
Given a string and a pattern, find the **smallest substring that contains all characters of the pattern** (characters may appear in any order and the window may have extras).  
Key difference from Permutation: `matched` counts total instances (= `pattern.length`), not distinct chars. Redundant extra copies (freq < 0) can be shrunk past without breaking the match.

- 🔗 [LeetCode 76 – Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/minimum-window-substring.html)

---

#### 13. Words Concatenation
Given a string and a list of words (all the same length), find **all starting indices of substrings that are a concatenation of all the given words exactly once**.  
This is the only problem here that uses **two HashMaps** (`wordFreq` + `wordsSeen`) and a nested loop — making it O(N × M × wordLen) rather than O(N).

- 🔗 [LeetCode 30 – Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)
- ▶ [Interactive Visualization](https://haneel-kumar.github.io/Data-Structures-and-Algorithms/Sliding%20Window/substring-with-concatenation-of-all-words.html)

---

## Pattern Summary

```
Fixed window (size K or pattern.length)
├── Find Averages          →  running sum ÷ K
├── Max Sum Subarray       →  track max while sliding
├── Permutation in String  →  isMatch counter, fixed size = pattern.length
└── String Anagrams        →  same + collect all indices

Variable window
├── Sum-based
│   └── Smallest Subarray ≥ S     →  expand right, shrink left while sum ≥ S
└── Char frequency
    ├── K Distinct / Fruits / 2-Distinct  →  HashMap char→count, shrink when distinct > K
    ├── No-repeat Substring               →  index map char→lastIdx, O(1) jump
    ├── Char Replacement (LC 424)         →  windowSize − maxRepeat ≤ K (never decrement maxRepeat)
    └── Ones Replacement (LC 1004)        →  same formula, maxOnesCount DOES decrement

Advanced
├── Min Window Substring  →  matched = pattern.length, redundant copies (freq<0) safe to shrink
└── Words Concatenation   →  nested loop, wordFreq + wordsSeen, O(N·M·wordLen)
```
