---
title: 557. 反转字符串中的单词 III
categories:
- leetcode算法题
tags:
- Java
---
题目链接：https://leetcode-cn.com/problems/reverse-words-in-a-string-iii/

执行用时：9 ms, 在所有 Java 提交中击败了48.91% 的用户
内存消耗：39.2 MB, 在所有 Java 提交中击败了31.61% 的用户

```Java
class Solution {
    public String reverseWords(String s) {
        StringBuffer res = new StringBuffer();
        s+=" ";
        StringBuffer str = new StringBuffer(s);
        str.reverse();
        int last = str.length();
        for (int i = str.length()-1; i>=0 ; i--) {
            if (str.charAt(i)!=' '){
                continue;
            }else{
                res.append(str.substring(i+1,last));
                if (i>0) {
                    res.append(' ');
                }
                last=i;
            }
        }
        return res.toString();
    }
}
```
