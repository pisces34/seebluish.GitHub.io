---
title: 21. 合并两个有序链表
categories:
- leetcode算法题
tags:
- Swift
- 链表
---
题目链接：https://leetcode-cn.com/problems/merge-two-sorted-lists/

执行用时：12 ms, 在所有 Swift 提交中击败了88.31%的用户
内存消耗：13.7 MB, 在所有 Swift 提交中击败了9.96%的用户
``` swift
class Solution {
    func mergeTwoLists(_ l1: ListNode?, _ l2: ListNode?) -> ListNode? {
        var head = ListNode(0), cur = head, target = head
        var p1 = l1, p2 = l2
        while p1 != nil && p2 != nil {
            if p1?.val ?? -101 < p2?.val ?? 101 {
                target = p1!
                p1 = p1?.next
            }else {
                target = p2!
                p2 = p2?.next
            }
            cur.next = target
            cur = cur.next!
        }
        cur.next = p1 == nil ? p2 : p1
        return head.next
    }
}
```