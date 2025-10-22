<div align="right">
<details>
<summary><b>📅 Navigate Days</b></summary>

- [Day 1](#day-1)
- [Day 2](#day-2)
- [Day 3](#day-3)
- [Day 4](#day-4)
- [Day 5](#day-5)
- [Day 6](#day-6)
- [Day 7](#day-7)
- [Day 8](#day-8)
- [Day 9](#day-9)
- [Day 10](#day-10)
- [Day 11](#day-11)
- [Day 12](#day-12)
- [Day 13](#day-13)
- [Day 14](#day-14)
- [Day 15](#day-15)

</details>
</div>

## Day 1
# 🚀 50 Days of LeetCode — Day 1

Welcome to **Day 1** of my #50DaysOfCode challenge!  
Today’s focus was on problem-solving, logic building, and deepening my understanding of **Data Structures & Algorithms** through five LeetCode problems.

---

## 🧩 Problem 1 — Successful Pairs of Spells and Potions  
**LeetCode 2300 | Medium**

### 🔍 Problem Description  
You are given two integer arrays `spells` and `potions` and an integer `success`.  
A pair `(spell, potion)` is **successful** if `spell * potion >= success`.  
For each spell, return the number of potions that make it successful.

### 💡 Approach  
- Sort the `potions` array.  
- For each spell, use **binary search** to find the first potion that meets or exceeds the success threshold.  
- Count all potions from that point onward.  
- Time complexity: `O((m + n) log n)`.

### 💻 Code
```java
class Solution {
    public int[] successfulPairs(int[] spells, int[] potions, long success) {
        Arrays.sort(potions);
        int n = potions.length;
        int[] result = new int[spells.length];
        
        for (int i = 0; i < spells.length; i++) {
            int left = 0, right = n - 1, index = n;
            while (left <= right) {
                int mid = left + (right - left) / 2;
                if ((long) spells[i] * potions[mid] >= success) {
                    index = mid;
                    right = mid - 1;
                } else {
                    left = mid + 1;
                }
            }
            result[i] = n - index;
        }
        return result;
    }
}
```
---

## 🧩 Problem 2 — Water Bottles  
**LeetCode 1518 | Easy**

### 🔍 Problem Description  
You have `numBottles` full water bottles and an exchange rate `numExchange`.  
You can drink one bottle at a time and exchange empty bottles for new full ones.  
Find the **maximum number of bottles you can drink**.

### 💡 Approach  
- Keep track of total bottles drunk and empty bottles.  
- While empty bottles ≥ `numExchange`, exchange them for full bottles.  
- Add the newly acquired full bottles to the total and update empty bottles accordingly.

### 💻 Code
```java
class Solution {
    public int numWaterBottles(int numBottles, int numExchange) {
        int total = numBottles;
        int empty = numBottles;
        while (empty >= numExchange) {
            int newBottles = empty / numExchange;
            total += newBottles;
            empty = newBottles + empty % numExchange;
        }
        return total;
    }
}

```
---

## 🧩 Problem 3 — Two Sum  
**LeetCode 1 | Easy**

### 🔍 Problem Description  
Given an array of integers `nums` and an integer `target`,  
return indices of the two numbers such that they add up to the target.

### 💡 Approach  
- Use a **HashMap** to store each element and its index.  
- For each element, check if `target - nums[i]` already exists in the map.  
- Return indices when found.  
- Time complexity: `O(n)`.

### 💻 Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        return new int[] {};
    }
}
```
---

## 🧩 Problem 3 — Two Sum  
**LeetCode 1 | Easy**

### 🔍 Problem Description  
Given an array of integers `nums` and an integer `target`,  
return indices of the two numbers such that they add up to the target.

### 💡 Approach  
- Use a **HashMap** to store each element and its index.  
- For each element, check if `target - nums[i]` already exists in the map.  
- Return indices when found.  
- Time complexity: `O(n)`.

### 💻 Code
```java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<>();
        for (int i = 0; i < nums.length; i++) {
            int complement = target - nums[i];
            if (map.containsKey(complement)) {
                return new int[] { map.get(complement), i };
            }
            map.put(nums[i], i);
        }
        return new int[] {};
    }
}
```
---

## 🧩 Problem 5 — Longest Substring Without Repeating Characters  
**LeetCode 3 | Medium**

### 🔍 Problem Description  
Given a string `s`, find the length of the longest substring without duplicate characters.

### 💡 Approach  
- Use a **sliding window** with a `HashSet` to track characters in the current window.  
- Move the right pointer until a duplicate is found, then move the left pointer to remove the duplicate.  
- Keep updating the maximum length found.  
- Time complexity: `O(n)`.

### 💻 Code
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        Set<Character> set = new HashSet<>();
        int left = 0, maxLen = 0;
        
        for (int right = 0; right < s.length(); right++) {
            while (set.contains(s.charAt(right))) {
                set.remove(s.charAt(left));
                left++;
            }
            set.add(s.charAt(right));
            maxLen = Math.max(maxLen, right - left + 1);
        }
        return maxLen;
    }
}
```
---

### 🎯 Conclusion — Day 1  
Day 1 of #50DaysOfCode was a great start!  
Solved 5 diverse problems, strengthening my skills in binary search, hashing, linked lists, and sliding window techniques.  
Excited to keep building momentum and learning more each day! 🚀

---

## Day 2
# 🚀 50 Days of LeetCode — Day 2

Welcome to **Day 2** of my #50DaysOfCode challenge!  
Today’s focus was on advanced problem-solving with **dynamic programming** and **optimization techniques**.

---

## 🧩 Problem 1 — Find the Minimum Amount of Time to Brew Potions  
**LeetCode 3494 | Medium**

### 🔍 Problem Description  
You are given two integer arrays `skill` and `mana`, representing `n` wizards and `m` potions respectively.  
Each potion must pass through all wizards sequentially.  
Time taken by wizard `i` on potion `j` is `skill[i] * mana[j]`.  
Find the **minimum time required** to brew all potions.

### 💡 Approach  
- Use **prefix sums** to store brewing times for each potion.  
- Maintain a `prev` array to track the cumulative time taken for potions.  
- For each potion, compute the earliest start time considering synchronization constraints.  
- Swap arrays to optimize space usage.  
- Time complexity: `O(n × m)`.

### 💻 Code
```java
import java.io.*;

class Solution {
    public long minTime(int[] skill, int[] mana) {
        int n = skill.length;
        int m = mana.length;
        
        long[] prev = new long[n + 1];
        long[] curr = new long[n + 1];
        
        // First potion
        long sum = 0;
        for (int i = 0; i < n; i++) {
            sum += (long) skill[i] * mana[0];
            prev[i + 1] = sum;
        }
        
        long prevStart = 0;
        long result = prev[n];
        
        for (int j = 1; j < m; j++) {
            // Compute current prefix inline
            sum = 0;
            for (int i = 0; i < n; i++) {
                sum += (long) skill[i] * mana[j];
                curr[i + 1] = sum;
            }
            
            // Find minimum start time
            long minStart = prevStart + (long) skill[0] * mana[j - 1];
            
            for (int i = 0, end = n - 1; i < end; i++) {
                long constraint = prevStart + prev[i + 2] - curr[i + 1];
                if (constraint > minStart) minStart = constraint;
            }
            
            result = minStart + curr[n];
            prevStart = minStart;
            
            // Swap
            long[] temp = prev; prev = curr; curr = temp;
        }
        
        return result;
    }
}

public class Main {
    public static void main(String[] args) throws IOException {
        StreamTokenizer in = new StreamTokenizer(new BufferedReader(new InputStreamReader(System.in), 65536));
        StringBuilder out = new StringBuilder();
        
        in.nextToken();
        int testCases = (int) in.nval;
        
        Solution sol = new Solution();
        
        while (testCases-- > 0) {
            in.nextToken();
            int n = (int) in.nval;
            int[] skill = new int[n];
            for (int i = 0; i < n; i++) {
                in.nextToken();
                skill[i] = (int) in.nval;
            }
            
            in.nextToken();
            int m = (int) in.nval;
            int[] mana = new int[m];
            for (int i = 0; i < m; i++) {
                in.nextToken();
                mana[i] = (int) in.nval;
            }
            
            out.append(sol.minTime(skill, mana)).append('\n');
        }
        
        System.out.print(out);
    }
}
```

## 🧩 Problem 2 — Median of Two Sorted Arrays  
**LeetCode 4 | Hard**

### 🔍 Problem Description  
Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively,  
return the **median** of the two sorted arrays.  
The overall run time complexity should be **O(log (m + n))**.

### 💡 Approach  
- Always perform **binary search** on the smaller array to minimize complexity.  
- Partition both arrays so that left partitions contain smaller half of the numbers and right partitions contain larger half.  
- Ensure `maxLeftX <= minRightY` and `maxLeftY <= minRightX` to satisfy median condition.  
- Time complexity: `O(log(min(m, n)))`.

### 💻 Code
```java
public class Solution {
    public double findMedianSortedArrays(int[] nums1, int[] nums2) {
        if (nums1.length > nums2.length) {
            return findMedianSortedArrays(nums2, nums1); // Always binary search smaller array
        }

        int m = nums1.length;
        int n = nums2.length;
        int low = 0, high = m;

        while (low <= high) {
            int partitionX = (low + high) / 2;
            int partitionY = (m + n + 1) / 2 - partitionX;

            int maxLeftX = (partitionX == 0) ? Integer.MIN_VALUE : nums1[partitionX - 1];
            int minRightX = (partitionX == m) ? Integer.MAX_VALUE : nums1[partitionX];

            int maxLeftY = (partitionY == 0) ? Integer.MIN_VALUE : nums2[partitionY - 1];
            int minRightY = (partitionY == n) ? Integer.MAX_VALUE : nums2[partitionY];

            if (maxLeftX <= minRightY && maxLeftY <= minRightX) {
                if ((m + n) % 2 == 0) {
                    return (Math.max(maxLeftX, maxLeftY) + Math.min(minRightX, minRightY)) / 2.0;
                } else {
                    return Math.max(maxLeftX, maxLeftY);
                }
            } else if (maxLeftX > minRightY) {
                high = partitionX - 1; // Move left
            } else {
                low = partitionX + 1; // Move right
            }
        }

        throw new IllegalArgumentException("Input arrays are not sorted.");
    }
}
```

## 🧩 Problem 3 — Longest Palindromic Substring  
**LeetCode 5 | Medium**

### 🔍 Problem Description  
Given a string `s`, return the **longest palindromic substring** in `s`.

### 💡 Approach  
- Use **expand around center** technique.  
- Palindrome centers can be single character (odd length) or two characters (even length).  
- Expand around each possible center and keep track of the longest palindrome found.  
- Time complexity: `O(n^2)`, Space complexity: `O(1)`.

### 💻 Code
```java
class Solution {
    public String longestPalindrome(String s) {
        if (s == null || s.length() < 1) return "";

        int start = 0, end = 0;

        for (int i = 0; i < s.length(); i++) {
            int len1 = expandAroundCenter(s, i, i);     // Odd length
            int len2 = expandAroundCenter(s, i, i + 1); // Even length
            int len = Math.max(len1, len2);

            if (len > end - start) {
                start = i - (len - 1) / 2;
                end = i + len / 2;
            }
        }

        return s.substring(start, end + 1);
    }

    private int expandAroundCenter(String s, int left, int right) {
        while (left >= 0 && right < s.length() && s.charAt(left) == s.charAt(right)) {
            left--;
            right++;
        }
        return right - left - 1; // Length of palindrome
    }
}
```

## 🧩 Problem 4 — Zigzag Conversion  
**LeetCode 6 | Medium**

### 🔍 Problem Description  
The string `"PAYPALISHIRING"` is written in a zigzag pattern on a given number of rows like this:  

P     I    N
A   L S  I G
Y A   H R
P     I

Then read line by line: `"PAHNAPLSIIGYIR"`  

Write code that converts a given string into its zigzag form given a number of rows.

### 💡 Approach  
- Use a cycle length of `2 * numRows - 2`.  
- Traverse each row, collecting characters at appropriate indices.  
- For middle rows, add the extra characters that fall in between cycles.  
- Time complexity: `O(n)`.

### 💻 Code
```java
class Solution {
    public String convert(String s, int numRows) {
        if (numRows == 1 || s.length() <= numRows) return s;

        int len = s.length();
        char[] result = new char[len];
        int idx = 0;
        int cycleLen = 2 * numRows - 2;

        for (int i = 0; i < numRows; i++) {
            for (int j = i; j < len; j += cycleLen) {
                result[idx++] = s.charAt(j);

                // Add middle character (not on first or last row)
                int midIdx = j + cycleLen - 2 * i;
                if (i != 0 && i != numRows - 1 && midIdx < len) {
                    result[idx++] = s.charAt(midIdx);
                }
            }
        }
        return new String(result);
    }
}
```

## 🧩 Problem 5 — Reverse Integer  
**LeetCode 7 | Medium**

### 🔍 Problem Description  
Given a signed 32-bit integer `x`, return `x` with its digits reversed.  
If reversing `x` causes the value to go outside the signed 32-bit integer range `[-2^31, 2^31 - 1]`, return `0`.

You must assume the environment does not allow you to store 64-bit integers.

#### Examples:
- **Example 1:**  
  Input: `x = 123`  
  Output: `321`

- **Example 2:**  
  Input: `x = -123`  
  Output: `-321`

- **Example 3:**  
  Input: `x = 120`  
  Output: `21`

### 💡 Approach  
- Pop the last digit of `x` using modulus operation.  
- Push it into `reversed` by multiplying `reversed` by 10 and adding the popped digit.  
- Check for overflow by reversing the operation and ensuring the result is consistent.  
- Time complexity: `O(log₁₀ n)` where `n` is the value of `x`.

### 💻 Code
```java
class Solution {
    public int reverse(int x) {
        int reversed = 0;

        while (x != 0) {
            int pop = x % 10;
            x /= 10;

            // Check for overflow
            int temp = reversed * 10 + pop;
            if ((temp - pop) / 10 != reversed) return 0;

            reversed = temp;
        }

        return reversed;
    }
}
```

---

### 🎯 Conclusion — Day 2  
Day 2 of #50DaysOfCode was a productive challenge!
Solved 5 diverse problems that strengthened my skills in binary search, string manipulation, array handling, and integer operations.
Each problem pushed me to think critically and optimize efficiently. Excited for Day 3! 🚀

---

## Day 3
# 🚀 50 Days of LeetCode — Day 3

Welcome to **Day 3** of my #50DaysOfCode challenge!  
Today’s focus was on advanced problem-solving with **dynamic programming** and **optimization techniques**.

---

## 🧩 Problem 1 — Taking Maximum Energy From the Mystic Dungeon  
**LeetCode 3147 | Medium**

### 🔍 Problem Description  
You are given an integer array `energy` and an integer `k`.  
Starting from any magician `i`, you absorb their energy (which can be positive or negative) and are then **teleported to magician (i + k)** repeatedly — until you move out of the array.  

You must **choose a starting point** that maximizes the **total energy gained** during this teleportation sequence.  

Return the **maximum possible energy** you can obtain. 

---

### 💭 Approach  

1. Traverse **from the end** of the array because teleportation moves forward by `k` steps.  
2. For each possible starting point within the last `k` positions, simulate the jumps backward by steps of `k`.  
3. Keep a **running sum** of energies and track the **maximum total** encountered.  
4. The result is the **maximum energy** among all possible paths.  

This approach ensures we efficiently evaluate all valid teleportation paths without redundant recomputation.  

---

### 💻 Code  
```java
class Solution {
    public int maximumEnergy(int[] energy, int k) {
        int n = energy.length;
        int maxEnergy = Integer.MIN_VALUE;
        
        for (int start = n - 1; start >= n - k && start >= 0; start--) {
            int sum = 0;
            for (int i = start; i >= 0; i -= k) {
                sum += energy[i];
                maxEnergy = Math.max(maxEnergy, sum);
            }
        }
        
        return maxEnergy;
    }
}
```

---

### 🎯 Conclusion — Day 3  
Day 3 of #50DaysOfCode was a great deep dive into optimization and simulation problems.
Solved an interesting teleportation energy problem while strengthening algorithmic thinking and efficiency techniques.
Excited to tackle more challenging problems tomorrow! 🚀

---

## Day 4
# 🚀 50 Days of LeetCode — Day 4

Welcome to **Day 4** of my #50DaysOfCode challenge!  
Today’s focus was on **Dynamic Programming** and **Greedy Optimization** — solving problems that require efficient state management and decision-making.

---

## 🧩 Problem — Taking Maximum Total Damage  
**LeetCode 3148 | Medium**

### 🔍 Problem Description  
You are given an integer array `power`, where each element represents the damage value of a spell.  
If you pick a spell with damage `x`, you **cannot** pick any spell with damage values of `x - 2`, `x - 1`, `x + 1`, or `x + 2`.  
Your goal is to **maximize the total damage** you can deal.

In other words, you must choose a subset of spells such that no two chosen spells have damage values within a difference of 2, while maximizing the sum of their total damage values.

---

### 💭 Approach  

1. **Sort and group** all spells by their damage value.  
   - Count the occurrences of each damage value and multiply to get total damage for that group.
2. Use **Dynamic Programming (DP)** where  
   - `dp[i]` = maximum damage obtainable considering all spells up to group `i`.
3. For each group `i`:
   - Either **skip** the current group (`dp[i] = dp[i-1]`)  
   - Or **take** it and add to the last compatible group (`damage[j] <= damage[i] - 3`).
4. The final answer is the last value in the `dp` array.

This method ensures optimal substructure and avoids recomputation, achieving an **O(n)** time complexity.

---

### 💻 Code  
```java
class Solution {
    public long maximumTotalDamage(int[] power) {

        Arrays.sort(power);
        
        int n = power.length;
        if (n == 0) return 0;
        
        int[] damages = new int[n];
        int[] counts = new int[n];
        int groupCount = 0;
        
        for (int i = 0; i < n; ) {
            int damage = power[i];
            int count = 0;
            while (i < n && power[i] == damage) {
                count++;
                i++;
            }
            damages[groupCount] = damage;
            counts[groupCount] = count;
            groupCount++;
        }
        
        if (groupCount == 0) return 0;
        
        long[] dp = new long[groupCount];
        dp[0] = (long) damages[0] * counts[0];
        
        int j = 0;
        
        for (int i = 1; i < groupCount; i++) {
            long totalDamage = (long) damages[i] * counts[i];
            
            dp[i] = dp[i - 1];
            
            while (j < i && damages[j] <= damages[i] - 3) {
                j++;
            }
            
            long takeValue = totalDamage;
            if (j > 0) {
                takeValue += dp[j - 1];
            }
            
            dp[i] = Math.max(dp[i], takeValue);
        }
        
        return dp[groupCount - 1];
    }
}
```

---

### 🎯 Conclusion — Day 4  
Day 4 of #50DaysOfCode was all about mastering Dynamic Programming with constraints.
This problem taught me how to efficiently combine grouping, sorting, and state optimization to handle overlapping intervals.
Each day, the logic feels more intuitive — and the grind continues! ⚔️🔥

---

## Day 5
# 🚀 50 Days of LeetCode — Day 5

Welcome to **Day 5** of my #50DaysOfCode challenge!  
Today’s focus was on **Dynamic Programming**, **Combinatorics**, and **Bit Manipulation**, diving deep into a challenging mathematical problem that combined logic with optimization.

---

## 🧩 Problem — Find Sum of Array Product of Magical Sequences  
**LeetCode 3539 | Hard**

### 🔍 Problem Description  
You are given two integers `m` and `k`, and an integer array `nums`.

A sequence `seq` is called **magical** if:  
- `seq` has a size of `m`.  
- `0 <= seq[i] < nums.length`.  
- The binary representation of `2^seq[0] + 2^seq[1] + ... + 2^seq[m - 1]` has exactly `k` set bits.  

The **array product** of this sequence is defined as:  
`prod(seq) = nums[seq[0]] * nums[seq[1]] * ... * nums[seq[m - 1]]`.  

You must return the **sum of all array products** of valid magical sequences, modulo `10^9 + 7`.

---

### 💭 Approach  

This problem blends **Dynamic Programming** with **Combinatorics** to efficiently compute valid sequences without explicitly generating all possibilities.

1. **DP State:**  
   Use recursion with memoization to track:  
   - `remM`: remaining selections  
   - `remK`: remaining set bits  
   - `idx`: current index in `nums`  
   - `carry`: accumulated carry bits  

2. **Transition Logic:**  
   For each count of selections for `nums[idx]`, calculate:  
   - The number of ways (`nCr`)  
   - The power contribution (`nums[idx]^count`)  
   - The carry propagation for new set bits  

3. **Memoization:**  
   Cache states using a string key to prevent recomputation.  

4. **Precomputations:**  
   - Precompute all powers (`powNums[i][t]`)  
   - Precompute combinations (`comb[i][j]`) using Pascal’s triangle.  

This approach efficiently navigates the combinatorial explosion and handles bit operations smartly.

---

### 💻 Code  
```java
class Solution {
    static final int MOD = 1_000_000_007;
    int m, k, n;
    long[][] powNums;
    long[][] comb;
    int[] nums;
    java.util.Map<String, Long> memo;

    public int magicalSum(int m, int k, int[] nums) {
        this.m = m;
        this.k = k;
        this.n = nums.length;
        this.nums = nums;
        this.memo = new java.util.HashMap<>();

        precomputePowers();
        precomputeCombinations();

        long ans = dp(m, k, 0, 0);
        return (int)(ans % MOD);
    }

    private long dp(int remM, int remK, int idx, int carry) {
        if (remM < 0 || remK < 0) return 0;
        if (remM == 0)
            return (remK == Integer.bitCount(carry)) ? 1 : 0;
        if (idx == n) return 0;

        String key = remM + "," + remK + "," + idx + "," + carry;
        if (memo.containsKey(key)) return memo.get(key);

        long res = 0;
        for (int count = 0; count <= remM; count++) {
            long ways = comb[remM][count];
            long val = powNums[idx][count];
            long contribution = (ways * val) % MOD;

            int newCarry = carry + count;
            int bitHere = newCarry & 1;
            int nextCarry = newCarry >> 1;

            long sub = dp(remM - count, remK - bitHere, idx + 1, nextCarry);
            if (sub != 0) {
                res = (res + sub * contribution) % MOD;
            }
        }

        memo.put(key, res);
        return res;
    }

    private void precomputePowers() {
        powNums = new long[n][m + 1];
        for (int i = 0; i < n; i++) {
            powNums[i][0] = 1;
            for (int t = 1; t <= m; t++) {
                powNums[i][t] = (powNums[i][t - 1] * nums[i]) % MOD;
            }
        }
    }

    private void precomputeCombinations() {
        comb = new long[m + 1][m + 1];
        for (int i = 0; i <= m; i++) {
            comb[i][0] = 1;
            for (int j = 1; j <= i; j++) {
                comb[i][j] = (comb[i - 1][j - 1] + comb[i - 1][j]) % MOD;
            }
        }
    }
}
```
---

### 🎯 Conclusion — Day 5  

Day 5 was a deep dive into mathematical DP and bit-level logic.
It tested my understanding of combinatorics, memoization, and bitwise operations all in one challenge!

Proud to see progress through tougher problems — the journey continues with even greater enthusiasm. 🚀
Here’s to consistent growth and sharper problem-solving!

---
## Day 6
# 🚀 50 Days of LeetCode — Day 6

Welcome to **Day 6** of my #50DaysOfCode challenge!  
Today’s focus was on **String Manipulation**, **Anagram Checking**, and **Efficient Comparison Logic** — a simple yet elegant problem that reinforced the power of clean iteration and frequency analysis.

---

## 🧩 Problem — Find Resultant Array After Removing Anagrams  
**LeetCode 2273 | Easy**

### 🔍 Problem Description  
You are given a 0-indexed string array `words`, where each element consists of lowercase English letters.  

You can perform the following operation any number of times:
- Choose an index `i` such that `0 < i < words.length` and `words[i - 1]` and `words[i]` are **anagrams**,  
  then delete `words[i]` from the array.

Return the resulting array after performing all such operations.  
The key observation is that the **order of deletion does not affect the final result**.

An **anagram** is a word formed by rearranging all letters of another word exactly once.

---

### 💭 Approach  

1. **Iterative Filtering:**  
   Iterate through the `words` array, maintaining only those that are **not anagrams** of the previous word.  

2. **Frequency Comparison:**  
   Convert each word into a frequency array of size 26 (for each lowercase letter).  
   Two words are anagrams if their frequency arrays are identical.  

3. **Optimization:**  
   - Avoid sorting each string (O(n log n)) by directly comparing character counts (O(26)).  
   - Update the “previous frequency” only when a non-anagram word is added to the result.  

This leads to an **O(n * word_length)** time complexity — highly efficient for the given constraints.

---

### 💻 Code  
```java
class Solution {
    public List<String> removeAnagrams(String[] words) {
        List<String> result = new ArrayList<>(words.length);
        result.add(words[0]);
        
        int[] prevFreq = getFrequency(words[0]);
        
        for (int i = 1; i < words.length; i++) {
            String word = words[i];
            
            // Early exit: if lengths differ, can't be anagrams
            if (word.length() != words[i - 1].length()) {
                result.add(word);
                prevFreq = getFrequency(word);
                continue;
            }
            
            int[] currFreq = getFrequency(word);
            
            if (!Arrays.equals(currFreq, prevFreq)) {
                result.add(word);
                prevFreq = currFreq;
            }
        }
        return result;
    }
    
    private int[] getFrequency(String word) {
        int[] freq = new int[26];
        int len = word.length();
        for (int i = 0; i < len; i++) {
            freq[word.charAt(i) - 'a']++;
        }
        return freq;
    }
}

```
---

### 🎯 Conclusion — Day 6  

Day 6 was all about clarity and precision in handling string-based logic.
It was a refreshing reminder that even simple problems can teach valuable lessons in clean code structure, iteration control, and efficient data comparison.

One more day, one more lesson — consistency is the real magic. 🌟
Can’t wait to take on Day 7! 🚀

---

## Day 7
# 🚀 50 Days of LeetCode — Day 7

Welcome to **Day 7** of my #50DaysOfCode challenge!  
Today’s challenge focused on **Array Traversal**, **Pattern Recognition**, and **Subarray Analysis** — a great exercise in understanding how to validate structured sequences efficiently.  

---

## 🧩 Problem — Adjacent Increasing Subarrays Detection I  
**LeetCode 3349 | Easy**

### 🔍 Problem Description  
You are given an integer array `nums` of length `n` and an integer `k`.  
Your task is to determine whether there exist **two adjacent subarrays** of length `k` such that both are **strictly increasing**.  

Formally, check if there are two subarrays starting at indices `a` and `b` (where `b = a + k`) such that:  
- Both `nums[a..a + k - 1]` and `nums[b..b + k - 1]` are strictly increasing.  

Return **true** if such subarrays exist, and **false** otherwise.  

---

### 💭 Approach  

1. **Sliding Window Traversal:**  
   Iterate through the array while checking every window of size `2 * k` to find possible pairs of adjacent increasing subarrays.  

2. **Helper Function for Validation:**  
   Define a helper method `isIncreasing()` to verify if a given range of elements is strictly increasing.  

3. **Efficient Comparison:**  
   For each valid start index `i`, check if both subarrays `[i..i+k-1]` and `[i+k..i+2k-1]` meet the increasing condition.  

4. **Early Exit:**  
   As soon as one valid pair is found, return `true` immediately to optimize runtime.  

This approach ensures clarity and efficiency with **O(n × k)** time complexity and **O(1)** space complexity.  

---

### 💻 Code
```java
import java.util.*;

class Solution {
    public boolean hasIncreasingSubarrays(List<Integer> nums, int k) {
        int n = nums.size();

        for (int i = 0; i + 2 * k <= n; i++) {
            if (isIncreasing(nums, i, i + k - 1) &&
                isIncreasing(nums, i + k, i + 2 * k - 1)) {
                return true;
            }
        }
        return false;
    }

    private boolean isIncreasing(List<Integer> nums, int start, int end) {
        for (int i = start; i < end; i++) {
            if (nums.get(i) >= nums.get(i + 1)) {
                return false;
            }
        }
        return true;
    }
}
```

---

### 🎯 Conclusion — Day 7  

Day 7 was a strong exercise in logical reasoning and structured array validation.
It emphasized breaking problems into smaller, reusable components — like the isIncreasing() helper — and understanding the balance between clarity and optimization.

Every new problem builds better intuition, stronger debugging instincts, and deeper algorithmic thinking.
On to the next challenge — Day 8, here we come! 🚀

---

## Day 8
# 🚀 50 Days of LeetCode — Day 8

Welcome to **Day 8** of my #50DaysOfCode challenge!  
Today’s focus was on **Array Analysis**, **Pattern Detection**, and **Subarray Optimization** — stepping up from Day 7 with a medium-level challenge that demanded analytical precision and clean logic.

---

## 🧩 Problem — Adjacent Increasing Subarrays Detection II  
**LeetCode 3350 | Medium**

### 🔍 Problem Description  
You are given an integer array `nums` of length `n`.  
Your task is to find the **maximum value of `k`** such that there exist **two adjacent subarrays** of length `k`, where both subarrays are **strictly increasing**.

Formally, check if there exist subarrays starting at indices `a` and `b` (where `b = a + k`) such that:  
- Both `nums[a..a + k - 1]` and `nums[b..b + k - 1]` are strictly increasing.  

Return the **maximum possible value of `k`**.

---

### 💭 Approach  

1. **Tracking Increasing Segments:**  
   Iterate through the array and calculate the lengths of consecutive increasing subarrays.

2. **Compare Adjacent Lengths:**  
   For every point where the sequence breaks, compute the overlap of two adjacent increasing segments using `Math.min(prevLen, currLen)`.

3. **Edge Handling:**  
   The final check ensures the last subarray is also considered, updating the result accordingly.

4. **Optimization Insight:**  
   The approach cleverly combines pattern tracking and comparison within a single traversal — achieving **O(n)** time complexity with **O(1)** extra space.

---

### 💻 Code
```java
import java.util.*;

class Solution {
    public int maxIncreasingSubarrays(List<Integer> nums) {
        int n = nums.size();
        int ans = 0;
        int prevLen = 0;  // Length of previous increasing subarray
        int currLen = 1;  // Length of current increasing subarray
        
        for (int i = 1; i < n; i++) {
            if (nums.get(i) > nums.get(i - 1)) {
                currLen++;
            } else {
                // Check adjacent increasing subarrays
                ans = Math.max(ans, Math.min(prevLen, currLen));
                ans = Math.max(ans, currLen / 2);
                
                prevLen = currLen;
                currLen = 1;
            }
        }
        
        // Handle the last increasing subarray
        ans = Math.max(ans, Math.min(prevLen, currLen));
        ans = Math.max(ans, currLen / 2);
        
        return ans;
    }
}
```

---

### 🎯 Conclusion — Day 8  

Day 8 took the previous problem to a deeper, more analytical level — focusing not just on detecting patterns, but on quantifying them efficiently.
It was a fun challenge that strengthened my grasp on sequence logic, pattern overlap, and single-pass optimization.

Each day adds a new layer of understanding — and today’s was about clarity through logic.
Onward to Day 9! 🚀🔥

---

## Day 9
# 🚀 50 Days of LeetCode — Day 9

Welcome to **Day 9** of my #50DaysOfCode challenge!  
Today’s focus was on **Modular Arithmetic**, **Frequency Mapping**, and **Optimized Array Transformation** — tackling a medium-level problem that tested logic precision and mathematical reasoning. 🧮⚙️

---

## 🧩 Problem — Smallest Missing Non-negative Integer After Operations  
**LeetCode 2598 | Medium**

### 🔍 Problem Description  
You are given a 0-indexed integer array `nums` and an integer `value`.

In one operation, you can **add or subtract `value`** from any element in `nums`.  
The goal is to find the **maximum possible MEX (minimum excluded number)** of the array after performing any number of operations.

**MEX** of an array is the smallest non-negative integer not present in it.

#### Example:
**Input:**  
`nums = [1, -10, 7, 13, 6, 8]`, `value = 5`  
**Output:** `4`  

**Explanation:**  
By adding and subtracting `value` strategically, we can transform the array to make MEX = 4 — the maximum achievable.

---

### 💭 Approach  

1. **Use Modular Arithmetic:**  
   Each number can be transformed into a set of values differing by multiples of `value`.  
   Hence, `nums[i] % value` determines its *group*.

2. **Frequency Counting:**  
   Create an array `freq[value]` to count how many numbers fall into each modulo class.

3. **Determine MEX:**  
   - The smallest MEX corresponds to the first missing count pattern.  
   - For each `i`, MEX = `minFreq * value + minIdx`,  
     where `minFreq` is the smallest frequency among remainders.

This approach ensures **O(n)** time complexity and **O(value)** space — perfect for large constraints.

---

### 💻 Code
```java
class Solution {
    public int findSmallestInteger(int[] nums, int value) {
        int[] freq = new int[value];
        
        for (int i = 0, len = nums.length; i < len; i++) {
            int x = nums[i];
            int r = x % value;
            freq[r < 0 ? r + value : r]++;
        }
        
        int minFreq = freq[0];
        int minIdx = 0;
        
        for (int i = 1; i < value; i++) {
            int f = freq[i];
            if (f < minFreq) {
                minFreq = f;
                minIdx = i;
            }
        }
        return minFreq * value + minIdx;
    }
}
```

### 🎯 Conclusion — Day 9  

Day 9 pushed the boundaries of mathematical problem-solving — showing how modular arithmetic can simplify complex transformations elegantly.
This challenge reinforced the importance of pattern grouping and frequency balancing to derive efficient results.

Each day of this journey strengthens logic and boosts confidence — one MEX at a time! 💪
On to Day 10, with even more excitement ahead! 🚀✨

---

## Day 10
# 🚀 50 Days of LeetCode — Day 10

Welcome to **Day 10** of my #50DaysOfCode challenge!  
Today’s focus was on **Bitmasking**, **String Manipulation**, and **Dynamic Partitioning Optimization** — tackling a hard-level problem that required clever state tracking and optimization. ⚙️💡

---

## 🧩 Problem — Maximize the Number of Partitions After Operations  
**LeetCode 3003 | Hard**

### 🔍 Problem Description  
You are given a string `s` and an integer `k`.  

First, you are allowed to **change at most one index** in `s` to another lowercase English letter.  

After that, perform the following partitioning operation until `s` is empty:  

- Choose the **longest prefix** of `s` containing at most `k` distinct characters.  
- Delete the prefix and increase the partition count by 1.  
- Continue until the string becomes empty.  

Return the **maximum number of partitions** after optimally performing at most one change.  

#### Example 1:
**Input:** `s = "accca"`, `k = 2`  
**Output:** `3`  

**Explanation:** Change `s[2]` to `'b'` to get `"acbca"`.  
Partition prefixes of at most 2 distinct characters: `"ac"`, `"bc"`, `"a"`.  
Total partitions = 3.

#### Example 2:
**Input:** `s = "aabaab"`, `k = 3`  
**Output:** `1`  

**Explanation:** No matter which character you change, the whole string has at most 3 distinct characters.  
The longest prefix = entire string. Total partitions = 1.

---

### 💭 Approach

1. **Use Bitmasking for Tracking Characters:**  
   Represent characters seen so far as bits in an integer for fast checking and updating.

2. **Process from Right to Left:**  
   Precompute `ansr[i]` — maximum partitions starting at index `i`.  

3. **Dynamic Partitioning:**  
   Iterate from left to right while keeping track of used characters.  
   Split when `k` distinct characters are reached and update maximum partitions using previously computed suffix results.  

4. **Edge Cases:**  
   Handle cases where `k = 26` (all letters), and consider at most one character change for optimal partitioning.

This approach ensures efficient computation even for strings of length up to 10⁴.

---

### 💻 Code
```java
public class Solution {
    private static final int ALPHABET_SIZE = 'z' - 'a' + 1;

    public int maxPartitionsAfterOperations(String s, int k) {
        if (k == ALPHABET_SIZE) return 1;

        int n = s.length();
        int[] ansr = new int[n];
        int[] usedr = new int[n];
        int used = 0, cntUsed = 0, ans = 1;

        for (int i = n - 1; i >= 0; --i) {
            int ch = s.charAt(i) - 'a';
            if ((used & (1 << ch)) == 0) {
                if (cntUsed == k) {
                    cntUsed = 0;
                    used = 0;
                    ans++;
                }
                used |= (1 << ch);
                cntUsed++;
            }
            ansr[i] = ans;
            usedr[i] = used;
        }

        int ansl = 0;
        ans = ansr[0];
        int l = 0;

        while (l < n) {
            used = 0;
            cntUsed = 0;
            int usedBeforeLast = 0;
            int usedTwiceBeforeLast = 0;
            int last = -1;
            int r = l;

            while (r < n) {
                int ch = s.charAt(r) - 'a';
                if ((used & (1 << ch)) == 0) {
                    if (cntUsed == k) break;
                    usedBeforeLast = used;
                    last = r;
                    used |= (1 << ch);
                    cntUsed++;
                } else if (cntUsed < k) {
                    usedTwiceBeforeLast |= (1 << ch);
                }
                r++;
            }

            if (cntUsed == k) {
                if (last - l > Integer.bitCount(usedBeforeLast)) {
                    ans = Math.max(ans, ansl + 1 + ansr[last]);
                }
                if (last + 1 < r) {
                    if (last + 2 >= n) {
                        ans = Math.max(ans, ansl + 1 + 1);
                    } else {
                        if (Integer.bitCount(usedr[last + 2]) == k) {
                            int canUse = ((1 << ALPHABET_SIZE) - 1) & ~used & ~usedr[last + 2];
                            if (canUse > 0) {
                                ans = Math.max(ans, ansl + 1 + 1 + ansr[last + 2]);
                            } else {
                                ans = Math.max(ans, ansl + 1 + ansr[last + 2]);
                            }
                            int l1 = s.charAt(last + 1) - 'a';
                            if ((usedTwiceBeforeLast & (1 << l1)) == 0) {
                                ans = Math.max(ans, ansl + 1 + ansr[last + 1]);
                            }
                        } else {
                            ans = Math.max(ans, ansl + 1 + ansr[last + 2]);
                        }
                    }
                }
            }
            l = r;
            ansl++;
        }
        return ans;
    }
}
```

### 🎯 Conclusion — Day 10  

Day 10 was a challenging exercise in bitmasking, prefix/suffix optimization, and careful character tracking.
It strengthened my skills in transforming a complex string manipulation problem into a manageable algorithm using efficient state representation.

Every day builds deeper intuition and sharper problem-solving skills — onward to Day 11! 🚀✨

---
## Day 11
# 🚀 50 Days of LeetCode — Day 11

Welcome to **Day 11** of my #50DaysOfCode challenge!  
Today’s focus was on **Greedy Algorithms**, **Sorting Optimization**, and **Range Adjustment** — tackling a medium-level problem that balanced numerical precision with algorithmic strategy. ⚙️📊

---

## 🧩 Problem — Maximum Number of Distinct Elements After Operations  
**LeetCode 3397 | Medium**

### 🔍 Problem Description  
You are given an integer array `nums` and an integer `k`.

You are allowed to perform the following operation on each element **at most once**:

➡️ Add an integer in the range `[-k, k]` to the element.

Your goal is to return the **maximum possible number of distinct elements** in the array after performing the operations optimally.

---

#### Example 1:
**Input:**  
`nums = [1,2,2,3,3,4]`, `k = 2`  
**Output:** `6`  

**Explanation:**  
By adjusting the first four elements as `[-1, 0, 1, 2, 3, 4]`,  
we obtain six distinct numbers — the maximum achievable.

---

#### Example 2:
**Input:**  
`nums = [4,4,4,4]`, `k = 1`  
**Output:** `3`  

**Explanation:**  
Adding `-1` to `nums[0]` and `+1` to `nums[1]` makes `nums = [3, 5, 4, 4]`,  
resulting in three distinct values.

---

### 💭 Approach  

1. **Sort the Array:**  
   Sorting allows processing from smallest to largest, maintaining order for unique placement.

2. **Greedy Distinct Placement:**  
   For each element, try to shift it within its allowed range to the **lowest possible distinct value** that hasn’t been used yet.

3. **Track Next Available Number:**  
   Maintain a `next` pointer indicating the smallest unused number that can be assigned while staying within the `[-k, k]` range.

4. **Count Distincts:**  
   Increment the counter every time a new unique number is successfully assigned.

This approach ensures **O(n log n)** time complexity due to sorting and **O(1)** extra space — optimal for large input arrays.

---

### 💻 Code
```java
import java.util.Arrays;

public class Solution {
    public int maxDistinctElements(int[] nums, int k) {
        Arrays.sort(nums);
        int next = nums[0] - k + 1;
        int n = nums.length;
        int ans = 1;
        for (int i = 1; i < n; i++) {
            if (nums[i] + k < next) {
                continue;
            }
            next = Math.max(next, nums[i] - k);
            ans++;
            next++;
        }
        return ans;
    }
}
```

### 🎯 Conclusion — Day 11  

Day 11 sharpened my greedy problem-solving skills — showing how small adjustments and smart iteration can maximize distinctness and efficiency!
Learning to balance constraints while pushing boundaries made this challenge both logical and rewarding. 💡🔥

Each day continues to strengthen analytical reasoning and reinforces the joy of consistent problem-solving! 🚀✨
Here’s to more optimization and insight ahead on Day 12! 💪👨‍💻

---
## Day 12

# 🚀 50 Days of LeetCode — Day 12

Welcome to **Day 12** of my #50DaysOfCode challenge!
Today’s challenge took me into the world of **string transformations**, **modular arithmetic**, and **cyclic operations** — blending math and pattern recognition to achieve lexicographical perfection. 🔄💡

---

## 🧩 Problem — Lexicographically Smallest String After Applying Operations

**LeetCode 1625 | Medium**

### 🔍 Problem Description

You are given a numeric string `s` of even length and two integers `a` and `b`.
You can perform the following two operations any number of times and in any order:

1. **Add Operation:**
   Add `a` to all digits at **odd indices** (`0-indexed`).
   After `9`, digits cycle back to `0`.

2. **Rotate Operation:**
   Rotate the string to the right by `b` positions.

Your goal is to find the **lexicographically smallest string** achievable through any sequence of these operations.

---

#### Example 1:

**Input:**
`s = "5525"`, `a = 9`, `b = 2`
**Output:** `"2050"`

**Explanation:**
Applying a smart mix of rotations and additions leads to the smallest possible sequence:
`"5525" → "2555" → "2454" → "2353" → "5323" → "2151" → "2050"`

---

#### Example 2:

**Input:**
`s = "74"`, `a = 5`, `b = 1`
**Output:** `"24"`

**Explanation:**
Rotation and addition together create the minimal lexicographic sequence `"24"`.

---

### 💭 Approach

1. **Rotation Cycle Detection:**
   Since the string length is even, only certain rotations need checking — precisely every `gcd(b, n)` steps.

2. **Precomputation for Additions:**
   Precompute all 10 possible additions for each digit to avoid redundant calculations.

3. **Explore All Combinations:**
   For each rotation, test all possible odd-index (and even-index, if applicable) additions.

4. **Lexicographic Comparison:**
   Continuously compare generated strings and keep the smallest one.

This systematic approach ensures that all possible transformations are explored efficiently while avoiding duplicates, leading to an optimized and elegant solution. ⚙️✨

---

### 💻 Code

```java
public class Solution {
    public String findLexSmallestString(String s, int a, int b) {
        int n = s.length();
        char[] sArr = s.toCharArray();
        char[] result = sArr.clone();
        char[] temp = new char[n];
        
        int gcd = gcd(b, n);
        boolean canModifyEven = (gcd & 1) == 1;
        
        // Precompute addition results
        int[][] addTable = new int[10][10];
        for (int digit = 0; digit < 10; digit++) {
            for (int ops = 0; ops < 10; ops++) {
                addTable[digit][ops] = (digit + ops * a) % 10;
            }
        }
        
        // Try all rotation positions
        for (int rot = 0; rot < n; rot += gcd) {
            if (rot == 0) {
                System.arraycopy(sArr, 0, temp, 0, n);
            } else {
                System.arraycopy(sArr, n - rot, temp, 0, rot);
                System.arraycopy(sArr, 0, temp, rot, n - rot);
            }
            
            // Try all odd index modifications
            for (int oddOps = 0; oddOps < 10; oddOps++) {
                if (canModifyEven) {
                    // Try all even index modifications
                    for (int evenOps = 0; evenOps < 10; evenOps++) {
                        boolean isBetter = true;
                        for (int i = 0; i < n; i++) {
                            int val = (i & 1) == 1 
                                ? addTable[temp[i] - '0'][oddOps]
                                : addTable[temp[i] - '0'][evenOps];
                            
                            if (val < result[i] - '0') {
                                break;
                            } else if (val > result[i] - '0') {
                                isBetter = false;
                                break;
                            }
                        }
                        
                        if (isBetter) {
                            for (int i = 0; i < n; i++) {
                                int val = (i & 1) == 1 
                                    ? addTable[temp[i] - '0'][oddOps]
                                    : addTable[temp[i] - '0'][evenOps];
                                result[i] = (char) (val + '0');
                            }
                        }
                    }
                } else {
                    boolean isBetter = true;
                    for (int i = 0; i < n; i++) {
                        int val = (i & 1) == 1 
                            ? addTable[temp[i] - '0'][oddOps]
                            : temp[i] - '0';
                        
                        if (val < result[i] - '0') {
                            break;
                        } else if (val > result[i] - '0') {
                            isBetter = false;
                            break;
                        }
                    }
                    
                    if (isBetter) {
                        for (int i = 0; i < n; i++) {
                            int val = (i & 1) == 1 
                                ? addTable[temp[i] - '0'][oddOps]
                                : temp[i] - '0';
                            result[i] = (char) (val + '0');
                        }
                    }
                }
            }
        }
        
        return new String(result);
    }
    
    private int gcd(int a, int b) {
        while (b != 0) {
            int t = b;
            b = a % b;
            a = t;
        }
        return a;
    }
}
```

---

### 🎯 Conclusion — Day 12

Day 12 was a real **brain-twister** — combining rotation logic, modular arithmetic, and lexicographical ordering into one compact challenge! 🧠⚡
This problem reinforced how **pattern observation** and **mathematical symmetry** can drastically simplify complex problems.

Every rotation, every addition, and every comparison reminded me how deep algorithmic problem-solving truly goes. 💪
On to Day 13 — with even more logic, creativity, and code! 🚀👨‍💻

---

## Day 13

# 🚀 50 Days of LeetCode — Day 13

Welcome to **Day 13** of my #50DaysOfCode challenge!
Today’s problem may seem simple at first glance — but it’s a classic reminder that **clarity of logic** and **attention to detail** are key to solving even the most basic problems efficiently. ⚙️✨

---

## 🧩 Problem — Final Value of Variable After Performing Operations

**LeetCode 2011 | Easy**

### 🔍 Problem Description

There is a programming language with only four operations and a single variable **X**, initially equal to `0`:

* `++X` and `X++` increment the value of `X` by `1`.
* `--X` and `X--` decrement the value of `X` by `1`.

You are given an array of strings `operations`, each representing one of these operations.
Your task is to return the **final value** of `X` after performing all the operations in order.

---

#### Example 1:

**Input:**
`operations = ["--X","X++","X++"]`
**Output:**
`1`

**Explanation:**

```
Initially, X = 0  
--X → X = -1  
X++ → X = 0  
X++ → X = 1  
```

---

#### Example 2:

**Input:**
`operations = ["++X","++X","X++"]`
**Output:**
`3`

**Explanation:**

```
Initially, X = 0  
++X → X = 1  
++X → X = 2  
X++ → X = 3  
```

---

#### Example 3:

**Input:**
`operations = ["X++","++X","--X","X--"]`
**Output:**
`0`

**Explanation:**

```
Initially, X = 0  
X++ → X = 1  
++X → X = 2  
--X → X = 1  
X-- → X = 0  
```

---

### 💭 Approach

1. Initialize a variable `X` to `0`.
2. Loop through each operation in the array.
3. If the operation contains `'+'`, increment `X`. Otherwise, decrement `X`.
4. Return the final value of `X`.

This approach is **O(n)** in time complexity and requires only **O(1)** space — clean, simple, and efficient. ⚡

---

### 💻 Code

```java
class Solution {
    public int finalValueAfterOperations(String[] operations) {
        int X = 0;
        for (String op : operations) {
            // If the operation contains '+', increment; else decrement
            if (op.charAt(1) == '+') {
                X++;
            } else {
                X--;
            }
        }
        return X;
    }
}
```

---

### 🎯 Conclusion — Day 13

Day 13 brought me back to the basics — reinforcing how even **simple problems** sharpen our focus on **precision, pattern recognition, and clean code structure**. 🧠💡
This challenge was a reminder that not all problems need complex logic — sometimes, it’s about implementing the **right logic** simply and effectively.

On to **Day 14** — with more logic, learning, and leaps of progress! 🚀👨‍💻

---

## Day 14

# 🚀 50 Days of LeetCode — Day 14

Welcome to **Day 14** of my #50DaysOfCode challenge!
Today’s problem took me deeper into the realm of **range updates**, **frequency optimization**, and **difference arrays** — an elegant mix of mathematics and algorithmic precision. ⚙️📊

---

## 🧩 Problem — Maximum Frequency of an Element After Performing Operations I

**LeetCode 3346 | Medium**

### 🔍 Problem Description

You are given an integer array `nums` and two integers `k` and `numOperations`.

You must perform an operation `numOperations` times on `nums`, where in each operation you:

1. Select an index `i` that has **not been selected** in any previous operations.
2. Add an integer in the range **[-k, k]** to `nums[i]`.

Your goal is to **maximize the frequency** of any element in `nums` after performing all the operations.

---

#### Example 1:

**Input:**
`nums = [1, 4, 5]`, `k = 1`, `numOperations = 2`
**Output:**
`2`

**Explanation:**
We can achieve a maximum frequency of two by:

```
Add 0 to nums[1] → [1, 4, 5]
Add -1 to nums[2] → [1, 4, 4]
```

Now, the number 4 appears twice.

---

#### Example 2:

**Input:**
`nums = [5, 11, 20, 20]`, `k = 5`, `numOperations = 1`
**Output:**
`2`

**Explanation:**
We can add 0 to nums[1] → [5, 11, 20, 20]
Here, 20 already appears twice, so the maximum frequency is 2.

---

### 💭 Approach

1. **Range Marking via Difference Array:**
   For each number `v`, mark the range `[v - k, v + k]` in a difference array to represent all reachable values.

2. **Prefix Sum to Build Reach Array:**
   The prefix sum of the difference array gives the count of how many numbers can be transformed into each target value.

3. **Combine with Existing Frequency:**
   For each target `T`, compute the total frequency as the minimum of reachable numbers and possible operations.

4. **Maximize Frequency:**
   The maximum across all targets gives the final answer.

This approach ensures **O(n + max(nums))** efficiency, which is scalable for large input sizes. ⚡

---

### 💻 Code

```java
import java.util.Arrays;

class Solution {
    public int maxFrequency(int[] nums, int k, int numOperations) {
        int n = nums.length;
        if (n == 0) return 0;

        int maxVal = 0;
        for (int v : nums) if (v > maxVal) maxVal = v;
        int limit = maxVal + k;

        int size = limit + 1;
        int[] diff = new int[size + 1];
        int[] cnt = new int[size];

        for (int v : nums) {
            int l = v - k;
            if (l < 0) l = 0;
            int r = v + k;
            if (r > limit) r = limit;
            diff[l] += 1;
            if (r + 1 <= limit) diff[r + 1] -= 1;

            // Count exact occurrences (if within size)
            if (v >= 0 && v <= limit) cnt[v] += 1;
        }

        // Prefix sum to get reach[T]
        int[] reach = new int[size];
        int cur = 0;
        for (int i = 0; i < size; i++) {
            cur += diff[i];
            reach[i] = cur;
        }

        // Evaluate answer
        int ans = 0;
        for (int T = 0; T < size; T++) {
            int possible = Math.min(reach[T], cnt[T] + numOperations);
            if (possible > ans) ans = possible;
        }

        return ans;
    }
}
```

---

### 🎯 Conclusion — Day 14

Day 14 was all about mastering **range logic** and **frequency balancing** — learning how minor numerical shifts can create significant optimization outcomes. 🔄✨
This problem reinforced the value of **prefix sums**, **difference arrays**, and a **strategic mindset** in algorithm design.

Every challenge continues to sharpen my ability to think in patterns, reason in ranges, and implement efficiently. 💪💻
On to **Day 15**, with even more passion for clean code and clever solutions! 🚀👨‍💻

---

## Day 15

# 🚀 50 Days of LeetCode — Day 15

Welcome to **Day 15** of my #50DaysOfCode challenge!
Today’s problem took me deeper into **advanced range reasoning**, **window balancing**, and **frequency maximization with constraints** — truly a test of both logic and precision! ⚙️🔥

---

## 🧩 Problem — Maximum Frequency of an Element After Performing Operations II

**LeetCode 3347 | Hard**

### 🔍 Problem Description

You are given an integer array `nums` and two integers `k` and `numOperations`.

You must perform an operation `numOperations` times on `nums`, where in each operation you:

1. Select an index `i` that has **not been selected** in any previous operations.
2. Add an integer in the range **[-k, k]** to `nums[i]`.

Your goal is to **maximize the frequency** of any element in `nums` after performing all the operations.

---

#### Example 1:

**Input:**
`nums = [1, 4, 5]`, `k = 1`, `numOperations = 2`

**Output:**
`2`

**Explanation:**
We can achieve a maximum frequency of two by:

```
Adding 0 to nums[1] → [1, 4, 5]
Adding -1 to nums[2] → [1, 4, 4]
```

Now, the number 4 appears twice.

---

#### Example 2:

**Input:**
`nums = [5, 11, 20, 20]`, `k = 5`, `numOperations = 1`

**Output:**
`2`

**Explanation:**
Adding 0 to nums[1] keeps `[5, 11, 20, 20]`, and since 20 already appears twice, the maximum frequency remains 2.

---

### 💭 Approach

1. **Sort the Array:**
   Sorting helps to efficiently compare ranges and detect overlapping intervals.

2. **Two-Pointer Window Technique:**
   Expand and contract a sliding window to maintain valid value ranges (where `nums[r] - nums[l] <= 2 * k`).

3. **Dynamic Frequency Calculation:**
   Use two nested sweeps:

   * The first determines potential overlapping ranges.
   * The second adjusts boundaries considering the allowed operations (`numOperations`).

4. **Optimization Insight:**
   The combination of sorting and window expansion ensures the solution works in **O(n log n)**, which is optimal for constraints up to `10^5`. ⚡

---

### 💻 Code

```java
import java.util.Arrays;

public class Solution {
    public int maxFrequency(int[] nums, int k, int numOperations) {
        Arrays.sort(nums);
        int n = nums.length;
        int l = 0;
        int r = 0;
        int i = 0;
        int j = 0;
        int res = 0;
        while (i < n) {
            while (j < n && nums[j] == nums[i]) {
                j++;
            }
            while (l < i && nums[i] - nums[l] > k) {
                l++;
            }
            while (r < n && nums[r] - nums[i] <= k) {
                r++;
            }
            res = Math.max(res, Math.min(i - l + r - j, numOperations) + j - i);
            i = j;
        }
        i = 0;
        j = 0;
        while (i < n && j < n) {
            while (j < n && j - i < numOperations && nums[j] - nums[i] <= k * 2) {
                j++;
            }
            res = Math.max(res, j - i);
            i++;
        }
        return res;
    }
}
```

---

### 🎯 Conclusion — Day 15

Day 15 challenged my understanding of **range overlaps**, **sliding windows**, and **operation constraints** — blending intuition with algorithmic finesse. ⚙️💡
This problem emphasized that even the hardest challenges can be cracked with structure, logic, and consistent focus.

Each new day in this challenge sharpens not just my coding ability but also my problem-analysis mindset — a reminder that mastery is built one logic block at a time. 💻💪
On to **Day 16**, where the journey continues toward stronger problem-solving and sharper algorithms! 🚀👨‍💻

---
