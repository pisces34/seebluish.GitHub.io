---
title: 232. 用栈实现队列
categories:
- leetcode算法题
tags:
- Swift
- 队列
- 栈
--- 
题目链接：https://leetcode-cn.com/problems/implement-queue-using-stacks/

执行用时：0 ms, 在所有 Swift 提交中击败了100.00%的用户
内存消耗：13.7 MB, 在所有 Swift 提交中击败了92.41%的用户

``` swift
class MyQueue {
    var front = 0
    var inStack = [Int]()
    var outStack = [Int]()
    init() {
        front = 0
        inStack = []
        outStack = []
    }

    func push(_ x: Int) {
        if inStack.isEmpty {
            front = x
        }
        inStack.append(x)
    }

    func pop() -> Int {
        if outStack.isEmpty {
            while !inStack.isEmpty {
                outStack.append(inStack.removeLast())
            }
        }
        return outStack.removeLast()
    }

    func peek() -> Int {
        if !outStack.isEmpty {
            return outStack.last!
        }
        return front
    }

    func empty() -> Bool {
        return inStack.isEmpty && outStack.isEmpty
    }
}
```