---
title: 剑指 Offer 10- I. 斐波那契数列
categories:
- leetcode算法题
tags:
- Swift
--- 

题目链接：https://leetcode-cn.com/problems/fei-bo-na-qi-shu-lie-lcof/submissions/

执行用时：0 ms, 在所有 Swift 提交中击败了100.00%的用户
内存消耗：13.5 MB, 在所有 Swift 提交中击败了37.95%的用户

``` swift
class Solution {
    func fib(_ n: Int) -> Int {
        if n == 0 {
            return 0
        }
        if n == 1 {
            return 1
        }
        var arr = [Int].init(repeating: 0, count: n+1)
        arr[0] = 0
        arr[1] = 1
        for i in 2 ... n {
            arr[i] = (arr[i-1] + arr[i-2]) % (Int(1e9)+7)
        }
        return arr[n]
    }
}
```