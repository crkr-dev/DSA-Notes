Best Time to Buy and Sell Stock

1. Problem Statement

You are given an array prices where prices[i] is the price of a given stock on the ith day.

You want to maximize your profit by choosing:

* One day to buy the stock.
* A different future day to sell the stock.

Return the maximum profit you can achieve.

If no profit can be achieved, return 0.

---

2. Problem Explanation

We need to buy the stock at a lower price and sell it later at a higher price.

The selling day must always come after the buying day.

Example

Input:

prices = [7,1,5,3,6,4]

Output:

5

Explanation:

Buy at price 1

Sell at price 6

Profit = 6 - 1 = 5

---

3. Intuition (Brute Force)

Try every possible buy day.

For each buy day:

Try every possible sell day after it.

Calculate profit:

sellPrice - buyPrice

Keep track of the maximum profit.

Example

prices = [7,1,5,3,6,4]

Buy at 7:

Profits:

1-7 = -6

5-7 = -2

3-7 = -4

6-7 = -1

4-7 = -3

---

Buy at 1:

Profits:

5-1 = 4

3-1 = 2

6-1 = 5

4-1 = 3

Maximum Profit = 5

Complexity

Time Complexity : O(n²)

Space Complexity : O(1)

---

4. Better Approach

Observation:

For every day, we only need to know:

* The minimum price seen so far.
* The profit if we sell today.

Profit:

currentPrice - minimumPriceSoFar

Update the answer whenever we get a better profit.

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

5. Optimal Approach

Pattern:

Array Traversal

Running Minimum

Maximum Profit

Observation:

While traversing:

* Keep track of the minimum stock price seen so far.
* Calculate profit for the current day.
* Update maximum profit.

Example

prices = [7,1,5,3,6,4]

Initial:

minPrice = 7

maxProfit = 0

---

Price = 1

minPrice = 1

---

Price = 5

Profit = 5 - 1 = 4

maxProfit = 4

---

Price = 3

Profit = 3 - 1 = 2

maxProfit = 4

---

Price = 6

Profit = 6 - 1 = 5

maxProfit = 5

---

Price = 4

Profit = 4 - 1 = 3

maxProfit = 5

Answer = 5

Complexity

Time Complexity : O(n)

Space Complexity : O(1)

---

6. Common Mistakes

Mistake 1

Selling before buying.

The selling day must always come after the buying day.

---

Mistake 2

Updating minimum price incorrectly.

Always keep the smallest price seen so far.

---

Mistake 3

Returning a negative profit.

If no profit is possible, return 0.

---

Mistake 4

Using nested loops even after identifying the running minimum pattern.

---

7. Code

Brute Force Approach

```java
public int maxProfit(int[] prices) {

    int maxProfit = 0;

    for(int i = 0; i < prices.length; i++) {

        for(int j = i + 1; j < prices.length; j++) {

            maxProfit = Math.max(maxProfit,
                                 prices[j] - prices[i]);
        }
    }

    return maxProfit;
}
```

---

Optimal Approach

```java
public int maxProfit(int[] prices) {

    int minPrice = Integer.MAX_VALUE;
    int maxProfit = 0;

    for(int price : prices) {

        minPrice = Math.min(minPrice, price);

        int profit = price - minPrice;

        maxProfit = Math.max(maxProfit, profit);
    }

    return maxProfit;
}
```

---

8. Pattern Recognition

Pattern:

Array Traversal

Running Minimum

Maximum Profit

Observation:

For every day:

Find the minimum buying price before it.

Calculate the profit if sold today.

Trigger Words:

* Buy and Sell
* Maximum Profit
* Stock Price
* Best Profit
* One Transaction

Think:

Maintain Minimum So Far

Calculate Current Profit

Track Maximum Profit

---

9. Problem Link

LeetCode 121 - Best Time to Buy and Sell Stock

https://leetcode.com/problems/best-time-to-buy-and-sell-stock/

---

10. YouTube Link

YouTube Video:

(Paste your YouTube video link here)
