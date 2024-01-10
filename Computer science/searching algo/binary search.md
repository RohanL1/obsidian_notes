____
Name: binary search
Timestamp: 06-01-2024 00:55:42,
Related Tags:  #leetcode #code #cs #searching,
Summary: same as title,
Note:
____
# Binary Search

![[Pasted image 20240106010601.png]]


#### [[time complexity]] : O(log n)
#### [[space complexity]]: O(1)


#### approach

2 approaches **recursive** and **iterative**
take left and right pointers ( init : 0, len - 1 )

**breaking condition left <= right**

calculate mid from left and right 
target is equal to mid return mid index
if target is **greater** than the mid then **search RIGHT** (mid to right) i.e. change left pointer to mid + 1
**else  search LEFT** (mid to right) i.e. change right pointer to mid - 1


NOTE : 
mid =( l + r) // 2 -> for small arrays 
mid = ( l + (r-l) ) // 2 -> for large array sizes, in this case mid might overflow if indices are too large.

#### recursive method

```python
	##### add code here
	def search(self, nums: List[int], target: int) -> int:

        #recursive method
        def bi_search (nums , low , high ):
            if low > high : return -1
            
            mid = ( low + high ) // 2
            
            if (nums[mid] == target):
                return mid
            elif (nums[mid] > target):
                return bi_search(nums, low, mid-1 )
            else :
                return bi_search(nums, mid +1 , high )

        return bi_search(nums, 0 , 6)

```

#### iterative method

```python
	##### add code here
	def search(self, nums: List[int], target: int) -> int:
        ln=len(nums)
        low , high = 0, ln-1

        while low < high :
            mid = ( high + low ) // 2
            if nums[mid] == target :
                return mid
            elif nums[mid] > target :
                high = mid - 1
            else :
                low  = mid + 1
          
        return -1

```
___
Other related Links:
	neetcode video: [https://youtu.be/s4DPM8ct1pI](https://youtu.be/s4DPM8ct1pI)
____
____
