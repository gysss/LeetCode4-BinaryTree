###要求
* 根据一棵树的中序遍历与后序遍历构造二叉树。
  注意:
  你可以假设树中没有重复的元素。

### python 代码
* 思路：后续遍历的最后一个数便是根结点，在中序遍历中找到根结点对应的下标，则左边为左子树，右边为右子树

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def buildTree(self, inorder, postorder):
        """
        :type inorder: List[int]
        :type postorder: List[int]
        :rtype: TreeNode
        """
        if not inorder:
            return None
        root = TreeNode(postorder.pop())
        idx = inorder.index(root.val)
        
        # 先右后左
        root.right = self.buildTree(inorder[idx+1:], postorder)
        root.left = self.buildTree(inorder[:idx], postorder)
        return root
```