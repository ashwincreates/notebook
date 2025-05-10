Given an array **`arr[]`** containing integers and an integer **`k`**, your task is to find the length of the longest subarray where the sum of its elements is equal to the given value **`k`**. If there is no subarray with sum equal to **`k`**, return **`0`**.

```python
def longestSubarray(self, arr, k):  
    curr = 0
    prefix = { 0 : -1 }
    ans = 0
    for i in range(len(arr)):
        curr += arr[i]
        if curr - k in prefix: # check if prefix available
            ans = max(ans, i - prefix[curr - k])
        if curr not in prefix:
            prefix[curr] = i  # store prefix
    return ans
```

This is based on _prefix sum_. ==One can represent a subarray as difference of 2 prefix subarrays==. We store the prefix sum and check for it in the loop
###### Questions
1. https://practice.geeksforgeeks.org/problems/longest-sub-array-with-sum-k0809/1?utm_source=youtube&utm_medium=collab_striver_ytdescription&utm_campaign=longest-sub-array-with-sum-k