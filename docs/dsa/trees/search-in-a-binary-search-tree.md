```python
def searchBST(self, root, val):
		if root is None:
			return None
		if root.val == val:
			return root
		if val < root.val:
			return searchBST(root.left, val)
		else:
			return searchBST(root.right, val)
```
