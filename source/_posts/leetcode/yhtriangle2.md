---
title: 119. 杨辉三角 II
categories:
- leetcode算法题
tags:
- Java
---
执行用时：0 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：35.9 MB, 在所有 Java 提交中击败了90.20% 的用户
//把118的题里面的修改一下就通过了
//其实有线性递推的公式，看了官方题解才注意到。
题目链接：https://leetcode-cn.com/problems/pascals-triangle-ii/
``` Java
class Solution {
    public List<Integer> getRow(int rowIndex) {
        List<Integer> row = new ArrayList<Integer>();
        row.add(1);
        for (int i = 1; i <= rowIndex; ++i) {
            row.add((int) ((long) row.get(i - 1) * (rowIndex - i + 1) / i));
        }
        return row;
    }
}

class Solution1 {
    public List<Integer> getRow(int rowIndex) {
        List<List<Integer>> res = new ArrayList<List<Integer>>();
        for (int i = 0; i <= rowIndex; i++) {
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
        return res.get(rowIndex);
    }
}
```