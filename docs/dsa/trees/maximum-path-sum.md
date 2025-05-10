Find the sequence of nodes with the maximum sum

```python
def maximum_path_sum(root):
    maxSum = -100000
    def helper(root):
        if root is None:
            return 0
        left = 0
        right = 0
        if root.left is not None:
            left = max(left, helper(root.left))
        if root.right is not None:
            right = max(right, helper(root.right))
        nonlocal maxSum
        maxSum = max(maxSum, left + right + root.val)
        return max(left, right) + root.val
    helper(root)
    return maxSum
```

Similar to diameter problem on every node we calculate the max sum as:
$$
max(maxSum,\ maxSum\ of\ left\ subtree\ +\ maxSum\ of\ right\ subtree\ +\ value\ of\ root)
$$
