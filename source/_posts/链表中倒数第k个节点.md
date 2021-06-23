---
title: 链表中倒数第k个节点
date: 2020-10-19 22:08:46
tags: 
- Python刷题
- ListNode
- Easy

---

链接：https://leetcode-cn.com/problems/lian-biao-zhong-dao-shu-di-kge-jie-dian-lcof/submissions/

思路：

- ​	快慢指针

```python
# Definition for singly-linked list.
# class ListNode:
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution:
    def getKthFromEnd(self, head: ListNode, k: int) -> ListNode:
        first_ptr,last_ptr = head,head
        for i in range(k):
            first_ptr = first_ptr.next
        while first_ptr:
            first_ptr = first_ptr.next
            last_ptr = last_ptr.next
        return last_ptr
```

