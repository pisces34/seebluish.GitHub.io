---
title: 153. 寻找旋转排序数组中的最小值
categories:
- leetcode算法题
tags:
- Java
- Swift
- 二分法
---
题目链接：https://leetcode-cn.com/problems/find-minimum-in-rotated-sorted-array/
二分法, 刚刚开始学习Swift
执行用时：16 ms, 在所有 Swift 提交中击败了88.24%的用户
内存消耗：13.7 MB, 在所有 Swift 提交中击败了50.98%的用户
``` Swift
class Solution {
    func findMin(_ nums: [Int]) -> Int {
        var low = 0
        var high = nums.count - 1
        while low < high {
            var pivot = low + (high - low)/2
            if nums[high] > nums[pivot] {
                high = pivot
            }else {
                low = pivot + 1
            }
        }
        return nums[low]
    }
}

```
普通O(n)
执行用时：0 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：37.9 MB, 在所有 Java 提交中击败了42.64% 的用户
```Java
class Solution {
    public int findMin(int[] nums) {
        int left = nums[0];
        int flag = 0;
        int min = 0;
        for (int i = 0; i < nums.length-1; i++) {
            if (nums[i]>nums[i+1]){
                min = nums[i+1];
                flag = 1;
                break;
            }
        }
        if (flag == 1){
            return min;
        }
        return left;
    }
}
```

