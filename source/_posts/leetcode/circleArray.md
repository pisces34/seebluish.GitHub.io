---
title: 457. 环形数组是否存在循环
categories:
- leetcode算法题
tags:
- Swift
- 双指针
---

题目链接：https://leetcode-cn.com/problems/circular-array-loop/

执行用时：72 ms, 在所有 Swift 提交中击败了100.00%的用户
内存消耗：13.5 MB, 在所有 Swift 提交中击败了100.00%的用户

快慢指针终会相遇，参考了官方题解

### 代码

```swift
class Solution {
    func circularArrayLoop(_ nums: [Int]) -> Bool {
        func next(cur: Int) -> Int{
            return ((cur+nums[cur])%n + n) % n  //保证落在0-n上
        }
        let n = nums.count
        
        var slow = 0,fast = 0
        for i in 0 ..< n {
            slow = i
            //表示nums[i]移动后的位置
            fast = next(cur: slow)
            //确保所处位置上的元素和起点都是相同符号
            while nums[fast]*nums[i] > 0 && nums[next(cur: fast)] * nums[i] > 0 {
                if fast == slow {
                    if slow == next(cur: slow) {    //判断是否回到自身
                        break
                    }
                    return true
                }
                slow = next(cur: slow)  
                fast = next(cur: next(cur: fast))
            }
        }
        return false
    }
}

```