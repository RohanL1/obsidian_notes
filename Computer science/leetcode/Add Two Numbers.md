____
Name: Add Two Numbers
Timestamp: 08-01-2024 03:10:31,
Related Tags:  #leetcode #code #cs #mid,
Summary: same as title,
Note:
____
# [Add Two Numbers](https://leetcode.com/problems/add-two-numbers/)

##### Question 

You are given two **non-empty** linked lists representing two non-negative integers. The digits are stored in **reverse order**, and each of their nodes contains a single digit. Add the two numbers and return the sum as a linked list.

You may assume the two numbers do not contain any leading zero, except the number 0 itself.

#### Answer 

### This is a *[[liked list]]* problem.

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)


#### itr through both LLs, while maintaining Carry


```python
	##### add code here
def addTwoNumbers(self, l1: Optional[ListNode], l2: Optional[ListNode]) -> Optional[ListNode]:
        dummy = ListNode(0)
        res = dummy
        carry = 0

        while l1 or l2 or carry:
            d1 = l1.val if l1 else 0
            d2 = l2.val if l2 else 0

            curr_sum = d1 + d2 + carry
            res.next = ListNode(curr_sum % 10)
            carry = curr_sum // 10

            res = res.next
            l1 = l1.next if l1 else None
            l2 = l2.next if l2 else None
        
        return dummy.next

```

___
Other related Links:
	neetcode video:
____
____
