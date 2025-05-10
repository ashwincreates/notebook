```python
def findTheCity(self, n: int, edges: List[List[int]], distanceThreshold: int):
    dist = [[math.inf for i in range(n)] for j in range(n)]
    for i in range(n):
        dist[i][i] = 0
    for u, v, w in edges:
        dist[u][v] = dist[v][u] = w
    for k in range(n):
        for i in range(n):
            for j in range(n):
                dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j])
    minReachableCities = float('inf')
    bestCity = -1
    for i in range(n):
        reachableCities = 0
        for j in range(n):
            if dist[i][j] <= distanceThreshold:
                reachableCities += 1
        if reachableCities <= minReachableCities:
            minReachableCities = reachableCities
            bestCity = i
    return bestCity
```