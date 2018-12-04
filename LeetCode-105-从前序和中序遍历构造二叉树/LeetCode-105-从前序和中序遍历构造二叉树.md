### 要求
*   根据一棵树的前序遍历与中序遍历构造二叉树。
    注意:
    你可以假设树中没有重复的元素。

### python 代码
* 思路：前序的第一个数便是一个根节点，找到该节点在中序的下标，则前面为左子树，后面为右子树

```python
# Definition for a binary tree node.
# class TreeNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution:
    def buildTree(self, preorder, inorder):
        """
        :type preorder: List[int]
        :type inorder: List[int]
        :rtype: TreeNode
        """
        if not inorder:
            return None
        root = TreeNode(preorder[0])
        idx = inorder.index(preorder[0])
        del preorder[0]
        
        # 先左后右
        root.left = self.buildTree(preorder, inorder[:idx])
        root.right = self.buildTree(preorder, inorder[idx+1:])
        return root
```