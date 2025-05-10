Given an array of integers `nums` and an integer `target`, return _indices of the two numbers such that they add up to `target`_.

```python
def twoSum(self, nums: List[int], target: int) -> List[int]:
    pre = {}
    for i in range(len(nums)):
        num = nums[i]
        if target - num in pre:
            return [pre[target - num], i]
        if num not in pre:
            pre[num] = i
    return
```
###### Questions
1. https://leetcode.com/problems/two-sum/