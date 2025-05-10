![[Pasted_image_20240401211016.png]]
```python
def isValidBST(root):
    mn = -10000000000
    mx = 10000000000
    def isPossible(root, minimum, maximum):
        if root is None:
            return True
        if minimum < root.val and root.val < maximum:
            return isPossible(root.left, minimum, root.val) and isPossible(root.right, root.val, maximum)
        else:
            return False
    return isPossible(root, mn, mx)
```