---
title: 167. 两数之和 II - 输入有序数组
categories:
- leetcode算法题
tags:
- Java
- 双指针
---
题目链接：https://leetcode-cn.com/problems/two-sum-ii-input-array-is-sorted/
和第一题的两数之和有些不同，因为是升序排列的，双指针，map，双循环都可以通过。

执行用时：1 ms, 在所有 Java 提交中击败了93.85% 的用户
内存消耗：38.7 MB, 在所有 Java 提交中击败了47.70% 的用户
``` Java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        int left = 0;
        int right = numbers.length-1;
        while (left<right){
            int mid = left+(right-left)/2;
            int sum = numbers[left]+numbers[right];
            if (target == sum){
                return new int[]{left+1,right+1};
            }else if(target>sum){
                left ++;
            }else{
                right --;
            }
        }
        return new int[]{-1,-1};
    }
}
``` 

执行用时：294 ms, 在所有 Java 提交中击败了5.03% 的用户
内存消耗：38.8 MB, 在所有 Java 提交中击败了32.46% 的用户
``` Java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
            for (int i=0; i<numbers.length; i++){
                for (int j =i+1; j<numbers.length; j++){
                    if (target - numbers[i] == numbers[j]){
                        return new int[] {i+1,j+1};
                    }
                }
            }
            return new int[]{-1,-1};
    }
}
``` 
map
执行用时：2 ms, 在所有 Java 提交中击败了33.04% 的用户
内存消耗：38.7 MB, 在所有 Java 提交中击败了38.82% 的用户
``` Java
class Solution {
    public int[] twoSum(int[] numbers, int target) {
        Map<Integer,Integer> map = new HashMap<>(numbers.length);
        for (int i = 0; i < numbers.length; i++) {
            if (map.get(target - numbers[i])!=null){
                return new int[] {map.get(target-numbers[i])+1,i+1};
            }
            map.put(numbers[i],i);
        }
        return new int[]{-1,-1};
    }
}
```