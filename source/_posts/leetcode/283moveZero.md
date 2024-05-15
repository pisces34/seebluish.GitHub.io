---
title: 283. 移动零
categories:
- leetcode算法题
tags:
- Swift
- 双指针
---

题目链接：https://leetcode-cn.com/problems/move-zeroes/
### 解题思路
slow 所指总是为0 ，fast 所指为非0元素，交换元素后，向后移动slow

执行用时：32 ms, 在所有 Swift 提交中击败了97.37%的用户
内存消耗：14.3 MB, 在所有 Swift 提交中击败了35.41%的用户

### 代码

```swift
class Solution {
    func moveZeroes(_ nums: inout [Int]) {
        var slow = 0, fast = 0
        while fast < nums.count {
            if nums[fast] != 0 {
                nums.swapAt(slow, fast)
                slow += 1
            }
            fast += 1
        }
    }
}
```

执行用时：32 ms, 在所有 Swift 提交中击败了99.72%的用户
内存消耗：14 MB, 在所有 Swift 提交中击败了90.08%的用户
``` Swift
class Solution {
    func moveZeroes(_ nums: inout [Int]) {
        var  fast = 0
        for i in 0..<nums.count {
            if nums[i] == 0 && nums[fast] != 0 {
                fast = i
            } else if nums[i] != 0 && nums[fast] == 0 {
                nums[fast] = nums[i]
                fast += 1
                nums[i] = 0
            }
        }
    }
}
```

