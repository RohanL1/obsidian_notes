____
Name: Copy List with Random Pointer
Timestamp: 08-01-2024 02:24:36,
Related Tags:  #leetcode #code #cs #mid,
Summary: same as title,
Note:
____
# [Copy List with Random Pointer](https://leetcode.com/problems/copy-list-with-random-pointer/)

##### Question 
A linked list of length `n` is given such that each node contains an additional random pointer, which could point to any node in the list, or `null`.

Construct a [**deep copy**](https://en.wikipedia.org/wiki/Object_copying#Deep_copy) of the list. The deep copy should consist of exactly `n` **brand new** nodes, where each new node has its value set to the value of its corresponding original node. Both the `next` and `random` pointer of the new nodes should point to new nodes in the copied list such that the pointers in the original list and copied list represent the same list state. **None of the pointers in the new list should point to nodes in the original list**.

For example, if there are two nodes `X` and `Y` in the original list, where `X.random --> Y`, then for the corresponding two nodes `x` and `y` in the copied list, `x.random --> y`.

Return _the head of the copied linked list_.

The linked list is represented in the input/output as a list of `n` nodes. Each node is represented as a pair of `[val, random_index]` where:

- `val`: an integer representing `Node.val`
- `random_index`: the index of the node (range from `0` to `n-1`) that the `random` pointer points to, or `null` if it does not point to any node.

Your code will **only** be given the `head` of the original linked list.

![[Pasted image 20240108025027.png]]
#### Answer 

### This is a *[[liked list]]* problem.

#### 1. Using HashMap

#### [[time complexity]] : O(n)                      [O(2n) -> O(n)]
#### [[space complexity]]: O(n)

so 2 itr as follows 
create the new nodes without the next and random and store it in dict
add next and random from dict 


```python
	##### add code here
def copyRandomList(self, head: 'Optional[Node]') -> 'Optional[Node]':
        old_new_map = {}
        curr = head
	    #create the new nodes without the next and random and store it in dict
        while curr:
            old_new_map[curr] = Node(curr.val)
            curr = curr.next

        curr = head
		#add next and random from dict 
        while curr:
            old_new_map[curr].next = old_new_map.get(curr.next)
            old_new_map[curr].random = old_new_map.get(curr.random)
            curr = curr.next

        return old_new_map[head]

```

#### 2. Interweaving Nodes

#### [[time complexity]] : O(n)
#### [[space complexity]]: O(1)

![[Pasted image 20240108023513.png]]
**approach description** 
create new nodes in-between existing nodes
assign correct random nodes to new nodes (**curr.next.random = curr.random.next**)
separate old and new LL

**IMP** as last new does not have next node but old one does.
curr_new.next = curr_new.next.next if curr_new.next else None 

```python
	##### add code here

def copyRandomList(self, head: 'Optional[Node]') -> 'Optional[Node]':
        if not head:
            return None

		# create new nodes in-between existing nodes
        curr = head
        while curr:
            new_node = Node(curr.val, curr.next)
            curr.next = new_node
            curr = new_node.next
		#assign correct random nodes to new nodes
        curr = head
        while curr:
            if curr.random:
                curr.next.random = curr.random.next
            curr = curr.next.next
        
        old_head = head 
        new_head = head.next
        curr_old = old_head
        curr_new = new_head
		#separate old and new LL
        while curr_old:
            curr_old.next = curr_old.next.next
            curr_new.next = curr_new.next.next if curr_new.next else None #IMP as last new does not have next node but old one does.
            curr_old = curr_old.next
            curr_new = curr_new.next

        return new_head
```

___
Other related Links:
	neetcode video:
____
____
