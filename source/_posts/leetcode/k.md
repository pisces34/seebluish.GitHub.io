---
title: 剑指 Offer 22. 链表中倒数第k个节点
categories:
- leetcode算法题
tags:
- C++
- 双指针
- 链表
---

``` c++
/**
 * Definition for singly-linked list.
 * struct ListNode {
 *     int val;
 *     ListNode *next;
 *     ListNode(int x) : val(x), next(NULL) {}
 * };
 */
class Solution {
public:
    ListNode* getKthFromEnd(ListNode* head, int k) {
        //初始化指向表头
        ListNode *pre=head, *last=head;
        //先往后走
        for(int i =1; i<=k; i++){
            last = last->next;
        }
        //同时移动指针
        while(last != NULL){
            pre = pre->next;
            last = last->next;
        }
        //返回前一个指针
        return pre;
    }
};
```
执行用时：0 ms, 在所有 C++ 提交中击败了100.00% 的用户
内存消耗：10.3 MB, 在所有 C++ 提交中击败了57.96% 的用户
