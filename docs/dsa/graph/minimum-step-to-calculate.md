```python
def minimumMultiplications(self, arr : List[int], s : int, e: int) -> int:
    heap = [(0, s)]
    minSteps = [math.inf for i in range(100000)]
    minSteps[s] = 0
    while heap:
        step, start = heapq.heappop(heap)
        if start == e:
            return minSteps[e]
        for n in arr:
            newStart = (n * start) % 100000
            if step + 1 < minSteps[newStart]:
                minSteps[newStart] = step + 1
                heapq.heappush(heap, (step + 1, newStart))
    return -1
```