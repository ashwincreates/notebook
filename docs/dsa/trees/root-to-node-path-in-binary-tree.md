Find the path from root to given node

```python
def node_path(root, target):
    path = []
    def helper(root):
        nonlocal path
        if root is None:
            return False
        if root.val == target:
            path.append(root.val)
            return True
        left = helper(root.left)
        right = helper(root.right)
        if left or right:
            path.append(root.val)
            return True
    helper(root)
    return path[::-1]
```
