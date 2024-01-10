
____
Name: median of 2 sorted arrays
Timestamp: 07-01-2024 03:22:15,
Related Tags:  #leetcode #code #cs #hard,
Summary: same as title,
Note:
____
# [Median of Two Sorted Arrays](https://leetcode.com/problems/median-of-two-sorted-arrays/)

##### Question 
Given two sorted arrays `nums1` and `nums2` of size `m` and `n` respectively, return **the median** of the two sorted arrays.

The overall run time complexity should be `O(log (m+n))`.


#### Answer 

### This is a *[[Binary Search]]* problem.

#### [[time complexity]] : O(log (n+m))
#### [[space complexity]]: O(1)


#### finding correct left part with binary search ( use smaller size array )

![[Pasted image 20240107032220.png]]

we have to find the correct left part for smaller array that fits within half size like above pic.

1. we take smaller (A) array for binary search, init left, right  half accordingly
2. Breaking condition : **TRUE** 
3. calculate the indx of last ele for A (using left and right ptr) , and B (using half and just calculated indx from A)
4. get last element of left part (Aleft), first element of right part (Aright) for A and last element of left part (Bleft), first element of right part (Aright) for B, if any of these over/under flows assign +/- infinity for the same
5. check if correct partition is done for both array i.e. Aleft <= Bright and Bleft <= Aright( as above pic.) and return the result 
6. if not then change the pointers




```python
	##### add code here
def findMedianSortedArrays(self, nums1: List[int], nums2: List[int]) -> float:
        A,B = nums1, nums2
        lenA, lenB = len(A), len(B)
        total = lenA + lenB
        half = total // 2

        if lenA > lenB :
            A,B = B,A
            lenA, lenB = lenB, lenA
        
        left,right = 0, lenA - 1 

        while True:

            m = ( left + right ) // 2 # index of last ele of left part for A
            k = half - m - 2         # index of last ele of left part for B

            Aleft  = A[m]    if m >= 0       else float('-inf')
            Aright = A[m+1]  if m + 1 < lenA else float('inf')

            Bleft  = B[k]    if k >= 0       else float('-inf')
            Bright = B[k+1]  if k + 1 < lenB else float('inf')

            # correct left part for both array
            if Aleft <= Bright and Bleft <= Aright:
                #ODD
                if total % 2 :
                    return min(Aright, Bright)
                
                #EVEN
                else :
                    return (max(Aleft, Bleft) +  min(Aright, Bright)) / 2 
            
            # NOT correct parts do binary search on A
            elif Aleft > Bright:
                right = m - 1
            else:
                left = m + 1

```

___
Other related Links:
	neetcode video: [https://youtu.be/q6IEA26hvXc](https://youtu.be/q6IEA26hvXc)
____
____
