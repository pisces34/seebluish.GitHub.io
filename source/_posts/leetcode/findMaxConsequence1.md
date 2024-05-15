---
title: 485. 最大连续 1 的个数
categories:
- leetcode算法题
tags:
- Java
- 双指针
---
题目链接：https://leetcode-cn.com/problems/max-consecutive-ones/

执行用时：3 ms, 在所有 Java 提交中击败了32.06% 的用户
内存消耗：39.8 MB, 在所有 Java 提交中击败了78.24% 的用户
双指针
``` Java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int one = 0, zero = 0, res = 0, count = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] != 1) {
                zero = i - 1;  //前一个连续1的终点
                res = Math.max(zero - one, res);
                one = i; //下一个连续1的起点
                count = 0;
            } else {
                count++;
                res = Math.max(res, count);
            }
        }
        return res;
    }
}
```

执行用时：3 ms, 在所有 Java 提交中击败了32.06% 的用户
内存消耗：39.8 MB, 在所有 Java 提交中击败了82.46% 的用户
贪心算法
``` Java
class Solution {
    public int findMaxConsecutiveOnes(int[] nums) {
        int sum=0;
        int res = 0;
        for (int i = 0; i < nums.length; i++) {
            if (nums[i] == 1){
                sum++;
            }else {
                res = Math.max(res,sum);
                sum = 0;
            }
            res = Math.max(res,sum);
        }
        return res;
    }
}
```