---
title: 剑指 Offer 22. 链表中倒数第k个节点
categories:
- leetcode算法题
tags:
- Java
--- 

题目链接：https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/    

执行用时：0 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：39.1 MB, 在所有 Java 提交中击败了72.30% 的用户
通过测试用例：208 / 208


``` java
class Solution {
    public ListNode getKthFromEnd(ListNode head, int k) {
        ListNode slow = head, fast = head;
        for (int i = 0; i < k; i++) {
            fast = fast.next;
        }
        while (fast != null) {
            slow = slow.next;
            fast = fast.next;
        }
        return slow;
    }
}
```