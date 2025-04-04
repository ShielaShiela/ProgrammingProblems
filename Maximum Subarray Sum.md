# 💰 Problem Maximum Subarray Sum

🔗 **Problem Link**: [CSES - Maximum Subarray Sum](https://cses.fi/problemset/task/1643/)

---

## 📋 Problem Description

Given an array of `n` integers, your task is to find the **maximum sum** of values in a **contiguous, nonempty subarray**.

---

## 💻 Python Solution

```python
def max_subarray_sum(arr):
    max_sum = current_sum = arr[0]
    for x in arr[1:]:
        current_sum = max(x, current_sum + x)
        max_sum = max(max_sum, current_sum)
    return max_sum

if __name__ == "__main__":
    n = int(input())
    arr = list(map(int, input().split()))
    print(max_subarray_sum(arr))
```
## 💻 C++ Solution

```cpp
#include <iostream>
#include <vector>
#include <algorithm>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<long long> arr(n);
    for (int i = 0; i < n; ++i)
        cin >> arr[i];

    long long max_sum = arr[0], current_sum = arr[0];
    for (int i = 1; i < n; ++i) {
        current_sum = max(arr[i], current_sum + arr[i]);
        max_sum = max(max_sum, current_sum);
    }

    cout << max_sum << endl;
    return 0;
}
```
