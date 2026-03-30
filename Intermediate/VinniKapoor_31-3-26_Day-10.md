## Problem

**Add Two Numbers (LeetCode 2)**

You are given two non-empty linked lists representing two non-negative integers.  
The digits are stored in reverse order, and each of their nodes contains a single digit.

Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

---

## Approach

Use **simulation with carry handling**.

### Logic:

* Use a dummy node to build the result list
* Traverse both lists simultaneously
* At each step:
  - Add digits from both lists (if available)
  - Add carry from previous step
* Create a new node with `(sum % 10)`
* Update carry as `(sum / 10)`
* Continue until both lists and carry are exhausted

---

## Complexity

* **Time Complexity:** O(max(n, m))  
* **Space Complexity:** O(max(n, m))  

---

## Solution

```cpp
class Solution {
public:
    ListNode* addTwoNumbers(ListNode* l1, ListNode* l2) {
        
        ListNode dummy(0);          // dummy head for result list
        ListNode* tail = &dummy;    // pointer to build the list
        int carry = 0;              // carry for addition

        while (l1 || l2 || carry) {
            int sum = carry;        // start with carry from previous step
            
            if (l1) {
                sum += l1->val;    // add digit from l1
                l1 = l1->next;     // move to next node
            }
            if (l2) {
                sum += l2->val;    // add digit from l2
                l2 = l2->next;     // move to next node
            }

            carry = sum / 10;                 // update carry
            tail->next = new ListNode(sum % 10); // create new node with single digit
            tail = tail->next;                // move tail
        }

        return dummy.next;  // return head of the result list
        
    }
};
```

---

## Proof of Submission

![alt text](../screenshots/Intermediate/day-10.png)

---