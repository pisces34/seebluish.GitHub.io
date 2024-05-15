---
title: 剑指 Offer 53 - II. 0～n-1中缺失的数字
categories:
- leetcode算法题
tags:
- Java
- 数组
- 二分查找
--- 

题目链接：https://leetcode-cn.com/problems/que-shi-de-shu-zi-lcof/

执行用时：0 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：42.3 MB, 在所有 Java 提交中击败了5.02% 的用户

``` java
class Solution {
    public int missingNumber(int[] nums) {
        int left = 0, right = nums.length - 1;
        while (left <= right) {
            int mid = (left + right) >> 1;
            if (nums[mid] == mid) {
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return left;
    }
}
```