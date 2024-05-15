---
title: 1026 程序运行时间 (java)
categories:
- pat乙级
tags:
- Java
--- 
```java
import java.util.Scanner;
public class Main {
    public static void main(String[] args) {
        Scanner in = new Scanner(System.in);
        int C1, C2;
        C1 = in.nextInt();
        C2 = in.nextInt();
        int tck = (C2 - C1 +50)/100 ;
        int hour, minute, second;
        hour = tck / 3600;
        minute = tck % 3600 / 60;
        second = tck % 60;
        System.out.println(String.format("%02d:%02d:%02d",hour,minute,second));
    }
}
```