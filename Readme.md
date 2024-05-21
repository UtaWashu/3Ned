**21.You are given the heads of two sorted linked lists list1 and list2.**
**Решение:**
```cpp
class Solution {
public:
    ListNode* mergeTwoLists(ListNode* list1, ListNode* list2) {
        if (!list1) {
            return list2;
        }
        if (!list2) {
            return list1;
        }
        
        ListNode* mergedHead = new ListNode();
        ListNode* current = mergedHead;
        
        while (list1 && list2) {
            if (list1->val < list2->val) {
                current->next = list1;
                list1 = list1->next;
            } else {
                current->next = list2;
                list2 = list2->next;
            }
            current = current->next;
        }
        
        current->next = list1 ? list1 : list2;
        
        return mergedHead->next;
    }
};
```
**Задача:**
**22.Given n pairs of parentheses, write a function to generate all combinations of well-formed parentheses.**
**Решение:**
```cpp
class Solution {
public:
    vector<string> generateParenthesis(int n) {
        vector<string> result;
        backtrack(result, "", 0, 0, n);
        return result;
    }
    
    void backtrack(vector<string>& result, string current, int open, int close, int max) {
        if (current.length() == max * 2) {
            result.push_back(current);
            return;
        }
        
        if (open < max) {
            backtrack(result, current + "(", open + 1, close, max);
        }
        if (close < open) {
            backtrack(result, current + ")", open, close + 1, max);
        }
    }
};
```
**Задача:**
**27.Given an integer array nums and an integer val, remove all occurrences of val in nums in-place. The order of the elements may be changed. Then return the number of elements in nums which are not equal to val.**
**Решение:**
```cpp
class Solution {
public:
int removeElement(vector<int>& nums, int val) {
int k = 0;

for (int i = 0; i < nums.size(); i++) {
if (nums[i] != val) {
nums[k++] = nums[i];
}
}

return k;
}
};
```