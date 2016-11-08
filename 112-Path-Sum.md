# Path Sum

> Given a binary tree and a sum, determine if the tree has a root-to-leaf path such that adding up all the values along the path equals the given sum.

>For example:
> Given the below binary tree and sum = 22,
> 
              5
             / \
            4   8
           /   / \
          11  13  4
         /  \      \
        7    2      1
return true, as there exist a root-to-leaf path 5->4->11->2 which sum is 22.

---

```python
# Definition for a binary tree node.
# class TreeNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.left = None
#         self.right = None

class Solution(object):
    def hasPathSum(self, root, sum):
        """
        :type root: TreeNode
        :type sum: int
        :rtype: bool
        """
        if root==None:
            return False
        def hasSum(node,needSum):
            
            if node.left==None and node.right==None:
                if node.val==needSum:
                    return True
                else:
                    return False
            left=False
            right=False
            if node.left!=None:
                left=hasSum(node.left,needSum-node.val)
            if node.right!=None:
                right=hasSum(node.right,needSum-node.val)
            
            return left or right
                    
        
        return hasSum(root,sum)
```
- 这道题目有几个要点在于，一定找到的是path，即从root到leaf，比如[1,2]中到sum=1，下面这个返回的应该是False

```
     1
    /
   2
```


- path所在路径上的数有正负之分，比如在下面找-1，

```python
            1
           / \
         -2   -3
        /
       1
      /
     -1
```
因为root=1，那么在左子树上找-1-1=-2，不能因为左子树的根为-2，就认为该条路径上相加不能为-2，其下面的1和-1之和为0






