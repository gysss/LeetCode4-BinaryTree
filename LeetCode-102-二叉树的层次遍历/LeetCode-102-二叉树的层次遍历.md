## 二叉树的层次遍历
### 要求
* 给定一个二叉树，返回其按层次遍历的节点值。 （即逐层地，从左到右访问所有节点）。

### 思路
* 迭代算法
* 栈1 栈2保存节点，依次退出栈1的节点，并将子节点加入到栈2中，栈2同理

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def levelOrder(self, root):
        """
        :type root: TreeNode
        :rtype: List[List[int]]
        """
        stack1 = []
        stack2 = []
        if not root:
            return []
        node = root
        temp = []
        ans = []
        stack1.append(node)
        while len(stack1)>0 or len(stack2)>0:
            if len(stack1)>0:
                while len(stack1)>0:       
                    node = stack1[0]
                    temp.append(node.val)
                    if node.left:
                        stack2.append(node.left)
                    if node.right:
                        stack2.append(node.right)
                    del stack1[0]
            else:
                while len(stack2)>0:
                    node = stack2[0]
                    temp.append(node.val)
                    if node.left:
                        stack1.append(node.left)
                    if node.right:
                        stack1.append(node.right)
                    del stack2[0]
            ans.append(temp)
            temp = []
        return ans                    
```

* 递归算法
* 函数dfs传入参数为节点，层次，返回的列表，所以列表的长度代表了层数，所以如果当前传入的层数大于列表的长度，则在列表末尾加一个空的[]，用以存放新的一层的节点信息

```python
class Solution:
   def levelOrder(self, root):
       def dfs(node, level, res):
           if not node:
               return
           if len(res) < level:
               res.append([])
           res[level-1].append(node.val)
           dfs(node.left, level+1, res)
           dfs(node.right, level+1, res)
       res = []
       dfs(node, 1, res)
       return res
```