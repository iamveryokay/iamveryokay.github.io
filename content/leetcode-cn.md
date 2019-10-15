Title: leetcode-cn做题笔记
Date: 2019-10-15
Category: Misc
Modified: 2019-10-15 22:32
Tags: Program, Algorithm

# 砖墙
### 超时版本
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
