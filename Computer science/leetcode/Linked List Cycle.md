____
Name: Linked List Cycle
Timestamp: 08-01-2024 03:17:13,
Related Tags:  #leetcode #code #cs #easy ,
Summary: same as title,
Note:
____
# [Linked List Cycle](https://leetcode.com/problems/linked-list-cycle/)

##### Question 

Given `head`, the head of a linked list, determine if the linked list has a cycle in it.

There is a cycle in a linked list if there is some node in the list that can be reached again by continuously following the `next` pointer. Internally, `pos` is used to denote the index of the node that tail's `next` pointer is connected to. **Note that `pos` is not passed as a parameter**.

Return `true` _if there is a cycle in the linked list_. Otherwise, return `false`.

#### Answer 

### This is a *[[liked list]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)


#### approach heading

init slow and fast pointers

slow moves 1 element per loop
fast moves 2

if they meet i.e. fast == slow
then there is a loop in LL, return True

if while exits without returning then there is no loop
return false



```python
	##### add code here
def hasCycle(self, head: Optional[ListNode]) -> bool:
        if head == None : 
	        return False
	    
        fast, slow = head, head

        while fast and fast.next:
            slow = slow.next
            fast = fast.next.next
            
            if fast == slow :
                return True
	    return False

```

___
Other related Links:
	neetcode video:
____
____
