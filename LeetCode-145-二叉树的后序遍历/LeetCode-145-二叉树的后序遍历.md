## 二叉树的后序遍历
### 要求
*   给定一个二叉树，返回它的 后序 遍历。

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
    def postorderTraversal(self, root):
        """
        :type root: TreeNode
        :rtype: List[int]
        """
        res = []
        if root is None:
            return res
        if root.left:
            res.extend(self.postorderTraversal(root.left))
        if root.right:
            res.extend(self.postorderTraversal(root.right))
        res.append(root.val)
        return res
```

### 迭代算法
* 因为先序遍历是中左右，后序遍历是左右中，所以可以采用中右左的方式进栈，最后输出时倒序输出即可

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def postorderTraversal(self, root):
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
                res.append(node.val)
                stack.append(node)
                node = node.right   // 不同点
            else:
                node = stack.pop()
                node = node.left    // 不同点
        return res[::-1] // 不同点
```