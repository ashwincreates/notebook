##### Preorder Traversal
Traversal where we access root node, left child and then right child node

$$
root \rightarrow left\ child \rightarrow right\ child
$$

###### Preorder Recursive Approach
```python
def preorder(node):
    if node is None:
        return
    print(node.val)
    preorder(node.left)
    preorder(node.right)
```

###### Preorder Iterative Approach
```python
def preorder():
    stack = [root]
    while len(stack) != 0:
        node = stack.pop()
        print(node.val)
        if node.right is not None:
            stack.append(node.right)
        if node.left is not None:
            stack.append(node.left)
```
