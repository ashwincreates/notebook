###### Construct a binary tree from Inorder and Preorder Traversal
```python
def create_tree(inorder, preorder):
    indexOf = {}
    for i, val in enumerate(inorder):
        indexOf[val] = i
    def helper(istart, iend, pstart, pend):
        if istart > iend or pstart > pend:
            return None
        root = Node(preorder[pstart])

        rootIndex = indexOf[root.val]
        leftElements = rootIndex - istart
        root.left = helper(istart, rootIndex - 1, pstart + 1, pstart + leftElements)
        root.right = helper(rootIndex + 1, iend, pstart + leftElements + 1, pend)
        return root
    newRoot = helper(0, len(inorder) - 1, 0, len(preorder) - 1)
    return newRoot
```

###### Construct a binary tree from Inorder and Postorder Traversal
```python
def create_tree(inorder, postorder):
    indexOf = {}
    for i, val in enumerate(inorder):
        indexOf[val] = i
    def helper(istart, iend, pstart, pend):
        if istart > iend or pstart > pend:
            return None
        root = Node(postorder[pend])

        rootIndex = indexOf[root.val]
        leftElements = rootIndex - istart
        root.left = helper(istart, istart + leftElements, pstart, pstart + leftElements - 1)
        root.right = helper(rootIndex + 1, iend, pstart + leftElements, pend - 1)
        return root
    newRoot = helper(0, len(inorder) - 1, 0, len(postorder) - 1)
    return newRoot
```