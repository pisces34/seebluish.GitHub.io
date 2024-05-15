---
title: 724. 寻找数组的中心下标 C++
categories:
- leetcode算法题
tags:
- C++
---
hhh，执行结果不稳定，有时候挺好的。
执行用时：20 ms, 在所有 C++ 提交中击败了93.14% 的用户
内存消耗：30.2 MB, 在所有 C++ 提交中击败了77.02% 的用户

``` C++
class Solution {
public:
    int pivotIndex(vector<int> &nums) {
        int leftSum = 0;
        int sum = 0;
        for (int val:nums) sum += val;
        for (int i = 0; i < nums.size(); ++i) {
            if (leftSum == sum - nums[i] - leftSum) { //左边之和等于右边之和，当下i为中间下标
                return i;
            }
            leftSum += nums[i];
        }
        return -1;
    }
};
```
