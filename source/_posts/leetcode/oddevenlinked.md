---
title: 328. 奇偶链表
categories:
- leetcode算法题
tags:
- Swift
- 链表
- C++
---
题目链接：https://leetcode-cn.com/problems/odd-even-linked-list/
### 解题思路

让奇数节点的指针指向偶数节点指针的下一个节点，移动奇数指针到这个新节点，
新节点的下一个指针也就是前面偶数节点的下一个，交替移动。
循环判断条件：偶数节点必然先达到链表尾部。
（增加判断even != nil 可以省略前面链表小于等于3的判断，因为1，2，3个节点时已经排好序了

### 代码

```swift
class Solution {
    func oddEvenList(_ head: ListNode?) -> ListNode? {
        if head == nil || head?.next == nil || head?.next?.next == nil{
            return head
        }
        var odd = head
        var even = head?.next
        var evenHead = even
        while even?.next != nil {
            odd?.next = even?.next
            odd = odd?.next
            even?.next = odd?.next
            even = even?.next
        }
        odd?.next = evenHead
        return head
    }
}
```

```C++
class Solution {
public:
    ListNode *oddEvenList(ListNode *head) {
        if (!head || !head->next) return head;
        ListNode *odd = head;

        ListNode *even = head->next;
        ListNode *evenHead = even;
        while (even && even->next){
           odd->next = even->next;
           odd = odd->next;
           even->next = odd->next;
           even = even->next;
        }
        odd->next = evenHead;
        return head;
    }
};
```