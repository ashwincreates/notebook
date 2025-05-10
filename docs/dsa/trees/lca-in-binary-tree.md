Finding the lowest common ancestor of two nodes in a binary tree

```python
def lca(root, node1, node2):
    ancestor = None
    def helper(root):
        nonlocal ancestor
        if root is None:
            return False
        left = helper(root.left)
        right = helper(root.right)
        if left and right:
            ancestor = root
            return True
        if root.val == node1.val or root.val == node2.val: 
            ancestor = root
            return True
        return left or right
    helper(root)

    if ancestor is None:
        print("No Ancestor")
    else:
        print(ancestor.val)
```

- The target node could itself  be the ancestor
- The node which has node1 in left subtree and node2 in right subtree could also be the ancestor