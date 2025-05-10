```python
def print_at_k(root, target, k):
    parent_map = {}

	# Creating Graph (Adjacent list)
    def create_map(root):
        nonlocal parent_map
        queue = [root]
        while len(queue) != 0:
            size = len(queue)
            for i in range(size):
                node = queue.pop(0)

                if node not in parent_map:
                    parent_map[node] = []
                if node.left not in parent_map and node.left is not None:
                    parent_map[node.left] = []
                if node.right not in parent_map and node.right is not None:
                    parent_map[node.right] = []

                if node.left is not None:
                    parent_map[node].append(node.left)
                    parent_map[node.left].append(node)
                    queue.append(node.left)
                if node.right is not None:
                    parent_map[node].append(node.right)
                    parent_map[node.right].append(node)
                    queue.append(node.right)
    create_map(root)
    for key in parent_map:
        print(key.val, list(map(lambda x: x.val, parent_map[key])))
    visited = {}
    queue = [target]
    curr_k = 0

	# BFS
    while len(queue) != 0:
        if curr_k == k:
            break
        curr_k = curr_k + 1
        size = len(queue)
        for i in range(size):
            node = queue.pop(0)
            visited[node] = True
            for node in parent_map[node]:
                if node in visited:
                    continue
                queue.append(node)
    print(list(map(lambda x: x.val, queue)))

print_at_k(tree, tree.left.left, 2)
```

- Basically create a graph out of tree and traverse it breadth first, with each breadth as a level