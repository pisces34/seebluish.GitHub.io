---
title: 551. 学生出勤记录 I
categories:
- leetcode算法题
tags:
- Swift
---
题目链接：https://leetcode-cn.com/problems/student-attendance-record-i/

执行用时：4 ms, 在所有 Swift 提交中击败了100.00% 的用户
内存消耗：13.9 MB, 在所有 Swift 提交中击败了100.00% 的用户

``` swift
class Solution {
    func checkRecord(_ s: String) -> Bool {
        var A = 0, L = 0
        for i in s {
            switch i {
            case "A":
                A += 1
                L = 0
            case "L":
                L += 1
            default:
                L = 0
            }
            if A > 1 || L > 2 {
                return false
            }
        }
        return true
    }
}


```