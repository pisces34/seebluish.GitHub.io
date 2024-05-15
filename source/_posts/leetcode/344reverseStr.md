---
title: 344. 反转字符串
categories:
- leetcode算法题
tags:
- C++
- Java
- 双指针
---
题目链接：https://leetcode-cn.com/problems/reverse-string/
执行用时：12 ms, 在所有 C++ 提交中击败了99.55% 的用户
内存消耗：22.7 MB, 在所有 C++ 提交中击败了5.09% 的用户
``` C++
class Solution {
public:
    void reverseString(vector<char>& s) {
        int left =0, right = s.size()-1;
        char t;
        while (left<right){
            t=s[left];
            s[left] = s[right];
            s[right]=t;
            left++;
            right--;
        }
    }
};
```

执行用时：1 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：45.1 MB, 在所有 Java 提交中击败了58.14% 的用户
``` Java
 class Solution {
        public void reverseString(char[] s) {
            int left =0, right = s.length-1;
            char t;
            while (left < right){
                t = s[left];
                s[left] = s[right];
                s[right] = t;
                left++;
                right--;
            }
        }
    }
```

执行用时：156 ms, 在所有 Swift 提交中击败了98.87% 的用户
内存消耗：18.1 MB, 在所有 Swift 提交中击败了27.44% 的用户
```swift
class Solution {
    func reverseString(_ s: inout [Character]) {
        var left = 0, right = s.count - 1
        var t : Character
        while left < right {
            t = s[left]
            s[left] = s[right]
            s[right] = t
            left += 1
            right -= 1
        }
    }
}
```