# 1.add two sums

> You are given two linked lists representing two non-negative numbers. The digits are stored in reverse order and each of their nodes contain a single digit. Add the two numbers and return it as a linked list.

>Input: (2 -> 4 -> 3) + (5 -> 6 -> 4)

>Output: 7 -> 0 -> 8


---
> answers:

```python
# Definition for singly-linked list.
# class ListNode(object):
#     def __init__(self, x):
#         self.val = x
#         self.next = None

class Solution(object):
    def addTwoNumbers(self, l1, l2):
        """
        :type l1: ListNode
        :type l2: ListNode
        :rtype: ListNode
        """
        carry = 0
        root = n = ListNode(0)
        while l1 or l2 or carry:
            v1 = v2 = 0
            if l1:
                v1 = l1.val
                l1 = l1.next
            if l2:
                v2 = l2.val
                l2 = l2.next
            carry, val = divmod(v1+v2+carry, 10)
            n.next = ListNode(val)
            n = n.next
        return root.next
```

我在做这道题的时候，每次是讲l2的值加到l1上来，并返回l1，这样做有一个不好的地方在于需要对边界情况写很多代码，比如l1比l2先结束，或者l1比l2后结束，以及同时结束的时候还有进位，或者l1结束后l2为9->9->9...且此时进位为1.

使用上面的解法，我们新起一个根节点，每次利用l1,l2和carry，计算其和并且生成一个新节点添加到上一个节点之后，这样不管l1,l2,carry的边界情况如何，我们同样处理即可。

我们都首先假设l1、l2的节点值为0，如果l1、l2不为none，再将其更新到真实值，这样就可以用同样的加法对l1、l2、carry进行相加。

