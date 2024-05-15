---
title: 剑指 Offer 61. 扑克牌中的顺子
categories:
- leetcode算法题
tags:
- Java
--- 

题目链接：https://leetcode-cn.com/problems/bu-ke-pai-zhong-de-shun-zi-lcof/

执行用时：0 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：38.7 MB, 在所有 Java 提交中击败了5.14% 的用户
通过测试用例：203 / 203

桶计数+双指针
``` java
class Solution {
    public boolean isStraight(int[] nums) {
        int[] arr = new int[14];
        for (int x : nums) {
            if (x > 0 && arr[x] > 0) {
                return false;
            }
            arr[x]++;
        }
        int l = 1, r = 13;
        while (arr[l] == 0) {
            l++;
        }
        while (arr[r] == 0) {
            r--;
        }
        return r - l < 5;
    }
}
```

排序+遍历
``` java
class Solution {
    public boolean isStraight(int[] nums) {
        Arrays.sort(nums);
        int joker = 0;
        for (int i = 0; i < 4; i++) {
            if (nums[i] == 0) {
                joker++;
            } else if (nums[i] == nums[i+1]) {
                return false;
            }
        }
        return nums[4] - nums[joker] < 5;
    }
}

```