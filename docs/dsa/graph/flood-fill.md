```python
    def floodFill(self, image: List[List[int]], sr: int, sc: int, color: int) -> List[List[int]]:

        n = len(image)

        m = len(image[0])

        queue = [[sr, sc]]

        while len(queue) > 0:

            x, y = queue.pop(0)

            for xx, yy in [(1, 0), (-1, 0), (0, 1), (0, -1)]:

                p, q = x + xx, y + yy

                if p >= 0 and p < n and q >= 0 and q < m and image[p][q] != color and image[x][y] == image[p][q]:

                    queue.append([p, q])

            image[x][y] = color

        return image
```