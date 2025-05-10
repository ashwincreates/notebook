Topological sorting for **Directed Acyclic Graph (DAG)** is a linear ordering of vertices such that for every directed edge u-v, vertex **u** comes before **v** in the ordering

> [!important]  Topological sort is not possible for undirected graph or graph having a cycle

The basic idea to traverse the node and store the visited node in a stack, important thing to note is the use of stack.

###### Using DFS
```python
# Function to perform Topological Sort
def topologicalSort(adj, V):
    # Stack to store the result
    stack = []
    visited = [False] * V
    
    def helper(v, adj):
        nonlocal visited, stack
        # Mark the current node as visited
        visited[v] = True
    
        # Recur for all adjacent vertices
        for i in adj[v]:
            if not visited[i]:
                helper(i, adj)
    
        # Push current vertex to stack which stores the result
        stack.append(v)

    # Call the recursive helper function to store
    # Topological Sort starting from all vertices one by
    # one
    for i in range(V):
        if not visited[i]:
            helper(i, adj)

    # Print contents of stack
    print("Topological sorting of the graph:", end=" ")
    while stack:
        print(stack.pop(), end=" ")
```
###### Using BFS (Kahn's Algorithm)
```python
def topologicalSort(V, adj):
        # Create a list to store in-degree of all vertices
        in_degree = [0] * V

        # Traverse adjacency lists to fill in_degree of vertices
        for i in range(V):
            for j in adj[i]:
                in_degree[j] += 1

        # Create a queue and enqueue all vertices with in-degree 0
        q = []
        for i in range(self.V):
            if in_degree[i] == 0:
                q.append(i)

        # Initialize count of visited vertices
        count = 0

        # Create a list to store topological order
        top_order = []

        # One by one dequeue vertices from queue and enqueue
        # adjacent vertices if in-degree of adjacent becomes 0
        while q:
            # Extract front of queue (or perform dequeue)
            # and add it to topological order
            u = q.pop(0)
            top_order.append(u)

            # Iterate through all its neighbouring nodes
            # of dequeued node u and decrease their in-degree
            # by 1
            for node in adj[u]:
                # If in-degree becomes zero, add it to queue
                in_degree[node] -= 1
                if in_degree[node] == 0:
                    q.append(node)

            count += 1

        # Check if there was a cycle
        if count != V:
            print("Graph contains cycle")
            return

        # Print topological order
        print("Topological Sort:", top_order)
```
###### Applications
- Finding dependent nodes
- Finding a cycle