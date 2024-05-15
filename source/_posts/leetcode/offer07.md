---
title: 剑指 Offer 07. 重建二叉树
categories:
- leetcode算法题
tags:
- Java
- 二叉树
--- 

题目链接：https://leetcode-cn.com/problems/zhong-jian-er-cha-shu-lcof/

执行用时：1 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：38.7 MB, 在所有 Java 提交中击败了17.04% 的用户

前序遍历第一个值为根结点，在哈希表中存入中序遍历数组中的值和索引
分别对前序和中序的左子树递归，然后再对右子树递归
``` java
class Solution {
    HashMap<Integer, Integer> indexMap;
    public TreeNode buildTree(int[] preorder, int[] inorder) {
        int n = preorder.length
        indexMap = new HashMap<>();
        for(int i = 0; i < n; i++) {
            indexMap.put(inorder[i], i);
        }
        return myBuildTree(preorder, inorder, 0, n-1, 0, n-1);
    }

    private TreeNode myBuildTree(int[] preorder, int[] inorder, int preorderLeft, int preorderRight, int inorderLeft, int inorderRight) {
        if (preorderLeft > preorderRight) {
            return null;
        }
        int preorderRoot = preorderLeft;
        int inorderRoot = indexMap.get(preorder[preorderLeft])
        TreeNode root = new TreeNode(preorder[preorderLeft]);
        int sizeLeftSubTree = inorderRoot - inorderLeft;
        root.left = myBuildTree(preorder,inorder, preorderLeft+1, preorderLeft+sizeLeftSubTree, inorderLeft, inorderRoot-1);
        root.right = myBuildTree(preorder,inorder, preorderLeft+sizeLeftSubTree+1, preorderRight, inorderRoot+1, inorderRight);
        return root;
    }
}
```