____
Name: Diameter of Binary Tree
Timestamp: 08-01-2024 13:24:05,
Related Tags:  #leetcode #code #cs #mid ,
Summary: same as title,
Note:
____
# [Diameter of Binary Tree](https://leetcode.com/problems/diameter-of-binary-tree/)

##### Question 
Given the `root` of a binary tree, return _the length of the **diameter** of the tree_.

The **diameter** of a binary tree is the **length** of the longest path between any two nodes in a tree. This path may or may not pass through the `root`.

The **length** of a path between two nodes is represented by the number of edges between them.


#### Answer 

### This is a *[[binary tree]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)


#### same as [[Maximum Depth of Binary Tree]], checking diameter at each level to find the global max, rather than diameter at root


```python
	##### add code here
def diameterOfBinaryTree(self, root: Optional[TreeNode]) -> int:
        di = [0]
        def dfs(root):
            if not root:
                return 0
            
            l = dfs(root.left)
            r = dfs(root.right)

            di[0] = max(l+r, di[0])
            return 1 + max(l,r)
        
        dfs(root)
        return di[0]

```

___
Other related Links:
	neetcode video:
____
____
