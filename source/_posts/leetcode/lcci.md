---
title: 面试题 03.01. 三合一
categories:
- leetcode算法题
tags:
- Swift
- 栈
---

题目链接：https://leetcode-cn.com/problems/three-in-one-lcci/

### 解题思路
每个stackNum前后增加一个位置来判断是空还是满。
    //[-1 0 -1] [-1 1 -1] [-1 2 -1]
    //0          3          6
    //[-1 0 1 -1]  [-1 2 3 -1] [-1 4 5 -1]
    //0              4           8
    //[-1 0 1 2 -3] [-1 3 4 5 -1] [-1 6 7 8 -1]
    //0               5           10

应该是没什么人用swift提交。。
执行用时：216 ms, 在所有 Swift 提交中击败了100.00%的用户
内存消耗：15.9 MB, 在所有 Swift 提交中击败了100.00%的用户

### 代码

```swift
class TripleInOne {
    var arr: [Int]
    var x: Int
    var y: Int
    var z: Int
    let width:Int
    init(_ stackSize: Int) {
        width = (stackSize+2)
        arr = [Int].init(repeating: -1, count: width*3)
        x = 0
        y = width
        z = width*2
    }
    func push(_ stackNum: Int, _ value: Int) {
        if stackNum == 0 {
            if x < width - 2 {
                x += 1
                arr[x] = value
            }
        } else if stackNum == 1 {
            if y < width*2 - 2 {
                y += 1
                arr[y] = value
            }
        } else {
            if z < width*3 - 2 {
                z += 1
                arr[z] = value
            }
        }
    }

    func pop(_ stackNum: Int) -> Int {
        var res = 0
        if stackNum == 0 {
            if x == 0 {
                res = -1
            } else {
                res = arr[x]
                arr[x] = -1
                x -= 1
            }
        } else if stackNum == 1 {
            if y == width {
                res = -1
            } else {
                res = arr[y]
                arr[y] = -1
                y -= 1
            }
        } else {
            if z == width*2 {
                res = -1
            } else {
                res = arr[z]
                arr[z] = -1
                z -= 1
            }
        }
        return res
    }

    func peek(_ stackNum: Int) -> Int {
        if stackNum == 0 {
            return arr[x]
        } else if stackNum == 1 {
            return arr[y]
        } else {
            return arr[z]
        }
    }

    func isEmpty(_ stackNum: Int) -> Bool {
        if stackNum == 0 {
            if x == 0 {
                return true
            }
        } else if stackNum == 1 {
            if y == width {
                return true
            }
        } else {
            if z == width*2 {
                return true
            }
        }
        return false
    }
}
```