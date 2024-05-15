---
title: 1137. 第 N 个泰波那契数
categories:
- leetcode算法题
tags:
- Swift
---

题目链接：https://leetcode-cn.com/problems/n-th-tribonacci-number/
### 解题思路
预处理n = 1，2，3的情况
再迭代模拟运算

执行用时：0 ms, 在所有 Swift 提交中击败了100.00%的用户
内存消耗：13.3 MB, 在所有 Swift 提交中击败了70.83%的用户


### 代码

```swift
class Solution {
    func tribonacci(_ n: Int) -> Int {
        var t0 = 0, t1 = 1, t2 = 1, t3 = 0
        var count = n-2
        if count == 0 || count == -1 {
            return 1
        }else if count == -2{
            return 0
        }
        while count > 0 {
            t3 = t0 + t1 + t2
            t0 = t1
            t1 = t2
            t2 = t3
            count -= 1
        }
        return t3
    }
}
```