---
title: 剑指 Offer 57. 和为s的两个数字
categories:
- leetcode算法题
tags:
- Java
- 数组
- 二分查找
--- 

题目链接：https://leetcode-cn.com/problems/he-wei-sde-liang-ge-shu-zi-lcof/

执行用时：1 ms, 在所有 Java 提交中击败了99.43% 的用户
内存消耗：60.2 MB, 在所有 Java 提交中击败了5.61% 的用户

``` java
class Solution {
    public int[] twoSum(int[] nums, int target) {
        int left = 0, right = nums.length-1;
        while (nums[right] + nums[left] != target) {
            if (nums[right] + nums[left] < target) {
                left++;
            } else {
                right--;
            }
        }
        int[] ans = {nums[left], nums[right]};
        return ans;
    }
}
```