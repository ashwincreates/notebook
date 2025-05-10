To find k smallest and largest element, we traverse the tree in a Inorder fashion and keep track of the index when traversal backtracks after reaching the leftmost node.

###### Finding K smallest element
```python
def kthSmallest(root, k)
    ans = 0
    index = 0
    def helper(root):
        nonlocal ans, index
        if root is None:
            return
        helper(root.left)
        index = index + 1
        if index == k:
            ans = root.val
            return
        helper(root.right)
    helper(root)
    return ans
```

Finding K largest element
```python
def kthLargest(root, k)
    ans = 0
    index = 0
    def helper(root):
        nonlocal ans, index
        if root is None:
            return
        helper(root.right)
        index = index + 1
        if index == k:
            ans = root.val
            return
        helper(root.left)
    helper(root)
    return ans
```