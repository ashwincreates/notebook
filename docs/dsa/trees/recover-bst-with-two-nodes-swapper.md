Given a BST with exactly two nodes being swapped by mistake, recover the BST
```python
def recoverTree(root):
    first = None
    second = None
    prev = TreeNode(-1e10)
    def helper(root):
        nonlocal first, second, prev
        if root is None:
            return
        helper(root.left)
        if first is None and prev.val > root.val:
            first = prev
        if first is not None and prev.val > root.val:
            second = root
        prev = root
        helper(root.right)
    helper(root)
    temp = first.val
    first.val = second.val
    second.val = temp
```