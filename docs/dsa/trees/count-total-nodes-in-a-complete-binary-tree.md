Count total nodes in a complete binary tree, where a complete binary tree is a tree where all 
- All levels except the last one are completely filled. The last level may or may not be completely filled.
- Nodes in the last level are as left as possible.

*Properties of a complete binary tree*:
- left most depth will be the height of the tree
- hence, if the right most depth is equal to left most depth then the tree is complete binary, having all nodes and we can find total maximum nodes as $2^h + 1$.
- if the right most depth is not equal to left most depth, we can go one step down either left and right and check the same, then total nodes would be $$\text{Total nodes = 1 + nodes in left subtree + nodes in right subtree}$$
```python
def countNodes(root):
		def goLeft(root):
			if root is None:
				return 0
			return 1 + goLeft(root.left)
		def goRight(root):
			if root is None:
				return 0
			return 1 + goRight(root.right)
		
		leftHeight = goLeft(root)
		rightHeight = goRight(root)
		if leftHeight == rightHeight:
			return 2 ** leftHeight - 1
		else:
			return 1 + self.countNodes(root.left) + self.countNodes(root.right)
```
