## 要求
* 给定一个二叉树，检查它是否是镜像对称的。

## Python 代码
### 递归算法
* 思路：应满足的条件是两个根节点的值相同，同时每个根节点的左子树与另一个节点的右子树镜像对称

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        def isMirror(t1, t2):
            if t1 == None and t2 == None:
                return True
            if t1 == None or t2 == None:
                return False
            return t1.val == t2.val and isMirror(t1.right, t2.left) and isMirror(t1.left, t2.right)
        return isMirror(root, root)
```

### 迭代算法
* 思路：建立一个队列，每次

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def isSymmetric(self, root):
        """
        :type root: TreeNode
        :rtype: bool
        """
        queue = []
        queue.append(root)
        queue.append(root)
        while len(queue) != 0:
            t1 = queue[0]
            del queue[0]
            t2 = queue[0]
            del queue[0]
            if t1 == None and t2 == None:
                continue
            if t1 == None or t2 == None:
                return False
            if t1.val != t2.val:
                return False
            queue.append(t1.left)
            queue.append(t2.right)
            queue.append(t1.right)
            queue.append(t2.left)
        return True
```