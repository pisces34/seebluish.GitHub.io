---
title: 26. 删除有序数组中的重复项
categories:
- leetcode算法题
tags:
- C++
- Swift
- 链表
---
题目链接：https://leetcode-cn.com/problems/remove-duplicates-from-sorted-array/
执行用时：68 ms, 在所有 Swift 提交中击败了94.44%的用户
内存消耗：14.4 MB, 在所有 Swift 提交中击败了61.90%的用户

``` Swift
class Solution {
    func removeDuplicates(_ nums: inout [Int]) -> Int {
        var low = 0
        if nums.isEmpty {
            return 0
        }
        for i in 0 ..< nums.count {
            if nums[low] != nums[i] {
                low += 1
                nums[low] = nums[i]
            }
        }
        return low+1
    }
}
```

执行用时：4 ms, 在所有 C++ 提交中击败了99.00%的用户
内存消耗：17.8 MB, 在所有 C++ 提交中击败了16.35%的用户

``` C++
class Solution {
public:
    int removeDuplicates(vector<int> &nums) {
        int low = 0;
        if (nums.empty()) { return low; }
        for (int i = 0; i < nums.size(); ++i) {
            if (nums[low] != nums[i]) {
                nums[++low] = nums[i];
            }
        }
        return low + 1;
    }
};
```