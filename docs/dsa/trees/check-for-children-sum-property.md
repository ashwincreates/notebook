Modify a binary tree so that each node follow children sum property, where children sum property is 
$$
\text{sum of right subtree + sum of left subtree = value of root}
$$
```python
def child_sum(root):
    if root is None:
        return
        
    childsum=0
    
    if root.left:
        childsum = childsum + root.left.val
    if root.right:
        childsum = childsum + root.right.val
        
    if childsum < root.val:
        if root.left:
            root.left.val = childsum
        elif root.right:
            root.right.val = childsum
            
    child_sum(root.left)
    child_sum(root.right)
    
    total=0
    if root.left:
        total = total + root.left.val
    if root.right:
        total = total + root.right.val
    if root.left or root.right:
        root.val = total
```

- If sum of right and left subtree is greater than root's value we can simply set root's value as sum of left and right subtree
- else, if not copy the value to left or right subtree, this will ensure sum of children is greater than the node