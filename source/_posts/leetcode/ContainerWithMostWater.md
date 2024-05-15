---
title: 11. 盛最多水的容器
categories:
- leetcode算法题
tags:
- Java
- 双指针
---
```java
//双指针法
class Solution {
    public int maxArea(int[] height) {
        int ans = 0;
        int area = 0;
        int left = 0;
        int right = height.length-1;
        while (left < right) {
            area = Math.min(height[left], height[right])*(right-left);
            ans = Math.max(area, ans);
            if(height[left] >= height[right]) {
                right--;
            }else{
                left++;
            }
        }
        return ans;
    }
}

//暴力法
class Violence {
    public int maxArea(int[] height) {
        int max = -1;
        int area = 0;
        int left = 0;
        int right = 0;
        int wide = height.length;
        int blow = wide -1;
        for(left=0; left < wide; left++) {
            blow = wide- 1 - left;
            for(right = wide -1; right> left ; right --) {
                if(height[left] <= height[right]) {
                    area = height[left]*blow;
                    blow --;
                }else{
                    area = height[right]*blow;
                    blow --;
                }
                if(area >= max) {
                    max = area;
                }
            }
        }
        return max;
    }
}
```