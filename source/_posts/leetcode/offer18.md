---
title: 剑指 Offer 18. 删除链表的节点
categories:
- leetcode算法题
tags:
- Java
--- 

题目链接：https://leetcode-cn.com/problems/shan-chu-lian-biao-de-jie-dian-lcof/

执行用时：0 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：40.7 MB, 在所有 Java 提交中击败了65.58% 的用户


``` java
class Solution {
    public ListNode deleteNode(ListNode head, int val) {
        ListNode res = head;
        if (head.val == val) {
            res = head.next;
            head = null;
        } else {
            while (head.next != null && head.next.val != val) {
                head = head.next;
            }
            head.next = head.next.next;
        }
        return res;
    }
}

```