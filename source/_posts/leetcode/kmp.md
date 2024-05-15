---
title: 28. 实现 strStr()
categories:
- leetcode算法题
tags:
- C++
- KMP
- 字符串匹配
---
```C++
class Solution {
public:
    int strStr(string haystack, string needle) {
        int m = haystack.size(), i = 0;
        int n = needle.size(), j = 0;
        if (needle.empty()) {
            return 0;
        }else if(haystack.empty()|| m<n){
            return -1;
        }
        size_t length = needle.size(), fast = 0;
        int *next = new int[length];
        int slow = next[0] = -1;
        while (fast < length-1) {
            if ((0 > slow || needle[fast] == needle[slow])) {
                fast++;
                slow++;
                next[fast] = slow;
                //next[fast] = (needle[fast] != needle[slow] ? slow : next[slow]);
            } else {
                slow = next[slow];
            }
        }
        int flag = 0;
        while (j < n && i < m) {
            if (0 > j || haystack[i] == needle[j]) {
                i++;
                j++;
                if(needle[j]=='\0'){
                    flag = 1;break;//已经找到末尾
                }
            } else {
                j = next[j];
            }
        }
        delete[] next;
        if (flag) return i-j;
        return -1;
    }
};

//KMP 主算法参考代码：
int match (char* P, char* S){ // KMP 算法
    int* next = buildNext(P); // 构造 next 表
    int m = (int) strlen (S), i = 0; // 文本串指针
    int n = (int) strlen(P), j = 0; //模式串指针
    while (j < n && i < m) // 自左向右逐个比对字符
        if (0 > j || S[i] == P[j]) // 若匹配，或 P 已移除最左侧
            {i++; j++;} // 则转到下一字符
        else
            j = next[j]; // 模式串右移（注意：文本串不用回退）
    delete [] next; // 释放 next 表
    return i - j;
}
//构造 next 表参考代码：
int* buildNext(char* P) { // 构造模式串 P 的 next 表
    size_t m = strlen(P), j = 0; // “主”串指针
    int* N = new int[m]; // next 表
    int  t = N[0] = -1; // 模式串指针
    while (j < m - 1)
        if ( 0 > t || P[j] == P[t]){ // 匹配
            j++; t++;
            N[j] = t; // 此句可改进为 N[j] = (P[j] != P[t] ? t : N[t]);
        }else // 失配
        t = N[t];
    return N;

}
```