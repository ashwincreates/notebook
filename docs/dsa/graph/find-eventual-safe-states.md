```python
def eventualSafeNodes(self, graph: List[List[int]]) -> List[int]:
    indegree = [0] * len(graph)
    adj = [[] for i in range(len(graph))]
    for node in range(len(graph)):
        for neighbour in graph[node]:
            adj[neighbour].insert(0, node)
            indegree[node] += 1
            
    q = []
    for node in range(len(indegree)):
        if indegree[node] == 0:
            q.insert(0, node)
            
    safe = [False for i in range(len(graph))]
    while len(q) != 0:
        node = q.pop(0)
        safe[node] = True
        for nextNode in adj[node]:
            indegree[nextNode] -= 1
            if indegree[nextNode] == 0:
                q.append(nextNode)
    return [i for i in range(len(safe)) if safe[i] == True]
```
