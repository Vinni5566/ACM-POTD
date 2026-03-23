## Problem

**Two Sum (LeetCode 1)**

Given an array of integers `nums` and an integer `target`, return indices of the two numbers such that they add up to target.

You may assume that each input has exactly one solution, and you may not use the same element twice.

You can return the answer in any order.

---

## Approach

Use a **hash map (unordered_map)** to store elements while iterating.

* Key → number  
* Value → index  

### Logic:

* Traverse the array
* For each element, calculate:
  
  `complement = target - nums[i]`

* Check if complement exists in the map:
  * If yes → solution found  
  * If no → store current element in map  

---

## Complexity

* **Time Complexity:** O(n)  
* **Space Complexity:** O(n)  

---

## Solution

```cpp
class Solution {
public:
    vector<int> twoSum(vector<int>& nums, int target) {
        // Map to store: {value : index}
        unordered_map<int, int> numMap;
        
        for (int i = 0; i < nums.size(); i++) {
            int complement = target - nums[i];
            
            // Check if complement already exists in the map
            if (numMap.find(complement) != numMap.end()) {
                return {numMap[complement], i};
            }
            
            // Otherwise, store current number and its index
            numMap[nums[i]] = i;
        }
        
        return {};
    }
};

---

## Proof of Submission

![alt text](screenshots/Beginner/day-2.png)

---