Here, we need to find all the ones, from which we cannot step outside the grid when travelling 4-directionally

So, first we find all the 1's that are at the edge of the grid, and then do BFS from them, reducing the total count of 1's
```python
def numEnclaves(grid: List[List[int]]):
    queue = []
    rs = len(grid)
    cs = len(grid[0])
    total = 0
    for i in range(rs):
        for j in range(cs):
            total += grid[i][j]
            if (i == 0 or i == rs - 1 or j == 0 or j == cs - 1) and grid[i][j] == 1:
                total -= 1
                grid[i][j] = 0
                queue.append([i, j])
    while len(queue) > 0:
        i, j = queue.pop(0)
        for xx, yy in [(1, 0), (0, 1), (-1, 0), (0, -1)]:
            p = i + xx
            q = j + yy
            if p >= 0 and p < rs and q >= 0 and q < cs and grid[p][q] == 1:
                grid[p][q] = 0
                total -= 1
                queue.append([p, q])
    return total
```