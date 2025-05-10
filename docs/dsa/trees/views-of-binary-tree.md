![[Pasted_image_20240404221007.png]]
##### Top/Bottom  View
To create top/bottom views we create imaginary numbered ==vertical== lines through nodes, and map top nodes of these lines for top view and bottom nodes for bottom views

###### Top View
```python
def top(root):
    queue = [[root, 0]]
    lines = {}
    while len(queue) != 0:
        node, line = queue.pop(0)
        if line not in lines:
            lines[line] = node.val
        if node.left is not None:
            queue.append([node.left, line + 1])
        if node.right is not None:
            queue.append([node.right, line - 1])
    print(sorted(list(lines.items()), key=lambda x: x[0]))
```

###### Bottom View
```python
def bottom(root):
    queue = [[root, 0]]
    lines = {}
    while len(queue) != 0:
        node, line = queue.pop(0)
        if line not in lines:
            lines[line] = node.val
        else:
            lines[line] = node.val
        if node.left is not None:
            queue.append([node.left, line + 1])
        if node.right is not None:
            queue.append([node.right, line - 1])
    print(sorted(list(lines.items()), key=lambda x: x[0]))
```

##### Left/Right Views
To create left/right views we create imaginary ==horizontal== lines/level through nodes, and map left-most nodes of these values for left view and right-most nodes for right 
###### Left View
```python
def left(root):
    left_view = []
    queue = [root]
    while len(queue) != 0:
        level = []
        queue_size = len(queue)
        for i in range(0, queue_size):
            node = queue.pop(0)
            level.append(node.val)
            if node.left is not None:
                queue.append(node.left)
            if node.right is not None:
                queue.append(node.right)
        left_view.append(level[0])
    print(left_view)
```

###### Right View
```python
def right(root):
    right_view = []
    queue = [root]
    while len(queue) != 0:
        level = []
        queue_size = len(queue)
        for i in range(0, queue_size):
            node = queue.pop(0)
            level.append(node.val)
            if node.left is not None:
                queue.append(node.left)
            if node.right is not None:
                queue.append(node.right)
        right_view.append(level[-1])
    print(right_view)
```
