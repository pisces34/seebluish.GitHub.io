---
title: 209. 长度最小的子数组
categories:
- leetcode算法题
excerpt: 用了暴力循环，下次改进
tags:
- Java
- 双指针
---

题目链接：https://leetcode-cn.com/problems/minimum-size-subarray-sum/
执行用时：152 ms, 在所有 Java 提交中击败了10.69% 的用户
内存消耗：38.5 MB, 在所有 Java 提交中击败了33.53% 的用户

``` Java
class Solution {
    public int minSubArrayLen(int target, int[] nums) {
        int len=100001;
        int sum;
        for (int i = 0; i < nums.length; i++) {
            if (target <= nums[i]) {
                len = 1;
                break;
            }
            sum=nums[i];
            for (int j=i+1; j<nums.length;j++) {
                sum +=nums[j];
                if ( sum>= target) {
                    len = Math.min(len,j-i+1);
                    break;
                }
            }
        }
        if (len<100001){
            return len;
        }else{
            return 0;
        }
    }
}
```