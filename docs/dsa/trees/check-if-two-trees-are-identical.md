Two trees are identical when corresponding values of node are equal

```python
def is_identical(root1, root2):
    if root1 is None and root2 is None:
        return True
    if root1 is None or root2 is None:
        return False
    return is_identical(root1.left, root2.left) and is_identical(root1.right, root2.right) and root1.val == root2.val
```
