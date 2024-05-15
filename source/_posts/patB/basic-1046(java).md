---
title: 1046 划拳 (java)
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
        int N;
        int say1,do1,say2,do2;
        int A = 0;
        int B = 0;
        N = in.nextInt();
        while(N != 0) {
            say1 = in.nextInt();
            do1 = in.nextInt();
            say2 = in.nextInt();
            do2 = in.nextInt();
            int sum = say1 + say2;
            if(sum == do1 && sum != do2){
                B++;
            }else if(sum == do2 && sum != do1){
                A++;
            }
            N--;
        }
        System.out.println(A+" "+B);
    }
}
```