## Problem

**Remove Duplicates from Sorted List II (LeetCode 82)**

Given the head of a sorted linked list, delete all nodes that have duplicate numbers, leaving only distinct numbers from the original list.

Return the linked list sorted as well.

---

## Approach

Use **in-place traversal with duplicate detection**.

### Logic:

* Traverse the list using pointer `curr`
* For each group of nodes:
  - Check if it contains duplicates
  - Skip all duplicate nodes
* If a value appears only once:
  - Add it to the new list
* Maintain:
  - `newHead` → head of result list  
  - `tail` → last node of result list  

---

## Complexity

* **Time Complexity:** O(n)  
* **Space Complexity:** O(1)  

---

## Solution

```cpp
class Solution {
public:
    ListNode* deleteDuplicates(ListNode* head) {

        if(head == NULL || head->next == NULL) return head;

        ListNode* curr = head;

        ListNode* newHead = NULL;
        ListNode* tail = NULL;

        while(curr != NULL) {

            bool isDuplicate = false;

            while(curr->next != NULL && curr->val == curr->next->val) {
                curr = curr->next;
                isDuplicate = true;
            }

            if(!isDuplicate) {
                if(!newHead) {
                    newHead = curr;
                    tail = curr;
                } else {
                    tail->next = curr;
                    tail = tail->next;
                }
            }

            curr = curr->next;
        }

        if(newHead != NULL) tail->next = NULL;

        return newHead;
        
    }
};
```

---

## Proof of Submission

![alt text](../screenshots/Intermediate/day-13.png)

---