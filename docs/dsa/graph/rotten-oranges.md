```python
def orangesRotting(self, grid: List[List[int]]) -> int:
    queue = []
    fresh = 0
    n = len(grid)
    m = len(grid[0])
    for i in range(n):
        for j in range(m):
            if grid[i][j] == 2:
                queue.append([i, j])
            if grid[i][j] == 1:
                fresh = fresh + 1
    minutes = 0
    while len(queue) > 0 and fresh != 0:
        size = len(queue)
        minutes = minutes + 1
        for i in range(size):
            x, y = queue.pop(0)
            for xx, yy in [(1, 0), (-1, 0), (0, 1), (0, -1)]:
                p, q = x + xx, y + yy
                if p >= 0 and p < n and q >= 0 and q < m and grid[p][q] == 1:
                    grid[p][q] = 2
                    queue.append([p, q])
                    fresh = fresh - 1
    if fresh != 0:
        return -1
    else:
        return minutes
```