---
title: 7. 整数反转
categories:
- leetcode算法题
tags:
- Swift
- C++
---

题目链接：https://leetcode-cn.com/problems/reverse-integer/
执行用时：0 ms, 在所有 C++ 提交中击败了100.00%的用户
内存消耗：5.8 MB, 在所有 C++ 提交中击败了51.54%的用户

``` C++
class Solution {
public:
    int reverse(int x) {
        long long res = 0;
        while (x!=0){
            res = res*10 + x%10;
            x /= 10;
        }
        if (res>pow(2,31)-1 || res<(pow(-2,31))){return 0;}
        return res;
    }
};
```

执行用时： 4 ms , 在所有 Swift 提交中击败了 95.41% 的用户 
内存消耗:13.7 MB , 在所有 Swift 提交中击败了 25.63% 的用户
``` Swift
class Solution {
    func reverse(_ x: Int) -> Int {
        var value = x
        var res = 0
        while value != 0 {
            res = res*10 + value%10
            if res > Int32.max || res < Int32.min {
                return 0
            }
            value /= 10
        }
        return res
    }
}
```