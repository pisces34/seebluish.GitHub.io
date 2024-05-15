---
title: 剑指 Offer 66. 构建乘积数组
categories:
- leetcode算法题
tags:
- Java
--- 

题目链接：https://leetcode-cn.com/problems/gou-jian-cheng-ji-shu-zu-lcof/

算法流程
    首先申请结果数组 res
    求出左侧三角从上到下的值，依次存入 res[i] 中
    求出右侧三角从下到上的值，并且和之前的 res[i] 做乘积存入，即可得到结果

作者：画手大鹏
链接：https://leetcode-cn.com/leetbook/read/illustrate-lcof/5wpmzm/

``` java
class Solution {
    public int[] constructArr(int[] a) {
        int[] res = new int[a.length];
        int left = 1, right = 1;
        for (int i = 0; i < a.length; i++) {
            res[i] = left;
            left *= a[i];
        }
        for (int i = a.length - 1; i >= 0; i--) {
            res[i] *= right;
            right *= a[i];
        }
        return res;
    }
}
```