---
title: 118. 杨辉三角
categories:
- leetcode算法题
tags:
- Java
---

题目链接：https://leetcode-cn.com/problems/pascals-triangle/
``` Java
class Solution {
    public List<List<Integer>> generate(int numRows) {
        List<List<Integer>> res = new ArrayList<List<Integer>>();
        for (int i = 0; i < numRows; i++) {
            List<Integer> L = new ArrayList<Integer>();
            for (int j = 0; j <= i; j++) {
                if (j == 0 || i == j) {
                    L.add(1);
                } else {
                    L.add(res.get(i - 1).get(j - 1) + res.get(i - 1).get(j));
                }
            }
            res.add(L);
        }
        return res;
    }
}
```