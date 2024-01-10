____
Name: Find Minimum in Rotated Sorted Array
Timestamp: 06-01-2024 00:22:02,
Related Tags:  #leetcode #code #cs #mid,
Summary: same as title,
Note:
____
# [Find Minimum in Rotated Sorted Array](https://leetcode.com/problems/find-minimum-in-rotated-sorted-array/)

##### Question 
Suppose an array of length `n` sorted in ascending order is **rotated** between `1` and `n` times. For example, the array `nums = [0,1,2,4,5,6,7]` might become:

- `[4,5,6,7,0,1,2]` if it was rotated `4` times.

Given the sorted rotated array `nums` of **unique** elements, return _the minimum element of this array_.

#### Answer 

### This is a [[binary search]] problem.
### 2 approaches 

for both 
#### [[time complexity]] : O(log n)
#### [[space complexity]]: O(1)


#### 1 find the Piot and return

![[Pasted image 20240106011354.png]]

check if array is not rotated, i.e. num rotation == len, then return first element of the array

do binary search and check for the mid for which next element is less than the mid i.e. Piot of the rotation, return the Piot

if while ended before we got the Piot, return the min of current start and end elements

```python
    def findMin(self, nums: List[int]) -> int:
        start = 0
        end = len(nums) - 1
        
        # array is rotated n times where n % len(nums) == 0
        if nums[end] > nums[start]:
            return nums[0]

        while start + 1 < end:
            mid = (start + end) // 2
            
            if nums[mid + 1] < nums[mid]:
                return nums[mid + 1]
            elif nums[mid] > nums[start]:
                start = mid
            else:
                end = mid

        return min(nums[start], nums[end])

```



#### 2 maintain min, search right or left

![[Pasted image 20240106005421.png]]
maintain a min variable for current min, 

checks if we entered the sorted section of the array ( nums[l] < nums[r] ) and return left element 
if not depending on the mid and left element (nums[left] <= nums[mid]), decide which section to search next i.e. LEFT SECTION or RIGHT SECTION

if not return from first condition then return the min var



```python
    def findMin(self, nums: List[int]) -> int:
        l,r = 0, len(nums) - 1
        res = nums[0]

        if nums[l] < nums[r]:
            return nums[l]

        while l <= r :
            if nums[l] < nums[r]:
                res = min(res, nums[l])
                break

            mid = l + ((r - l) // 2 )
            res = min(res, nums[mid])
            
            if nums[l] <= nums[mid]:
                l = mid + 1

            else :
                r = mid - 1

        return res
```

___
Other related Links:
neetcode video: [https://youtu.be/nIVW4P8b1VA](https://youtu.be/nIVW4P8b1VA "Share link")
____
____
