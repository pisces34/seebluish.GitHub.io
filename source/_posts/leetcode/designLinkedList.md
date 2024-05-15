---
title: 707. 设计链表
categories:
- leetcode算法题
tags:
- Swift
- C++
- 链表
---

题目链接：https://leetcode-cn.com/problems/design-linked-list/
执行用时：340 ms, 在所有 Swift 提交中击败了55.54%的用户
内存消耗：14.1 MB, 在所有 Swift 提交中击败了80.33%的用户
``` Swift
class MyLinkedList {
    class ListNode {
        var element: Int        //元素值
        var next: ListNode?     //下个节点
        init(_ element: Int) {  //初始化传值
            self.element = element
            self.next = nil
        }
    }
    var head: ListNode?
    var size: Int
    /** Initialize your data structure here. */
    init() {
        head = ListNode(0)  //初始化头节点
        size = 0            //长度
    }
    
    /** Get the value of the index-th node in the linked list. If the index is invalid, return -1. */
    func get(_ index: Int) -> Int {
        if index > (size-1) || index < 0  { 
            return -1
        }
        var cur = head?.next    //指向头节点后的第一个节点
        var step = index
        while step > 0 {
            cur = cur?.next     //指针向后移动
            step -= 1
        }
        return cur!.element     //返回当前节点元素
    }
    
    /** Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list. */
    func addAtHead(_ val: Int) {    //头插法
        let cur = ListNode(val)     //初始化给新节点赋值
        cur.next = head?.next       //当前插入节点指向第一个节点
        head?.next = cur            //移动头节点指向插入节点
        size += 1                   //长度+1
    }
    
    /** Append a node of value val to the last element of the linked list. */
    func addAtTail(_ val: Int) {
        let cur = ListNode(val)
        var tail = head                 //尾指针指向头节点
        while ((tail!.next) != nil) {   //判断是否在尾部
            tail = tail?.next
        }
        cur.next = tail!.next           //插入节点指向空
        tail?.next = cur                //当前最后一个尾节点指向插入节点
        size += 1                       //长度+1
    }
    
    /** Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted. */
    func addAtIndex(_ index: Int, _ val: Int) {
        if index >= 0 && index <= size {        //判断插入索引是否在有效区间
            let newNode = ListNode(val)         //创建新节点并赋值
            var pre = head                      //定义一个指针来移动找到插入位置
            var step = index
            while step > 0 {
                pre = pre?.next                 
                step -= 1
            }                                   //插入前index所指位置为pre所指下一个节点
            newNode.next = pre?.next            //插入节点指向pre后一个节点
            pre?.next = newNode                 //pre指向新插入节点
            size += 1
        }
    }
    
    /** Delete the index-th node in the linked list, if the index is valid. */
    func deleteAtIndex(_ index: Int) {
        if (index < 0) || (index >= size) {     //判断索引是否在有效区间
            return
        }
        var pre = head
        var step = index
        while step > 0 {                       //移动指针到指定删除位置前一个节点处
            pre = pre?.next
            step -= 1
        }
        pre?.next = pre?.next?.next            //将要删除节点处的下一处节点位置赋给前一个节点的指针
        size -= 1
    }
}

```
执行用时：32 ms, 在所有 C++ 提交中击败了99.11% 的用户
内存消耗：19.1 MB, 在所有 C++ 提交中击败了45.07% 的用户

``` C++
class MyLinkedList {
public:
    /** Initialize your data structure here. */
    struct SinglyListNode {
        int val;
        SinglyListNode *next;
        SinglyListNode(int x) : val(x), next(NULL) {}
    };
    SinglyListNode *head;
    int size;
    MyLinkedList() {
        head = new SinglyListNode(0);
        size = 0;
    }

    /** Get the value of the index-th node in the linked list. If the index is invalid, return -1. */
    int get(int index) {
        if (index > (size-1) || index <0) {return -1;}
        SinglyListNode *cur = head->next;
        while (index--) cur = cur->next;
        return cur->val;
    }

    /** Add a node of value val before the first element of the linked list. After the insertion, the new node will be the first node of the linked list. */
    void addAtHead(int val) {
        SinglyListNode *node = new SinglyListNode(val);
        node->next = head->next;
        head->next = node;
        size++;
    }

    /** Append a node of value val to the last element of the linked list. */
    void addAtTail(int val) {
        SinglyListNode *node = new SinglyListNode(val);
        SinglyListNode *tail = head;
        while (tail->next) tail = tail->next;
        node->next = tail->next;
        tail->next = node;
        size++;
    }

    /** Add a node of value val before the index-th node in the linked list. If index equals to the length of linked list, the node will be appended to the end of linked list. If index is greater than the length, the node will not be inserted. */
    void addAtIndex(int index, int val) {
        if (index >=0 && index <= size) {
            SinglyListNode *node = new SinglyListNode(val);
            SinglyListNode *cur = head;
            while (index--) cur = cur->next;
            node->next = cur->next;
            cur->next = node;
            size++;
        }
    }

    /** Delete the index-th node in the linked list, if the index is valid. */
    void deleteAtIndex(int index) {
        if(index < 0 || index >= size) return ;
        SinglyListNode *cur = head;
        while (index--) cur = cur->next;
        cur->next = cur->next->next;
        size--;
    }
};
```
