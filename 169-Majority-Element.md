# 169. Majority Element
>Given an array of size n, find the majority element. The majority element is the element that appears more than ⌊ n/2 ⌋ times.

>You may assume that the array is non-empty and the majority element always exist in the array.

---

```python
class Solution(object):
    def majorityElement(self, nums):
        """
        :type nums: List[int]
        :rtype: int
        """
        ### Boyer-Moore majority algorithms
        
        count=0
        
        for num in nums:
            if count==0:
                candidate=num
            
            if candidate==num:
                count+=1
            else:
                count-=1
        
        return candidate
```

这个算法叫做Boyer-Moore Majority algorithm，找出存在超过半数的数据

