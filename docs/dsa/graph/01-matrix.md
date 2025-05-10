Here, we need to find the nearest zero for each one

So solve this, what we do is for each 0, we do a BFS, the search which reaches the nearest first, marks the nearest distance in that cell

> [!note] BFS reaches the shortest node

```python
def updateMatrix(self, mat: List[List[int]]) -> List[List[int]]:
    queue = []
    rows = len(mat)
    cols = len(mat[0])
    for row in range(rows):
        for col in range(cols):
            if mat[row][col] == 0:
                queue.append([row, col])
            else:
                mat[row][col] = -1

    visited = [[False for i in range(cols)] for j in range(rows)]
    while len(queue) > 0:
        row, col = queue.pop(0)
        for xx, yy in [(1, 0), (0, 1), (-1, 0), (0, -1)]:
            p = row + xx
            q = col + yy
            if p >= 0 and q >= 0 and p < rows and q < cols and mat[p][q] == -1:
                mat[p][q] = mat[row][col] + 1
                queue.append([p, q])
    return mat
```