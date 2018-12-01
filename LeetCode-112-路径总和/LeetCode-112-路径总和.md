### 要求
* 给定一个二叉树和一个目标和，判断该树中是否存在根节点到叶子节点的路径，这条路径上所有节点值相加等于目标和。

### Python 代码
* 递归实现

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def hasPathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: bool
        """
        if not root :
            return False
        if sum == root.val and root.left == None  and root.right == None:
            return True
        return self.hasPathSum(root.right,sum-root.val) or self.hasPathSum(root.left,sum-root.val)
```