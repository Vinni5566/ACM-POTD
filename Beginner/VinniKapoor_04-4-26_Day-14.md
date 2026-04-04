## Problem

**Palindrome Linked List (LeetCode 234)**

Given the head of a singly linked list, return `true` if it is a palindrome, otherwise return `false`.

---

## Approach

Use a **stack to compare forward and reverse order**.

### Logic:

* Traverse the list and push all values into a stack
* Traverse the list again:
  - Compare current node value with top of stack
  - If mismatch → return false
* If all values match → return true

---

## Complexity

* **Time Complexity:** O(n)  
* **Space Complexity:** O(n)  

---

## Solution

```cpp
#include <stack>

class Solution {
public:
    bool isPalindrome(ListNode* head) {
        if (head == nullptr || head->next == nullptr) return true;

        std::stack<int> s;
        ListNode* curr = head;

        // Push all values onto the stack
        while (curr != nullptr) {
            s.push(curr->val);
            curr = curr->next;
        }

        // Compare stack (reverse order) with linked list (original order)
        curr = head;
        while (curr != nullptr) {
            if (curr->val != s.top()) {
                return false;
            }
            s.pop();
            curr = curr->next;
        }

        return true;
    }
};
```

---

## Proof of Submission

![alt text](../screenshots/Intermediate/day-14.png)

---