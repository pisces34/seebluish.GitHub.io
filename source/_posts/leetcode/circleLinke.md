---
title: 141. 环形链表
categories:
- leetcode算法题
tags:
- C++
- Swift
- 双指针
---

题目链接：https://leetcode-cn.com/problems/linked-list-cycle/
类比于操场跑步。快指针每次走两步，慢指针每次走一步，如果存在环，快指针一定会与慢指针相遇。

执行用时：64 ms, 在所有 Swift 提交中击败了96.77%的用户

```Swift
class Solution {
    func hasCycle(_ head: ListNode?) -> Bool {
        if head == nil {
            return false
        }
        var fast = head
        var slow = head
        while fast != nil && fast?.next != nil {
            fast = fast?.next?.next
            slow = slow?.next
            if fast === slow {
                return true
            }
        }
        return false
    }
}

```
除了用map来存指针地址之外，题目val的值是有范围的，所以将访问过的值修改为区间以外的即可当作标志。
下次访问时若值为这个标志说明指针已经指回到了前面访问过的节点。

执行用时：68 ms, 在所有 Swift 提交中击败了88.17%的用户

``` Swift
class Solution {
    func hasCycle(_ head: ListNode?) -> Bool {
        if head == nil {return false}
        var fast = head
        var slow = head
        while fast != nil && fast?.next != nil {
            fast = fast?.next?.next
            slow = slow?.next
            if fast === slow {
                return true
            }
        }
        return false
    }
}
```

执行用时：4 ms, 在所有 C++ 提交中击败了99.77%的用户
内存消耗：8 MB, 在所有 C++ 提交中击败了30.61%的用户

``` C++
class Solution {
public:
    bool hasCycle(ListNode *head) {
        if (head == NULL) return false;
        ListNode *point = head;
        while (point->next != NULL){
            if (point->val == 100001){
                return true;
            }
            point->val = 100001;
            point = point->next;
        }
        return false;
    }
};
```