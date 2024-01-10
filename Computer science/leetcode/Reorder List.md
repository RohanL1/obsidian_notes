____
Name: Reorder List
Timestamp: 08-01-2024 01:50:14,
Related Tags:  #leetcode #code #cs #mid,
Summary: same as title,
Note:
____
# [Reorder List](https://leetcode.com/problems/reorder-list/)

##### Question 
You are given the head of a singly linked-list. The list can be represented as:

L0 → L1 → … → Ln - 1 → Ln

_Reorder the list to be on the following form:_

L0 → Ln → L1 → Ln - 1 → L2 → Ln - 2 → …

You may not modify the values in the list's nodes. Only nodes themselves may be changed.


#### Answer 

### This is a *[[liked list]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)


#### mid, reverse and reorder

![[Screenshot 2024-01-08 015249.png]]

find the mid point  
reverse the list from mid  
use these two to change links



```python
	##### add code here
def reorderList(self, head: Optional[ListNode]) -> None:
        """
        Do not return anything, modify head in-place instead.
        """
        
        #find the middle point for LL
        slow,fast = head, head.next

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            
        second = slow.next
        slow.next = None
        prev = None
      
      # reverse second list
        while second:
            tmp = second.next
            second.next = prev
            prev = second
            second = tmp
        
        
        second = prev
        first = head

		#reorder the lists
        while second:
            tmp1, tmp2 = first.next, second.next
            first.next = second
            second.next = tmp1
            first, second = tmp1, tmp2

```

___
Other related Links:
	neetcode video:[https://youtu.be/S5bfdUTrKLM](https://youtu.be/S5bfdUTrKLM)
____
____
