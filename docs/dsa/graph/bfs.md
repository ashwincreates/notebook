Breadth first search in a graph traverses from starting node to each of the neighbors and then next neighbors
```python
def bfsOfGraph(V, adj):
    visited = [False] * V
    queue = [0]
    ans = []
    while len(queue) > 0:
        node = queue.pop(0)
        if visited[node]:
            continue
        visited[node] = True
        for neighbour in adj[node]:
            queue.append(neighbour)
        ans.append(node)
    return ans
```