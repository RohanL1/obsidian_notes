____
Name: Balanced Binary Tree
Timestamp: 08-01-2024 13:43:51,
Related Tags:  #leetcode #code #cs #easy ,
Summary: same as title,
Note:
____
# [Balanced Binary Tree](https://leetcode.com/problems/balanced-binary-tree/)

##### Question 
Given a binary tree, determine if it is **height-balanced.**
A **height-balanced** binary tree is a binary tree in which the depth of the two subtrees of every node never differs by more than one.

#### Answer 

### This is a *[[binary tree]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)


#### same as [[Maximum Depth of Binary Tree]] and [[Diameter of Binary Tree]], checking if subtree is balanced at each level



```python
	##### add code here

def isBalanced(self, root: Optional[TreeNode]) -> bool:
        flag = [True]
        def check_bal(root):
            if not root:
                return 0

            l = check_bal(root.left)
            r = check_bal(root.right)
            diff = abs(l-r)
            
            if diff > 1:
                flag[0] = False
            
            return 1 + max(l,r)
            
        check_bal(root)
        return flag[0]
```

___
Other related Links:
	neetcode video:
____
____
