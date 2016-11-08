# Intersection of Two Linked Lists

> Write a program to find the node at which the intersection of two singly linked lists begins.


For example, the following two linked lists:

```
A:          a1 → a2
                   ↘
                     c1 → c2 → c3
                   ↗            
B:     b1 → b2 → b3
```

begin to intersect at node c1.


Notes:

- If the two linked lists have no intersection at all, return null.
- The linked lists must retain their original structure after the function returns.
- You may assume there are no cycles anywhere in the entire linked structure.
- Your code should preferably run in O(n) time and use only O(1) memory.


```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def getIntersectionNode(self, headA, headB):
        """
        :type head1, head1: ListNode
        :rtype: ListNode
        """
        lenA=0
        lenB=0
        p=headA
        while p!=None:
            lenA+=1
            p=p.next
        
        p=headB
        while p!=None:
            lenB+=1
            p=p.next
        pA=headA
        pB=headB
        if lenA>lenB:
            for i in xrange(lenA-lenB):
                pA=pA.next
        if lenB>lenA:
            for i in xrange(lenB-lenA):
                pB=pB.next
        
        while pA!=None:
            if pA==pB:
                break
            pA=pA.next
            pB=pB.next
        
        return pA
```


> 这道题目因为是链表，而链表只有一个next指针，只要有重合的节点，那么此节点之后的节点一定重合