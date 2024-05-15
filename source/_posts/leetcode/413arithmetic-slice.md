---
title: 413. 等差数列划分
categories:
- leetcode算法题
tags:
- Swift
- 双指针
---

题目链接：https://leetcode-cn.com/problems/arithmetic-slices/
### 解题思路
用快指针递增，来判断下一对数值之间的差是否与前面一对数值的差，相等则为等差数列计数增加，
快指针向后移动，即滑动窗口扩大。
否则退出循环，慢指针递增，进行一下一组子数列的判断。

执行用时：8 ms, 在所有 Swift 提交中击败了100.00%的用户
内存消耗：13.8 MB, 在所有 Swift 提交中击败了40.00%的用户

### 代码

```swift
class Solution {
    func numberOfArithmeticSlices(_ nums: [Int]) -> Int {
        var length = nums.count
        if length < 3 {
            return 0
        }
        var slow = 0, fast = 1
        var count = 0
        while slow != length - 1 {
            var diff = nums[fast]-nums[slow]
            while fast != length - 1 {
                if  diff == nums[fast+1] - nums[fast] {
                    count += 1
                    fast += 1
                    continue
                }else{
                    break
                }
            }
            slow += 1
            fast = slow + 1
        }
        return count
    }
}

```