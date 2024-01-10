
____
Name: Maximum Depth of Binary Tree
Timestamp: 08-01-2024 12:50:51,
Related Tags:  #leetcode #code #cs,
Summary: same as title,
Note:
____
# [Maximum Depth of Binary Tree](https://leetcode.com/problems/maximum-depth-of-binary-tree/)

##### Question 
Given the `root` of a binary tree, return _its maximum depth_.

A binary tree's **maximum depth** is the number of nodes along the longest path from the root node down to the farthest leaf node.


#### Answer 

### This is a *[[binary tree]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)


#### recursive max length
go to leaf nodes through recursion
after that return 1 for each level 
and take max height from left and right subtree and propagate to top




```python
	##### add code here
def maxDepth(self, root: Optional[TreeNode]) -> int:
	if not root:
		return 0
	left_h  = self.maxDepth(root.left)
	right_h = self.maxDepth(root.right)

	return max(left_h, right_h)
	
	## one liner
	## return max(self.maxDepth(root.left),self.maxDepth(root.right)) + 1 if root else 0
```

___
Other related Links:
	neetcode video:
____
____
