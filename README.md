<!-- ──────────────── 🎯 NAVIGATION DROPDOWN ──────────────── -->
<div align="right">

<details>
<summary><b>📅 Navigate Days</b></summary>

- [Day 1 — Problem Solving & DSA](#-day-1)
- [Day 2 — Dynamic Programming & Optimization](#-day-2)
- [Day 3 — Coming Soon 🚧](#coming-soon-)
- [Day 4 — Coming Soon 🚧](#coming-soon-)
- [Day 5 — Coming Soon 🚧](#coming-soon-)

</details>

</div>

## Day 1
# 🚀 50 Days of Code — Day 1

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
# 🚀 50 Days of Code — Day 2

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

