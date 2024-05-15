---
title: 剑指 Offer 09. 用两个栈实现队列
categories:
- leetcode算法题
tags:
- Swift
- Java
--- 

题目链接：https://leetcode-cn.com/problems/yong-liang-ge-zhan-shi-xian-dui-lie-lcof/

执行用时：928 ms, 在所有 Swift 提交中击败了95.83% 的用户
内存消耗：15.9 MB, 在所有 Swift 提交中击败了95.08% 的用户

Swift:
``` swift
class CQueue {
    var s1 = [Int]()
    var s2 = [Int]()
    init() { 
    }
    func appendTail(_ value: Int) {
        s1.append(value)
    }
    func deleteHead() -> Int {
        if s2.isEmpty {
            while let head = s1.popLast() {
                s2.append(head)
            }
        }
        return s2.popLast() ?? -1
    }
}
```

Java:
``` java
class CQueue {
    Deque<Integer> s1;
    Deque<Integer> s2;
    public CQueue() {
        s1 = new LinkedList<Integer>();
        s2 = new LinkedList<Integer>();
    }

    public void appendTail(int value) {
        s1.push(value);
    }

    public int deleteHead() {
        if (s2.isEmpty()) {
            while (!s1.isEmpty()) {
                s2.push(s1.pop());
            }
        }
        if (s2.isEmpty()) {
            return -1;
        }
        return s2.pop();
    }
}
```