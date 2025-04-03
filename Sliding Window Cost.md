# 💵 Problem Sliding Window Cost

---

## 📋 Problem Description

Given an array of `n` integers and a window size `k`, compute the **cost** of each window, where the cost is defined as the **sum of absolute differences** between each element in the window and the **median** of that window.

---

## 💻 Python Solution

```python
from sortedcontainers import SortedList

def sliding_window_cost(nums, k):
    window = SortedList()
    result = []

    for i in range(len(nums)):
        window.add(nums[i])
        if i >= k:
            window.remove(nums[i - k])

        if i >= k - 1:
            mid = k // 2
            median = window[mid] if k % 2 == 1 else window[mid - 1]
            cost = sum(abs(x - median) for x in window)
            result.append(cost)

    return result

if __name__ == "__main__":
    n, k = map(int, input().split())
    nums = list(map(int, input().split()))
    output = sliding_window_cost(nums, k)
    for val in output:
        print(val)
```
