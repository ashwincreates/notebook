Disjoint set data structure
```python
def find(A, X):
    p = A[X - 1]
    if p == X:
        return X
    else:
        A[X - 1] = find(A, p)
        return A[X - 1]

def unionSet(A, X, Z):
    pX = find(A, X)
    pZ = find(A, Z)
    A[pX - 1] = pZ
```

##### Union By Rank

```python
def find(A, X):
    p = A[X - 1]
    if p == X:
        return X
    else:
        A[X - 1] = find(A, p)
        return A[X - 1]

def unionSet(A, X, Z, rank):
    pX = find(A, X)
    pZ = find(A, Z)
    if pX == pZ: return
    if rank[pX] < rank[pZ]:
        A[pX - 1] = pZ
    elif rank[pX] > rank[pZ]:
        A[pZ - 1] = pX
    else:
        A[pX - 1] = pZ
        rank[pZ - 1] = rank[pZ - 1] + 1
```
##### Union By Size

```python
def find(A, X):
    p = A[X - 1]
    if p == X:
        return X
    else:
        A[X - 1] = find(A, p)
        return A[X - 1]

def unionSet(A, X, Z, size):
    pX = find(A, X)
    pZ = find(A, Z)
    if pX == pZ: return
    if size[pX] < size[pZ]:
        A[pX - 1] = pZ
        size[pX] = size[pX] + size[pZ]
    else:
        A[pZ - 1] = pX
        size[pZ] = size[pX] + size[pZ]
```
