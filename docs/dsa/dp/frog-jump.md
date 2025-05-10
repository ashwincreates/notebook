Geek wants to climb from the 0th stair to the $(n-1)_{th} stair$. At a time the Geek can climb either one or two steps. A height array is also given. Whenever the geek jumps from stair i to stair j, the energy consumed in the jump is $abs(height_i - height_j)$, where abs() means the absolute difference. return the minimum energy that can be used by the Geek to jump from stair 0 to stair N-1.

##### Top Down Approach
```python
def minimumEnergy(self, height, l):
    dp=[-1 for i in range(n+1)]
    def energy(step: int):
        if dp[step] != -1:
            return dp[step]
        if step == n - 1:
            return 0
        if step >= n:
            return math.inf
        stepOne = math.inf
        stepTwo= math.inf
        if step + 1 < n:
            stepOne = abs(height[step] - height[step + 1]) + energy(step + 1)
        if step + 2 < n:
            stepTwo = abs(height[step] - height[step + 2]) + energy(step + 2)
        dp[n] = min(stepOne, stepTwo)
        return dp[n]

    energy(0)
    return dp[n]
```

##### Bottom Up Approach
```python
def minimumEnergy(self, height, n):
    dp=[math.inf for i in range(n)]
    if len(height) == 1:
        return 0
    dp[0] = 0
    dp[1] = abs(height[0] - height[1])
    for stair in range(2, n):
        stepOne = abs(height[stair - 1] - height[stair])
        stepTwo = abs(height[stair - 2] - height[stair])
        dp[stair] = min(dp[stair - 1] + stepOne, dp[stair - 2] + stepTwo)
    return dp[n - 1]
```