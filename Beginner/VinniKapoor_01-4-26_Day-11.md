## Problem

**Merge Two Sorted Lists (LeetCode 21)**

You are given the heads of two sorted linked lists `list1` and `list2`.

Merge the two lists into one sorted list. The list should be made by splicing together the nodes of the first two lists.

Return the head of the merged linked list.

---

## Approach

Use **iterative merging with two pointers**.

### Logic:

* Traverse both lists using pointers
* At each step:
  - Pick the smaller node
  - Attach it to the merged list
* Maintain:
  - `head` → start of merged list  
  - `tail` → last node in merged list  
* After loop, attach remaining nodes

---

## Complexity

* **Time Complexity:** O(n + m)  
* **Space Complexity:** O(1)  

---

## Solution

```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {

        if (list1 == NULL) return list2;

        if(list2 == NULL) return list1;

        // Head of merged list
        ListNode* head = NULL;
        // Tail pointer to build the list
        ListNode* tail = NULL;

        ListNode* h1 = list1;
        ListNode* h2 = list2;

        // Merge while both lists have nodes
        while (h1 && h2) {

            // Pick smaller node
            ListNode* chosen;
            if (h1->val <= h2->val) {
                chosen = h1;
                h1 = h1->next;
            } else {
                chosen = h2;
                h2 = h2->next;
            }

            if (head == NULL) {
                head = chosen;
                tail = chosen;
            } 
            // Attach node to merged list
            else {
                tail->next = chosen;
                tail = tail->next;
            }
        }

        // Attach remaining nodes
        if (h1) tail->next = h1;
        if (h2) tail->next = h2;

        return head;
    }
};
```

---

## Proof of Submission

![alt text](../screenshots/Beginner/day-11.png)

---