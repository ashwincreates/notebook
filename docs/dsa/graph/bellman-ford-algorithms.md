The Bellman-Ford algorithm guarantees that shortest paths can be correctly computed in `V - 1` iterations due to its approach to edge relaxation and the properties of shortest paths in graphs. Here's a deeper dive into why `V - 1` iterations are sufficient:

### Concept of Shortest Path

1. **Path Lengths:**
    - In a graph, the shortest path from a source vertex to any other vertex can be at most `V - 1` edges long if there are `V` vertices. This is because a path that uses more than `V - 1` edges would necessarily involve revisiting some vertices, potentially creating a cycle.

### Edge Relaxation

2. **Relaxation:**
    
    - **Relaxing an edge `(u, v)` with weight `w`:** If the current known distance to vertex `v` can be shortened by taking the edge from `u` to `v`, then update the distance:
        
        python
        
        Copy code
        
        `if distance[u] + w < distance[v]:     distance[v] = distance[u] + w`
        
3. **Relaxation Process Over `V - 1` Iterations:**
    
    - During each iteration, every edge in the graph is examined and relaxed if a shorter path is found. The process of relaxing edges allows the algorithm to progressively build up the shortest path estimates.

### Why `V - 1` Iterations Are Enough

4. **Path Length and Relaxation:**
    
    - In a shortest path that uses up to `V - 1` edges, the maximum number of edges involved is `V - 1`. This is because any path that uses `V` or more edges would necessarily contain cycles. The algorithm needs `V - 1`iterations to ensure that all possible paths up to `V - 1` edges are considered.
    
1. **Convergence of Shortest Paths:**
    
    - After `V - 1` iterations, the algorithm will have relaxed all edges enough times to ensure that the shortest path distances are correct. This is because every path from the source to any vertex that uses up to `V - 1` edges will have been fully considered.

##### Code
```python
def bellman_ford(self, V, edges, S):
    dist = [100000000 for i in range(V)]
    dist[S] = 0
    for i in range(V):
        for u, v, w in edges:
            newDist = dist[u] + w
            if dist[u] != 100000000 and newDist < dist[v]:
                dist[v] = newDist
    for u, v, w in edges:
        newDist = dist[u] + w
        if dist[u] != 100000000 and newDist < dist[v]:
            return [-1]
                
    return dist
```