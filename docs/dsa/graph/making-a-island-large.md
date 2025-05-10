```python
class Solution:
    def largestIsland(self, grid: List[List[int]]) -> int:
        # standard find and union
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
                
        n = len(grid)
        parent = [i for i in range(n * n)]

        # first we find all the components
        for i in range(n):
            for j in range(n):
                if grid[i][j] == 0: continue
                fi = i * n + j
                for p, q in [[0, 1], [0, -1], [1, 0], [-1, 0]]:
                    x = i + p
                    y = j + q
                    if x >= 0 and x < n and y >= 0 and y < n and grid[x][y] == 1:
                        si = x * n + y
                        if find(fi, parent) != find(si, parent):
                            union(fi, si, parent)

        # find size of each component (can be done by union by size)
        size = [0 for i in range(n * n)]
        for idx in range(n * n):
            size[find(idx, parent)] += 1

        ans = max(size)
        # now we try to find a node which join adjoining components
        # total size of result component would be 
        # total = sum of sizes of adjoining components + 1
        for i in range(n):
            for j in range(n):
                if grid[i][j] == 1: continue
                adj = set()
                for p, q in [[0, 1], [0, -1], [1, 0], [-1, 0]]:
                    x = i + p
                    y = j + q
                    if x >= 0 and x < n and y >= 0 and y < n and grid[x][y] == 1:
                        si = x * n + y
                        adj.add(find(si, parent))
                total = 0
                for c in adj:
                    total += size[c]
                ans = max(ans, total + 1)
                    
        return ans
```