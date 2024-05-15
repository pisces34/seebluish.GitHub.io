---
title: 611. 有效三角形的个数
categories:
- leetcode算法题
tags:
- Swift
- Java
- C++
- 双指针
- 数组
---
题目链接：https://leetcode-cn.com/problems/valid-triangle-number/
执行用时：128 ms, 在所有 Swift 提交中击败了100.00%的用户
内存消耗：13.7 MB, 在所有 Swift 提交中击败了40.00%的用户

### 解题思路

1，先将数组升序排列，外层循环i递增，每次向后扫描的数即还未进行比较的第三条边
2，第三条边之前一个数为第二条边，就是右指针所在位置，即右边界
3，左指针总是从最左边开始，作为比较的第一条边，即左边界
4，从左开始比较，需要满足三角形条件两边之和大于第三边，由于是升序，当符合条件时，
从左指针开始的位置到右指针前的数，它们加上第二条边都大于第三边
5，所以边界作差即为有效个数。
6，此时右指针向左移动，修改为要比较的第二条边，
如果和左指针重合说明左边的数都已比较，就会退出循环进入下一轮外循环扫描新的边。


### 代码

```swift
class Solution {
    func triangleNumber(_ nums: [Int]) -> Int {
        if nums.count < 3 { return 0 }
        var sortnum = nums
        sortnum.sort()
        let len = nums.count - 1
        var left = 0
        var right = 1
        var count = 0
        for i in 2 ... len {
            right = i - 1
            left = 0
            while left < right {
                if sortnum[left] + sortnum[right] > sortnum[i]{
                    count += right - left
                    right -= 1
                } else {
                    left += 1
                }
            }
        }
        return count
    }
}

```

java时间给的时间多，略有区别，当一二条边重合时，固定第二条边，向后移动第三条边。
当第三条边走过末尾时，使得第二条边往后，此时后一位数位第三条边。
```java
class Solution {
    public int triangleNumber(int[] nums) {
        int len = nums.length;
        if(len < 3) {return 0;}
        Arrays.sort(nums);
        int res = 0;
        int a =0,b=1,c=2;
        while (b!=len-1) {      //走到最后一个下标时即全部访问完
            while (a != b) {    //第一条边和第二条边尚未重合
                if (nums[a] + nums[b] > nums[c]) {
                    res = res + b - a;      //边界之差
                    break;
                }
                a += 1;     //向后移动第一条边
            }
            a = 0;          //第一条边从起点开始
            c += 1;         //向后移动第三条边
            if (c == len) { //第三条边下标在加1后等于数组长度即越界
                b += 1;     //向后移动第二条边
                c = b + 1;  //向后移动第三条边
            }
        }
        return res;
    }
}
```