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
import bisect

def concertTickets(price , pay):

    # Create a multiset to store the prices of all tickets
    maxPrice = sorted(price)

    # Create an array answer to store the answer for each customer
    ans = [0 for j in range(len(pay))]

    # Now iterate through every customer
    for i in range(len(pay)):
    
        temp = pay[i]

        # Find the upper bound of maximum price offered by customer in the multiset
        itr = bisect.bisect(maxPrice,temp)

        # If it points to the beginning, that means no ticket is available for the customer
        # Otherwise, decrement the iterator and get the value out of it and then erase that value from the multiset
        if (itr == 0):
            ans[i] = -1
        else:
            itr -= 1
            ans[i] = maxPrice[itr]
            maxPrice.remove(ans[i])
        
    # Return the array answer
    return ans

def main():
    # Example ticket prices and customer offers
    ticket_prices = [5, 3, 7, 8, 5]
    customer_offers = [4, 8, 3]

    # Get the result from the concertTickets function
    results = concertTickets(ticket_prices, customer_offers)

    # Print the results
    print("Ticket prices assigned to customers:", results)

if __name__ == "__main__":
    main()

```
