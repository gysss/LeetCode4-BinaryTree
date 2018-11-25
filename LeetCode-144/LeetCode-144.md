## 二叉树的前序遍历
### 要求
*   给定一个二叉树，返回它的 前序 遍历。

### 进阶
*   递归算法很简单，你可以通过迭代算法完成吗？

### 递归算法

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        res = []
        if root is None:
            return res
        res.append(root.val)
        if root.left:
            res.extend(self.preorderTraversal(root.left))
        if root.right:
            res.extend(self.preorderTraversal(root.right))
        return res
```

### 迭代算法
*   相较于中序遍历，只是改变了将节点值加入列表的位置

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def preorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        res = []
        node = root
        if node is None:
            return res
        stack = []
        while node is not None or len(stack)>0:
            if node is not None:
                res.append(node.val) // 不同点
                stack.append(node)
                node = node.left
            else:
                node = stack.pop()
                node = node.right
        return res
```