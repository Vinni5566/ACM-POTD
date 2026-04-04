## Problem

**Swap Nodes in Pairs (LeetCode 24)**

Given a linked list, swap every two adjacent nodes and return its head.

You must solve the problem without modifying the values in the list's nodes (i.e., only nodes themselves may be changed).

---

## Approach

Use **iterative traversal and swap values of adjacent nodes**.

### Logic:

* Traverse the list using pointer `curr`
* While there are at least two nodes:
  - Swap values of current node and next node
  - Move `curr` by two steps
* Continue until end of list

---

## Complexity

* **Time Complexity:** O(n)  
* **Space Complexity:** O(1)  

---

## Solution

```cpp
class Solution {
public:
    ListNode* swapPairs(ListNode* head) {
        
        if(head == NULL || head->next == NULL) return head;

        ListNode* curr = head;

        while(curr && curr->next) {
            int temp = curr->val;
            curr->val = curr->next->val;
            curr->next->val = temp;

            curr = curr->next->next;
        }

        return head;
    }
};
```

---

## Proof of Submission

![alt text](../screenshots/Intermediate/day-14.png)

---