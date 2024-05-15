---
title: 9. 回文数
categories:
- leetcode算法题
tags:
- Swift
- 回文
---

题目链接：https://leetcode-cn.com/problems/palindrome-number/
执行用时：32 ms, 在所有 Swift 提交中击败了97.60%的用户
内存消耗: 13.6MB, 在所有 Swift 提交中击败了81.97%的用户

``` Swift
class Solution {
    func isPalindrome(_ x: Int) -> Bool {
        if x < 0 {
            return false
        }
        var value = x
        var res = 0
        while value > 0 {
            res = res*10 + (value % 10)
            value /= 10
        }
        return res == x
    }
}

```