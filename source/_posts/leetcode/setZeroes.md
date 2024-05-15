---
title: 面试题 01.08. 零矩阵
categories:
- leetcode算法题
tags:
- C++
- 数组
- 矩阵
---
链接：https://leetcode-cn.com/problems/zero-matrix-lcci/
暴力循环法
执行用时：12 ms, 在所有 C++ 提交中击败了88.06% 的用户
内存消耗：11.9 MB, 在所有 C++ 提交中击败了45.29% 的用户
``` C++
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int row = matrix.size();
        int col = matrix[0].size();
        int index[row][col];
        memset(&index[0][0],0,sizeof(index)); 
        int i,j;
        for(i=0; i<row; ++i){
            for(j=0; j<col; ++j){
                if(matrix[i][j] == 0){
                    index[i][j] = 1;
                }
            }
        }
        for(i=0; i<row; ++i){
            for(j=0; j<col; ++j){
                if(index[i][j]){
                    for(int k=0; k<col; ++k){
                        matrix[i][k] = 0;
                    }
                }
            }
        }
        for(i=0; i<row; ++i){
            for(j=0; j<col; ++j){
                if(index[i][j]){
                    for(int k=0; k<row; ++k){
                        matrix[k][j] = 0;
                    }
                }
            }
        }
    }
};

//另一种简化版
class Solution {
public:
    void setZeroes(vector<vector<int>>& matrix) {
        int rowLength = matrix.size();
        int colLength = matrix[0].size();
        vector<int> row;
        vector<int> col;
        int i,j;
        for(i=0; i<rowLength; ++i){
            for(j=0; j<colLength; ++j){
                if(matrix[i][j] == 0){
                    row.push_back(i);
                    col.push_back(j);
                }
            }
        }
        for(i=0; i<rowLength; ++i){
            for(j=0; j<colLength; ++j){
                matrix[row[i]][j] = 0;
            }
        }
        for(i=0; i<colLength; ++i){
            for(j=0; j<colLength; ++j){
               matrix[j][col[i]] = 0;
            }
        }
    }
};
```