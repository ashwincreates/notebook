###### Shortest Path in UG
```python
def shortestPath(self, edges, n, m, src):
    dist = [1e9] * n
    adj = [[] for i in range(n)]
    for edge in edges:
        adj[edge[0]].append(edge[1])
        adj[edge[1]].append(edge[0])
    dist[src] = 0
    visited = [False] * n
    visited[src] = True
    q = [src]
    while len(q) != 0:
        node = q.pop(0)
        for neighbour in adj[node]:
            if visited[neighbour]:
                continue
            dist[neighbour] = dist[node] + 1
            visited[neighbour] = True
            q.append(neighbour)
    return [d if d != 1e9 else -1 for d in dist]
```
