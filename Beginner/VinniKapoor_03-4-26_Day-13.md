## Problem

**Rotate List (LeetCode 61)**

Given the head of a linked list, rotate the list to the right by `k` places.

---

## Approach

Use **circular linked list + pointer adjustment**.

### Logic:

* Handle edge cases:
  - Empty list
  - Single node
  - `k = 0`

* Traverse to:
  - Find length `n`
  - Get last node

* Make list circular:
  - Connect last node to head

* Compute effective rotation:
  - `k = k % n`

* Find new tail:
  - `(n - k - 1)` steps from head

* Set:
  - `newHead = newTail->next`

* Break the cycle:
  - `newTail->next = NULL`

---

## Complexity

* **Time Complexity:** O(n)  
* **Space Complexity:** O(1)  

---

## Solution

```cpp
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        
        if (!head || !head->next || k == 0) return head;

        //find length and last node
        ListNode* curr = head;
        int n = 1;
        while (curr->next) {
            curr = curr->next;
            n++;
        }

        //make it circular
        curr->next = head;

        //find new tail and new head
        k = k % n; //handle k > n
        int stepsToNewTail = n - k - 1;
        ListNode* newTail = head;
        for (int i = 0; i < stepsToNewTail; i++) {
            newTail = newTail->next;
        }

        ListNode* newHead = newTail->next;

        //break the circle
        newTail->next = nullptr;

        return newHead;

    }
};
```

---

## Proof of Submission

![alt text](../screenshots/Beginner/day-13.png)

---