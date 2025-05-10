```python
def serialize(self, root):
	ans = ""
	queue = [root]
	while len(queue) != 0:
		node = queue.pop(0)
		if node is not None:
			ans = ans + str(node.val)
			queue.append(node.left)
			queue.append(node.right)
		else:
			ans = ans + "N"
		ans = ans + " "
	return ans
	
def deserialize(self, data):
	data = list(data.split(" "))[:-1]
	if  data[0] == 'N':
		return None
	root = TreeNode(int(data[0]))
	data.pop(0)
	queue = [root]
	while len(data) > 0 and len(queue) > 0:
		node = queue.pop(0)
		if data[0] != 'N':
			node.left = TreeNode(int(data.pop(0)))
			queue.append(node.left)
		else:
			data.pop(0)
		if  data[0] != 'N':
			node.right = TreeNode(int(data.pop(0)))
			queue.append(node.right)
		else:
			data.pop(0)
	return root
```