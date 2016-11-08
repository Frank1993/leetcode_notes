# 141. Linked List Cycle

>Given a linked list, determine if it has a cycle in it.

>Follow up:
Can you solve it without using extra space?


```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def hasCycle(self, head):
        """
        :type head: ListNode
        :rtype: bool
        """
        if head==None:
            return False
        fast=head
        low=head
        
        while fast!=None and fast.next!=None:
            fast=fast.next.next
            low=low.next
            if fast==low:
                return True
            
        return False
```

这种快慢指针的思想好好体会。