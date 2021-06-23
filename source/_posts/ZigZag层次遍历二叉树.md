---
title: ZigZag层次遍历二叉树
date: 2020-10-19 23:09:46
tags: 
- Python刷题
- BinaryTree
- Easy
---

链接：https://leetcode-cn.com/problems/cong-shang-dao-xia-da-yin-er-cha-shu-iii-lcof/

思路：

- 搞一个flag 记录一下

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def levelOrder(self, root: TreeNode) -> List[List[int]]:
        if not root: return None
        results,nodes = [],[root]
        flag = 0
        while(nodes):
            curStack,nextStack = [],[]
            for node in nodes:
                curStack.append(node.val)
                if node.left:
                    nextStack.append(node.left)
                if node.right:
                    nextStack.append(node.right)
            if flag%2 ==1:
                curStack = curStack[::-1]
            flag+=1
            results.append(curStack)
            nodes = nextStack
        return results

```

