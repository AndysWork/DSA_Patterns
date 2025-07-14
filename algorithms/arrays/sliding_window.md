## 1. **What is the Sliding Window Pattern?**

The **Sliding Window** pattern is a method to process a subset (window) of a sequence (array/string) at a time, then move ("slide") this window across the sequence to solve a problem efficiently (usually in O(n) time).

**Key idea:**
Instead of using nested loops to process all subarrays/substrings (which is O(n²)), maintain a window—defined by start and end indices—that moves forward in the sequence, updating results as you go.

---

## 2. **When to Use the Sliding Window Pattern**

* **Contiguous subarray/substrings:** Find sum, max, min, length, or any property for all subarrays of a fixed or variable size.
* **Problems with phrases like:**

  * “longest/shortest subarray/substring…”
  * “maximum sum/minimum length…”
  * “all windows of size k…”
  * “find/count substrings with property X…”

**Classic use-cases:**

* Maximum/minimum sum of subarray of size *k*.
* Longest substring with K distinct characters.
* Smallest window with all required characters.

---

## 3. **Types of Sliding Window Problems**

### a) **Fixed Size Window**

The window size is constant, usually for problems like “max sum of any subarray of size k.”

#### **Example Problem**

**Maximum Sum Subarray of Size K**

* LeetCode: [Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/)
* GfG: [Max Sum Subarray of Size K](https://www.geeksforgeeks.org/find-maximum-minimum-sum-subarray-size-k/)

#### **Approach (Python)**

```python
def max_sum_subarray_k(nums, k):
    max_sum = cur_sum = sum(nums[:k])
    for i in range(k, len(nums)):
        cur_sum += nums[i] - nums[i - k]
        max_sum = max(max_sum, cur_sum)
    return max_sum
```

---

### b) **Variable Size Window**

The window expands and contracts to meet a condition.
Common for “longest/shortest substring with at most/at least K property.”

#### **Example Problem**

**Longest Substring Without Repeating Characters**

* LeetCode: [Link](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

#### **Approach (Python)**

```python
def lengthOfLongestSubstring(s):
    char_index = {}
    left = result = 0
    for right, ch in enumerate(s):
        if ch in char_index and char_index[ch] >= left:
            left = char_index[ch] + 1
        char_index[ch] = right
        result = max(result, right - left + 1)
    return result
```

---

## 4. **How to Master Sliding Window Problems**

### **Step-by-Step Mastery Guide**

#### **Step 1: Understand the Two Variants**

* **Fixed window:** Sum/count in every window of size k.
* **Variable window:** Expand/shrink window to maintain constraints (at most/at least K distinct elements, etc).

#### **Step 2: Learn the “Template”**

**Fixed Size Window Template:**

```python
window_sum = sum(nums[:k])
for i in range(k, len(nums)):
    window_sum += nums[i] - nums[i - k]
    # Update result
```

**Variable Size Window Template:**

```python
left = 0
for right in range(len(nums)):
    # Expand window by moving right
    # ... (update counts, state)
    while <window_invalid_condition>:
        # Shrink window from left
        left += 1
    # Update result if needed
```

#### **Step 3: Practice Common Patterns**

* **Max/Min Sum/Avg of Size K**
* **Longest Substring/Window with K Unique Characters**
* **Smallest Window Containing All Chars**
* **Longest Subarray with Sum at Most/Exactly K**
* **Number of Subarrays with Property X**

#### **Step 4: Recognize When to Use Sliding Window**

* If you’re dealing with *contiguous* sections and need to optimize from brute force O(n²) to O(n).
* If adding the next element (expanding window) and/or removing the first element (shrinking window) can be managed in O(1) or O(log n) (e.g., with hash maps, counters, deques).

#### **Step 5: Advanced Problems**

* **Deques for Min/Max in window** ([Sliding Window Maximum](https://leetcode.com/problems/sliding-window-maximum/))
* **Hashmaps for counts or tracking frequencies**
* **Multiple constraints:** Longest/Shortest substring with *exactly* K distinct, etc.

---

## 5. **Essential Problems to Practice (with links)**

* [Maximum Sum Subarray of Size K (GfG)](https://www.geeksforgeeks.org/find-maximum-minimum-sum-subarray-size-k/)
* [Longest Substring Without Repeating Characters (LeetCode)](https://leetcode.com/problems/longest-substring-without-repeating-characters/)
* [Longest Substring with At Most K Distinct Characters (LeetCode)](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)
* [Minimum Size Subarray Sum (LeetCode)](https://leetcode.com/problems/minimum-size-subarray-sum/)
* [Sliding Window Maximum (LeetCode)](https://leetcode.com/problems/sliding-window-maximum/)
* [Smallest Window in a String containing all Characters of another String (GfG)](https://www.geeksforgeeks.org/smallest-window-contains-characters-string/)

---

## 6. **Pro Tips for Mastery**

* **Draw out examples** for each window move.
* **Always track what’s inside the window (sum, counts, set/map of characters, etc).**
* **Ask yourself:** What is the invariant for my window?
* **Practice both types** (fixed and variable) and understand when to shrink/expand.
* **Review solutions in multiple languages** (Python, JS, C#).

---

**Summary Table of Key Problems:**

| Pattern                  | Problem Example                                      | LC Link                                                                                             | GfG Link                                                                                           |
| ------------------------ | ---------------------------------------------------- | --------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------- |
| Fixed Size Window        | Maximum Sum Subarray of Size K                       | [LeetCode 643](https://leetcode.com/problems/maximum-average-subarray-i/)                           | [GfG](https://www.geeksforgeeks.org/find-maximum-minimum-sum-subarray-size-k/)                     |
| Variable Size Window     | Longest Substring Without Repeating Characters       | [LeetCode 3](https://leetcode.com/problems/longest-substring-without-repeating-characters/)         | [GfG](https://www.geeksforgeeks.org/length-of-the-longest-substring-without-repeating-characters/) |
| Variable, with Frequency | Longest Substring with At Most K Distinct Characters | [LeetCode 340](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/) |                                                                                                    |
| Shrinking to Condition   | Minimum Size Subarray Sum                            | [LeetCode 209](https://leetcode.com/problems/minimum-size-subarray-sum/)                            | [GfG](https://www.geeksforgeeks.org/minimum-length-subarray-sum-greater-given-value/)              |
| Deque/Max in Window      | Sliding Window Maximum                               | [LeetCode 239](https://leetcode.com/problems/sliding-window-maximum/)                               | [GfG](https://www.geeksforgeeks.org/sliding-window-maximum-maximum-of-all-subarrays-of-size-k/)    |

---

## 7. **Summary**

* **Sliding Window is about maintaining a dynamic window over your data.**
* **Practice both fixed-size and variable-size patterns.**
* **Templates are key – adapt them to problem variations.**
* **Focus on optimal O(n) solutions using window logic.**
* **Solve a variety of window problems to gain confidence.**

---

# 🚀 Sliding Window Pattern: Templates in JS & C\#

---

## 1. **Fixed Size Sliding Window Template**

**Scenario:** Find sum/max/min/etc. for all windows of size `k`.

### **JavaScript**

```js
function maxSumSubarrayK(nums, k) {
    let maxSum = 0, windowSum = 0;
    for (let i = 0; i < k; i++) windowSum += nums[i];
    maxSum = windowSum;
    for (let i = k; i < nums.length; i++) {
        windowSum += nums[i] - nums[i - k];
        maxSum = Math.max(maxSum, windowSum);
    }
    return maxSum;
}
```

### **C#**

```csharp
int MaxSumSubarrayK(int[] nums, int k) {
    int maxSum = 0, windowSum = 0;
    for (int i = 0; i < k; i++) windowSum += nums[i];
    maxSum = windowSum;
    for (int i = k; i < nums.Length; i++) {
        windowSum += nums[i] - nums[i - k];
        maxSum = Math.Max(maxSum, windowSum);
    }
    return maxSum;
}
```

---

## 2. **Variable Size Sliding Window Template**

**Scenario:** Expand and shrink window to meet a condition (e.g., "at most K distinct", "sum ≥ target", etc.)

### **JavaScript**

```js
function minSubArrayLen(target, nums) {
    let left = 0, sum = 0, minLen = Infinity;
    for (let right = 0; right < nums.length; right++) {
        sum += nums[right];
        while (sum >= target) {
            minLen = Math.min(minLen, right - left + 1);
            sum -= nums[left++];
        }
    }
    return minLen === Infinity ? 0 : minLen;
}
```

### **C#**

```csharp
int MinSubArrayLen(int target, int[] nums) {
    int left = 0, sum = 0, minLen = int.MaxValue;
    for (int right = 0; right < nums.Length; right++) {
        sum += nums[right];
        while (sum >= target) {
            minLen = Math.Min(minLen, right - left + 1);
            sum -= nums[left++];
        }
    }
    return minLen == int.MaxValue ? 0 : minLen;
}
```

---

## 3. **Sliding Window with Hash Map (for frequencies/unique items)**

### **JavaScript**

```js
function lengthOfLongestSubstring(s) {
    let map = {}, maxLen = 0, left = 0;
    for (let right = 0; right < s.length; right++) {
        if (map[s[right]] !== undefined && map[s[right]] >= left)
            left = map[s[right]] + 1;
        map[s[right]] = right;
        maxLen = Math.max(maxLen, right - left + 1);
    }
    return maxLen;
}
```

### **C#**

```csharp
int LengthOfLongestSubstring(string s) {
    var map = new Dictionary<char, int>();
    int maxLen = 0, left = 0;
    for (int right = 0; right < s.Length; right++) {
        if (map.ContainsKey(s[right]) && map[s[right]] >= left)
            left = map[s[right]] + 1;
        map[s[right]] = right;
        maxLen = Math.Max(maxLen, right - left + 1);
    }
    return maxLen;
}
```

---

# 🏆 **Advanced Sliding Window Problems Set**

| **Pattern**                     | **Problem Name**                                                          | **LeetCode**                                                                                                               | **GeeksforGeeks**                                                                                                                             |
| ------------------------------- | ------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| **Variable Window, Min Window** | Minimum Window Substring                                                  | [LeetCode 76](https://leetcode.com/problems/minimum-window-substring/)                                                     | [GfG: Smallest window containing all chars](https://www.geeksforgeeks.org/smallest-window-contains-characters-string/)                        |
| **Window + Hash Map**           | Longest Substring with At Most K Distinct Characters                      | [LeetCode 340](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)                        |                                                                                                                                               |
| **Window, Multiple Conditions** | Fruits into Baskets (Longest Subarray with 2 distinct elements)           | [LeetCode 904](https://leetcode.com/problems/fruit-into-baskets/)                                                          | [GfG: Longest Subarray with at most two distinct elements](https://www.geeksforgeeks.org/longest-subarray-with-atmost-two-distinct-elements/) |
| **Deque Optimization**          | Sliding Window Maximum                                                    | [LeetCode 239](https://leetcode.com/problems/sliding-window-maximum/)                                                      | [GfG: Sliding window max](https://www.geeksforgeeks.org/sliding-window-maximum-maximum-of-all-subarrays-of-size-k/)                           |
| **Sum Variation**               | Subarrays with K Different Integers (at most/exactly K distinct elements) | [LeetCode 992](https://leetcode.com/problems/subarrays-with-k-different-integers/)                                         |                                                                                                                                               |
| **Unique Counter**              | Count Number of Nice Subarrays (subarrays with exactly K odd numbers)     | [LeetCode 1248](https://leetcode.com/problems/count-number-of-nice-subarrays/)                                             |                                                                                                                                               |
| **Multi-Pointer/Generalized**   | Longest Subarray with Absolute Diff Less Than or Equal to Limit           | [LeetCode 1438](https://leetcode.com/problems/longest-continuous-subarray-with-absolute-diff-less-than-or-equal-to-limit/) |                                                                                                                                               |
| **String Variant**              | Permutation in String (Check if s2 contains a permutation of s1)          | [LeetCode 567](https://leetcode.com/problems/permutation-in-string/)                                                       | [GfG: String permutation as substring](https://www.geeksforgeeks.org/find-permutation-string-string/)                                         |
| **Binary Array**                | Max Consecutive Ones III (replace up to K zeros with ones)                | [LeetCode 1004](https://leetcode.com/problems/max-consecutive-ones-iii/)                                                   |                                                                                                                                               |
| **Window with Counter**         | Longest Repeating Character Replacement                                   | [LeetCode 424](https://leetcode.com/problems/longest-repeating-character-replacement/)                                     | [GfG: Longest substring with same letters after K changes](https://www.geeksforgeeks.org/longest-substring-contains-1-letter-changed/)        |

---

# ⭐ **How to Master Advanced Sliding Window Problems**

1. **Always identify:**

   * What expands the window?
   * When/why do you need to shrink it?
   * What do you track inside (counts, sets, min/max, etc.)?
2. **For frequency/count constraints:** Use a hash map/dictionary.
3. **For “max in window” types:** Use a deque for O(1) min/max tracking.
4. **For “at most K” vs. “exactly K”:**

   * “Exactly K” = (at most K) - (at most K-1)
5. **Draw/test your algorithm with small examples.**
6. **Implement the general template, adapt based on what you’re tracking.**


