```python
 def swimInWater(self, grid: List[List[int]]) -> int:
        n = len(grid)
        start = (0, 0)
        end = (n - 1, n - 1)
        t = 0
        heap = [[grid[0][0], (0, 0)]]
        visited = [[False for i in range(n)] for i in range(n)]
        maxTime = 0
        while True:
            time, cell = heappop(heap)
            print(time, grid[cell[0]][cell[1]], cell)
            maxTime = max(time, maxTime)
            if cell == end:
                return maxTime
            i, j = cell
            visited[i][j] = True
            for p, q in [(1, 0), (0, 1), (-1, 0), (0, -1)]:
                x = p + i
                y = q + j
                if x >= 0 and x < n and y >= 0 and y < n and not visited[x][y]:
                    f = grid[i][j]
                    t = grid[x][y]
                    heappush(heap, [t, (x, y)])
```