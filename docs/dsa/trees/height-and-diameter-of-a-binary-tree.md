##### Height
Height of a binary tree is ==count of longest path== from the root node

```python
def height(root):
    def helper(node, height):
        if node is None:
            return height
        left = 0
        right = 0
        if node.left is not None:
            left = helper(node.left, height + 1)
        if node.right is not None:
            right = helper(node.right, height + 1)
        return max(left, right) + 1
    return helper(root, 0)
```

##### Diameter
Diameter of a binary tree is count of the ==longest path between any two nodes== in a binary tree

```python
def diameter(root):
    diameter = 0
    def helper(node, height):
        if node is None:
            return height
        left = 0
        right = 0
        if node.left is not None:
            left = helper(node.left, height + 1)
        if node.right is not None:
            right = helper(node.right, height + 1)
        nonlocal diameter
        diameter = max(diameter, left + right)
        return max(left, right) + 1
    helper(root, 0)
    return diameter
```

Here for calculating diameter we consider each node as the curving point, and the node with maximum sum of height of left and right subtrees would be the longest path.  
