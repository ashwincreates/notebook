The recurrence is 
$$𝑑𝑖𝑠𝑡(𝑖,𝑗,𝑘)=𝑚𝑖𝑛(𝑑𝑖𝑠𝑡(𝑖,𝑗,𝑘−1), 𝑑𝑖𝑠𝑡(𝑖,𝑘,𝑘−1)+𝑑𝑖𝑠𝑡(𝑘,𝑗,𝑘−1))$$
with the base case 𝑑𝑖𝑠𝑡(𝑖,𝑗,0)=𝑤(𝑖,𝑗). There is only one way we can achieve this iteratively, by calculating all cases of 𝑘−1 before calculating cases of 𝑘.

```python
def floydWarshall(self, n: int, edges: List[List[int]], distanceThreshold: int):
    dist = [[math.inf for i in range(n)] for j in range(n)]
    for i in range(n):
        dist[i][i] = 0
    for u, v, w in edges:
        dist[u][v] = dist[v][u] = w
    for k in range(n):
        for i in range(n):
            for j in range(n):
                dist[i][j] = min(dist[i][j], dist[i][k] + dist[k][j])
```