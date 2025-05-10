##### Solution without minHeap
```python
def minimumEffortPath(self, heights: List[List[int]]) -> int:

        n = len(heights)

        m = len(heights[0])

        start = (0, 0)

        end = (n - 1, m - 1)

  

        min_effort = [[0 for i in range(m)] for i in range(n)]

        min_effort[0][0] = 0

  

        visited = [[False for i in range(m)] for i in range(n)]

        dist = [[1e9 for _ in range(m)] for i in range(n)]

        dist[0][0] = 0

  

        for _ in range(n * m):

            min_dist = 1e9

            min_node = (0, 0)

  

            for x in range(n):

                for y in range(m):

                    if not visited[x][y] and dist[x][y] < min_dist:

                        min_dist = dist[x][y]

                        min_node = (x, y)

  

            x, y = min_node

            visited[x][y] = True

  

            if min_node == end:

                return dist[n - 1][m - 1]

  

            for i, j in [(0, 1), (0, -1), (1, 0), (-1, 0)]:

                p = x + i

                q = y + j

                if p >= 0 and p < n and q >= 0 and q < m:

                    dist[p][q] = min(max(abs(heights[p][q] - heights[x][y]), dist[x][y]), dist[p][q])

        return dist[n - 1][m - 1]
```

##### Solution with minHeap
```python
def minimumEffortPath(self, heights):
        m, n = len(heights), len(heights[0])
        dist = [[math.inf] * n for _ in range(m)]
        dist[0][0] = 0
        minHeap = [(0, 0, 0)] # distance, row, col
        DIR = [0, 1, 0, -1, 0]

        while minHeap:
            d, r, c = heappop(minHeap)
            if d > dist[r][c]: continue  # this is an outdated version -> skip it
            if r == m - 1 and c == n - 1:
                return d  # Reach to bottom right
            
            for i in range(4):
                nr, nc = r + DIR[i], c + DIR[i+1]
                if 0 <= nr < m and 0 <= nc < n:
                    newDist = max(d, abs(heights[nr][nc] - heights[r][c]))
                    if dist[nr][nc] > newDist:
                        dist[nr][nc] = newDist
                        heappush(minHeap, (dist[nr][nc], nr, nc))
```