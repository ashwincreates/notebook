Find the maximum width of the binary tree, where width is the no. of nodes (null or non-null) between leftmost and rightmost node of a particular level

```python
def maxWidth(node):
    width = 0
    queue = [(node, 0)]
    while len(queue) != 0:
        left_most = 0
        right_most = 0
        size = len(queue)
        print(queue)
        for i in range(0, size):
            temp, curr_index = queue[0]
            queue.pop(0)
            if i == 0:
                left_most = curr_index
            if i == size - 1:
                right_most = curr_index
            if temp.left is not None:
                queue.append((temp.left, curr_index * 2 + 1))
            if temp.right is not None:
                queue.append((temp.right , curr_index * 2 + 2))
        width = max(width, right_most - left_most + 1)
    print(width)
```
