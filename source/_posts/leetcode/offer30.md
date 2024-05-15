---
title: 剑指 Offer 30. 包含min函数的栈
categories:
- leetcode算法题
tags:
- Java
--- 

题目链接：https://leetcode-cn.com/problems/bao-han-minhan-shu-de-zhan-lcof/

执行用时：17 ms, 在所有 Java 提交中击败了93.54% 的用户
内存消耗：40.2 MB, 在所有 Java 提交中击败了59.44% 的用户

``` java
class MinStack {
    Stack<Integer> s1,s2;
    /** initialize your data structure here. */
    public MinStack() {
        s1 = new Stack<>();
        s2 = new Stack<>();
    }

    public void push(int x) {
        s1.push(x);
        if (s2.isEmpty() || x <= s2.lastElement()) {
            s2.push(x);
        }
    }

    public void pop() {
        if (s1.pop().equals(s2.lastElement())) {
            s2.pop();
        }
    }

    public int top() {
        return s1.peek();
    }

    public int min() {
        return s2.peek();
    }
}
```

``` java
class MinStack {
    Deque<Integer> data;
    Deque<Integer> help ;
    public MinStack() {
        data = new ArrayDeque<>();
        help = new ArrayDeque<>();
    }

    public void push(int x) {
        data.addLast(x);
        if (help.isEmpty() || help.peekLast() >= x) {
            help.addLast(x);
        } else {
            help.addLast(help.peekLast());
        }
    }

    public void pop() {
        help.pollLast();
        data.pollLast();
    }

    public int top() {
        return data.peekLast();
    }

    public int min() {
        return help.peekLast();
    }
}
```