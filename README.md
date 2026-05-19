# leetcode-61-rotate-list
C++ solution for LeetCode 61 - Rotate List using efficient circular linked list approach.
# Rotate List (LeetCode 61)

## 🚀 Problem Statement
Given the head of a linked list, rotate the list to the right by `k` places.

---

## 💡 Approach
- Find the length of the linked list.
- Connect the last node to the head to form a circular list.
- Compute effective rotations using `k % n`.
- Find the new tail at position `(n - k - 1)`.
- Break the circle to get the rotated list.

---

## 🧠 Example
Input:
head = [1,2,3,4,5], k = 2  

Output:
[4,5,1,2,3]

---

## ✅ Code (C++)
```cpp
class Solution {
public:
    ListNode* rotateRight(ListNode* head, int k) {
        if (!head || !head->next || k == 0) return head;

        ListNode* temp = head;
        int n = 1;

        while (temp->next) {
            temp = temp->next;
            n++;
        }

        temp->next = head;

        k = k % n;
        int steps = n - k;

        ListNode* newTail = head;
        for (int i = 1; i < steps; i++) {
            newTail = newTail->next;
        }

        ListNode* newHead = newTail->next;
        newTail->next = NULL;

        return newHead;
    }
};
