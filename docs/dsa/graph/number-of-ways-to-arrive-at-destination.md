```python
def countPaths(self, n: int, roads: List[List[int]]) -> int:

    adj = [[] for i in range(n)]
    
    for road in roads:
    
        u, v, w = road
        
        adj[u].append((w, v))
        
        adj[v].append((w, u))
    
    heap = [(0, 0)]
    
    mindist = [math.inf for i in range(n)]
    
    mindist[0] = 0
    
    count = [0 for i in range(n)]
    
    count[0] = 1
    
    while heap:
    
        w1, s = heappop(heap)
        
        if mindist[s] < w1: continue
        
        for road in adj[s]:
        
            w2, d = road
            
            if mindist[d] > mindist[s] + w2:
            
            mindist[d] = mindist[s] + w2
            
            count[d] = count[s]
            
            heappush(heap, (mindist[d], d))
            
            elif mindist[d] == mindist[s] + w2:
            
            count[d] = (count[d] + count[s]) % 1_000_000_007
            
    return count[n - 1]
```