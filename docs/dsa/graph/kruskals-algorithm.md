**Kruskal's algorithm** finds a minimum spanning forest of an undirected edge-weighted graph ("Weighted graph"). If the graph is ==connected==, it finds a minimum spanning tree. It is a greedy algorithm that in each step adds to the forest the lowest-weight edge that will not form a cycle "Cycle (graph theory)". The key steps of the algorithm are sorting to detect cycles. Its running time is dominated by the time to sort all of the graph edges by their weight.

```python
def spanningTree(self, V, adj):
    parent = [i for i in range(V)]
    edges = []
    for u in range(V):
        for v, w in adj[u]:
            edges.append((u, v, w))
    minsum = 0
    
    def find(v, parent):
        if parent[v] == v:
            return v
        p = find(parent[v], parent)
        parent[v] = p
        return p
    
    def union(u, v, w, parent):
        nonlocal minsum
        pu = find(u, parent)
        pv = find(v, parent)
        if pu == pv:
            return
        else:
            parent[pu] = pv
            minsum += w
    edges = sorted(edges, key=lambda x: x[2])
    for u, v, w in edges:
        union(u, v, w, parent)
    return minsum
```