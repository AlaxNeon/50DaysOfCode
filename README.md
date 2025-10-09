<div align="right">
<details>
<summary><b>📅 Navigate Days</b></summary>

- [Day 1](#day-1)
- [Day 2](#day-2)
- [Day 3 — Coming Soon 🚧](#day-3)
- [Day 4 — Coming Soon 🚧](#day-4)
- [Day 5 — Coming Soon 🚧](#day-5)

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