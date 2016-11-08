# delete node in a linked list

>Write a function to delete a node (except the tail) in a singly linked list, given only access to that node.

>Supposed the linked list is 1 -> 2 -> 3 -> 4 and you are given the third node with value 3, the linked list should become 1 -> 2 -> 4 after calling your function.

---

```python
class Solution(object):
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        node.val,node.next=node.next.val,node.next.next
```

体会一下链表的删除操作应该在常数时间内

我之前的方案如下，明显不实用：


```python
class Solution(object):
    def deleteNode(self, node):
        """
        :type node: ListNode
        :rtype: void Do not return anything, modify node in-place instead.
        """
        while node.next.next!=None:
            node.val=node.next.val
            node=node.next
        node.val=node.next.val
        node.next=None
```