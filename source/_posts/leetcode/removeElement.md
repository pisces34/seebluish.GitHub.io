---
title: 27. 移除元素
categories:
- leetcode算法题
excerpt: 第一次提交就接近双100%，哈哈。
tags:
- Java
- 双指针
---
题目链接：https://leetcode-cn.com/problems/remove-element/

执行用时：1 ms, 在所有 Java 提交中击败了100.00% 的用户
内存消耗：36.7 MB, 在所有 Java 提交中击败了96.64% 的用户

``` Java
class Solution {
    public int removeElement(int[] nums, int val) {
        int count=0;
        int temp;
        int right = nums.length-1;
        Arrays.sort(nums);
        for (int i=0; i< nums.length; ++i){
            if(nums[i] !=val){
                count++;
            }else if(i<right){
                temp = nums[i];
                if (nums[right]!=temp){
                    nums[i] = nums[right];
                    nums[right] = temp;
                    count++;
                }
                right--;
            }
        }
        return count;
    }
}
```