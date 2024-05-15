---
title: 剑指 Offer 32 - III. 从上到下打印二叉树 III
categories:
- leetcode算法题
tags:
- Swift
- Kotlin
- 二叉树
--- 

题目链接：https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/

执行用时：12 ms, 在所有 Swift 提交中击败了73.68% 的用户
内存消耗：13.5 MB, 在所有 Swift 提交中击败了94.74% 的用户

### 解题思路
奇数行逆序

### 代码

``` swift
class Solution {
    func levelOrder(_ root: TreeNode?) -> [[Int]] {
        if root == nil {
            return []
        }
        var queue = [TreeNode]()
        var res = [[Int]]()
        var isOdd = true
        queue.append(root!)
        while !queue.isEmpty {
            var row = [Int]()
            for i in 0 ..< queue.count {
                var cur = queue.removeFirst()
                row.append(cur.val)
                if let node = cur.left {
                    queue.append(node)
                }
                if let node = cur.right {
                    queue.append(node)
                }
            }
            if !isOdd {
                row.reverse()
            }
            res.append(row)
            isOdd = !isOdd
        }
        return res
    }
}
```

Kotlin:
``` swift
class Solution {
    fun levelOrder(root: TreeNode?): List<List<Int>> {
        if (root == null) {
            return emptyList()
        }
        val queue = ArrayDeque<TreeNode>()
        val list = ArrayList<ArrayList<Int>>()
        queue.add(root)
        while (queue.isNotEmpty()) {
            var arr = ArrayDeque<Int>()
            for (i in queue.size downTo 1 step 1) {
                var cur = queue.removeFirst()
                if (list.size % 2 == 0) {
                    arr.addLast(cur.`val`)
                } else {
                    arr.addFirst(cur.`val`)
                }
                cur.left?.let {
                    queue.add(cur.left!!)
                }
                cur.right?.let {
                    queue.add(cur.right!!)
                }
            }
            var res = ArrayList<Int>(arr)
            list.add(res)
        }
        return list
    }
}
```
