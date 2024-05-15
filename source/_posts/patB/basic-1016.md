---
title: 1016 部分A+B
categories:
- pat乙级
tags:
- C++
--- 
``` C++
#include <iostream>
#include <cstdio>
using namespace std;
int main() {
    int a,da,b,db;
    int pa=0,pb=0;
    scanf("%d %d %d %d",&a,&da,&b,&db);
    while(a){
        if(a%10 == da){
            pa= pa*10;
            pa+=da;
        }
        a= a/10;
    }
    while(b){
        if(b%10 == db){
            pb= pb*10;
            pb+=db;
        }
        b= b/10;
    }
    cout<<(pa+pb)<<endl;
    return 0;
}
```
