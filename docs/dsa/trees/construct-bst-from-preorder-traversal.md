We are given a preorder array of a BST, and we have to create a BST. To solve this we have three solutions

###### $O(n^2)$ Solution
We take the 0th index of the preorder as the root, then find index of the number, just greater than root, let say $i$ , now all elements below $i$, will go in the left, while rest will go in the right subtree. Since we are searching for the element every time, this method's complexity is $O(n^2)$.

```python
def bstFromPreorder(self, preorder):
    if len(preorder) == 0:
        return None
    root = TreeNode(preorder.pop(0))
    index = len(preorder)
    for i in range(len(preorder)):
        if preorder[i] > root.val:
            index = i
            break
    root.left = self.bstFromPreorder(preorder[:index])
    root.right = self.bstFromPreorder(preorder[index:])
    return root
```

###### $O(nlogn)$ Solution
Instead of searching linearly we can use upper bound and lower bound function to find the element in $log(n)$.
```python
def bstFromPreorder(self):
    if len(preorder) == 0:
        return None
    root = TreeNode(preorder.pop(0))
    index = bisect.bisect(preorder, root.val)
    root.left = self.bstFromPreorder(preorder[:index])
    root.right = self.bstFromPreorder(preorder[index:])
    return root
```

###### $O(n)$ Solution
This solution tracks and indexes the preorder
```python
def bstFromPreorder(preorder):
    i = 0
    def helper(A, bound):
        nonlocal i
        if i == len(A) or A[i] > bound:
            return None
        root = TreeNode(A[i])
        i += 1
        root.left = bstFromPreorder(A, root.val)
        root.right = bstFromPreorder(A, bound)
        return root
    return helper(preorder, 10000000000)
```
