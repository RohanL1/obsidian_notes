____
Name: Subtree of Another Tree
Timestamp: 09-01-2024 18:01:50,
Related Tags:  #leetcode #code #cs #easy ,
Summary: same as title,
Note:
____
# [Subtree of Another Tree](https://leetcode.com/problems/subtree-of-another-tree/)

##### Question 
Given the roots of two binary trees `root` and `subRoot`, return `true` if there is a subtree of `root` with the same structure and node values of `subRoot` and `false` otherwise.

A subtree of a binary tree `tree` is a tree that consists of a node in `tree` and all of this node's descendants. The tree `tree` could also be considered as a subtree of itself.


#### Answer 

### This is a *[[binary tree]]* problem.

#### [[time complexity]] : O(n * m)
#### [[space complexity]]: O(1)


#### DFS and count of children nodes

define is equal function to compare the trees same as [[Same Tree]] problem.
define count elements function to count the no. of children of each node

get total no of elements in subRoot tree 
do dfs and check if the count is same for current node and Subtree
if count is same then perform the is equal check and return True if they are equal 

if we dont find any sub tree till end return False


```python
	##### add code here

def isSubtree(self, root: Optional[TreeNode], subRoot: Optional[TreeNode]) -> bool:
        if not root and not subRoot:
            return True
        
        def is_equal(p,q):
            if not p and not q:
                return True
            
            if not p or not q or p.val != q.val:
                return False
            
            return is_equal(p.left, q.left) and is_equal(p.right, q.right)
        
        def count_elements(root):
            if not root:
                return 0
            cnt = 1 + count_elements(root.left) + count_elements(root.right)
            root.count = cnt
            return cnt
            
        count_elements(root)
        sub_cnt = count_elements(subRoot)
        q = [ root ]

        while q:
            node = q.pop(0)
            if sub_cnt == node.count  and is_equal(node, subRoot):
                return True
            if node.left:
                q.append(node.left) 
            if node.right:
                q.append(node.right)
        
        return False

        is_sub(root, subRoot)
```

___
Other related Links:
	neetcode video:
____
____
