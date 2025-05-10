This solution is based on the fact that in
- preorder traversal we print the node when we visit the node 1st time
- inorder traversal we print the node when we visit the node 2nd time
- postorder traversal we print the node when we visit the node 3rd time

```python
def single_traversal(root):
    preorder = []
    postorder = []
    inorder = []
    stack = [[root, 1]]
    while len(stack) != 0:
        node, count = stack.pop()
        if count == 1:
            preorder.append(node.val)
            stack.append([node, count + 1])
            if node.left is not None:
                stack.append([node.left, 1])
        elif count == 2:
            inorder.append(node.val)
            stack.append([node, count + 1])
            if node.right is not None:
                stack.append([node.right, 1])
        else:
            postorder.append(node.val)
    print(preorder)
    print(postorder)
    print(inorder)
```
