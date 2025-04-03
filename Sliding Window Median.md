# 🪟 Problem Sliding Window Median

---

## 📋 Problem Description

Given an array of `n` integers and an integer `k`, compute the median of every contiguous subarray (window) of size `k`.

The median is the middle element after sorting the elements in the window. If the size of the window is even, the median is the average of the two middle elements.

---

## 💻 Python Solution

```python
from sortedcontainers import SortedList

def sliding_window_median(nums, k):
    window = SortedList()
    medians = []

    for i in range(len(nums)):
        window.add(nums[i])
        if i >= k:
            window.remove(nums[i - k])

        if i >= k - 1:
            mid = k // 2
            if k % 2 == 0:
                medians.append((window[mid - 1] + window[mid]) / 2)
            else:
                medians.append(window[mid])

    return medians

if __name__ == "__main__":
    n, k = map(int, input().split())
    nums = list(map(int, input().split()))
    result = sliding_window_median(nums, k)
    for val in result:
        print(val)
```
