### 要求
*   填充它的每个 next 指针，让这个指针指向其下一个右侧节点。如果找不到下一个右侧节点，则将 next 指针设置为 NULL。

    初始状态下，所有 next 指针都被设置为 NULL。

### Python代码
* 思路：大体上同LeetCode-102层次遍历中的迭代算法，只不过不需要保存节点的值了，改为将节点的next指针指向列表中的下一个点，如果列表中没有下一个点了，就break

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