

### 题目描述

有一个mxn的正方形矩阵，求从左上角到右下角的最短路径。
上下左右四个方向均可走，其中1不能走，0可走

0000
0100
1011
0011

### 思路解析

```python
def main(nums):
    col, row = len(nums[0]), len(nums)
    queue = [(nums[0], 0, 0)]
    levelNum = 0
    res = float('inf')
    while queue:
        length = len(queue)
        levelNum += 1
        for i in range(length):
            cur = queue.pop(0)

            if cur[1] == row - 1 and cur[2] == col - 1:
                res = min(res, levelNum)

            if nums[cur[1] + 1, cur[2]] == 0:
                queue.append((nums[cur[1] + 1, cur[2]], cur[1] + 1, cur[2]))
            if nums[cur[1] - 1, cur[2]] == 0:
                queue.append((nums[cur[1] - 1, cur[2]], cur[1] - 1, cur[2]))
            if nums[cur[1], cur[2] + 1] == 0:
                queue.append((nums[cur[1], cur[2] + 1], cur[1], cur[2] + 1))
            if nums[cur[1], cur[2] - 1] == 0:
                queue.append((nums[cur[1], cur[2] - 1], cur[1], cur[2] - 1))
    return res
```

