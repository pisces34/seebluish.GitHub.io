---
title: 35. 搜索插入位置
categories:
- leetcode算法题
tags:
- C++
- 二分法
---
题目链接 https://leetcode-cn.com/problems/search-insert-position/
除了二分法外，还可以遍历全部，找不到即输出数组长度的值，也就是插入未知的下标。
``` C++
class Solution {
public:
    int searchInsert(vector<int> &nums, int target) {
        int right = nums.size()-1; //注意边界
        int left = 0;
        int mid;
        while (left <= right) {
            mid = left + (right - left) / 2;
            if (target > nums[mid] ) { 
                left = mid + 1;
            } else {
                right = mid - 1;
            }
        }
        return left;
    }
};
```
