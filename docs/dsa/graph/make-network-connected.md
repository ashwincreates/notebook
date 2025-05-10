```python
def makeConnected(n, connections):
    
    if len(connections) < n - 1:
        return -1
    
    parent = [i for i in range(n)]
    
    def find(v, parent):
        if parent[v] == v:
            return v
        p = find(parent[v], parent)
        parent[v] = p
        return p
    
    def union(u, v, parent):
        pu = find(u, parent)
        pv = find(v, parent)
        
        if pu == pv:
            return
        else:
            parent[pu] = pv
    
    for u, v in connections:
        union(u, v, parent)
    
    components = 0
    
    for i in range(n):
        if parent[i] == i:
            components += 1
    
    return components - 1
```