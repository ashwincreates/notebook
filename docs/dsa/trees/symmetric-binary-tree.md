Find if a binary tree is a mirror image of itself

```python
def is_symmetrical(root):
    def helper(root1, root2):
        if root1 is None and root2 is None:
            return True
        if root1 is None or root2 is None:
            return False
        return root1.val == root2.val and helper(root1.left, root2.right) and helper(root1.right, root2.left)
    return helper(root.left, root.right)
```
