____
Name: Same Tree
Timestamp: 08-01-2024 14:04:37,
Related Tags:  #leetcode #code #cs #easy ,
Summary: same as title,
Note:
____
# [Same Tree](https://leetcode.com/problems/same-tree/)

##### Question 
Given the roots of two binary trees `p` and `q`, write a function to check if they are the same or not.

Two binary trees are considered the same if they are structurally identical, and the nodes have the same value.


#### Answer 

### This is a *[[binary tree]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)


#### recursive equal check



```python
	##### add code here

def isSameTree(self, p: Optional[TreeNode], q: Optional[TreeNode]) -> bool:
        if not p and not q:
            return True
        if (not q) or (not p) or (p.val != q.val):
            return False
        return self.isSameTree(p.left, q.left) and self.isSameTree(p.right, q.right)
```

___
Other related Links:
	neetcode video:
____
____
