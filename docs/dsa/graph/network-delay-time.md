```python
def networkDelayTime(self, times: List[List[int]], n: int, k: int) -> int:
    adj = [[] for i in range(n)]
    for node in times:
        u, v, w = node
        adj[u - 1].append((w, v - 1))
    
    dist = [1e9 for i in range(n)]
    dist[k - 1] = 0
    minheap = [(0, k - 1)]
    
    while minheap:  
        w1, u = heappop(minheap)
        for node in adj[u]:
            w2, v = node 
            if dist[v] > dist[u] + w2: 
                dist[v] = dist[u] + w2   
                heappush(minheap, (dist[v], v))
    
    ans = max(dist)
    return ans if ans is not 1e9 else -1
```