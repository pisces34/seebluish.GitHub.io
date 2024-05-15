---
title: 剑指 Offer 58 - I. 翻转单词顺序
categories:
- leetcode算法题
tags:
- C++
- 双指针
---
题目链接：https://leetcode-cn.com/problems/fan-zhuan-dan-ci-shun-xu-lcof/

执行用时：0 ms, 在所有 C++ 提交中击败了100.00% 的用户
内存消耗：7.1 MB, 在所有 C++ 提交中击败了47.16% 的用户
``` C++
class Solution {
public:
    string reverseWords(string s) {
        int i=0,start;
        while (s[i]==' '){
            start++;
            i++;
        }
        int n =s.size();
        string res="";
        int right = n-1,left = right;
        while (left>=start){
            if (s[right]==32&&right>0){
                right--;
                continue;
            }
            left = right;
            while (s[left]!=32&&left>0){
                left--;
            }
            if (left==start){left--;};
            for (i = left+1; i <= right; ++i) {
                res+=s[i];
            }
            if (left>start){res+=' ';}
            right = left;
        }
        return res;
    }
};
```