If a node let's $x$ is the LCA of $p$ and $q$ then 
$$
\begin{equation}
\text{p.val <= x.val <= q.val}
\end{equation}
$$
```python
def lowestCommonAncestor(root, p, q):
    # Bring the root in range
    if root.val < p.val and root.val < q.val:
        return lowestCommonAncestor(root.right, p, q)
    elif root.val > p.val and root.val > q.val:
        return lowestCommonAncestor(root.left, p, q)
    else:
        # This is LCA
        return root
```