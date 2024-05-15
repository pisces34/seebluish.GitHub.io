---
title: 1012 数字分类
categories:
- pat乙级
tags:
- C++
excerpt: 模拟题
--- 
题目链接： https://pintia.cn/problem-sets/994805260223102976/problems/994805311146147840
``` C++
#include <iostream>
using namespace std;
int main() {
    int a1 = 0, a2 = 0, a3 = 0, a4 = 0, a5 = 0;
    float sum = 0;
    int N;
    int flag = 0,x=1;
    cin >> N;
    int arr[N];
    for (int i = 0; i < N; ++i) {
        cin >> arr[i];
        if (arr[i] % 10 == 0) {
            a1 += arr[i];
        } else if (arr[i] % 5 == 1) {
            flag = 1;
            a2 += x * arr[i];
            x = -x;;
        } else if (arr[i] % 5 == 2) {
            a3++;
        } else if (arr[i] % 5 == 3) {
            a4++;
            sum += arr[i];
        } else if (arr[i] % 5 == 4) { if (arr[i] >= a5) a5 = arr[i]; }
    }
    if(a1 == 0) printf("N "); else printf("%d ", a1);
    if(flag == 0) printf("N "); else printf("%d ", a2);
    if(a3 == 0) printf("N "); else printf("%d ", a3);
    if(a4 == 0) printf("N "); else printf("%.1f ", sum/a4*1.0);
    if(a5 == 0) printf("N");  else printf("%d", a5);
    return 0;
}
```