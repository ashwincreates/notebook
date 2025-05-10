```python
def shortestPathBinaryMatrix(self, grid: List[List[int]]) -> int:
    n = len(grid)
    if grid[0][0] == 1 or grid[n - 1][n - 1] == 1:
        return -1
    start = (0, 0)
    end = (n - 1, n - 1)

    distance = [[0 for i in range(n)] for i in range(n)]
    distance[0][0] = 1



    grid[0][0] = 2

    queue = [start]



    while len(queue) > 0:

        x, y = queue.pop(0)

        for i, j in [(1, 1), (-1, -1), (1, -1), (-1, 1), (0, 1), (0, -1), (1, 0), (-1, 0)]:

            p = x + i

            q = y + j

            if p >= 0 and p < n and q >= 0 and q < n and grid[p][q] == 0:

                queue.append((p, q))

                grid[p][q] = 2

                distance[p][q] = distance[x][y] + 1

    if distance[n - 1][n - 1] == 0:

        return -1

    else:

        return distance[n - 1][n - 1]
```