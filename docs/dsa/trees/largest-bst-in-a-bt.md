We need to find largest BST in a binary tree. For that we need to tell that at a current node both ==left and right subtree is a binary tree or not== and the ==current node is also a valid node==.

- To do that we follow bottom up approach and maintain the minimum value found and the maximum value found while traversing up the tree.
- To find if the current node is a valid BST node or not, we see if the maximum value of subtree is smaller than current node and minimum value of right subtree is greater than the current node


```python
def largestBst(self, root):
        maxAns = 0
        # returned values are [maxSize, minimum, maximum]
        def helper(root):
            if root is None:
                # this is particulary of a edge
                # where we need to statisfy the bst condition
                return (0, 1e10, -1e10)
            lans, lmini, lmaxi = helper(root.left)
            rans, rmini, rmaxi = helper(root.right)
            
            if lmaxi < root.data < rmini:
                return (lans + rans + 1, min(lmini, root.data), max(rmaxi, root.data))
            
            return (max(lans, rans), -1e10, 1e10)
        return helper(root)[0]
```