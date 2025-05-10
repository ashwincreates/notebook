There is an array $arr$ of heights of stone and Geek is standing at the first stone and can jump to one of the following: Stone i+1, i+2, ... i+k stone, where k is the maximum number of steps that can be jumped and cost will be $|h_i-h_j|$ is incurred, where j is the stone to land on. Find the minimum possible total cost incurred before the Geek reaches the last stone.

##### Top Down Approach
```python
def minimizeCost(self, k, arr):
    dp = [-1 for _ in range(len(arr))]
    def min_jump(stone):
        if dp[stone] != -1:
            return dp[stone]
        if stone >= len(arr):
            return math.inf
        if stone == len(arr) - 1:
            return 0
        
        min_step = math.inf
        for i in range(1, k + 1):
            if stone + i < len(arr):
                min_step = min(min_step, abs(arr[stone] - arr[stone + i]) + min_jump(stone + i))
        dp[stone] = min_step
        return min_step
    return min_jump(0)
```

##### Top Down Approach
```python
def minimizeCost(self, k, arr):
    dp = [math.inf for i in range(len(arr))]
    if k >= len(arr):
        return abs(arr[0] - arr[-1])
    for i in range(k):
        dp[i] = abs(arr[0] - arr[i])
    for step in range(k, len(arr)):
        for i in range(1, k + 1):
            dp[step] = min(dp[step], dp[step - i] + abs(arr[step] - arr[step - i]))
    return dp[len(arr) - 1]
```