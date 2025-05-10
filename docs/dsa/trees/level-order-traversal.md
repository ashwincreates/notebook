Traversing the tree level by level

```python
def levelorder(root):
    queue = [root]
    level = 0
    while len(queue) != 0:
        print(level, end=" -> ")
        level = level + 1
        queue_size = len(queue)
        for i in range(0, queue_size):
            node = queue.pop(0)
            print(node.val, end=" ")
            if node.left is not None:
                queue.append(node.left)
            if node.right is not None:
                queue.append(node.right)
        print()
```
