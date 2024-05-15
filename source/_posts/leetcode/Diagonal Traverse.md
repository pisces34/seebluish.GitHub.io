---
title: 498. Diagonal Traverse
categories:
- leetcode算法题
excerpt: 对角线迭代和翻转，看答案才会写，模拟没写出来
tags:
- C++
- vector
- 矩阵
---
链接：https://leetcode-cn.com/problems/diagonal-traverse/
执行用时：28 ms, 在所有 C++ 提交中击败了79.11% 的用户
内存消耗：18 MB, 在所有 C++ 提交中击败了17.22% 的用户
``` C++
class Solution {
public:
    vector<int> findDiagonalOrder(vector<vector<int>>& mat) {
        int row = mat.size();
        int col = mat[0].size();
        vector<int> res;
        vector<int> mid;
        if(mat.empty()) return mid;
        for (int i=0; i<row+col-1; ++i) {
            mid.clear();
            int r = i<col?0:i-col+1; // 行遍历完到下一列
            int c = i<col?i:col-1;
            while (r< row && c>-1) {
                mid.push_back(mat[r][c]);
                ++r; // 下一行
                --c; // 左边的列
            }
            if(i%2==0){ //需要翻转的对角线
                reverse(mid.begin(), mid.end());
            }
            for (int i = 0; i < mid.size(); i++) {
                res.push_back(mid[i]);
            }
        }
        return res;
    }
};
```