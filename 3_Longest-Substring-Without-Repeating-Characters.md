# Longest Substring Without Repeating Characters

Given a string, find the length of the longest substring without repeating characters.

Examples:

Given "abcabcbb", the answer is "abc", which the length is 3.

Given "bbbbb", the answer is "b", with the length of 1.

Given "pwwkew", the answer is "wke", with the length of 3. Note that the answer must be a substring, "pwke" is a subsequence and not a substring.

> 这种解法叫做  sliding windows 滑动窗口


```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """  
        :type s: str
        :rtype: int
        """
        dict={}
        j=0
        max_length=0
        for i in xrange(len(s)):
            if s[i] in dict:
                j=max(j,dict[s[i]]+1)
            dict[s[i]]=i
            max_length=max(max_length,i-j+1)
    
        return max_length
```

我采取的错误解法如下：

```python
class Solution(object):
    def lengthOfLongestSubstring(self, s):
        """
        :type s: str
        :rtype: int
        """
        if s=='':
            return 0
        def lenthOfLSInRange(st,i,j):
            if i==j:
                return 1
            x=s[j]
            indexOfSameX=-1
            for h in range(j-1,i-1,-1):
                if s[h]==x:
                    indexOfSameX=h
                    break
            if indexOfSameX==-1:
                return 1+lenthOfLSInRange(st,i,j-1)
                
            else:
                return max(lenthOfLSInRange(st,i,h),lenthOfLSInRange(st,h+1,j))
        
        return lenthOfLSInRange(s,0,len(s)-1)
```

这种解法的错误是对于abcb来说我考虑的是ab和cb，得出的结果是2，但是abc的长度是3。
可见不是所有问题都适合二分法和动态规划，

说到动态规划是因为我之前想到可以用a[i]来表示到i为止的输入s中的longest substring，但是这一题应该没有最优子结构