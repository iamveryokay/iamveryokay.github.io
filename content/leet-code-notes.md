Title: Leetcode 笔记
Date: 2019-04-21
Category: Python
Tags: Python, Leetcode

# Two Sums
## My Version
用的是两个for循环的搜索，搜到了就返回下标，比较无脑。。
```python
class Solution:
    def twoSum(self, nums: List[int], target: int) -> List[int]:
        for i in range(len(nums)-1):
            for j in range(i+1, len(nums)):
                if nums[i] + nums[j] == target:
                    return [i, j]
```
## Good practice
主要思想是用到了字典，字典的key是要配对的值，value是索引，然后只要一遍循环就可以了。
```python
def twoSum(self, num, target):
    d = {}
    for i in range(len(num)):
        if num[i] in d.keys():
            return (d[num[i]]+1, i+1)
        else:
            d[target - num[i]] = i
```