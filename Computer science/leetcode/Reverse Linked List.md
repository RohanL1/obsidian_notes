____
Name: Reverse Linked List
Timestamp: 07-01-2024 04:21:52,
Related Tags:  #leetcode #code #cs #easy,
Summary: same as title,
Note:
____
# [Reverse Linked List](https://leetcode.com/problems/reverse-linked-list/)

##### Question 
Given the `head` of a singly linked list, reverse the list, and return _the reversed list_.


#### Answer 

### This is a *[[liked list]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)


#### linked list traversal while updating the next nodes 

![[Pasted image 20240107042621.png]] 

init current and previous ptrs
traverse the linked list while changing the current next to previous



```python
	##### add code here

def reverseList(self, head: Optional[ListNode]) -> Optional[ListNode]:
        prev,curr=None,head
        
        while curr :
            tmp = curr.next
            curr.next = prev
            prev = curr
            curr = tmp

        return prev
```

___
Other related Links:
	neetcode video:
____
____
