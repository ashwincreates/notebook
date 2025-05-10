###### Insertion
Inserting in a BST is straight forward
```python
def insertIntoBST(root, val):
	if root is None:
		return TreeNode(val)
	if val < root.val:
		root.left = self.insertIntoBST(root.left, val)
	else:
		root.right = self.insertIntoBST(root.right, val)
	return root
```
###### Deletion
In deletion to reduce complexity, we exchange the node to be deleted with it's Inorder predecessor, and remove the predecessor, this make it easy since predecessor is usually a leaf node.
```python
def helper(root, key):
	if root is not None:
		if root.val == key:
			if root.left and root.right:
				pre = root.left
					while pre.right:
						pre = pre.right
					# Assign predecessor as root 
					root.val = pre.val
					# Delete the predecessor
					root.left = helper(root.left, pre.val)
			elif root.left or root.right:
				return root.left if root.left else root.right
			else:
				return None
		elif key < root.val:
			root.left = helper(root.left, key)
		else:
			root.right = helper(root.right, key)
	return root
```
