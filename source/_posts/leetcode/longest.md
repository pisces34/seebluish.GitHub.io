---
title: 5. 最长回文子串
categories:
- leetcode算法题
excerpt: 循环找回文子串，记录起始下标
tags:
- C++
- 回文字符串
- 字符串
---
题目地址：https://leetcode-cn.com/problems/longest-palindromic-substring/
执行用时：304 ms, 在所有 C++ 提交中击败了51.32% 的用户
内存消耗：7 MB, 在所有 C++ 提交中击败了83.19% 的用户
``` C++
class Solution {
public:
    string longestPalindrome(string s) {
        int length = s.length();
        string maxs = "";
        if(s.empty()||s.size()<2){
            return s;
        } else {
            int end,left,right,i;
            for (i = 0; i < length; ++i) {
                end = length - 1;
                right = end;
                left = i;
                while (right > left){
                    if (s[right] == s[left]){
                        --right;
                        ++left;
                    }else{
                        end--;
                        right = end;
                        left = i;
                    }
                }
                if ((end-i+1) > maxs.size()){
                    maxs = s.substr(i,end-i+1);
                }
            }
        }
        return maxs;
    }
};
```