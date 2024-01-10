____
Name: Remove Nth Node From End of List
Timestamp: 08-01-2024 02:03:29,
Related Tags:  #leetcode #code #cs #mid,
Summary: same as title,
Note:
____
# [Remove Nth Node From End of List](https://leetcode.com/problems/remove-nth-node-from-end-of-list/)

##### Question 
Given the `head` of a linked list, remove the `nth` node from the end of the list and return its head.


#### Answer 

### This is a *[[liked list]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)


#### approach heading

![[Pasted image 20240108020747.png]]

add dummy node in front of LL (in case we are removing the head)
init left right (dummy and head)
**move right by N positions**
take left to prev of right (by simultaneously itr both left and right till right reaches the end )
remove the next of left and return the **dummy next** (in case we remove head)



```python
	##### add code here
def removeNthFromEnd(self, head: Optional[ListNode], n: int) -> Optional[ListNode]:
        dummy = ListNode(0, head)
        left, right = dummy, head

        # find the nth element
        while n and right:
            right = right.next
            n -= 1
        
        # get left ptr to prev node of nth
        while right:
            right = right.next
            left = left.next
        
        # remove nth node
        left.next = left.next.next

        #return dummy next (NOT head directly as it might get removed in earlier step)
        return dummy.next

```

___
Other related Links:
	neetcode video:
____
____
