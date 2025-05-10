Here we need to flip all 'O's which are directly or indirectly not in touch a 'O' at the edge

So we do a DFS from 'O's at the edges, and mark all neighbors '#', then we traverse again traverse the board and flip 'O's which are not marked
```python
def solve(self, board: List[List[str]]) -> None:
    rows = len(board)
    cols = len(board[0])
    def dfs(row, col):
        nonlocal rows, cols
        board[row][col] = '#'
        for xx, yy in [(1, 0), (0, 1), (-1, 0), (0, -1)]:
            p, q = row + xx, col + yy
            if p >= 0 and q >= 0 and p < rows and q < cols and board[p][q] == 'O':
                dfs(p, q)
    for row in range(rows):
        for col in range(cols):
            if (row == 0 or col == 0 or row == rows - 1 or col == cols - 1) and board[row][col] == 'O':
                dfs(row, col)
    for row in range(rows):
        for col in range(cols):
            if board[row][col] == 'O':
                board[row][col] = 'X'
            if board[row][col] == '#':
                board[row][col] = 'O'
```