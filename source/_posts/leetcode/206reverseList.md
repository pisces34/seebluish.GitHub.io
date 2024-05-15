---
title: 206. 反转链表 C++
categories:
- leetcode算法题
excerpt: 结构体指针定义在循环外面时间更短
tags:
- C++
- 三指针
- 反转链表
- Swift
---
题目链接：https://leetcode-cn.com/problems/reverse-linked-list/
执行用时：4 ms, 在所有 C++ 提交中击败了96.52% 的用户
内存消耗：8 MB, 在所有 C++ 提交中击败了91.52% 的用户
``` C++
**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode() : val(0), next(nullptr) {}
 *     ListNode(int x) : val(x), next(nullptr) {}
 *     ListNode(int x, ListNode *next) : val(x), next(next) {}
 * };
 */
class Solution {
public:
    ListNode* reverseList(ListNode* head) {
        ListNode *pre = NULL;
        ListNode *cur = head;
        ListNode *next = NULL;
        while (cur != NULL){
            next = cur->next;
            cur->next = pre;
            pre = cur;
            cur= next;
        }
        return pre;
    }
};
```
执行用时：12 ms, 在所有 Swift 提交中击败了96.71%的用户
内存消耗：14.6 MB, 在所有 Swift 提交中击败了29.72%的用户
### 解题思路
1，添加一个空的头节点A，相当于头插法的入口
2，设置一个实际的lasthead指针，表示上一次链表的头节点
3，头节点A每次指向当前cur访问节点的下一个节点
4，然后cur就可以跳过这个被A选中的节点，指向下一个，直到最后cur指向空
5，修改被选中的节点的next指针，使它指向旧的头节点
6，将lasthead向前移动，指向被A选中的节点，也就是新插入的节点
7，最后返回链表的实际起点lasthead


### 代码

```swift
/**
 * Definition for singly-linked list.
 * public class ListNode {
 *     public var val: Int
 *     public var next: ListNode?
 *     public init() { self.val = 0; self.next = nil; }
 *     public init(_ val: Int) { self.val = val; self.next = nil; }
 *     public init(_ val: Int, _ next: ListNode?) { self.val = val; self.next = next; }
 * }
 */
class Solution {
    func reverseList(_ head: ListNode?) -> ListNode? {
        var A = ListNode(0,head)
        var cur = head
        var lastHead = head
        while cur?.next != nil {
            A.next = cur?.next
            cur?.next = cur?.next?.next
            A.next?.next = lastHead
            lastHead = A.next
        }
        return lastHead
    }
}
```

```swift
class Solution {
    func reverseList(_ head: ListNode?) -> ListNode? {
        if head == nil || head?.next == nil {
            return head
        }
        var cur = head, pre = ListNode(0).next , nextP = head
        while cur != nil {
            nextP = cur?.next
            cur?.next = pre
            pre = cur
            cur = nextP
        }
        return pre
    }
}
```