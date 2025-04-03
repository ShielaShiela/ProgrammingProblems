# 🎟️ Problem Concert Tickets

🔗 **Problem Link**: [CSES - Concert Tickets](https://cses.fi/problemset/task/1091/)

---

## 📋 Problem Description

There are `n` concert tickets available, each with a certain price. `m` customers arrive, one after another. Each customer is willing to pay at most `x` for a ticket.

Your task is to assign each customer a ticket with the **maximum possible price** (≤ their max budget) and remove that ticket from the pool.  
If no suitable ticket is available, print `-1`.

---
## 💻 Python Solution

```python
from bisect import bisect_right
from collections import deque

def concert_tickets(prices, customers):
    prices.sort()
    prices = deque(prices)
    result = []

    for x in customers:
        # Binary search to find the rightmost ticket <= x
        idx = bisect_right(prices, x) - 1
        if idx >= 0:
            result.append(prices[idx])
            del prices[idx]  # Remove the sold ticket
        else:
            result.append(-1)
    return result

if __name__ == "__main__":
    n, m = map(int, input().split())
    prices = list(map(int, input().split()))
    customers = list(map(int, input().split()))

    # Using a list to simulate a multiset is not efficient for large inputs.
    # It's better to use `SortedList` from `sortedcontainers`:
    from sortedcontainers import SortedList
    tickets = SortedList(prices)

    for x in customers:
        i = tickets.bisect_right(x) - 1
        if i >= 0:
            print(tickets[i])
            tickets.pop(i)
        else:
            print(-1)
```
