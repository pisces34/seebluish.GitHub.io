---
title: 160. 相交链表
categories:
- leetcode算法题
tags:
- Swift
- 双指针
- C++
---
题目链接：https://leetcode-cn.com/problems/intersection-of-two-linked-lists/

执行用时：268 ms, 在所有 Swift 提交中击败了95.76%的用户
内存消耗：16.7 MB, 在所有 Swift 提交中击败了40.39%的用户

### 解题思路
重点在于理清某一指针走到尾部时要放到另一条链表的头部，搭配官方题解更容易理解

1，先对链表进行判空，链表任意一个为空节点就不会相交
2，设定两个指针指向各自头节点
3，关键在于相遇节点时，p1经过了x长度，p2经过了y长度，余下要走的长度都是z
4，当x<y时, 那么先走完z的指针一定是p1，使它回到较长的那条链表的头节点
5，此时仍在较长链表的p2 距离走到尾部剩余的长度就是 y-x
6，p1和p2继续移动，当p2走到末尾，使其回到较短链表的头节点，那它距离相遇点的长度就是x
7，此时p1也经过了y-x的距离，最后两指针都经过x长度，p1就是 y-x+x = y 到达相遇点
8，如果没有相交点，指针将会同时走到y长度的终点，也就是链表尾部，返回的就是空指针


使用双层for循环会超时，C++可以. 还可以使用哈希表存储访问过的节点地址。
### 代码
Swift
```swift
class Solution {
    func getIntersectionNode(_ headA: ListNode?, _ headB: ListNode?) -> ListNode? {
        if headA == nil || headB == nil {
            return nil
        }
        var p1 = headA
        var p2 = headB
        while p1 !== p2 {
            p1 = p1 == nil ? headB : p1?.next
            p2 = p2 == nil ? headA : p2?.next

        }
        return p1
    }
}
```

C++ 快慢指针
``` C++
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        if (headA == nullptr || headB == nullptr) {
            return nullptr;
        }
        ListNode *p = headA, *q = headB;
        while(p != q){
           q = q == nullptr ? headA : q->next;
           p = p == nullptr ? headB : p->next;
        }
        return p;
    }
};
```

C++ 暴力循环
```C++
class Solution {
public:
    ListNode *getIntersectionNode(ListNode *headA, ListNode *headB) {
        ListNode *up = headA;
        ListNode *down = headB;
        while (up != nullptr){
            down = headB;
            while (down != nullptr){
                if(down == up){
                    return up;
                }
                down = down->next;
            }
            up = up->next;
        }
        return nullptr;
    }
};
```