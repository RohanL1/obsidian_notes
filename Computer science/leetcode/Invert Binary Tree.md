____
Name: Invert Binary Tree
Timestamp: 08-01-2024 12:38:45,
Related Tags:  #leetcode #code #cs #easy ,
Summary: same as title,
Note:
____
# [Invert Binary Tree](https://leetcode.com/problems/invert-binary-tree/)

##### Question 
Given the `root` of a binary tree, invert the tree, and return _its root_

![[Pasted image 20240108124044.png]]

#### Answer 

### This is a *[[binary tree]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(n) 


#### recursive invert

recursive function 
swap left and right sub tree
pass these subtrees to same function ( recursive call for left and right subtree)



```python
	##### add code here
	def invertTree(self, root: Optional[TreeNode]) -> Optional[TreeNode]:
        if not root :
            return root
        root.left, root.right = root.right, root.left
        self.invertTree(root.left)
        self.invertTree(root.right)
        return root

```

___
Other related Links:
	neetcode video:
____
____
