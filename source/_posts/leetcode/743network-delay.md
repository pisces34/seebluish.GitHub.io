---
title: 743. 网络延迟时间
categories:
- leetcode算法题
tags:
- Swift
- 图论
- 邻接矩阵
- Dijkstra
---

执行用时：412 ms, 在所有 Swift 提交中击败了100.00%的用户
内存消耗：13.9 MB, 在所有 Swift 提交中击败了100.00%的用户

### 解题思路

每次找最短路径，到其他各点的最短路径中的最大值也就是消息能发到的最少时间
如果还有一个正无穷也就是到不了的距离,说明无法全部送到


### 代码

```swift
class Solution {
    func networkDelayTime(_ times: [[Int]], _ n: Int, _ k: Int) -> Int {
        let maxDist = Int.max/2
        
        //邻接矩阵存储边信息
        var graph = [[Int]](repeating: [Int](repeating: maxDist, count: n), count: n)
        for i in 0 ..< times.count {
            // 边序号从 0 开始
            let x = times[i][0] - 1, y = times[i][1] - 1
            graph[x][y] = times[i][2]
        }
        // 从源点到某点的距离数组
        var dist = [Int](repeating: maxDist, count: n)
        
        // 由于从 k 开始，所以该点距离设为 0，也即源点
        dist[k - 1] = 0;
        
        //表示节点是否被更新的数组
        var used = [Bool](repeating: false, count: n)
        
        for _ in 0 ..< n {
            var x = -1
            for y in 0 ..< n {
                //x == -1说明是改变起点后(矩阵中换行了)
                //寻找新dist中的最小值且未被访问过
                if (!used[y] && (x == -1 || dist[y] < dist[x])) {
                    x = y
                }
            }
            
            //更新该点到邻接点的距离
            used[x] = true
            for y in 0 ..< n {
                dist[y] = min(dist[y], dist[x] + graph[x][y])
            }
            
        }
        //找到距离最远的点
        let res = dist.max()!
        return res == maxDist ? -1 : res
    }
}

```