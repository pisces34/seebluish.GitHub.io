---
title: 剑指 Offer 57 - II. 和为s的连续正数序列
categories:
- leetcode算法题
tags:
- Swift
- 双指针
--- 

题目链接：https://leetcode-cn.com/problems/he-wei-sde-lian-xu-zheng-shu-xu-lie-lcof/

执行用时：4 ms, 在所有 Swift 提交中击败了91.80% 的用户
内存消耗：13.6 MB, 在所有 Swift 提交中击败了70.49% 的用户

``` swift
class Solution {
    func findContinuousSequence(_ target: Int) -> [[Int]] {
        var left = 1, right = 2
        var ans = [[Int]]()
        while left < right {
            // 等差数列求和
            let sum = (left + right) * (right - left + 1) / 2
            if sum == target {
                ans.append(Array.init(left...right))
                left += 1
            } else if sum < target {
                right += 1
            } else {
                left += 1
            }
        }
        return ans
    }
}
```