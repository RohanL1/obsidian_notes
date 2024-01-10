____
Name: Merge Two Sorted Lists
Timestamp: 07-01-2024 04:29:40,
Related Tags:  #leetcode #code #cs #easy ,
Summary: same as title,
Note:
____
# [Merge Two Sorted Lists](https://leetcode.com/problems/merge-two-sorted-lists/)

##### Question 
You are given the heads of two sorted linked lists `list1` and `list2`.
Merge the two lists into one **sorted** list. The list should be made by splicing together the nodes of the first two lists.
Return _the head of the merged linked list_.


#### Answer 

### This is a *[[liked list]]* problem.

#### [[time complexity]] : O(n+m)
#### [[space complexity]]: O(n+m) ( to store the new linked list can be done in O(1) if we modify one of given linked lists)


#### approach heading

approach pic 

approach description 



```python
	##### add code here

def mergeTwoLists(self, list1: Optional[ListNode], list2: Optional[ListNode]) -> Optional[ListNode]:

        out_list = ListNode()
        out_itr = out_list

        while list1 and list2:
            if list1.val >= list2.val :
                out_itr.next = list2
                list2=list2.next

            else :
                out_itr.next = list1
                list1=list1.next

            out_itr = out_itr.next

        if list1 :
            out_itr.next = list1

        if list2 :
            out_itr.next = list2

        return out_list.next
```

#### recursive algorithm

```python
##### Recursive algo

        if not list1:

            return list2

        if not list2:

            return list1

        if list1.val < list2.val:

            list1.next = self.mergeTwoLists(list1.next, list2)

            return list1

        else:

            list2.next = self.mergeTwoLists(list1, list2.next)

            return list2

  

        def add_rem_ele(in_list, out_list):

            while in_list :

                out_list.next = ListNode(in_list.val, None)

                out_list = out_list.next

                in_list=in_list.next
```

___
Other related Links:
	neetcode video:
____
____
