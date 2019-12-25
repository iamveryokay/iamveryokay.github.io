Title: leetcode-cn做题笔记
Date: 2019-10-15
Category: Misc
Modified: 2019-10-15 22:32
Tags: Program, Algorithm

# 砖墙
## 超时版本
```python
class Solution:
    def leastBricks(self, wall: List[List[int]]) -> int:
        total_num = sum(wall[0])
        total_min = len(wall)
        candidate_set = set()
        for i in wall:
            for j in range(len(i)):
                tmp_sum = sum(i[:j])
                if not tmp_sum in candidate_set:
                    candidate_set.add(tmp_sum)
        candidate_set.remove(0)
        for i in candidate_set:
            tmp_min = len(wall)
            for j in wall:
                for k in range(len(j)):
                    if i == sum(j[:k]):
                        tmp_min -= 1
                        break
            if tmp_min < total_min:
                total_min = tmp_min
        return total_min
                
```

## AC版本
```python
class Solution:
    def leastBricks(self, wall: List[List[int]]) -> int:
        num_dict = dict()
        num_max = len(wall)
        for i in wall:
            tmp_num = 0
            for j in i:
                tmp_num += j
                if not tmp_num in num_dict:
                    num_dict[tmp_num] = 1
                else:
                    num_dict[tmp_num] += 1
        num_dict.pop(max(num_dict.keys()))
        if len(num_dict) == 0:
            return num_max
        else:
            return num_max - max(num_dict.values())
```
 
# 反转整数
```python
def reverse(x: int) -> int:
    if x < 0:
        sign = -1
    else:
        sign = 1
    x_str = str(x * sign)
    x_reverse = x_str[::-1]
    ans = sign * int(x_reverse)
    if not -2 ** 31 <= ans <= 2 ** 31 - 1:
        return 0
    return ans
```