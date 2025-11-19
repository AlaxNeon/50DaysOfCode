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
- [Day 16](#day-16)
- [Day 17](#day-17)
- [Day 18](#day-18)
- [Day 19](#day-19)
- [Day 20](#day-20)
- [Day 21](#day-21)
- [Day 22](#day-22)
- [Day 23](#day-23)
- [Day 24](#day-24)
- [Day 25](#day-25)
- [Day 26](#day-26)
- [Day 27](#day-27)
- [Day 28](#day-28)
- [Day 29](#day-29)
- [Day 30](#day-30)
- [Day 31](#day-31)
- [Day 32](#day-32)
- [Day 33](#day-33)
- [Day 34](#day-34)
- [Day 35](#day-35)
- [Day 36](#day-36)
- [Day 37](#day-37)
- [Day 38](#day-38)
- [Day 39](#day-39)
- [Day 40](#day-40)
- [Day 41](#day-41)
- [Day 42](#day-42)
- [Day 43](#day-43)


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

## Day 16

# 🚀 50 Days of LeetCode — Day 16

Welcome to **Day 16** of my #50DaysOfCode challenge!  
Today’s problem took me on a fascinating journey through **iterative digit transformation**, **modular arithmetic**, and **string-based logic reconstruction**. 🔢⚙️  
Even simple numbers can hide deep algorithmic beauty when repetitive operations reveal elegant symmetry!

---

## 🧩 Problem — Check If Digits Are Equal in String After Operations I

**LeetCode 3461 | Easy**

### 🔍 Problem Description

You are given a string `s` consisting of digits.  
Perform the following operation repeatedly until the string has exactly **two digits**:

1. For each pair of consecutive digits in `s`, calculate a new digit as the **sum of the two digits modulo 10**.
2. Replace `s` with the sequence of these new digits.

Return **true** if the final two digits are the same; otherwise, return **false**.

---

#### Example 1:

**Input:**  
`s = "3902"`

**Output:**  
`true`

**Explanation:**

```
Initial: "3902"
1st Operation → (3+9)%10=2, (9+0)%10=9, (0+2)%10=2 → "292"
2nd Operation → (2+9)%10=1, (9+2)%10=1 → "11"
Final two digits are equal → true ✅
```

---

#### Example 2:

**Input:**  
`s = "34789"`

**Output:**  
`false`

**Explanation:**

```
Initial: "34789"
1st Operation → "7157"
2nd Operation → "862"
3rd Operation → "48"
Final digits differ → false ❌
```

---

### 💭 Approach

1. **Convert the string to integers** for easy arithmetic manipulation.
2. **Iteratively transform** the array until only two digits remain.
3. In each step, compute `(arr[i] + arr[i+1]) % 10` and shift the results.
4. Finally, compare the remaining two digits — return `true` if they are equal.

This approach has **O(n²)** time complexity but is perfectly fine for input size ≤ 100.

---

### 💻 Code

```java
public class Solution {
    public boolean hasSameDigits(String s) {
        int n = s.length();
        int[] arr = new int[n];
        for (int i = 0; i < n; i++) arr[i] = s.charAt(i) - '0';
        
        while (n > 2) {
            for (int i = 0; i < n - 1; i++) {
                arr[i] = (arr[i] + arr[i + 1]) % 10;
            }
            n--;
        }
        
        return arr[0] == arr[1];
    }
}
```

---

### 🎯 Conclusion — Day 16

Day 16 was a reminder that **simple logic**, when repeated cleverly, can create **complex transformations**!  
Through modular addition and iterative compression, I explored how data patterns evolve step by step — a concept applicable to number theory, dynamic updates, and even signal analysis. ⚡💡  

Every problem sharpens the balance between **analytical precision** and **creative exploration** — that’s the real beauty of problem solving! 💻💪  
Here’s to more math, more logic, and the unstoppable momentum of learning! 🚀👨‍💻  

---

## Day 17

# 🚀 50 Days of LeetCode — Day 17

Welcome to **Day 17** of my #50DaysOfCode challenge!  
Today’s problem took me on an intriguing dive into **digit frequency logic**, **precomputation**, and **binary search optimization** — a smart balance between math-based reasoning and algorithmic precision. 🔢⚙️  

---

## 🧩 Problem — Next Greater Numerically Balanced Number

**LeetCode 2048 | Medium**

### 🔍 Problem Description

An integer `x` is **numerically balanced** if, for every digit `d` in the number `x`, there are exactly `d` occurrences of that digit in `x`.

Given an integer `n`, return the **smallest numerically balanced number** that is **strictly greater than n**.

---

#### Example 1:

**Input:**  
`n = 1`

**Output:**  
`22`

**Explanation:**  
`22` is numerically balanced since the digit `2` occurs **2 times**.  
It is also the smallest numerically balanced number strictly greater than `1`.

---

#### Example 2:

**Input:**  
`n = 1000`

**Output:**  
`1333`

**Explanation:**  
`1333` is numerically balanced since:  
- The digit `1` occurs once  
- The digit `3` occurs three times  
Hence, `1333` is the smallest numerically balanced number strictly greater than `1000`.

---

#### Example 3:

**Input:**  
`n = 3000`

**Output:**  
`3133`

**Explanation:**  
`3133` is numerically balanced since:  
- The digit `1` occurs once  
- The digit `3` occurs three times  
And it is the smallest number greater than `3000` that meets this property. ✅

---

### 💭 Approach

1. **Understanding Numerically Balanced Numbers:**  
   Each valid number follows the property where digit `d` appears exactly `d` times (e.g., `22`, `1333`, `3133`, etc.).  

2. **Precomputation:**  
   Since the possible range is limited (up to 10⁶), all numerically balanced numbers can be **precomputed** once and stored in an array.

3. **Binary Search:**  
   Use binary search to quickly find the **next greater** numerically balanced number after `n`.

4. **Efficiency:**  
   - Precomputation ensures constant lookup time for queries.  
   - Binary search runs in **O(log N)** over a small precomputed set.  

---

### 💻 Code

```java
public class Solution {
    // Precomputed all numerically balanced numbers up to 10^7
    private static final int[] BEAUTIFUL = {
        1, 22, 122, 212, 221, 333, 1333, 3133, 3313, 3331,
        4444, 14444, 22333, 23233, 23323, 23332, 32233, 32323,
        32332, 33223, 33232, 33322, 41444, 44144, 44414, 44441,
        55555, 122333, 123233, 123323, 123332, 132233, 132323,
        132332, 133223, 133232, 133322, 155555, 212333, 213233,
        213323, 213332, 221333, 223133, 223313, 223331, 224444,
        231233, 231323, 231332, 232133, 232313, 232331, 233123,
        233132, 233213, 233231, 233312, 233321, 242444, 244244,
        244424, 244442, 312233, 312323, 312332, 313223, 313232,
        313322, 321233, 321323, 321332, 322133, 322313, 322331,
        323123, 323132, 323213, 323231, 323312, 323321, 331223,
        331232, 331322, 332123, 332132, 332213, 332231, 332312,
        332321, 333122, 333212, 333221, 422444, 424244, 424424,
        424442, 442244, 442424, 442442, 444224, 444242, 444422,
        515555, 551555, 555155, 555515, 555551, 666666, 1224444
    };
    
    public int nextBeautifulNumber(int n) {
        int lo = 0, hi = BEAUTIFUL.length - 1;
        while (lo <= hi) {
            int mid = (lo + hi) >>> 1;
            if (BEAUTIFUL[mid] <= n) {
                lo = mid + 1;
            } else {
                hi = mid - 1;
            }
        }
        return lo < BEAUTIFUL.length ? BEAUTIFUL[lo] : -1;
    }
}
```

### 🎯 Conclusion — Day 17

Day 17 reminded me how precomputation and optimization can transform a seemingly brute-force problem into an elegant, fast, and scalable solution. ⚙️💡
The balance between mathematical properties and algorithmic efficiency showcased how pattern recognition often leads to powerful shortcuts in coding!

With each day, this challenge strengthens not only my problem-solving mindset but also my appreciation for the art of building smarter algorithms. 💻🔥
On to Day 18, where logic meets creativity again! 🚀👨‍💻

---

## Day 18

# 🚀 50 Days of LeetCode — Day 18

Welcome to **Day 18** of my #50DaysOfCode challenge!
Today’s problem revolved around **pattern recognition**, **arithmetic progression**, and **smart week-based computation** — proving that even simple financial logic can have elegant mathematical underpinnings! 💰📅

---

## 🧩 Problem — Calculate Money in Leetcode Bank

**LeetCode 1716 | Easy**

### 🔍 Problem Description

Hercy wants to save money for his first car. He deposits money into the Leetcode bank following this pattern:

* On **Monday** (the first day), he deposits **$1**.
* Each subsequent day of the week, he deposits **$1 more** than the previous day.
* On the next **Monday**, he deposits **$1 more than the previous Monday**, and the pattern continues.

Given `n`, return the **total amount of money** in the bank after the `n`th day.

---

#### Example 1:

**Input:**
`n = 4`

**Output:**
`10`

**Explanation:**
After the 4th day:
`1 + 2 + 3 + 4 = 10`

---

#### Example 2:

**Input:**
`n = 10`

**Output:**
`37`

**Explanation:**
After 10 days:
`(1 + 2 + 3 + 4 + 5 + 6 + 7) + (2 + 3 + 4) = 37`

---

#### Example 3:

**Input:**
`n = 20`

**Output:**
`96`

**Explanation:**
After 20 days:
`(1 + 2 + 3 + 4 + 5 + 6 + 7)` +
`(2 + 3 + 4 + 5 + 6 + 7 + 8)` +
`(3 + 4 + 5 + 6 + 7 + 8)` = `96` ✅

---

### 💭 Approach

1. **Identify weekly cycles:**
   Every week has 7 days, with deposits increasing linearly.

2. **Compute full weeks:**
   For each complete week, sum up all deposits using arithmetic series formula and adjust for increasing Monday starts.

3. **Handle remaining days:**
   For leftover days (less than a week), continue the pattern starting from the next Monday’s base value.

4. **Formula application:**

   * Sum for full weeks = `fullWeeks * 28 + 7 * fullWeeks * (fullWeeks - 1) / 2`
   * Sum for remaining days = `remainingDays * (fullWeeks + 1) + remainingDays * (remainingDays - 1) / 2`

5. **Final total:**
   Add both to get the complete savings.

---

### 💻 Code

```java
public class Solution {
    public int totalMoney(int n) {
        int fullWeeks = n / 7;
        int remainingDays = n % 7;
        int fullWeeksTotal = fullWeeks * 28 + 7 * fullWeeks * (fullWeeks - 1) / 2;
        int remainingTotal = remainingDays * (fullWeeks + 1) + remainingDays * (remainingDays - 1) / 2;
        
        return fullWeeksTotal + remainingTotal;
    }
}
```

---

### 🎯 Conclusion — Day 18

Day 18 was a perfect example of how **mathematical reasoning** can simplify iterative logic into a clean, constant-time formula! ✨
By breaking the problem into **weeks** and **remainders**, I learned how structured patterns can be expressed through elegant equations.

This problem reminded me that understanding the **underlying sequence** often unlocks the simplest — yet most powerful — solution. 💻📊

Here’s to another day of learning, logic, and levelling up! 🚀👨‍💻

---

## Day 19

# 🚀 50 Days of LeetCode — Day 19

Welcome to **Day 19** of my #50DaysOfCode challenge!
Today's problem focused on **object-oriented design**, **transaction validation**, and **state management** — demonstrating how to build a robust banking system with proper account handling! 💰🏦

---

## 🧩 Problem — Simple Bank System

**LeetCode 2043 | Medium**

### 🔍 Problem Description

Design a banking system that automates transactions (transfer, deposit, withdraw) for `n` accounts numbered from **1 to n**. Transactions are valid only if account numbers are within range and sufficient balance exists for withdrawals/transfers.

---

#### Example 1:

**Input:**
```
["Bank", "withdraw", "transfer", "deposit", "transfer", "withdraw"]
[[[10, 100, 20, 50, 30]], [3, 10], [5, 1, 20], [5, 20], [3, 4, 15], [10, 50]]
```

**Output:**
```
[null, true, true, true, false, false]
```

**Explanation:**
```java
Bank bank = new Bank([10, 100, 20, 50, 30]);
bank.withdraw(3, 10);    // return true, account 3 has $20, so valid to withdraw $10.
                         // Account 3 now has $20 - $10 = $10.
bank.transfer(5, 1, 20); // return true, account 5 has $30, so valid to transfer $20.
                         // Account 5 has $30 - $20 = $10, account 1 has $10 + $20 = $30.
bank.deposit(5, 20);     // return true, valid to deposit $20 to account 5.
                         // Account 5 now has $10 + $20 = $30.
bank.transfer(3, 4, 15); // return false, account 3 has $10, invalid to transfer $15.
bank.withdraw(10, 50);   // return false, account 10 does not exist.
```

---

### 💭 Approach

1. **Account Indexing:**
   Since accounts are numbered 1 to n but the array is 0-indexed, convert account numbers by subtracting 1.

2. **Validation Strategy:**
   Before any operation, validate:
   * Account numbers are within valid range (0 to accounts.length - 1)
   * For withdrawals/transfers, ensure sufficient balance exists

3. **Optimization Techniques:**
   * **Inline validation** — Remove helper method overhead by directly checking conditions
   * **Reduce array accesses** — Calculate index once and reuse
   * **Early termination** — Check bounds before checking balance to fail fast
   * **Simplified conditionals** — Use straightforward boolean logic

4. **Thread Safety (Optional):**
   For concurrent access, use `synchronized` methods or lock-free structures like `AtomicLongArray`

---

### 💻 Code

```java
public class Bank {
    private final long[] accounts;

    public Bank(long[] balance) {
        accounts = balance;
    }

    public synchronized boolean transfer(int account1, int account2, long money) {
        int idx1 = account1 - 1;
        int idx2 = account2 - 1;
        
        if (idx1 >= accounts.length || idx2 >= accounts.length || 
            idx1 < 0 || idx2 < 0 || accounts[idx1] < money) {
            return false;
        }
        
        accounts[idx1] -= money;
        accounts[idx2] += money;
        return true;
    }

    public synchronized boolean deposit(int account, long money) {
        int idx = account - 1;
        
        if (idx >= accounts.length || idx < 0) {
            return false;
        }
        
        accounts[idx] += money;
        return true;
    }

    public synchronized boolean withdraw(int account, long money) {
        int idx = account - 1;
        
        if (idx >= accounts.length || idx < 0 || accounts[idx] < money) {
            return false;
        }
        
        accounts[idx] -= money;
        return true;
    }
}
```

---

### 🎯 Conclusion — Day 19

Day 19 was an excellent exercise in **system design** and **optimization**! 🏗️
By focusing on **clean validation**, **efficient indexing**, and **thread-safe operations**, I learned how to build a production-ready banking system that handles transactions reliably.

This problem reinforced the importance of:
* **Index management** when converting between user-facing and internal representations
* **Validation order** to optimize for common failure cases
* **Code clarity** without sacrificing performance

Here's to building robust, real-world systems one line at a time! 🚀💻

---

## Day 20

# 🚀 50 Days of LeetCode — Day 20

Welcome to **Day 20** of my #50DaysOfCode challenge!  
Today’s problem focused on **matrix traversal**, **logical reasoning**, and **count-based computation** — showing how structured counting can simplify even 2D logic problems! 🏦💡

---

## 🧩 Problem — Number of Laser Beams in a Bank

**LeetCode 2125 | Medium**

### 🔍 Problem Description

You are given a `0-indexed` binary string array `bank` representing a bank’s floor plan, modeled as an **m × n matrix**.

Each row in `bank` represents devices (`'1'`) and empty spaces (`'0'`).  
A **laser beam** exists between two devices if:

1. They are on **different rows** (`r₁` < `r₂`), and  
2. Every row between them contains **no devices**.

Your task: return the **total number of laser beams** present in the bank.

---

### 💭 Approach

1. **Count active devices per row:**  
   For each row, count how many `'1'`s appear.

2. **Skip empty rows:**  
   Only rows with at least one device can form beams.

3. **Multiply adjacent non-empty rows:**  
   Each pair contributes `previous_count × current_count` beams.

4. **Iterate efficiently:**  
   Keep track of the previous non-empty row count and update beams in a single pass.

🧠 **Complexity:**  
Time = O(m × n)  
Space = O(1)

---

### 💻 Code

```java
public class Solution {
    public int numberOfBeams(String[] bank) {
        int beams = 0;
        int prevCount = 0;
        
        for (String row : bank) {
            int currentCount = 0;
            int len = row.length();
            for (int i = 0; i < len; i++) {
                currentCount += row.charAt(i) & 1;
            }
            
            if (currentCount > 0) {
                beams += prevCount * currentCount;
                prevCount = currentCount;
            }
        }
        
        return beams;
    }
}
```

---

### 🎯 Conclusion — Day 20

Day 20 reinforced the power of pattern simplification — transforming a grid-based challenge into simple arithmetic logic.
This problem was a great exercise in recognizing relationships between consecutive rows and using incremental computation to achieve efficiency.

Each challenge brings me closer to mastering data pattern intuition and logical design thinking! 🚀💻

---

## Day 21

# 🚀 50 Days of LeetCode — Day 21

Welcome to **Day 21** of my #50DaysOfCode challenge!
Today’s problem was a brilliant mix of **array manipulation**, **prefix-sum logic**, and **direction-based simulation** — blending mathematical balance with algorithmic clarity! ⚙️💫

---

## 🧩 Problem — Make Array Elements Equal to Zero

**LeetCode 3354 | Easy**

### 🔍 Problem Description

You are given an integer array `nums`.
You start from a position `curr` where `nums[curr] == 0` and pick a direction — left or right.

At each step:

* If you’re **out of bounds**, stop.
* If `nums[curr] == 0`, move in the current direction.
* If `nums[curr] > 0`, decrement it by 1, **reverse** direction, and move one step.

A selection is **valid** if, by the end of the process, all elements in `nums` become 0.
Your task is to return the **number of valid selections** of starting points and directions.

---

### 💭 Approach

1. **Compute total sum of elements** to track total decrements needed.
2. **Iterate through each index:**

   * Maintain a running sum of elements to the left (`leftSum`).
   * For every zero element, calculate the difference between left and right sums.
3. **Check balance conditions:**

   * If the difference is 0, both directions are valid → add 2.
   * If the difference is 1, only one direction is valid → add 1.

🧠 **Complexity:**
Time = O(n)
Space = O(1)

---

### 💻 Code

```java
public class Solution {
    public int countValidSelections(int[] nums) {
        int totalSum = 0;
        for (int num : nums) {
            totalSum += num;
        }
        
        int result = 0;
        int leftSum = 0;
        
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 0) {
                int rightSum = totalSum - leftSum;
                int diff = Math.abs(rightSum - leftSum);
                
                if (diff == 0) {
                    result += 2;
                } else if (diff == 1) {
                    result++;
                }
            }
            leftSum += nums[i];
        }
        
        return result;
    }
}
```

---

### 🎯 Conclusion — Day 21

Day 21 was a perfect reminder that even **simulation-based problems** can often be reduced to elegant **mathematical reasoning**! 🔢✨
By combining cumulative sums and balance checking, I discovered a clean linear-time solution that avoids brute-force simulation entirely.

This problem reinforced how **understanding symmetry** and **directional logic** can simplify dynamic processes into pure number relationships.
Here’s to more days of analytical discovery and elegant solutions! 🚀💻

---

## Day 22

# 🚀 50 Days of LeetCode — Day 22

Welcome to **Day 22** of my #50DaysOfCode challenge!
Today’s problem was a short yet powerful exercise in **bit manipulation**, **binary reasoning**, and **mathematical pattern detection** — showing how simplicity and insight can go hand in hand. ⚙️💡

---

## 🧩 Problem — Smallest Number With All Set Bits

**LeetCode 3370 | Easy**

### 🔍 Problem Description

You are given a positive integer `n`.

Your task is to find the **smallest number `x` greater than or equal to `n`** such that the **binary representation of `x` contains only set bits (1s)**.

---

### 🧠 Example

**Input:**
`n = 5`
**Output:**
`7`
**Explanation:**
Binary of 7 → `"111"`, which is the smallest all-set-bit number ≥ 5.

**Input:**
`n = 10`
**Output:**
`15`
**Explanation:**
Binary of 15 → `"1111"`, the smallest all-set-bit number ≥ 10.

---

### 💭 Approach

1. Start with `res = 1` — the smallest number with all bits set (`1` in binary).
2. Repeatedly **expand** the number by doubling and adding one:

   * This operation (`res = res * 2 + 1`) generates numbers like 1, 3, 7, 15, 31, 63, ...
   * Each is of the form `2^k - 1`, meaning all bits are set.
3. Stop once `res >= n`, ensuring it’s the smallest all-set-bit number that satisfies the condition.

🧠 **Complexity:**
Time = O(log n)
Space = O(1)

---

### 💻 Code

```java
public class Solution {
    public int smallestNumber(int n) {
        int res = 1;
        while (res < n) {
            res = res * 2 + 1;
        }
        return res;
    }
}
```

---

### 🎯 Conclusion — Day 22

Day 22 was a delightful reminder that **bit manipulation** problems often hide in plain sight! 💫
By recognizing that all-set-bit numbers follow the pattern `2^k - 1`, the challenge reduces to a clean loop with logarithmic growth.

It’s amazing how understanding **binary patterns** allows for quick, elegant, and mathematically sound solutions — proving once again that simplicity is the ultimate sophistication in coding! 🚀💻

---

## Day 23

# 🚀 50 Days of LeetCode — Day 23

Welcome to **Day 23** of my #50DaysOfCode challenge!
Today’s problem was a deep dive into **greedy algorithms**, **difference computation**, and **incremental array transformation** — tackling one of the most elegant subarray increment problems in LeetCode! 💪💡

---

## 🧩 Problem — Minimum Number of Increments on Subarrays to Form a Target Array

**LeetCode 1526 | Hard**

### 🔍 Problem Description

You are given an integer array `target`.
You start with another array `initial` of the same size, with all elements set to 0.

In one operation, you can choose **any subarray** of `initial` and **increment each value by 1**.
Your goal is to form `target` from `initial` using the **minimum number of operations**.

Return that minimum number.

---

### 🧠 Example

**Input:**
`target = [1,2,3,2,1]`
**Output:**
`3`

**Explanation:**
1️⃣ Increment all elements → `[1,1,1,1,1]`
2️⃣ Increment middle subarray → `[1,2,2,2,1]`
3️⃣ Increment center → `[1,2,3,2,1]`

Minimum operations = **3** ✅

---

### 💭 Approach

1. The number of operations equals how many **times we need to raise elements** compared to their previous element.
2. The **first element** requires `target[0]` operations (since we start from zero).
3. For each next element, if `target[i] > target[i - 1]`, we need extra operations equal to the **difference**.
4. Sum all these positive differences to get the total operations.

🧠 **Complexity:**
Time = O(n)
Space = O(1)

---

### 💻 Code

```java
public class Solution {
    public int minNumberOperations(int[] target) {
        int operations = target[0];
        for (int i = 1; i < target.length; i++) {
            if (target[i] > target[i - 1]) {
                operations += target[i] - target[i - 1];
            }
        }
        return operations;
    }
}
```

---

### 🎯 Conclusion — Day 23

Day 23 was a masterclass in **greedy problem-solving** — turning what seems like a simulation into a pure difference-based logic problem! 🔥
By focusing on **increment transitions** rather than entire subarrays, I learned how to reason in deltas, not absolute states — a key mindset for writing efficient, optimized algorithms.

This challenge beautifully showcased how understanding **change patterns** can simplify even the most complex transformations. 🚀💻

---

## Day 24

# 🚀 50 Days of LeetCode — Day 24

Welcome to **Day 24** of my #50DaysOfCode challenge!
Today’s problem was a fun and insightful journey into **array analysis**, **frequency tracking**, and **logical deduction** — solving a mystery straight from the digital town of *Digitville*! 🕵️‍♂️💡

---

## 🧩 Problem — The Two Sneaky Numbers of Digitville

**LeetCode 3289 | Easy**

### 🔍 Problem Description

In the town of **Digitville**, there was a list of numbers `nums` containing integers from `0` to `n - 1`.
Each number was supposed to appear **exactly once**, but two mischievous numbers appeared **twice**, making the list longer than usual! 😄

Your task is to find these two sneaky numbers and return them in an array (in any order).

---

### 🧠 Examples

**Example 1**
**Input:** `nums = [0,1,1,0]`
**Output:** `[0,1]`
➡️ Both 0 and 1 appear twice.

**Example 2**
**Input:** `nums = [0,3,2,1,3,2]`
**Output:** `[2,3]`

**Example 3**
**Input:** `nums = [7,1,5,4,3,4,6,0,9,5,8,2]`
**Output:** `[4,5]`

---

### 💭 Approach

1. Initialize a boolean array `seen` to track numbers that have already appeared.
2. Iterate through each number in `nums`.
3. If it has been seen before, it’s one of the sneaky numbers — add it to the result list.
4. Stop once both sneaky numbers are found.

🧠 **Complexity:**
Time = O(n)
Space = O(n)

---

### 💻 Code

```java
public class Solution {
    public int[] getSneakyNumbers(int[] nums) {
        int[] result = new int[2];
        int index = 0;
        int n = nums.length - 2; 
        boolean[] seen = new boolean[n];
        
        for (int num : nums) {
            if (seen[num]) {
                result[index++] = num;
                if (index == 2) {
                    break;
                }
            } else {
                seen[num] = true;
            }
        }
        
        return result;
    }
}
```

---

### 🎯 Conclusion — Day 24

Day 24 brought a delightful detective-style challenge — tracing sneaky duplicates hiding in an almost-perfect sequence! 🕵️‍♂️✨
This problem reinforced how **logical iteration** and **state tracking** can turn simple patterns into efficient and clean solutions.
A great reminder that even “easy” problems sharpen essential algorithmic instincts. 💪💻

---

## Day 26

# 🚀 50 Days of LeetCode — Day 26

Welcome to **Day 26** of my #50DaysOfCode challenge!
Today’s problem was an exciting exploration of **grid traversal**, **directional scanning**, and **spatial visibility simulation** — solving a problem that blends logic with geometry and optimization! 🧭⚙️

---

## 🧩 Problem — Count Unguarded Cells in the Grid

**LeetCode 2257 | Medium**

### 🔍 Problem Description

You are given two integers `m` and `n` representing a 0-indexed `m x n` grid.
You are also given two 2D integer arrays `guards` and `walls` representing the positions of guards and walls, respectively.

A **guard** can see every cell in the four directions — north, east, south, and west — until their view is blocked by a wall or another guard.
A cell is **guarded** if at least one guard can see it.

Return the number of **unguarded and unoccupied cells** in the grid.

---

### 🧠 Examples

**Example 1**
**Input:**
`m = 4, n = 6, guards = [[0,0],[1,1],[2,3]], walls = [[0,1],[2,2],[1,4]]`
**Output:** `7`
➡️ There are 7 unguarded cells after marking all visible positions from the guards.

**Example 2**
**Input:**
`m = 3, n = 3, guards = [[1,1]], walls = [[0,1],[1,0],[2,1],[1,2]]`
**Output:** `4`
➡️ The guards’ line of sight is blocked by walls, leaving 4 unguarded cells.

---

### 💭 Approach

1. Represent the grid as a **flattened byte array** for memory efficiency.
2. Mark guards with `1` and walls with `2`.
3. For each guard, simulate vision in four directions until a wall or another guard blocks the path.
4. Count all guarded cells by marking them as `-1`.
5. The number of unguarded cells is the total grid size minus guarded, guard, and wall cells.

🧠 **Complexity:**
Time = O(m × n)
Space = O(m × n)

---

### 💻 Code

```java
public class Solution {
    public int countUnguarded(int m, int n, int[][] guards, int[][] walls) {
        byte[] grid = new byte[m * n];
        
        // Mark guards
        for (int[] g : guards) {
            grid[g[0] * n + g[1]] = 1;
        }
        
        // Mark walls
        for (int[] w : walls) {
            grid[w[0] * n + w[1]] = 2;
        }
        
        int guarded = 0;
        
        // Process guard visibility
        for (int[] g : guards) {
            int r = g[0], c = g[1];
            int idx = r * n + c;
            
            // Left
            for (int j = c - 1, i = idx - 1; j >= 0; j--, i--) {
                byte val = grid[i];
                if (val > 0) break;
                if (val == 0) guarded++;
                grid[i] = -1;
            }
            
            // Right
            for (int j = c + 1, i = idx + 1; j < n; j++, i++) {
                byte val = grid[i];
                if (val > 0) break;
                if (val == 0) guarded++;
                grid[i] = -1;
            }
            
            // Up
            for (int i = idx - n; i >= 0; i -= n) {
                byte val = grid[i];
                if (val > 0) break;
                if (val == 0) guarded++;
                grid[i] = -1;
            }
            
            // Down
            for (int i = idx + n; i < m * n; i += n) {
                byte val = grid[i];
                if (val > 0) break;
                if (val == 0) guarded++;
                grid[i] = -1;
            }
        }
        
        return m * n - guards.length - walls.length - guarded;
    }
}
```

---

### 🎯 Conclusion — Day 26

Day 26 was a brilliant test of **spatial reasoning and algorithmic efficiency**! 💪
By leveraging flattened indexing and directional scanning, I learned how to simulate real-world visibility problems in an optimized manner.

It’s fascinating how **guard visibility**, **walls**, and **grid traversal** can be reduced to clean loops and logical checks — turning spatial problems into elegant algorithmic patterns. 🚀💻

---

## Day 27

# 🚀 50 Days of LeetCode — Day 27

Welcome to **Day 27** of my #50DaysOfCode challenge!
Today’s problem was a colorful mix of **greedy strategy**, **array optimization**, and **string manipulation** — solving how to minimize time while keeping the rope beautifully colorful! 🎨💡

---

## 🧩 Problem — Minimum Time to Make Rope Colorful

**LeetCode 1578 | Medium**

### 🔍 Problem Description

Alice has `n` balloons arranged on a rope, represented by a string `colors` where `colors[i]` is the color of the `i-th` balloon.
She wants the rope to be colorful — meaning **no two consecutive balloons should share the same color**.

Bob can remove balloons, and each removal takes `neededTime[i]` seconds.
Return the **minimum total time** needed to make the rope colorful.

---

### 🧠 Examples

**Example 1**
**Input:** `colors = "abaac"`, `neededTime = [1,2,3,4,5]`
**Output:** `3`
➡️ Remove the blue balloon at index 2 (time = 3). The rope becomes colorful.

**Example 2**
**Input:** `colors = "abc"`, `neededTime = [1,2,3]`
**Output:** `0`
➡️ Already colorful — no removal needed.

**Example 3**
**Input:** `colors = "aabaa"`, `neededTime = [1,2,3,4,1]`
**Output:** `2`
➡️ Remove balloons at indices 0 and 4 (time = 1 + 1 = 2).

---

### 💭 Approach

1. Traverse the rope balloon by balloon.
2. Whenever **two consecutive colors match**, remove the one with **less removal time** to minimize cost.
3. Keep updating the `cost[i]` to the **max of the pair**, ensuring future comparisons are correct.

🧠 **Complexity:**
Time = O(n)
Space = O(1)

---

### 💻 Code

```java
public class Solution {
    public int minCost(String s, int[] cost) {
        char[] str = s.toCharArray();
        int minCost = 0;
        for (int i = 1; i < str.length; i++) {
            if (str[i] == str[i - 1]) {
                minCost += Math.min(cost[i], cost[i - 1]);
                cost[i] = Math.max(cost[i], cost[i - 1]);
            }
        }
        return minCost;
    }
}
```

---

### 🎯 Conclusion — Day 27

Day 27 was all about mastering **greedy optimization and string traversal**! 💪
This problem beautifully illustrates how small, local decisions (removing the cheaper duplicate) can lead to a globally optimal result.

It’s another perfect reminder that sometimes the simplest logic — like comparing adjacent elements — can solve complex-looking challenges with elegance and precision. ⚙️💻

---

## Day 28

# 🚀 50 Days of LeetCode — Day 28

Welcome to **Day 28** of my #50DaysOfCode challenge!
Today’s problem combined **frequency analysis**, **selection-based optimization**, and **subarray computation** — exploring how to efficiently calculate the *X-Sum* for every subarray of length `k`! 🔢⚙️

---

## 🧩 Problem — Find X-Sum of All K-Long Subarrays I

**LeetCode 3318 | Easy**

### 🔍 Problem Description

You are given an array `nums` of `n` integers and two integers `k` and `x`.

The **x-sum** of an array is computed by:

1. Counting occurrences of each element.
2. Keeping only the top `x` most frequent elements.

   * If two elements have the same frequency, the **larger value** is considered more frequent.
3. Summing the resulting array.

If there are fewer than `x` distinct elements, the x-sum is simply the sum of the array.

Return an array `answer` where `answer[i]` is the x-sum of the subarray `nums[i..i + k - 1]`.

---

### 🧠 Examples

**Example 1**
**Input:** `nums = [1,1,2,2,3,4,2,3], k = 6, x = 2`
**Output:** `[6,10,12]`
➡️ The top 2 frequent elements are used to calculate each subarray’s X-sum.

**Example 2**
**Input:** `nums = [3,8,7,8,7,5], k = 2, x = 2`
**Output:** `[11,15,15,15,12]`
➡️ Since `k == x`, each X-sum equals the sum of its subarray.

---

### 💭 Approach

1. Iterate through all possible subarrays of size `k`.
2. Count frequencies using a fixed-size array (`freq[51]`) for fast access.
3. Store distinct elements and use **partial selection sorting** to get the top `x` by:

   * Frequency (descending)
   * Value (descending, for tie-breaking)
4. Compute the weighted sum of the top `x` elements to form the X-sum for that subarray.

🧠 **Complexity:**
Time = O(n × 50 × x) (manageable for constraints)
Space = O(50)

---

### 💻 Code

```java
class Solution {
    public int[] findXSum(int[] nums, int k, int x) {
        int n = nums.length;
        int[] answer = new int[n - k + 1];
        int[] freq = new int[51];
        int[] pairs = new int[51];
        
        for (int i = 0; i <= n - k; i++) {
            answer[i] = calculateXSum(nums, i, i + k - 1, x, freq, pairs);
        }
        
        return answer;
    }
    
    private int calculateXSum(int[] nums, int start, int end, int x, int[] freq, int[] pairs) {
        // Reset frequency array
        int distinctCount = 0;
        for (int i = 1; i <= 50; i++) {
            freq[i] = 0;
        }
        
        // Count frequencies
        for (int i = start; i <= end; i++) {
            if (freq[nums[i]] == 0) {
                pairs[distinctCount++] = nums[i];
            }
            freq[nums[i]]++;
        }
        
        // If less than x distinct elements, sum everything
        if (distinctCount <= x) {
            int sum = 0;
            for (int i = 0; i < distinctCount; i++) {
                int val = pairs[i];
                sum += val * freq[val];
            }
            return sum;
        }
        
        // Select top x by frequency (and value)
        for (int i = 0; i < x; i++) {
            int maxIdx = i;
            for (int j = i + 1; j < distinctCount; j++) {
                int val1 = pairs[j];
                int val2 = pairs[maxIdx];
                if (freq[val1] > freq[val2] || 
                    (freq[val1] == freq[val2] && val1 > val2)) {
                    maxIdx = j;
                }
            }
            int temp = pairs[i];
            pairs[i] = pairs[maxIdx];
            pairs[maxIdx] = temp;
        }
        
        // Compute sum of top x
        int sum = 0;
        for (int i = 0; i < x; i++) {
            int val = pairs[i];
            sum += val * freq[val];
        }
        return sum;
    }
}
```

---

### 🎯 Conclusion — Day 28

Day 28 was all about **frequency-driven logic** and **smart local selection**! 💪
By combining counting, ranking, and summing, I got to explore how **custom sorting logic** and **partial optimization** can simplify seemingly complex subarray problems.

It’s a beautiful mix of **mathematical reasoning** and **algorithmic clarity**, reminding me that elegant solutions often come from keeping both **logic and data flow simple**. 🚀💻

---

## Day 29

# 🚀 50 Days of LeetCode — Day 29

Welcome to **Day 29** of my #50DaysOfCode challenge!
Today’s challenge leveled up the complexity — turning a simple counting problem into a test of **data structure balancing**, **frequency tracking**, and **real-time subarray computation**! ⚙️🔥

---

## 🧩 Problem — Find X-Sum of All K-Long Subarrays II

**LeetCode 3321 | Hard**

### 🔍 Problem Description

You are given an array `nums` of `n` integers and two integers `k` and `x`.

The **x-sum** of an array is defined by:

1. Counting occurrences of all elements in the array.
2. Keeping only the occurrences of the top `x` most frequent elements.

   * If two elements have the same count, the **larger value** is considered more frequent.
3. Summing all occurrences of those top `x` elements.

If there are fewer than `x` distinct elements, the x-sum is the sum of the entire subarray.

Return an array `answer` where `answer[i]` is the x-sum of the subarray `nums[i..i + k - 1]`.

---

### 🧠 Examples

**Example 1**
**Input:** `nums = [1,1,2,2,3,4,2,3]`, `k = 6`, `x = 2`
**Output:** `[6,10,12]`
➡️ Each subarray keeps only the top 2 most frequent elements based on the defined rule.

**Example 2**
**Input:** `nums = [3,8,7,8,7,5]`, `k = 2`, `x = 2`
**Output:** `[11,15,15,15,12]`
➡️ Since `k == x`, every subarray’s x-sum equals the sum of its elements.

---

### 💭 Approach

This advanced variant of the X-Sum problem demanded maintaining **dynamic frequency states** across a sliding window efficiently.

1. Use two **balanced TreeSets (`s1` and `s2`)**:

   * `s1` holds the top `x` elements by frequency and value (for the current x-sum).
   * `s2` holds all other elements.
2. Track occurrences in a **HashMap** to update and rebalance frequencies as the window slides.
3. Maintain the **current sum** and **x-sum** dynamically:

   * When adding/removing an element, update sets and adjust sums in O(log n).
4. At each step, rebalance sets to ensure `s1` always contains exactly the top `x` elements.

🧠 **Complexity:**

* Time = O(n log n)
* Space = O(n)

Efficiently handling rebalancing between TreeSets was key to achieving optimal performance for large inputs (`n ≤ 10⁵`).

---

### 💻 Code

```java
import java.util.HashMap;
import java.util.Map;
import java.util.TreeSet;

@SuppressWarnings("java:S1210")
public class Solution {
    private static class RC implements Comparable<RC> {
        int val;
        int cnt;

        RC(int v, int c) {
            val = v;
            cnt = c;
        }

        public int compareTo(RC o) {
            if (cnt != o.cnt) return cnt - o.cnt;
            return val - o.val;
        }

        @Override
        public boolean equals(Object o) {
            if (!(o instanceof RC)) return false;
            RC other = (RC) o;
            return val == other.val && cnt == other.cnt;
        }

        @Override
        public int hashCode() {
            return val * 31 + cnt;
        }
    }

    public long[] findXSum(int[] nums, int k, int x) {
        int n = nums.length;
        long[] ans = new long[n - k + 1];
        Map<Integer, Integer> cnt = new HashMap<>();
        TreeSet<RC> s1 = new TreeSet<>();
        TreeSet<RC> s2 = new TreeSet<>();
        long sum = 0, xSum = 0;

        for (int i = 0; i < n; ++i) {
            sum += nums[i];
            int curCnt = cnt.getOrDefault(nums[i], 0);

            if (curCnt > 0) {
                RC old = new RC(nums[i], curCnt);
                if (s1.remove(old)) xSum -= (long) nums[i] * curCnt;
                else s2.remove(old);
            }

            cnt.put(nums[i], curCnt + 1);
            RC newRC = new RC(nums[i], curCnt + 1);
            s1.add(newRC);
            xSum += (long) nums[i] * (curCnt + 1);

            while (s1.size() > x) {
                RC l = s1.pollFirst();
                xSum -= (long) l.val * l.cnt;
                s2.add(l);
            }

            if (i >= k - 1) {
                ans[i - k + 1] = s1.size() == x ? xSum : sum;

                int v = nums[i - k + 1];
                sum -= v;
                curCnt = cnt.get(v);

                RC old = new RC(v, curCnt);
                if (s1.remove(old)) xSum -= (long) v * curCnt;
                else s2.remove(old);

                if (curCnt > 1) {
                    cnt.put(v, curCnt - 1);
                    s2.add(new RC(v, curCnt - 1));
                } else {
                    cnt.remove(v);
                }

                while (s1.size() < x && !s2.isEmpty()) {
                    RC r = s2.pollLast();
                    s1.add(r);
                    xSum += (long) r.val * r.cnt;
                }
            }
        }
        return ans;
    }
}
```

---

### 🎯 Conclusion — Day 29

Day 29 was a true test of **data structure mastery** and **logical precision**. 💪
By leveraging `TreeSet` balancing and real-time updates, this problem showcased how **ordered sets** and **incremental frequency tracking** can elegantly solve high-complexity sliding window problems.

It reinforced the power of **strategic design** — where thoughtful data handling transforms what seems like chaos into clarity and control. ⚡📊
A perfect blend of **mathematical insight** and **algorithmic finesse**! 🚀

---

## Day 30

# ⚡ 50 Days of LeetCode — Day 30

Welcome to **Day 30** of my #50DaysOfCode challenge!  
Today’s challenge was a thrilling journey through **Union-Find (Disjoint Set Union)** logic and **priority-based grid tracking**, testing the balance between **connectivity** and **dynamic state management**. ⚙️🔋

---

## 🧩 Problem — Power Grid Maintenance

**LeetCode 3607 | Medium**

### 🔍 Problem Description

You are given an integer `c` representing `c` power stations (1-based indexing).  
These stations are connected via `n` bidirectional cables given by `connections[i] = [ui, vi]`.  
Stations that are directly or indirectly connected form a **power grid**.

Initially, all stations are **online** (operational).

You are also given a list of queries of two types:

1. `[1, x]`: A maintenance check is requested for station `x`.  
   - If `x` is online, it resolves the check itself.  
   - If `x` is offline, the check is resolved by the **smallest operational station** in the same power grid.  
   - If there is no operational station, return `-1`.

2. `[2, x]`: Station `x` goes **offline** (becomes non-operational).

Return an array containing the results of all type `[1, x]` queries in order.

---

### 🧠 Example

**Input:**  
`c = 5, connections = [[1,2],[2,3],[3,4],[4,5]], queries = [[1,3],[2,1],[1,1],[2,2],[1,2]]`  

**Output:**  
`[3,2,3]`

**Explanation:**  
- Initially all stations `{1,2,3,4,5}` are online.  
- Query `[1,3]`: Station 3 is online → resolves itself → **3**  
- Query `[2,1]`: Station 1 goes offline.  
- Query `[1,1]`: Station 1 is offline → smallest online in grid is **2**  
- Query `[2,2]`: Station 2 goes offline.  
- Query `[1,2]`: Station 2 is offline → smallest online in grid is **3**  

---

### 💭 Approach

This problem revolves around efficiently maintaining **connected components** and dynamically tracking the **smallest online station** per grid.

1. **Union-Find (Disjoint Set Union)** is used to group stations into grids.  
   - Each component (grid) keeps track of all its station IDs in a **min-priority queue**.
2. Initially, all stations are marked **active (online)**.
3. For query `[1, x]`:  
   - If station `x` is active → return `x`.  
   - Else, find its grid parent → pop inactive stations from the PQ until we find the smallest online station.  
   - Return that station’s ID or `-1` if none exist.
4. For query `[2, x]`:  
   - Simply mark station `x` as **inactive**.
5. Union operations merge the smaller PQ into the larger one to keep operations efficient.

🧠 **Complexity:**  
- Time = `O((n + q) log n)` due to union and PQ operations.  
- Space = `O(n)` for parent arrays and queues.

---

### 💻 Code

```java
import java.util.ArrayList;
import java.util.List;
import java.util.PriorityQueue;

@SuppressWarnings("unchecked")
public class Solution {
    private static class UF {
        int[] par;
        PriorityQueue<Integer>[] pq;
        boolean[] active;

        UF(int n) {
            par = new int[n];
            pq = new PriorityQueue[n];
            active = new boolean[n];
            for (int i = 0; i < n; i++) {
                active[i] = true;
                par[i] = i;
                pq[i] = new PriorityQueue<>();
                pq[i].add(i);
            }
        }

        int find(int u) {
            if (par[u] == u) {
                return u;
            }
            par[u] = find(par[u]);
            return par[u];
        }

        void union(int u, int v) {
            int pu = find(u);
            int pv = find(v);
            if (pu == pv) {
                return;
            }
            if (pq[pu].size() > pq[pv].size()) {
                while (!pq[pv].isEmpty()) {
                    pq[pu].add(pq[pv].poll());
                }
                par[pv] = pu;
            } else {
                while (!pq[pu].isEmpty()) {
                    pq[pv].add(pq[pu].poll());
                }
                par[pu] = pv;
            }
        }

        void inactive(int u) {
            active[u] = false;
        }

        int check(int u) {
            if (active[u]) {
                return u;
            }
            int pu = find(u);
            while (!pq[pu].isEmpty() && !active[pq[pu].peek()]) {
                pq[pu].poll();
            }
            return pq[pu].isEmpty() ? -2 : pq[pu].peek();
        }
    }

    public int[] processQueries(int c, int[][] connections, int[][] queries) {
        UF uf = new UF(c);
        for (int[] con : connections) {
            int u = con[0];
            int v = con[1];
            uf.union(u - 1, v - 1);
        }
        List<Integer> res = new ArrayList<>();
        for (int[] q : queries) {
            if (q[0] == 1) {
                res.add(uf.check(q[1] - 1) + 1);
            } else {
                uf.inactive(q[1] - 1);
            }
        }
        return res.stream().mapToInt(Integer::intValue).toArray();
    }
}
```
### 🎯 Conclusion — Day 30

Day 30 tested connectivity logic, priority queue management, and Union-Find optimization — all in one! ⚡
By combining DSU for grid management and PQs for quick access to the smallest online station, I learned how to handle dynamic queries efficiently in interconnected systems.

This problem highlighted the beauty of data structure synergy — where the right mix of DSU and heap logic creates a clean, powerful solution. 🚀⚙️

---

## Day 31

# ⚙️ 50 Days of LeetCode — Day 31

Welcome to **Day 31** of my #50DaysOfCode challenge!  
Today’s problem took me deep into **binary search on answers**, **range coverage simulation**, and **prefix difference optimization** — all in one complex power-distribution scenario. ⚡🏙️

---

## 🧩 Problem — Maximize the Minimum Powered City

**LeetCode 2528 | Hard**

### 🔍 Problem Description

You are given a 0-indexed integer array `stations` of length `n`, where `stations[i]` represents the number of power stations in the `i-th` city.  
Each power station provides power to all cities within range `r`, meaning for every city `j` such that `|i - j| <= r`.

You are also given two integers `r` and `k`, where you can **build up to `k` more power stations** anywhere.  
Your goal is to **maximize the minimum power** among all cities, after optimally placing the new stations.

---

### 💡 Approach

This problem required a hybrid of **binary search** and **greedy prefix difference logic**:

1. Compute each city's **base power** using a sliding window of range `r`.  
2. Use **binary search** on the possible minimum power level `mid`.  
3. For each `mid`, simulate adding power stations using a **difference array** to ensure O(n) simulation.  
4. Greedily add stations where power < `mid` and adjust future effects via the diff array.  
5. Track if the total added stations ≤ `k`.  

The binary search continues until the maximum feasible `mid` is found — representing the highest possible *minimum city power*.

---

### ⚙️ Complexity

- **Time Complexity:** `O(n log M)` where `M` is the search range of power levels.  
- **Space Complexity:** `O(n)` due to auxiliary arrays.  

---

### 🧠 Key Insights

- Efficiently simulating station additions using a **difference array** avoids repetitive updates.  
- Binary search on the answer ensures we never overshoot feasible power values.  
- Careful window and index management is crucial to maintaining accuracy at scale (n ≤ 10⁵).

---

### 💻 Code Implementation (Java)

```java
public class Solution {
    public long maxPower(int[] stations, int r, int k) {
        int n = stations.length;
        long[] base = new long[n];
        long windowSum = 0;
        int rightBound = Math.min(n - 1, r);
        
        for (int i = 0; i <= rightBound; i++) {
            windowSum += stations[i];
        }
        base[0] = windowSum;
        
        for (int i = 1; i < n; i++) {
            int right = i + r;
            int left = i - r - 1;
            if (right < n) windowSum += stations[right];
            if (left >= 0) windowSum -= stations[left];
            base[i] = windowSum;
        }
        
        long minBase = base[0];
        long maxBase = base[0];
        for (int i = 1; i < n; i++) {
            if (base[i] < minBase) minBase = base[i];
            if (base[i] > maxBase) maxBase = base[i];
        }
        
        long low = minBase;
        long high = maxBase + k;
        if (low == high) return low;
        
        long[] diff = new long[n + 1];
        int doubleR = r << 1;
        
        while (low <= high) {
            long mid = low + ((high - low) >>> 1);
            for (int i = 0; i <= n; i++) diff[i] = 0;
            
            long added = 0;
            long remaining = k;
            boolean possible = true;
            int i = 0;
            int limit = n - 3;
            
            while (i < limit) {
                added += diff[i];
                long current = base[i] + added;
                if (current < mid) {
                    long need = mid - current;
                    if (need > remaining) {
                        possible = false;
                        break;
                    }
                    remaining -= need;
                    added += need;
                    int end = i + doubleR + 1;
                    if (end < n) diff[end] -= need;
                }
                i++;
            }
            
            while (possible && i < n) {
                added += diff[i];
                long current = base[i] + added;
                if (current < mid) {
                    long need = mid - current;
                    if (need > remaining) {
                        possible = false;
                        break;
                    }
                    remaining -= need;
                    added += need;
                    int end = i + doubleR + 1;
                    if (end < n) diff[end] -= need;
                }
                i++;
            }
            
            if (possible) {
                low = mid + 1;
            } else {
                high = mid - 1;
            }
        }
        
        return high;
    }
}
```

### 🎯 Conclusion — Day 31

Day 31 pushed my problem-solving boundaries by combining **binary search**, **range simulation**, and **greedy allocation** — all under tight performance limits. ⚙️📈  
By blending difference arrays with a smart binary search approach, I learned how to **simulate dynamic system constraints** efficiently and reason about **feasibility within optimization loops**.  

This problem beautifully demonstrated the power of algorithm layering — where mathematical reasoning meets computational precision to build scalable, high-performance solutions. 🚀💡

---

## Day 32  

# ⚙️ 50 Days of LeetCode — Day 32  

Welcome to **Day 32** of my #50DaysOfCode challenge!  
Today’s challenge was all about **bit manipulation**, **pattern recognition**, and **mathematical reasoning** — turning binary transformations into elegant XOR logic. ⚡💻  

---

## 🧩 Problem — Minimum One Bit Operations to Make Integers Zero  

**LeetCode 1611 | Hard**

### 🔍 Problem Description  

You are given an integer `n`, and you must transform it into `0` using the following operations any number of times:

1. **Change the rightmost (0th) bit** in the binary representation of `n`.  
2. **Change the ith bit** if the `(i-1)th` bit is set to 1 and all lower bits are 0.  

Return the *minimum number of operations* required to make `n = 0`.  

---

### 💡 Approach  

At first glance, this problem looks like a complex **bitwise toggle puzzle**, but beneath the surface lies a **Gray code transformation pattern**!  

Here’s how I broke it down:

1. Observe how bits flip in sequences similar to **binary reflected Gray codes**.  
2. The key insight:  
   - The number of operations needed to make `n = 0` follows a recursive XOR pattern.  
3. Instead of recursion, I optimized it into an iterative **bitwise XOR accumulation**:  
   - For every right shift of `n`, XOR it with the running total.  
4. This effectively simulates the Gray code inverse transformation in `O(log n)` time!  

---

### ⚙️ Complexity  

- **Time Complexity:** `O(log n)`  
- **Space Complexity:** `O(1)`  

---

### 🧠 Key Insights  

- Every operation mirrors **Gray code transitions** — only one bit changes at a time.  
- XOR chaining allows compact and efficient computation without recursion.  
- A pure bit-manipulation beauty — mathematical and elegant! ✨  

---

### 💻 Code Implementation (Java)

```java
public class Solution {
    public int minimumOneBitOperations(int n) {
        int result = 0;
        while (n > 0) {
            result ^= n;
            n >>= 1;
        }
        return result;
    }
}
```
### 🎯 Conclusion — Day 32

Day 32 was a mind-twister that showed how complex transformations can sometimes collapse into simple XOR patterns when you spot the underlying logic. 🔁✨

From recursive bit toggling to compact iterative logic, today’s problem was a beautiful reminder of how bit manipulation can turn chaos into clarity — the perfect harmony of math and code. 💡⚙️

---

## Day 33

# ⚙️ 50 Days of LeetCode — Day 33

Welcome to **Day 33** of my #50DaysOfCode challenge!  
Today’s problem focused on **mathematical optimization** and **Euclidean reduction**, blending number theory with iterative logic. 🔢⚙️

---

## 🧩 Problem — Count Operations to Obtain Zero

**LeetCode 2169 | Easy**

### 🔍 Problem Description

You are given two non-negative integers `num1` and `num2`.  
In one operation:
- If `num1 >= num2`, subtract `num2` from `num1`.
- Otherwise, subtract `num1` from `num2`.

The goal is to count the **number of operations** required until either `num1 = 0` or `num2 = 0`.

---

### 💡 Approach

At first glance, the problem looks like a repetitive subtraction loop.  
However, it’s actually based on the **Euclidean Algorithm** (used to find GCD).  

Instead of subtracting one by one, we can directly count how many times the smaller number fits into the larger one — using integer division.  
This significantly speeds up the process from *O(n)* to *O(log n)* efficiency. ⚡  

Each iteration performs:
1. Add `num1 / num2` to the operation count.
2. Replace `(num1, num2)` with `(num2, num1 % num2)` until one of them becomes zero.

---

### ⚙️ Complexity

- **Time Complexity:** `O(log(min(num1, num2)))`  
- **Space Complexity:** `O(1)`

---

### 💻 Code Implementation (Java)

```java
public class Solution {
    public int countOperations(int num1, int num2) {
        int ans = 0;
        while (num2 != 0) {  
            ans += num1 / num2;
            int temp = num1 % num2;
            num1 = num2;
            num2 = temp;
        }
        return ans;
    }
}
```
### 🎯 Conclusion — Day 33

Day 33 was all about recognizing hidden mathematical patterns inside a simple iterative problem.
By converting repeated subtraction into a division-based Euclidean step, I learned how mathematical insight can simplify logic and optimize runtime drastically. ⚙️💡

It’s fascinating how even “easy” problems often hide elegant, high-performance solutions waiting to be uncovered. 🚀✨

---

## Day 34

# ⚙️ 50 Days of LeetCode — Day 34

Welcome to **Day 34** of my #50DaysOfCode challenge!  
Today’s problem explored **subarray manipulation**, **monotonic stack logic**, and **pattern-based operation minimization** — a perfect blend of data structure efficiency and mathematical reasoning. ⚡📊  

---

## 🧩 Problem — Minimum Operations to Convert All Elements to Zero  

**LeetCode 3542 | Medium**

### 🔍 Problem Description  

You are given an array `nums` of non-negative integers.  
In one operation, you can:
- Select a subarray `[i, j]`.
- Set all occurrences of the **minimum non-negative integer** in that subarray to `0`.

The goal is to determine the **minimum number of operations** needed to make **all elements zero**.

---

### 💡 Approach  

This problem initially appears to require direct simulation, but a deeper insight reveals that it’s all about **tracking distinct positive layers** of reduction.  

I used a **monotonic stack-like approach** to efficiently handle overlapping subarrays and minimize redundant operations:
1. Traverse through `nums` while maintaining a stack of increasing elements.
2. When encountering a smaller element, pop larger ones and count unique reductions.
3. Reset on zero, since zero acts as a natural separator for subarrays.
4. The total count equals the distinct reduction operations needed.

This approach ensures that every new “rise” or “reset” in values contributes only when truly necessary — keeping the total operations minimal. ⚙️

---

### ⚙️ Complexity  

- **Time Complexity:** `O(n)`  
- **Space Complexity:** `O(n)`  

---

### 💻 Code Implementation (Java)  

```java
public class Solution {
    public int minOperations(int[] nums) {
        int[] mq = new int[nums.length];
        int idx = 0;
        int res = 0;
        for (int num : nums) {
            if (num == 0) {
                res += idx;
                idx = 0;
            } else {
                while (idx > 0 && mq[idx - 1] >= num) {
                    if (mq[idx - 1] > num) {
                        res++;
                    }
                    idx--;
                }
                mq[idx++] = num;
            }
        }
        return res + idx;
    }
}
```

### 🎯 Conclusion — Day 34

Day 34 reinforced the power of pattern recognition and stack-based reasoning in transforming a brute-force simulation into a linear-time solution.
By treating the array as layered subarrays of rising values, I learned how to peel away each layer efficiently — turning a seemingly complex process into a clean, elegant algorithm. 🌟💡

Each problem like this deepens my understanding of how data structures + logic design = true optimization magic. 🚀🔥

---

## Day 35

# ⚙️ 50 Days of LeetCode — Day 35

Welcome to **Day 35** of my #50DaysOfCode challenge!  
Today’s problem explored the fascinating intersection of **Dynamic Programming (DP)** and **resource allocation logic**, testing how efficiently we can maximize subsets under multiple constraints. ⚙️💡  

---

## 🧩 Problem — Ones and Zeroes  

**LeetCode 474 | Medium**

### 🔍 Problem Description  

You are given an array of binary strings `strs` and two integers `m` and `n`.  
Your task is to find the **largest subset** of `strs` such that:  
- The subset contains **at most `m` zeros** and **at most `n` ones**.  

Essentially, it’s about choosing the most strings possible while staying within two capacity limits — one for `0`s and one for `1`s.  

---

### 💡 Approach  

This problem is a perfect example of the **0/1 Knapsack** pattern extended into **two dimensions** — one for zeros and one for ones.  

Here’s the strategy:
1. For each binary string, count how many `0`s and `1`s it contains.
2. Use a **2D DP table** `dp[m+1][n+1]` where `dp[i][j]` represents the maximum subset size achievable with `i` zeros and `j` ones.
3. Iterate backward (to avoid overwriting previous states), and for each string, decide whether to include it or not.
4. The final answer lies in `dp[m][n]`, representing the largest subset fitting within the given limits.

This bottom-up dynamic approach ensures we explore all possibilities while maintaining efficiency. ⚙️✨  

---

### ⚙️ Complexity  

- **Time Complexity:** `O(len(strs) * m * n)`  
- **Space Complexity:** `O(m * n)`  

---

### 💻 Code Implementation (Java)  

```java
public class Solution {
    public int findMaxForm(String[] strs, int m, int n) {
        int[][] dp = new int[m + 1][n + 1];
        
        for (String str : strs) {
            int zeros = 0, ones = 0;
            
            for (char c : str.toCharArray()) {
                if (c == '0') zeros++;
                else ones++;
            }
            
            if (zeros > m || ones > n) continue;
            
            for (int i = m; i >= zeros; i--) {
                for (int j = n; j >= ones; j--) {
                    dp[i][j] = Math.max(dp[i][j], dp[i - zeros][j - ones] + 1);
                }
            }
        }
        
        return dp[m][n];
    }
}


```

### 🎯 Conclusion — Day 35

Day 35 was all about dynamic decision-making under dual constraints — a step deeper into advanced DP thinking.
By converting the problem into a 2D knapsack model, I learned how to manage multiple resource limits efficiently while maximizing outcomes. 🧠⚡

It was a strong reminder that DP isn’t about memorizing patterns — it’s about structuring logic to reuse past solutions smartly. 💪🚀

---
## Day 36  

# ⚙️ 50 Days of LeetCode — Day 36  

Welcome to **Day 36** of my #50DaysOfCode challenge!  
Today’s challenge delved into **GCD-based transformations**, **subarray optimization**, and **mathematical reasoning**, blending number theory with algorithmic problem-solving. 🧮⚙️  

---

## 🧩 Problem — Minimum Number of Operations to Make All Array Elements Equal to 1  

**LeetCode 2654 | Medium**  

### 🔍 Problem Description  

You are given a `0-indexed` array `nums` consisting of positive integers.  
You can perform the following operation any number of times:  
- Choose an index `i` such that `0 <= i < n - 1`  
- Replace **either** `nums[i]` or `nums[i+1]` with `gcd(nums[i], nums[i+1])`  

Return the **minimum number of operations** needed to make **all elements in the array equal to 1**.  
If it’s impossible, return `-1`.  

---

### 💡 Approach  

This problem combines **mathematics** and **optimization**:  
We first check if there are any existing `1`s — because each `1` can help convert neighboring numbers faster.  
If `cnt1 > 0`, we simply need `n - cnt1` operations to make all elements `1`.  

If there are **no 1s**, we must create one by finding the **shortest subarray** whose GCD equals `1`.  
Each such subarray represents the minimum number of operations required to generate the first `1`.  

Steps:  
1. Count how many elements are already `1`.  
2. If any exist, the result = `n - cnt1`.  
3. Otherwise, for each subarray `(i, j)`, compute cumulative `gcd`.  
4. When `gcd == 1`, update the smallest subarray length.  
5. Final answer = `minSubarray + n - 1` (total operations).  

If no subarray GCD ever reaches `1`, it’s **impossible**, hence return `-1`.  

---

### ⚙️ Complexity  

- **Time Complexity:** `O(n² * log(max(nums)))`  
- **Space Complexity:** `O(1)`  

---

### 💻 Code Implementation (Java)  

```java
public class Solution {
    private int gcd(int a, int b) {
        if (b == 0) {
            return a;
        }
        return gcd(b, a % b);
    }

    public int minOperations(int[] nums) {
        int cnt1 = 0;
        int minsubarray = Integer.MAX_VALUE;
        for (int x : nums) {
            if (x == 1) {
                cnt1++;
            }
        }

        if (cnt1 > 0) {
            return nums.length - cnt1;
        }

        for (int i = 0; i < nums.length; i++) {
            int curgcd = nums[i];
            for (int j = i + 1; j < nums.length; j++) {
                curgcd = gcd(curgcd, nums[j]);
                if (curgcd == 1) {
                    minsubarray = Math.min(minsubarray, j - i);
                    break;
                }
            }
        }
        if (minsubarray != Integer.MAX_VALUE) {
            return minsubarray + nums.length - 1;
        }
        return -1;
    }
}

```

### 🎯 Conclusion — Day 36

Day 36 was a perfect example of how number theory and logic flow together to form elegant solutions.
By combining GCD computation with minimal subarray tracking, I learned how mathematical insight can simplify what initially feels like a brute-force process.

This problem reinforced how understanding fundamental operations like GCD can unlock efficiency and clarity in algorithm design. 🚀🧠

---

## Day 37  

# ⚙️ 50 Days of LeetCode — Day 37  

Welcome to **Day 37** of my #50DaysOfCode challenge!  
Today’s problem focused on **binary string manipulation**, **pattern observation**, and **mathematical reasoning**, bringing together logical flow and efficient iteration. 💡⚙️  

---

## 🧩 Problem — Maximum Number of Operations to Move Ones to the End  

**LeetCode 3228 | Medium**  

### 🔍 Problem Description  

You are given a binary string `s`.  

You can perform the following operation any number of times:  
- Choose any index `i` where `0 <= i < s.length - 1`, such that `s[i] == '1'` and `s[i + 1] == '0'`.  
- Move `s[i]` to the right until it reaches the end of the string or just before another `'1'`.  

Return the **maximum number of operations** you can perform.  

---

### 💡 Approach  

The key insight is to **count valid transitions** where a `'1'` can move past `'0'`s — while keeping track of how many `'1'`s have appeared so far.  

Steps:  
1. Convert the string into a character array.  
2. Maintain two counters —  
   - `ones` → counts how many `'1'`s are seen so far.  
   - `result` → counts how many valid moves can be made.  
3. Traverse the string:  
   - For every `'1'`, increment `ones`.  
   - Whenever a `'1'` precedes a `'0'` (i.e., `arr[i] < arr[i - 1]`), it means this `'1'` can perform operations equal to `ones`.  
4. Sum up all possible moves.  

This efficient single-pass approach captures all valid transitions without any complex rearrangement simulation. ⚡  

---

### ⚙️ Complexity  

- **Time Complexity:** `O(n)`  
- **Space Complexity:** `O(1)`  

---

### 💻 Code Implementation (Java)  

```java
public class Solution {
    public int maxOperations(String s) {
        char[] arr = s.toCharArray();
        int result = 0;
        int ones = 0;
        int n = arr.length;
        for (int i = 0; i < n; ++i) {
            ones += arr[i] - '0';
            if (i > 0 && arr[i] < arr[i - 1]) {
                result += ones;
            }
        }
        return result;
    }
}
```

---

### 🎯 Conclusion — Day 37  

Day 37 reinforced the beauty of **pattern-based reasoning** — showing how understanding transitions and counters can replace brute-force simulation.  
By analyzing movement logic mathematically, I learned how to transform a seemingly complex “string shifting” problem into a clean linear solution. 🚀🧠  

---
## Day 38  

# ⚙️ 50 Days of LeetCode — Day 38  

Welcome to **Day 38** of my #50DaysOfCode challenge!  
Today’s problem explored **2D difference arrays**, **prefix sums**, and efficient matrix range updates — turning a brute-force problem into a fast and elegant solution. ⚡📊  

---

## 🧩 Problem — Increment Submatrices by One  

**LeetCode 2536 | Medium**  

### 🔍 Problem Description  

You are given an integer `n` representing an `n x n` matrix of zeroes.  
Each query `[row1, col1, row2, col2]` increments all cells in the defined submatrix by `1`.  

The challenge is to efficiently apply all queries and return the final matrix.

---

### 💡 Approach  

Directly incrementing each submatrix per query would be too slow.  
Instead, we use a **2D difference array**, which lets us mark each update in constant time.

Steps:  
1. Initialize a 2D diff array `g`.  
2. For each query, increment the top-left corner and adjust boundaries using difference array rules.  
3. Build the final matrix by applying prefix sums row-wise and column-wise.  

This transforms the problem from an expensive nested update process to an efficient prefix-based solution. 🚀

---

### ⚙️ Complexity  

- **Time Complexity:** `O(n² + q)`  
- **Space Complexity:** `O(n²)`  

---

### 💻 Code Implementation (Java)

```java
public class Solution {
    public int[][] rangeAddQueries(int n, int[][] queries) {
        int[][] g = new int[n][n];
        
        for (int[] q : queries) {
            int r1 = q[0], c1 = q[1], r2 = q[2], c2 = q[3];
            
            g[r1][c1]++;
            if (c2 + 1 < n) g[r1][c2 + 1]--;
            if (r2 + 1 < n) g[r2 + 1][c1]--;
            if (r2 + 1 < n && c2 + 1 < n) g[r2 + 1][c2 + 1]++;
        }
        
        for (int i = 0; i < n; i++) {
            for (int j = 1; j < n; j++) {
                g[i][j] += g[i][j - 1];
            }
        }
        
        for (int j = 0; j < n; j++) {
            for (int i = 1; i < n; i++) {
                g[i][j] += g[i - 1][j];
            }
        }
        
        return g;
    }
}
```

### 🎯 Conclusion — Day 38  

Day 38 highlighted the power of difference arrays and how they simplify multi-range updates.
It reinforced how clever preprocessing can turn a heavy 2D problem into a clean, optimized solution. 🧠✨

---
## Day 39  

# ⚙️ 50 Days of LeetCode — Day 39  

Welcome to **Day 39** of my #50DaysOfCode challenge!  
Today’s problem was a deep dive into **binary string analysis**, **mathematical constraints**, and **optimized substring counting**.  
A perfect blend of logic, pattern recognition, and performance-oriented thinking! 🧠⚡  

---

## 🧩 Problem — Count the Number of Substrings With Dominant Ones  

**LeetCode 3234 | Medium**  

### 🔍 Problem Description  

You are given a binary string `s`.  
A substring is said to have **dominant ones** if:  

**Ones ≥ (Zeros²)**

Your task is to **count how many substrings satisfy this condition**.  

With string lengths up to **40,000**, brute-force checking for all substrings is impossible — making optimization essential.  

---

### 💡 Approach  

The challenge lies in efficiently tracking zeros and determining valid substring ranges.  

This solution uses a combination of:  
- A **zero index list** to quickly identify zero positions  
- **Prefix-based logic** to count substrings with no zeros efficiently  
- A mathematical limit `j*(j+1) <= length` to decide how many zero-based checks are necessary  
- Sliding window around zero positions to compute valid ranges  

Key steps:  
1. Store indices of zeros for quick access.  
2. For each index, count zero-free substrings using previous zero boundaries.  
3. For substrings with zeros, calculate the maximum number of zeros allowed via mathematical constraints.  
4. For each valid zero count, update the result by examining gaps between zero indices.  

This transforms a potential *O(n²)* brute-force into a smart, optimized counting strategy. 🚀  

---

### ⚙️ Complexity  

- **Time Complexity:** ~`O(n * sqrt(n))` due to limited zero checks  
- **Space Complexity:** `O(n)`  

---

### 💻 Code Implementation (Java)

```java
public class Solution {
    public int numberOfSubstrings(String s) {
        int n = s.length();
        int[] zero = new int[n + 1];
        int zeroCount = 0;
        zero[zeroCount++] = -1;
        
        long result = 0;
        
        for (int i = 0; i < n; i++) {
            if (s.charAt(i) == '0') {
                zero[zeroCount++] = i;
            } else {
                result += i - zero[zeroCount - 1];
            }
            
            int maxJ = (int)((Math.sqrt(1 + 4.0 * (i + 1)) - 1) / 2);
            int limit = Math.min(zeroCount - 1, maxJ);
            
            for (int j = 1; j <= limit; j++) {
                int len = j * (j + 1);
                int prev = zero[zeroCount - j - 1];
                int curr = zero[zeroCount - j];
                int from = Math.min(i - len + 1, curr);
                
                if (from > prev) {
                    result += from - prev;
                }
            }
        }
        return (int) result;
    }
}

```

### 🎯 Conclusion — Day 39  

Day 39 showcased the beauty of combining mathematical constraints with prefix logic to solve complex substring problems efficiently.
This problem reinforced how thinking in terms of boundaries, zero positions, and mathematical limits can drastically reduce computation — turning an exponential problem into an elegant optimized solution. ✨

---
## Day 40  

# ⚙️ 50 Days of LeetCode — Day 40  

Welcome to **Day 40** of my #50DaysOfCode challenge!  
Today’s problem focused on **binary strings**, **consecutive sequences**, and a simple but powerful counting technique that avoids generating substrings directly. ⚡🔥  

---

## 🧩 Problem — Number of Substrings With Only 1s  

**LeetCode 1513 | Medium**  

### 🔍 Problem Description  

Given a binary string `s`, the goal is to count how many substrings consist only of `'1'` characters.  
Since the total count can be large, the result is returned modulo **1,000,000,007**.

---

### 💡 Approach  

Instead of checking every possible substring (which would be too slow), the solution uses the idea that:

- Every time we encounter a `'1'`, it extends all previous `'1'`-only substrings.
- A sequence of length `k` (like `"111"`) forms:
  - `1` substring of length 3  
  - `2` substrings of length 2  
  - `3` substrings of length 1  
- Altogether: `1 + 2 + 3 = 6` substrings.

So while iterating:
1. Maintain a running count of consecutive `'1'` characters.
2. Add this count to the result each time a `'1'` is found.
3. Reset the counter when a `'0'` appears.

This approach avoids substring generation and works in a single pass. 🚀

---

### ⚙️ Complexity  

- **Time Complexity:** `O(n)`  
- **Space Complexity:** `O(1)`  

---

### 💻 Code Implementation (Java)

```java
public class Solution {
    public int numSub(String s) {
        final int MOD = 1_000_000_007;
        long res = 0;
        int count = 0;
        int n = s.length();

        for (int i = 0; i < n; i++) {
            if (s.charAt(i) == '1') {
                count++;
                res += count;
            } else {
                count = 0;
            }
        }

        return (int)(res % MOD);
    }
}

```

### 🎯 Conclusion — Day 40  

Day 40 reinforced how recognizing patterns in sequences can simplify problems drastically.
By counting consecutive '1' runs efficiently, we transform what appears to be a substring-heavy problem into a clean linear solution. 🧠✨

---
## Day 41  

# ⚙️ 50 Days of LeetCode — Day 41  

Welcome to **Day 41** of my #50DaysOfCode challenge!  
Today’s problem explored **binary arrays**, **distance constraints**, and a clean linear scan to verify spacing rules between specific values. ⚡📏  

---

## 🧩 Problem — Check If All 1's Are at Least Length K Places Away  

**LeetCode 1437 | Easy**  

### 🔍 Problem Description  

You are given a binary array `nums` and an integer `k`.  
The task is to determine whether **every pair of `1`s** in the array is separated by **at least `k` zeroes**.

If every `1` satisfies this spacing condition, return `true`; otherwise return `false`.

---

### 💡 Approach  

The key observation is simple:

- Track the **distance** between consecutive `1`s.
- Maintain a counter `space` that counts how many elements have passed since the last `1`.
- When you encounter a new `1`:
  - If `space < k`, the spacing rule is violated → return false.
  - Reset `space` to 0.

This allows the entire check to be done in a **single pass**, without storing indices or doing extra computations. 🚀

---

### ⚙️ Complexity  

- **Time Complexity:** `O(n)`  
- **Space Complexity:** `O(1)`  

---

### 💻 Code Implementation (Java)

```java
public class Solution {
    public boolean kLengthApart(int[] nums, int k) {
        int space = k;
        for (int x : nums) {
            if (x == 1) {
                if (space < k) return false;
                space = 0;
            } else {
                space++;
            }
        }
        return true;
    }
}

```

### 🎯 Conclusion — Day 41  

Day 41 reinforced how simple constraints can often be validated with efficient linear logic.
Instead of tracking all positions of 1s, a running counter was enough to ensure the spacing condition — proving again that optimal solutions often come from clean, minimalistic thinking. 🧠✨

---
## Day 42  

# ⚙️ 50 Days of LeetCode — Day 42  

Welcome to **Day 42** of my #50DaysOfCode challenge!  
Today’s problem focused on interpreting **binary-encoded characters**, distinguishing between **1-bit** and **2-bit** patterns, and determining the type of the final character. ⚡🔢  

---

## 🧩 Problem — 1-bit and 2-bit Characters  

**LeetCode 717 | Easy**  

### 🔍 Problem Description  

You are given an array `bits` representing a sequence of characters:  
- `0` represents a **1-bit character**  
- `10` or `11` represents a **2-bit character**  

Since the array always ends with a `0`, you must determine whether this **last 0 represents a 1-bit character**.

You decode the array **from left to right**, skipping 1 or 2 positions depending on the bit pattern.

Return **true** if the last character is a *one-bit* character; otherwise return **false**.

---

### 💡 Approach  

The idea is to simulate the decoding process:

- Start from index `i = 0`.
- If `bits[i] == 1`, it must be a **2-bit character**, so skip `i += 2`.
- If `bits[i] == 0`, it's a **1-bit character**, so skip `i += 1`.
- Continue until reaching the final index.

In the end:
- If `i` stops **exactly at the last index**, the last character is a 1-bit character → return true.
- If `i` jumps past it, then the last bit was part of a 2-bit encoding → return false.

A clean linear simulation solves everything efficiently. 🚀

---

### ⚙️ Complexity  

- **Time Complexity:** `O(n)`  
- **Space Complexity:** `O(1)`  

---

### 💻 Code Implementation (Java)

```java
public class Solution {
    public boolean isOneBitCharacter(int[] arr) {
        int i = 0;
        while (i < arr.length - 1) {
            i = (arr[i] == 1) ? i + 2 : i + 1;
        }
        return (i == arr.length - 1);
    }
}

```

### 🎯 Conclusion — Day 42  

Day 42 highlighted how some decoding problems can be solved with a simple pointer walk.
Instead of reconstructing characters or storing patterns, just simulate the jumps — and the final position reveals the answer.
A great reminder that minimalistic logic often leads to the cleanest solutions! 🧠✨

---
## Day 43  

# ⚙️ 50 Days of LeetCode — Day 43  

Welcome to **Day 43** of my #50DaysOfCode challenge!  
Today’s problem explored **value tracking**, **set membership**, and repeatedly updating a number based on its presence in the array. 🔁⚡  

---

## 🧩 Problem — Keep Multiplying Found Values by Two  

**LeetCode 2154 | Easy**  

### 🔍 Problem Description  

You are given an integer array `nums` and an integer `original`.  
Your task is simple:

- If `original` exists in `nums`, multiply it by 2.  
- Repeat this process as long as the updated value still exists in the array.  
- Once the value is not found, return it.  

This creates a chain of transformations like:  
`original → 2×original → 4×original → ...`  
until the value no longer appears in the list.

---

### 💡 Approach  

To efficiently check whether a number exists in `nums`, we use a **boolean lookup array**:

1. Create a `seen[]` array to mark every number present in `nums`.  
2. While the current `original` value is found in `seen`, multiply it by 2.  
3. Stop when the value no longer exists and return it.

This avoids repeated scanning of the array and makes each lookup **O(1)** — perfect for quick iterations. 🚀  

---

### ⚙️ Complexity  

- **Time Complexity:** `O(n)`  
- **Space Complexity:** `O(max(nums[i]))`  

---

### 💻 Code Implementation (Java)

```java
public class Solution {
    public int findFinalValue(int[] nums, int original) {
        boolean[] seen = new boolean[2001];
        for (int x : nums) seen[x] = true;

        while (original < seen.length && seen[original]) {
            original <<= 1;
        }
        return original;
    }
}

```

### 🎯 Conclusion — Day 43  

Day 43 demonstrated how simple problems can be optimized with the right data structure.
Using a lookup array transformed repeated searches into instant checks, making the solution clean, fast, and scalable.
Another reminder that smart preprocessing often leads to elegant solutions! ✨🧠

---