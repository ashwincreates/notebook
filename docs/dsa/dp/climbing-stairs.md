You are climbing a staircase. It takes `n` steps to reach the top.

Each time you can either climb `1` or `2` steps. In how many distinct ways can you climb to the top?

##### Top Down Approach
We use recursion and keep breaking the problem in smaller cases until we reach the base case and then we calculate the answer bottom up, in different questions the way we calculate answer differs
```python
class Solution:
    def climbStairs(self, n: int) -> int:
        dp = [-1 for _ in range(n + 1)]
        def climb(n):
            if dp[n] != -1:
                return dp[n]
            if n < 0:
                return 0
            if n == 0:
                return 1
            dp[n] = climb(n - 1) + climb(n - 2)
            return dp[n]
        return climb(n)
```

##### Bottom Down Approach
We use top down approach where we declare the base case and solve for every possible state
```python
class Solution:
    def climbStairs(self, n: int) -> int:
        dp = [0 for _ in range(n + 1)]
        dp[0] = 1
        for step in range(n + 1):
            if step - 1 >= 0:
                dp[step] += dp[step - 1]
            if step - 2 >= 0:
                dp[step] += dp[step - 2]
        return dp[n]
```