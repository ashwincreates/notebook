> [!note] Djikstras Algorithm visits the node with the shortest distance to source first
  
```python
def dijkstra(self, n, adj, src):
        dist = [1e9] * n
        dist[src] = 0
        visited = [False] * n
        
        for _ in range(n):
            
            min_dist_in_set = 1e9
            # node closest to source
            min_dist_node = src
            for node in range(n):
                if not visited[node] and dist[node] < min_dist_in_set:
                    min_dist_in_set = dist[node]
                    min_dist_node = node
                
            visited[min_dist_node] = True
                
            for neighbour, wt in adj[min_dist_node]:
                new_dist = dist[min_dist_node] + wt
                if new_dist < dist[neighbour]:
                    dist[neighbour] = new_dist
        return dist 
```