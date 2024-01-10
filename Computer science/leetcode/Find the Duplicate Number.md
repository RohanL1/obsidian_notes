____
Name: Find the Duplicate Number
Timestamp: 08-01-2024 03:59:22,
Related Tags:  #leetcode #code #cs #mid,
Summary: same as title,
Note:
____
# [Find the Duplicate Number](https://leetcode.com/problems/find-the-duplicate-number/)

##### Question 
Given an array of integers `nums` containing `n + 1` integers where each integer is in the range `[1, n]` inclusive.

There is only **one repeated number** in `nums`, return _this repeated number_.

You must solve the problem **without** modifying the array `nums` and uses only constant extra space.

#### Answer 

#### Using Linked List cycle concept

### This is a *[[liked list]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)

![[Screenshot 2024-01-08 034304.png]]
![[Screenshot 2024-01-08 035226.png]]

consider each array val as pointer to other element i.e. val is index of other element in array.

take two ptr fast and slow
find where they meet
after finding the intersection take another slow ptr and find out where these two slows meet

that should be the starting point of cycle, i.e. duplicate number
(proof is in above pic).


```python
	##### add code here
    def findDuplicate(self, nums: List[int]) -> int:
        slow, fast = 0,0

        while True:
            slow = nums[slow]
            fast = nums[nums[fast]]

            if slow == fast :
                break
        
        slow2 = 0

        while True:
            slow = nums[slow]
            slow2 = nums[slow2]
            if slow == slow2:
                break
            
        return slow

```


#### Using set

### This is a *[[liked list]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(n) 

**Uses extra space, hence 1st approach is preferred** 

init a set

for every element 
check if it exists in set if yes return that element as dup
otherwise add that in the set

```python

def findDuplicate(self, nums: List[int]) -> int:
	seen_set = set()
	for num in nums:
		if num in seen_set:
			return num
		else:
			seen_set.add(num)
	
```

___
Other related Links:
	neetcode video:
____
____
