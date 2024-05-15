---
title: 剑指 Offer 24. 反转链表
categories:
- leetcode算法题
tags:
- Java
--- 

题目链接：https://leetcode-cn.com/problems/fan-zhuan-lian-biao-lcof/  

执行用时：0 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：40.6 MB, 在所有 Java 提交中击败了65.75% 的用户

``` java
class Solution {
    public ListNode reverseList(ListNode head) {
        ListNode pre = null, cur = head;
        while (cur != null) {
            ListNode temp = cur.next;
            cur.next = pre;
            pre = cur;
            cur = temp;
        }
        return pre;
    }
}
```