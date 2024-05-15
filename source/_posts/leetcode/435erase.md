---
title: 435. 无重叠区间
categories:
- leetcode算法题
tags:
- Swift
- 数组
---

``` swift
class Solution {
    func eraseOverlapIntervals(_ intervals: [[Int]]) -> Int {
        if intervals.count == 0 {
            return 0
        }
        var sortedArr = intervals.sorted { $0[0] < $1[0] }
        var res = 0
        let n = sortedArr.count
        for i in 1 ..< n {
            if sortedArr[i-1][1] - sortedArr[i][0] > 0 {
                res += 1
                sortedArr[i][1] = min(sortedArr[i-1][1],sortedArr[i][1])
            }
        }
        return res
    }
}
```