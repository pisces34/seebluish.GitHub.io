---
title: 561. 数组拆分 I
categories:
- leetcode算法题
tags:
- C++
- 双指针
---

双指针的写法
执行用时：60 ms, 在所有 C++ 提交中击败了60.86% 的用户
内存消耗：27.5 MB, 在所有 C++ 提交中击败了86.11% 的用户
``` C++
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        int slow=0,fast = 1;
        sort(nums.begin(),nums.end());
        int sum = 0;
        int n = nums.size();
        while (fast<n){
            if (nums[fast] >= nums[slow]) {
                sum+= min(nums[slow],nums[fast]);
                slow = fast+1;
                fast +=2;
            }else{
                fast++;
            }
        }
        return sum;
    }
};
```
排序后奇数下标的值都为较小值，求和即刻
执行用时：52 ms, 在所有 C++ 提交中击败了92.09% 的用户
内存消耗：27.6 MB, 在所有 C++ 提交中击败了20.27% 的用户
``` C++
class Solution {
public:
    int arrayPairSum(vector<int>& nums) {
        int slow=0,fast = 1;
        sort(nums.begin(),nums.end());
        int sum = 0;
        int n = nums.size();
        for (int i = 0; i < n; i++) {
            if(i%2==0){sum+=nums[i];}
        }
        return sum;
    }
};
```
