Depth first search in a graph traverses the graph in depth first fashion i.e. traversing a single child and it's child node and so on, until there is no child node
```python
def dfsOfGraph(V, adj):
    visited = [False] * V
    ans = []
    def helper(node, adj):
        nonlocal visited, ans
        if visited[node]:
            return
        visited[node] = True
        ans.append(node)
        for neighbour in adj[node]:
            helper(neighbour, adj)
    helper(0, adj)
    return ans
```