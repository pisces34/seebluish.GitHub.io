---
title: 剑指 Offer 06. 从尾到头打印链表
categories:
- leetcode算法题
tags:
- Java
- 链表
--- 

题目链接：https://leetcode-cn.com/problems/cong-wei-dao-tou-da-yin-lian-biao-lcof/

执行用时：0 ms, 在所有 Java 提交中击败了100.00%的用户
内存消耗：38.8 MB, 在所有 Java 提交中击败了78.66%的用户

在数组中倒序存放元素
``` java
class Solution {
    public int[] reversePrint(ListNode head) {
        int count = 0;
        ListNode p = head;
        while (p != null) {
            count++;
            p = p.next;
        }
        int arr[] = new int[count];
        while (head != null) {
            arr[--count] = head.val;
            head = head.next;
        }
        return arr;
    }
}
```

使用栈

``` java
class Solution {
    public int[] reversePrint(ListNode head) {
        Stack stack = new Stack();
        int size = 0;
        while (head != null) {
            stack.push(head.val);
            head = head.next;
            size++;
        }
        int[] arr = new int[size];
        for(int i = 0; i < size; i++) {
            arr[i] = (int) stack.pop();
        }
        return arr;
    }
}
```