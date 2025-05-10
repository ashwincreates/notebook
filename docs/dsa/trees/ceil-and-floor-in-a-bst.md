##### Ceil
Ceil of a number $x$ is the immediate greater number than $x$
![[image_1_20240330235536.png]]
```python
def findCeil(self,root, x):
    ans = -1
    def helper(root):
        nonlocal ans
        if root is None:
            return
    		if x > root.val:
    			helper(root.right)
    		elif x < root.val:
    			ans = root.val
    			helper(root.left)
    		else:
    			ans = root.val
	helper(root)
	return ans
```
*Note*: Iterative and Recursive approach to this solution is same
##### Floor
Floor of a number $x$ is the immediate smaller number than $x$
![[image_20240331000808.png]]
```python
def findFloor(self,root, x):
	ans = -1
	def helper(root):
		nonlocal ans
		if root is None:
			return
		if x > root.val:
			ans = root.val
			helper(root.right)
		elif x < root.val:
			helper(root.left)
		else:
			ans = root.val
	helper(root)
	return ans
```
*Note*: Iterative and Recursive approach to this solution is same