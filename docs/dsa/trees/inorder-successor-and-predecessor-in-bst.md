```python
def predecessorSuccessor(root, key):
    prev = -1
    succ = -1
    def helper(node):
        nonlocal prev,nex
        if node is None:
            return
        if key < node.data:
            succ = node.data
            helper(node.left)
        elif key > node.data:
            prev = node.data
            helper(node.right)
        else:
            helper(node.left)
            helper(node.right)
    helper(root)
    return [prev, succ]
```



