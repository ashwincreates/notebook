##### Inorder Traversal
Traversal where we access left child, root and then right child node

$$
	left\ child \rightarrow root \rightarrow right\ child
$$

###### Inorder Traversal Recursive
```python
def inorder():
    if node is None:
        return
    inorder(node.left)
    print(node.val)
    inorder(node.right)
```
###### Inorder Traversal Iterative
```python
def inorder():
    currNode = tree
    stack = []
    while currNode is not None or len(stack) != 0:
        if currNode != None:
            stack.append(currNode)
            currNode = currNode.left
        else:
            parent = stack.pop()
            rightNode = parent.right
            print(parent.val)
            
            if rightNode is None:
	            if len(stack) != 0:
		            parent = stack.pop()
	                print(parent.val)
	                currNode = parent.right
            else:
	            currNode = rightNode
```

