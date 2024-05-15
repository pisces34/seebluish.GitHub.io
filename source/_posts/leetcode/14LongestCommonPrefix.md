---
title: 14.最长公共前缀
categories:
- leetcode算法题
tags:
- C++
- 字符串
---
链接：https://leetcode-cn.com/problems/longest-common-prefix/


执行用时：4 ms, 在所有 C++ 提交中击败了85.15%的用户
内存消耗：8.9 MB, 在所有 C++ 提交中击败了60.86%的用户
``` C++
class Solution {
public:
    string longestCommonPrefix(vector<string>& strs) {
        if (strs[0].size() == 0) { return ""; }
        if(strs.size()==1){return strs[0];}
        int j = 0;
        string res = "";
        //纵向扫描
        for (int i = 0; i < strs[0].size(); ++i) {
            char common = strs[0][j];
            for (int k = 1; k < strs.size(); ++k) {
                if (common == strs[k][j]) {
                    continue;
                }else{
                    return res;
                }
            }
            j++;
            res += common;
        }
        return res;
    }
};
```
执行用时：4 ms, 在所有 C++ 提交中击败了89.08% 的用户
内存消耗：8.7 MB, 在所有 C++ 提交中击败了96.19% 的用户
``` C++
class Solution {
public:
    string longestCommonPrefix(vector<string> &strs) {
        int i = 1, j = 0;
        int n=strs.size();
        string sub = "";
        if (strs[0].size() == 0) { return sub; }
        if(n>1){
            while (strs[0][j] == strs[i][j] && (strs[i][j] != '\0')) {
                if (i == n- 1) {
                    sub += strs[0][j];
                    j++;
                    i = 1;
                    continue;
                }
                i++;
            }
            return sub;
        }
        return strs[0];
    }
};
```
