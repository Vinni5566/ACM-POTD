## Problem

**Min Stack (LeetCode 155)**

Design a stack that supports:

* push  
* pop  
* top  
* getMin  

All operations must run in **O(1)** time.

---

## Approach

Use **two stacks**:

### Logic:

* `st` → stores all elements  
* `min` → stores minimum elements  

* On push:
  - Push value to `st`
  - Push to `min` only if:
    * it is empty OR
    * value ≤ current minimum  

* On pop:
  - If top of both stacks is same → pop from both  

* `top()` → return top of `st`  
* `getMin()` → return top of `min`  

---

## Complexity

* **Time Complexity:** O(1) for all operations  
* **Space Complexity:** O(n)  

---

## Solution

```cpp
class MinStack {
private:
    stack<int> st;
    stack<int> min;
public:
    MinStack() {
        
    }
    
    void push(int val) {
        st.push(val);
        
        if(min.empty()) {
            min.push(val);
        } else {
            if(val <= min.top()) {
                min.push(val);
            }
        }
    }
    
    void pop() {

        if(!min.empty() && min.top() == st.top()) {
            min.pop();
        }

        if(!st.empty()) st.pop();
    }
    
    int top() {
        if(!st.empty()) return st.top();
        return -1;
    }
    
    int getMin() {
        if(!min.empty()) return min.top();
        return 0;
    }
};
```

---

## Proof of Submission

![alt text](../screenshots/Intermediate/day-15.png)

---