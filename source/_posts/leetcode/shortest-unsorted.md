---
title: 581. 最短无序连续子数组
categories:
- leetcode算法题
tags:
- Swift
- 数组
---
题目链接：https://leetcode-cn.com/problems/shortest-unsorted-continuous-subarray/

执行用时：264 ms, 在所有 Swift 提交中击败了70.59%的用户
内存消耗：14.1 MB, 在所有 Swift 提交中击败了29.41%的用户

### 解题思路
找到左边和右边从升序变为降序的边界，中间数组的最小值应该大于左边数组的最大值，中间数组的最大值要大于右边数组的最小值。
从左边界开始向前走，遇到大于中间数组最小值的数则需要被升序排序，左边界延长。
从右边界开始向后走，遇到小于中间数组最大值的数则需要被升序排序，右边界延长。
都符合条件时，一开始的左右边界长度就是连续子列的长度

### 代码

```swift
class Solution {
    func findUnsortedSubarray(_ nums: [Int]) -> Int {
        if nums.count == 1 {
            return 0
        }
        let len = nums.count
        //判断是否默认升序
        var up = 0
        for i in 0 ..< len - 1 {
            if nums[i] <= nums[i+1] {
                up += 1
            }
        }
        if up == len - 1 {
            return 0
        }
        //寻找左右升序的边界
        var left = 0
        var right = len - 1
        for i in 0 ..< len - 1 {
            if nums[i] > nums[i+1] {
                left = i
                break
            }
        }
        var j = len - 1
        while j>0 {
            if nums[j-1] > nums[j] {
                right = j
                break
            //相等时右边界移动
            }else if nums[j-1] == nums[j]{
                right = j
            }
            j -= 1
        }

        //寻找最值
        var midArray = nums[left...right]
        let mid = midArray.sorted()
        let midEnd = midArray.count - 1
        var L = left - 1
        var R = right + 1
        //从右边界开始向后走，遇到小于中间数组最大值的数则需要被升序排序，右边界延长。
        while R != len  {
            if mid[midEnd] > nums[R] {
                right += 1
            }
            R += 1
        }
        //从左边界开始向前走，遇到大于中间数组最小值的数则需要被升序排序，左边界延长。
        while L != -1 {
            if mid[0] < nums[L] {
                left -= 1
            }
            L -= 1
        }
        return right - left + 1
    }
}
```
另一种解法：
将数组拷贝一份升序排序后，遍历原数组，相同位置值相等时说明已经是升序，left 和 right 最后停在需要排序的区间上。

```swift
class Solution {
    func findUnsortedSubarray(_ nums: [Int]) -> Int {
        var sortNums = nums.sorted()
        var left = 0, right = nums.count - 1
        while left <= right && nums[left] == sortNums[left] {
            left += 1
        }
        while right >= left && nums[right] == sortNums[right] {
            right -= 1
        }
        return right - left + 1
        
    }
}
```