##### Indirect Graph
###### Using BFS
```python    
visited=[False] * V

def isCycle(v,adj):
    queue = [[v,-1]]  
    while len(queue) > 0:
        node,parent = queue.pop(0)
        visited[node] = True
        for neighbour in adj[node]:
            if not visited[neighbour]:
                queue.append([neighbour,node])
            elif neighbour != parent:
                return True
    return False

ans = False
for i in range(V):
    if visited[i]:
        continue
    ans = ans or isCycle(i, adj)
print(ans)
```

###### Using DFS
```python
visited=[False] * V

def isCycle(v, parent, adj):
    visited[v] = True
    for neighbour in adj[v]:
        if not visited[neighbour]:
            if solve(neighbour,v,adj) == True:
                return True
        elif neighbour != parent:
            return True
    return False

ans = False
for i in range(V):
    if visited[i]:
        continue
    ans= ans or isCycle(i, -1, adj)
```

##### Direct Graph

#todo🖋️ 