# 🧮 Problem 001: Increasing Array

## 📄 Problem Description

You are given an array of n integers. You want to modify the array so that it is increasing, i.e., every element is at least as large as the previous element.
On each move, you may increase the value of any element by one. What is the minimum number of moves required?

## 💻 Solutions

<summary><strong>🐍 Python</strong></summary>

```python
def minimum_moves_to_increasing(arr):
    moves = 0
    for i in range(1, len(arr)):
        if arr[i] < arr[i - 1]:
            moves += arr[i - 1] - arr[i]
            arr[i] = arr[i - 1]
    return moves

if __name__ == "__main__":
    n = int(input())
    arr = list(map(int, input().split()))
    print(minimum_moves_to_increasing(arr))
```
<summary>Click to view C++ solution</summary>

```cpp
#include <iostream>
#include <vector>
using namespace std;

int main() {
    int n;
    cin >> n;
    vector<long long> arr(n);
    for (int i = 0; i < n; ++i)
        cin >> arr[i];

    long long moves = 0;
    for (int i = 1; i < n; ++i) {
        if (arr[i] < arr[i - 1]) {
            moves += arr[i - 1] - arr[i];
            arr[i] = arr[i - 1];
        }
    }
    cout << moves << endl;
    return 0;
}
```

