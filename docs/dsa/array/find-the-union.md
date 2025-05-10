Given two **sorted** arrays $a$ and $b$, where each array may contain **duplicate** elements , the task is to return the elements in the **union** of the two arrays in **sorted** order.

```python
def findUnion(self,a,b):
    x, y = 0, 0
    ans = []
    while x < len(a) and y < len(b):
        if a[x] < b[y]:
            ans.append(a[x])
            x += 1
            while x < len(a) and a[x] == a[x - 1]: # skip the dupes
                x += 1
        elif b[y] < a[x]:
            ans.append(b[y])
            y += 1
            while y < len(b) and b[y] == b[y - 1]:
                y += 1
        else:
            x += 1
    while x < len(a):
        ans.append(a[x])
        x += 1
        while x < len(a) and a[x] == a[x - 1]:
            x += 1
    while y < len(b):
        ans.append(b[y])
        y += 1
        while y < len(b) and b[y] == b[y - 1]:
            y += 1
    return ans
```