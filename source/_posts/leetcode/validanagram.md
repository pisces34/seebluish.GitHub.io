---
title: 242. 有效的字母异位词
categories:
- leetcode算法题
tags:
- Swift
- 字符串    
- C++
---
题目链接：https://leetcode-cn.com/problems/valid-anagram/
### 解题思路

执行用时：16 ms, 在所有 Swift 提交中击败了99.02%的用户
内存消耗：14 MB, 在所有 Swift 提交中击败了78.43%的用户

排序字符串 或者 计数器
因为C++中 只要-'a'就转换成整数了，结果swift就卡在了讲a转为可运算的整数这里，参考了楼上的计数器题解
### 代码

```swift
class Solution {
    func isAnagram(_ s: String, _ t: String) -> Bool {
        if s.count != t.count {
            return false
        }
        // 都是小写字母，设定26个0
        var arr = [Int](repeating: 0, count: 26)
        let aChar = Int("a".unicodeScalars.first!.value)
        for i in s.unicodeScalars {
            arr[Int(i.value) - aChar] += 1
        }
        for j in t.unicodeScalars {
            arr[Int(j.value) - aChar] -= 1
        }
        //遇到第一个小于0的说明该字符在另一串中没有出现过
        if arr.first(where: {$0 < 0 }) == nil {
            return true
        }
        return false
    }
}

```
执行用时：4 ms, 在所有 Swift 提交中击败了97.63%的用户
内存消耗：7.1 MB, 在所有 Swift 提交中击败了70.26%的用户

``` C++
class Solution {
public:
    bool isAnagram(string s, string t) {
        if (s.length() != t.length()) return false;
        int arr[26]={0};
        for (int i = 0; i < s.length(); ++i) {
            arr[s[i]-'a']++;
        }
        for (int i = 0; i < t.length(); ++i) {
            arr[t[i]-'a']--;
        }
        for (int i = 0; i < 26; ++i) {
            if (arr[i] < 0) {
                return false;
            }
        }
        return true;
    }
};
```