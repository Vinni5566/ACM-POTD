## Problem

**Missing Number (LeetCode 268)**

Given an array `nums` containing `n` distinct numbers in the range `[0, n]`, return the only number in the range that is missing from the array.

---

## Approach

Use the **mathematical sum formula** to find the missing number.

### Logic:

* The sum of numbers from `0` to `n` is:

  `n * (n + 1) / 2`

* Compute:
  - `expectedSum` → sum of all numbers from `0` to `n`
  - `actualSum` → sum of elements in the array

* The missing number is:

  `expectedSum - actualSum`

---

## Complexity

* **Time Complexity:** O(n)  
* **Space Complexity:** O(1)  

---

## Solution

```cpp
class Solution {
public:
    int missingNumber(vector<int>& nums) {
        int n = nums.size();
        int expectedSum = n * (n + 1) / 2;  // sum from 0 to n
        int actualSum = 0;
        
        for (int num : nums) {
            actualSum += num;
        }
        
        return expectedSum - actualSum;
    }
};
```

---

## Proof of Submission

![alt text](../screenshots/Beginner/day-04.png)

---