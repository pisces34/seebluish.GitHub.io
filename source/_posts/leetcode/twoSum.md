---
title: 1. 两数之和(violence)
date: 2021-05-08 14:51:39
categories:
- leetcode算法题
tags:
- Java
---

```java

class Violence {
    public int[] twoSum(int[] nums, int target) {
        for (int i = 0; i < nums.length; i++) {
            for (int j = i + 1; j < nums.length; j++) {
                if (nums[j] == target - nums[i]) {
                    return new int[] { i, j };
                }
            }
        }
        throw new IllegalArgumentException("No two sum solution");
    }
}

/*
  复杂度分析：

时间复杂度：O(n^2)O(n2)
对于每个元素，我们试图通过遍历数组的其余部分来寻找它所对应的目标元素，
这将耗费 O(n)O(n) 的时间。因此时间复杂度为 O(n^2)O(n2)。

空间复杂度：O(1)O(1)。
 */
 ```