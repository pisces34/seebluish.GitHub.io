---
title: 19. 删除链表的倒数第 N 个结点
categories:
- leetcode算法题
tags:
- Swift
- 双指针
- C++
---

题目链接：https://leetcode-cn.com/problems/remove-nth-node-from-end-of-list/
执行用时：0 ms, 在所有 C++ 提交中击败了100.00%的用户
内存消耗：10.3 MB, 在所有 C++ 提交中击败了75.79%的用户

``` C++
class Solution {
public:
    ListNode* removeNthFromEnd(ListNode* head, int n) {
        ListNode *fast = head;
        int count = 0;
        while (fast->next){
            fast = fast->next;
            count++;    //最后一个节点前的节点数
        }
        if(count + 1 == n){
            head = head->next;
        }else{
            count = count  - n;
            if(count == 0 && n == 1){
                head->next = NULL;
            }else{
                fast = head;
                for (int i = 0; i < count; ++i) {
                    fast = fast->next;
                }
                fast->next = fast->next->next;
            }
        }
        return head;
    }
};
```

### 解题思路
设置慢指针指向头节点之前的新节点，当快指针先走n步后，和慢指针中间就隔了n个节点。
同时开始移动，当快指针移动到最后一个节点之后的空节点时，慢指针后面有n个节点，
于是倒数第n个节点就是慢指针后面的那个节点。

当链表中只有一个节点时，因为头节点前还一个节点，末尾又有一个节点，
删除唯一的节点时，就产生了和普通情况下删除中间节点一样的条件。

### 代码
执行用时：4 ms, 在所有 Swift 提交中击败了98.73%的用户
内存消耗：13.6 MB, 在所有 Swift 提交中击败了37.06%的用户
```swift
class Solution {
    func removeNthFromEnd(_ head: ListNode?, _ n: Int) -> ListNode? {
        var beforeHead = ListNode(0, head)
        var slow = beforeHead, fast = head
        for _ in 0..<n {
            fast = fast?.next
        }
        while fast != nil {
            fast = fast?.next
            slow = slow.next ?? beforeHead
        }
        slow.next = slow.next?.next
        return beforeHead.next
    }
}

```