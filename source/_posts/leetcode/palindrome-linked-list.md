---
title: 234. 回文链表
categories:
- leetcode算法题
tags:
- Swift
- 链表
- 双指针
---

执行用时：884 ms, 在所有 Swift 提交中击败了86.73% 的用户
内存消耗：32.3 MB, 在所有 Swift 提交中击败了19.43% 的用户

遍历一边取出数值放入数组，对数组进行双指针判断
```swift
class Solution {
    func isPalindrome(_ head: ListNode?) -> Bool {
        var arr = [Int]()
        var p = head
        while p != nil {
            arr.append(p?.val ?? 0)
            p = p?.next
        }
        p = head
        for i in (0 ..< arr.count).reversed() {
            if p?.val != arr[i] {
                return false
            }
            p = p?.next
        }
        return true
    }
}
```


执行用时：904 ms, 在所有 Swift 提交中击败了84.36% 的用户
内存消耗：26.7 MB, 在所有 Swift 提交中击败了58.77% 的用户

通过翻转链表的一半，再从头开始比对
```swift
class Solution {
    func isPalindrome(_ head: ListNode?) -> Bool {
        if head == nil || head?.next == nil {
            return true
        }
        var slow = head, fast = head
        var pre = head
        var prepre:ListNode? = nil
        //当快指针走两步时走完时，慢指针刚好走到中间位置
        while fast != nil && fast?.next != nil {
            pre = slow
            slow = slow?.next
            fast = fast?.next?.next
            pre?.next = prepre
            prepre = pre
        }
        //判断是否为奇数，奇数个则慢指针向后移动一步
        if fast != nil {
            slow = slow?.next
        }
        while pre != nil  {
            if pre?.val != slow?.val {
                return false
            }
            pre = pre?.next
            slow = slow?.next
        }
        return true
    }
}
```