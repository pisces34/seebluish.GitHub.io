---
title: 724. 寻找数组的中心下标
categories:
- leetcode算法题
tags:
- Java
---
```java
public class Solution {
    public int pivotIndex(int[] nums) {
        int sum=0;
        int leftSum =0;
        for (int i:nums) {
            sum+=i;
        }
        for (int i = 0; i < nums.length; i++) {
            if(leftSum == sum - leftSum-nums[i]){
                return i;
            }
            leftSum+=nums[i];
        }
        return -1;
    }
}
```
