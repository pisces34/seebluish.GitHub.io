---
title: 703. 数据流中的第 K 大元素
categories:
- leetcode算法题
tags:
- Java
- 优先队列
---

题目链接：https://leetcode-cn.com/problems/kth-largest-element-in-a-stream/



``` java
class KthLargest {
    PriorityQueue<Integer> queue = new PriorityQueue<>();
    int point = 0;
    public KthLargest(int k, int[] nums) {
        point = k;
        for (int num: nums) {
            add(num);
        }
    }

    public int add(int val) {
        queue.offer(val);
        if (queue.size() > point) {
            queue.poll();
        }
        return queue.peek();
    }
}
```