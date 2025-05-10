Find the number of provinces where each province is a group of nodes connected to each other. Here the observation is that each province is a graph, so we need to count the graph, to do that we traverse each graph and track a count of each traversal.
```python
def findCircleNum(self, isConnected: List[List[int]]) -> int:
    total = len(isConnected)
    visited = [False] * total
    ans = 0
    # dfs or you can use bfs
    def helper(node):
        nonlocal visited, total
        if visited[node]:
            return
        visited[node] = True
        for neighbour in range(total):
            if isConnected[node][neighbour]:
                helper(neighbour)
    # traverse each graph and track count
    for i in range(total):
        if visited[i]:
            continue
        ans = ans + 1
        helper(i)
    return ans
```