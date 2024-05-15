---
title: 1. 两数之和 (HashMap)
date: 2021-05-08 14:00:39
categories:
- leetcode算法题
tags:
- Java
- HashMap
---
```java
import java.util.HashMap;
import java.util.Map;

public class Solution2 {
    public int[] twoSum(int[] nums, int target) {
        Map<Integer, Integer> map = new HashMap<Integer, Integer>();
        for(int i=0; i< nums.length; i++){
            map.put(nums[i], i);
        }
        for(int i=0; i< nums.length; i++){
            int aim = target-nums[i];
            if(map.containsKey(aim) && map.get(aim) != i){
                return new int[] {i, map.get(aim)};
            }
        }
        return null;
    }
}
```