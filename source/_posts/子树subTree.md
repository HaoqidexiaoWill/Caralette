---
title: 子树subTree
date: 2020-10-19 22:07:46
tags: 
- Python刷题
- BinaryTree
- Easy
---

链接：https://leetcode-cn.com/problems/shu-de-zi-jie-gou-lcof/submissions/

思路：

- 这是一类题
- 这类题先匹配根节点
- 然后匹配子树

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSubStructure(self, A: TreeNode, B: TreeNode) -> bool:
        if not A or not B: return False
        return self.check(A,B) or self.isSubStructure(A.left,B) or self.isSubStructure(A.right,B)
    def check(self,A,B):
        if B == None :return True
        if A == None :return False
        return A.val==B.val and self.check(A.left,B.left) and self.check(A.right,B.right)
```

