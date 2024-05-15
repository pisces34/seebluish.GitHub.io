---
title: 1002 写出这个数
categories:
- pat乙级
tags:
- C++
--- 
``` C++
#include <iostream>
using namespace std;
int main() {
    string s;
    string pinyin[10]={"ling","yi","er","san","si","wu","liu","qi","ba","jiu"};
    cin>>s;
    int sum=0;
    for (int i = 0; i < s.length(); ++i) {
        sum+=(s[i]-'0');
    }
    string num = to_string(sum);
    for (int i = 0; i < num.length(); ++i) {
        if(i!=0) cout<<" ";
        cout<<pinyin[num[i]-'0'];
    }
    return 0;
}
```