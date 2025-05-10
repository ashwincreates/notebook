A graph is **bipartite** if the nodes can be partitioned into two independent sets `A` and `B` such that **every** edge in the graph connects a node in set `A` and a node in set `B`

```python
def isBipartite(graph):
    colors = [0] * len(graph)
    def helper(node, color):
        nonlocal colors
        if colors[node] != 0:
            return colors[node] == color
        colors[node] = color
        for neighbour in graph[node]:
            if not helper(neighbour, -color):
                return False
        return True
    for i in range(len(graph)):
        if colors[i] == 0 and not helper(i, 1):
            return False
    return True
```