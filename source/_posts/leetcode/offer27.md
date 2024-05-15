---
title: 剑指 Offer 27. 二叉树的镜像
categories:
- leetcode算法题
tags:
- Swift
- Kotlin
- 二叉树
--- 

题目链接：https://leetcode-cn.com/problems/er-cha-shu-de-jing-xiang-lcof/


### 代码

``` swift
class Solution {
    func mirrorTree(_ root: TreeNode?) -> TreeNode? {
        if root == nil {
            return root
        }
        var temp = root?.left
        root?.left = root?.right
        root?.right = temp
        mirrorTree(root?.left)
        mirrorTree(root?.right)
        return root
    }
}

```

Kotlin:
执行用时：132 ms, 在所有 Kotlin 提交中击败了94.87% 的用户
内存消耗：32.9 MB, 在所有 Kotlin 提交中击败了12.82% 的用户
``` swift
class Solution {
    fun mirrorTree(root: TreeNode?): TreeNode? {
        root ?: return null
        var temp = root.left
        root.left = root.right
        root.right = temp
        mirrorTree(root.left)
        mirrorTree(root.right)
        return root
    }
}

```
