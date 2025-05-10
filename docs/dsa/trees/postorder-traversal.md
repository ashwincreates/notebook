##### Postorder Traversal
Traversal where we access root node, left child and then right child node

$$
left\ child \rightarrow right\ child  \rightarrow root
$$

###### Postorder Traversal Recursive
```python
def postorder(node):
    if node is None:
        return
    postorder(node.left)
    postorder(node.right)
    print(node.val)
```

###### Postorder Traversal using 2 Stacks
```python
def postorder():
    stack = [tree]
    _stack = []
    while len(stack) != 0:
        node = stack.pop()
        if node.left is not None:
            stack.append(node.left)
        if node.right is not None:
            stack.append(node.right)
        _stack.append(node)
    while len(_stack) != 0:
        node = _stack.pop()
        print(node.val)
```

###### Postorder Traversal using 1 Stack
```python
def postorder():
    currNode = tree
    stack = []
    while currNode != None or len(stack) != 0:
        if currNode is not None:
            stack.append(currNode)
            currNode = currNode.left
        else:
            parent = stack[-1]
            rightNode = parent.right

            if rightNode is None:
                rightNode = stack.pop()
                print(rightNode.val)
                while len(stack) != 0 and rightNode == stack[-1].right:
                    rightNode = stack.pop()
                    print(rightNode.val)
            else:
                currNode = rightNode
```

***Explanation:***
- Start with current root and go left and push the current node to stack
- In case there is no left, change to current node to the immediate parent's right
- if there is no right, pop the immediate parent from the stack
- now the popped node could be the right child of the new immediate parent (the top element in stack) the means both child of the new immediate parents have been traversed, so pop that too, and loop till it's not the case










