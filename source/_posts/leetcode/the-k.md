---
title: 1337. 矩阵中战斗力最弱的 K 行
categories:
- leetcode算法题
tags:
- Swift
---
题目链接：https://leetcode-cn.com/problems/the-k-weakest-rows-in-a-matrix/
### 解题思路

执行用时：76 ms, 在所有 Swift 提交中击败了100.00%的用户
内存消耗：13.8 MB, 在所有 Swift 提交中击败了100.00%的用户


在按行统计每行士兵数量的数组中，下标即原矩阵的行数，用对应值在另一个排序后的数组匹配，
匹配成功时的下标就是顺序数组的下标。修改统计数组中的值，下次再匹配到相同的值也就是之后的行数。

1，先统计矩阵每一行1的数量，记录到第一个数组diff
2，拷贝到新数组copy
3，给diff数组排序
4，初始化res数组
5，在copy这个按行顺序排列的数组中，寻找与排序后diff中相同的元素
6，找到后即修改顺序数组copy中的元素值，避免重复匹配，记录下标，跳出循环，
7，i向后移动，用diff中下一个元素继续在顺序数组copy中匹配
### 代码

```swift
class Solution {
    func kWeakestRows(_ mat: [[Int]], _ k: Int) -> [Int] {
        var diff = [Int](repeating: 0, count: mat.count)
        for i in 0 ..< mat.count {
            for j in 0 ..< mat[i].count {
                if mat[i][j] == 1 {
                    diff[i] += 1
                }
            }
        }
        var copy = diff
        diff.sort()
        var res = [Int](repeating: 0, count: k)
        for i in 0 ..< k {
            for j in 0 ..< diff.count {
                if copy[j] == diff [i] {
                    copy[j] = -1
                    res[i] = j
                    break
                }
            }
        }
        return res
    }
}

```