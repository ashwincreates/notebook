Morris Traversal is a way to traverse a tree without the need of a stack or recursion. In Morris Traversal no recursion is necessary, because instead of relying on backtracking through a stack, a link back to the root of the (sub)tree is moved to the point at which it would be accessed in a recursive Inorder tree traversal algorithm anyway -- after its left subtree has finished.
![[morris_traveral.png]]
*Steps in Morris Inorder*:
- current is root, if there is a node left of current, ==find the rightmost node== in the left subtree of current and link it to the current node, we call this a ==backlink==. Now, move current node to left subtree
- Now, we continue, the first step, and go left
- if left is None, or there is no left subtree, we go right, now here right could be a *backlink* or a regular link down the node
- now if we rode a backlink, we would go back to the parent of the subtree, and follow step one, now since there is a backlink, finding the rightmost node of the subtree, will loop back to current. In which case we remove the backlink, and go further right

###### Morris Inorder
```python
def morris_inorder(root):
    curr = root
    while curr:
        if curr.left is None:
            print(curr.val, end = " ")
            curr = curr.right
        else:
            right_most = curr.left
            while right_most.right and right_most.right != curr:
                right_most = right_most.right

            if right_most.right is None:
                right_most.right = curr
                curr = curr.left
            else:
                right_most.right = None
                print(curr.val, end = " ")
                curr  = curr.right
```
###### Morris Preorder
```python
def morris_preorder(root):
    curr = root
    while curr:
        if curr.left is None:
            print(curr.val, end = " ")
            curr = curr.right
        else:
            right_most = curr.left
            while right_most.right and right_most.right != curr:
                right_most = right_most.right

            if right_most.right is None:
                right_most.right = curr
                print(curr.val, end = " ")
                curr = curr.left
            else:
                right_most.right = None
                curr  = curr.right
```
###### Morris Postorder
Morris post order is the mirror image of preorder
```python
def morris_postorder(root):
    curr = root
    postorder = []
    while curr:
        if curr.right is None:
            postorder.append(curr.val)
            curr = curr.left
        else:
            right_most = curr.right
            while right_most.left and right_most.left != curr:
                right_most = right_most.left

            if right_most.left is None:
                right_most.left = curr
                postorder.append(curr.val)
                curr = curr.right
            else:
                right_most.left = None
                curr  = curr.left
    print(" ".join(map(str, postorder[::-1])))
```