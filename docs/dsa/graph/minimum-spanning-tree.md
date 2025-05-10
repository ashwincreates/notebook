> [!note]  Among all possible spanning trees of a graph, the minimum spanning tree is the one for which the sum of all the edge weights is the minimum

Choose the smallest edge to find the MST (Prim's Algorithm)
```python
def spanningTree(self, V, adj):
    heap = [(0, 0)]
    mstSum = 0
    visited = [False] * V
    while heap:
        wt, node = heapq.heappop(heap)
        if visited[node]: continue
        mstSum = mstSum + wt
        visited[node] = True
        for neigh, w in adj[node]:
            heapq.heappush(heap, (w, neigh))
    return mstSum
```