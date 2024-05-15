---
title: 142. 环形链表 II
categories:
- leetcode算法题
tags:
- C++
- Swift
- 双指针
---

题目链接：https://leetcode-cn.com/problems/linked-list-cycle-ii/

解释来自于魏梦舒的《算法漫画》，简单概括成文字
（头节点）————D——（入环点）———S1———（首次相遇点）————S2————（回到入环点）
距离分别为 D S1 S2
1，慢指针每次走一步，到达相遇点时经过了 D+S1的距离
2，快指针每次走两步，当它到第一次到相遇点时经过了D+S1的距离，但是此时慢指针还未达到相遇点
3，所以它会一直在环里打圈，大概是n圈后才等到慢指针到达相遇点，环的长度一圈为S1+S2，那么快指针走过的总长度就是D+S1+n（S1+S2）
4，因为快指针速度是慢指针的两倍，同时出发经过相同时间，快指针走过的距离即慢指针的两倍
5，可以推出 2(D+S1) = D+S1+n(S1+S2)
6，整理后即为 D = (n-1)(S1+S2)+S2
7，D的距离就是从头节点到入环点的距离，等于经过（n-1）圈再加上S2的距离
8，假设经过1圈相遇，D = S2，此时慢指针从相遇点开始移动，快指针回到头节点向后移动，相等时即为入环点

无论是多少圈，等式右边表示慢指针之后将要移动的距离，都等于等式左边的D，遍历完D的长度就到了入环点。
注意判断传入的空链表和长度为1的链表。


执行用时：52 ms, 在所有 Swift 提交中击败了95.43%的用户
内存消耗：14.9 MB, 在所有 Swift 提交中击败了77.14%的用户

```Swift
class Solution {
    func detectCycle(_ head: ListNode?) -> ListNode? {
        var fast = head
        var slow = head
        while fast != nil && fast?.next != nil {
            fast = fast?.next?.next
            slow = slow?.next
            if fast === slow {
                break
            }
        }
        if fast === nil || fast?.next === nil { return nil}
        fast = head
        while fast !== slow {
            fast = fast?.next
            slow = slow?.next
        }
        return fast
    }
}
```

执行用时：8 ms, 在所有 C++ 提交中击败了88.53%的用户
内存消耗：7.5 MB, 在所有 C++ 提交中击败了63.93%的用户

``` C++
class Solution {
public:
    ListNode *detectCycle(ListNode *head) {
        ListNode *fast = head;
        ListNode *slow = head;
        while (fast && fast->next){
            fast = fast->next->next;
            slow = slow->next;
            if (slow == fast){break;}
        }
        if (fast == NULL || fast->next == NULL ){return NULL;}
        fast = head;
        while (fast != slow){
            fast = fast->next;
            slow = slow->next;
        }
        return fast;
    }
};
```