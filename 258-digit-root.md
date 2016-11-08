# 258 digit root
>Given a non-negative integer num, repeatedly add all its digits until the result has only one digit.

For example:

>Given num = 38, the process is like: 3 + 8 = 11, 1 + 1 = 2. Since 2 has only one digit, return it.

```python
class Solution(object):
    def addDigits(self, num):
        """
        :type num: int
        :rtype: int
        """
        return num-(num-1)/9*9 if num!=0 else 0
```

可以参照[wiki](https://en.wikipedia.org/wiki/Digital_root)