### 要求
    填充它的每个 next 指针，让这个指针指向其下一个右侧节点。如果找不到下一个右侧节点，则将 next 指针设置为 NULL。

  初始状态下，所有 next 指针都被设置为 NULL。
  
  
### Python代码
    之前的LeetCode-116代码同样适用于此题...两题区别在于116是完美二叉树，此题不是，但是之前的解法都适用。

```python
# Definition for binary tree with next pointer.
# class TreeLinkNode:
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None
#         self.next = None

class Solution:
    # @param root, a tree link node
    # @return nothing
    def connect(self, root):
        list1 = []
        list2 = []
        if not root:
            return
        list1.append(root)
        while len(list1)>0 or len(list2)>0:
            if len(list1)>0:
                while True:
                    node = list1[0]
                    if node.left:
                        list2.append(node.left)
                    if node.right:
                        list2.append(node.right)
                    del list1[0]
                    if len(list1)>0:
                        node2 = list1[0]
                        node.next = node2
                    else:
                        break
                        
            else:
                while True:
                    node = list2[0]
                    if node.left:
                        list1.append(node.left)
                    if node.right:
                        list1.append(node.right)
                    del list2[0]
                    if len(list2)>0:
                        node2 = list2[0]
                        node.next = node2
                    else:
                        break
        return
```