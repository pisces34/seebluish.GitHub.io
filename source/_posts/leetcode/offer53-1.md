---
title: 剑指 Offer 53 - I. 在排序数组中查找数字 I
categories:
- leetcode算法题
tags:
- Java
--- 

题目链接：https://leetcode-cn.com/problems/zai-pai-xu-shu-zu-zhong-cha-zhao-shu-zi-lcof/

执行用时：0 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：41.4 MB, 在所有 Java 提交中击败了36.74% 的用户

``` java
class Solution {
    public int search(int[] nums, int target) {
        if (nums.length == 0) {
            return 0;
        }
        int left = 0, right = nums.length - 1;
        int start = 0, count = 0;
        while (left <= right) {
            int mid = left + (right-left)/2;
            if (nums[mid] == target) {
                start = mid;
                break;
            } else if (nums[mid] > target) {
                right--;
            } else {
                left++;
            }
        }
        right = start;
        left = start-1;
        while (right < nums.length) {
            if (nums[right] == target) {
                count++;
            } else {
                break;
            }
            right++;
        }
        while (left >= 0) {
            if (nums[left] == target) {
                count++;
            } else {
                break;
            }
            left--;
        }
        return count;
    }
}
```