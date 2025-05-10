Given a **non-empty** array of integers `nums`, every element appears _twice_ except for one. Find that single one.

```python
def singleNumber(self, nums: List[int]) -> int:
    ans = 0
    for num in nums:
        ans ^= num
    return ans
```

> [!note]
> Xor of any two num gives the difference of bit as 1 and same bit as 0
>  $x \oplus x = 0$ and $x \oplus 0 = x$

