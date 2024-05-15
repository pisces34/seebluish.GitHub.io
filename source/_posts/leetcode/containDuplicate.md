---
title: 219. 存在重复元素 II
categories:
- leetcode算法题
tags:
- C++
- Set
- Java
---
题目链接：https://leetcode-cn.com/problems/contains-duplicate-ii/
执行用时：28 ms, 在所有 C++ 提交中击败了86.81% 的用户
内存消耗：15.9 MB, 在所有 C++ 提交中击败了72.51% 的用户
``` C++
class Solution {
public:
    bool containsNearbyDuplicate(vector<int> &nums, int k) {
        unordered_set<int> s;
        int n = nums.size();
        int cur = 0;
        for (int i = 0; i < n; ++i) {
            cur = nums[i];
            if (s.find(cur) == s.end()) {
                s.insert(cur);
                if (s.size() > k) { //一旦超过k的长度就去掉前面k距离前的值
                    s.erase(nums[i - k]);
                }
            }else{//再次找到nums[i]说明小于距离k
                return true;
            }
        }
        return false;
    }
};

```

执行用时：10 ms, 在所有 Java 提交中击败了58.33% 的用户
内存消耗：41.7 MB, 在所有 Java 提交中击败了68.78% 的用户
``` Java
class Solution {
    public boolean containsNearbyDuplicate(int[] nums, int k) {
        Set<Integer> set = new HashSet<>();
        for (int i = 0; i < nums.length; i++) {
            if (set.contains(nums[i])) {
                return true;
            }
            set.add(nums[i]);
            if (set.size() > k) {
                set.remove(nums[i - k]);
            }
        }
        return false;
    }
}
```