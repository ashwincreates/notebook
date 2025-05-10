We have tell if the sum $k$ , is possible by adding two nodes in the BST

```python
def findTarget(root, k):
    sumMap = {}
    ans = False
    def helper(root):
        nonlocal sumMap, ans
        if root is None:
            return None
        helper(root.left)
        if k - root.val in sumMap:
            ans = True
            return
        sumMap[root.val] = True
        helper(root.right)
    helper(root)
    return ans
```
*Note*: Approach is similar to using maps for two sum