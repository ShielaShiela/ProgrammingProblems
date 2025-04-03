# 📆 Problem 007: Tasks and Deadlines

🔗 **Problem Link**: [CSES - Tasks and Deadlines](https://cses.fi/problemset/task/1630/)

---

## 📋 Problem Description

There are `n` tasks, each with a **duration** and a **deadline**. You may process the tasks in any order, but **only one task at a time** (no overlap).

Your goal is to **maximize the total reward**, where the reward for a task is:


---

## 💻 Python Solution

```python
n = int(input())
tasks = [tuple(map(int, input().split())) for _ in range(n)]

# Sort tasks by duration (greedy)
tasks.sort()

current_time = 0
reward = 0

for duration, deadline in tasks:
    current_time += duration
    reward += deadline - current_time

print(reward)
```
