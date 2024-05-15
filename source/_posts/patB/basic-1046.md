---
title: 1046 划拳
categories:
- pat乙级
tags:
- C++
--- 
``` C++
#include <iostream>
using namespace std;
int main() {
    int A, a, B, b;
    int sum1, sum2;
    int N;
    cin >> N;
    while (N--) {
        scanf("%d %d %d %d", &A, &a, &B, &b);
        if ((A + B) == a && (A + B) != b) {
            sum1++;
        } else if ((A + B) == b && (A + B) != a) {
            sum2++;
        }
    }
    cout << sum2 << " " << sum1 << endl;
    return 0;
}
```