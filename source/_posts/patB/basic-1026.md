---
title: 1026 程序运行时间
categories:
- pat乙级
tags:
- C++
--- 
``` C++
#include <iostream>
#define CLK_TCK 100
using namespace std;
int main() {
    int c1,c2;
    scanf("%d %d",&c1,&c2);
    int second = (c2-c1+50)*1.0/CLK_TCK;
    int hour = second/3600;
    int minute = (second%3600)/60;
    int s = second-hour*3600-minute*60;
    printf("%02d:%02d:%02d",hour,minute,s);
    return 0;
}
```