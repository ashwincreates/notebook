Articulation point is the vertex which when removed increases the number of components in the graph

```python
def articulation_points(graph: Graph):
    time = 0
    is_ap = [False for _ in range(graph.nodes)] # if node u is a articulation point
    disc = [0 for _ in range(graph.nodes)] # discovery time / discovery order to reach node u
    low = [0 for _ in range(graph.nodes)] # lowest node through which you can reach u

    def dfs(u, p):
        nonlocal low, time, is_ap, disc
        children = 0
        time += 1
        low[u] = disc[u] = time
        for v in graph.adj[u]:
            if v == p:
                continue
            if disc[v] == 0:
                children += 1
                dfs(v, u)
                if disc[u] <= low[v]:
                    is_ap[u] = True
                low[u] = min(low[u], low[v])
            else:
                low[u] = min(low[u], disc[v])
        return children

    for node in range(graph.nodes):
        if disc[node] == 0:
            is_ap[node] = dfs(node, node) > 1
    
    print(is_ap)
```