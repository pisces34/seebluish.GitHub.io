---
title: 1008 数组元素循环右移问题
categories:
- pat乙级
excerpt: 要注意M的值会大于N，取余数处理即可
tags:
- Java
---
``` java
import java.util.Scanner;
public class Main {
    public static void main(String args[]) {
        Scanner in = new Scanner(System.in);
        int N = in.nextInt();
        int M = in.nextInt();
        int[] arr = new int[100];
        M = M % N;
        for (int i = 0; i < N; i++) {
            arr[i] = in.nextInt();
        }
        for (int i = N - M; i <= N - 1; i++) {
            System.out.print(arr[i] + " ");
        }
        for (int i = 0; i < N - M - 1; i++) {
            System.out.print(arr[i] + " ");
        }
        System.out.print(arr[N - M - 1]);
    }
}
```