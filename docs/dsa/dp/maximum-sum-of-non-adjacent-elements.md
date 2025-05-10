You are a professional robber planning to rob houses along a street. Each house has a certain amount of money stashed, the only constraint stopping you from robbing each of them is that adjacent houses have security systems connected and **it will automatically contact the police if two adjacent houses were broken into on the same night**.

Return _the maximum amount of money you can rob tonight **without alerting the police**_.

##### Top Down Approach
```python
def rob(self, nums: List[int]) -> int:
    dp = [-1 for _ in range(len(nums))]
    def go(house):
        if house >= len(nums):
            return 0
        if dp[house] != -1:
            return dp[house]
        dp[house] = max(nums[house] + go(house + 2), go(house + 1))
        return dp[house]
    return go(0)  
```

##### Bottom Up Approach
```python
def rob(self, nums: List[int]) -> int:
    dp = [0 for _ in range(len(nums))]
    if len(nums) == 1:
        return nums[0]
    dp[0] = nums[0]
    dp[1] = max(nums[0], nums[1])
    for house in range(2, len(nums)):
        dp[house] = max(nums[house] + dp[house - 2], dp[house - 1])
    return dp[len(nums) - 1]
```