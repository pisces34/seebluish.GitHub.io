---
title: 678. 有效的括号字符串
categories:
- leetcode算法题
tags:
- C++
- 双指针
---
``` C++
/***
看了题解下面的思路，非常便捷，原代码是三目表达式改写成if else了。
“有效的字符串，即从左向右看是有效的，从右向左看也是有效的
如果在遍历过程中，left或者right小于0，则是无效”
***/
class Solution {
public:
bool checkValidString(string s) {
    int left = 0;
    int right = 0;
    for (int i = 0; i < s.length(); ++i) {
        if(s[i]==')'){
            left--; 
        }else{
            left++;
        }
        if(s[s.length()-i-1]=='('){ //i从0开始，但是长度是从1开始数，所以-1
            right--;
        }else{
            right++;
        }
        if (left<0 || right <0) return false;
    }
    return true;
}
};
```