---
title: "Best Time to Buy and Sell Stock ( Leetcode121)"
datePublished: Sun Aug 25 2024 10:00:56 GMT+0000 (Coordinated Universal Time)
cuid: cm09efs4j000v08l1gco9ct3o
slug: best-time-to-buy-and-sell-stock-leetcode121
tags: javascript, dsa, leetcode, sliding-window

---

You are given an array where each element represents the price of a given stock on a day. You need to find the maximum profit you can achieve by buying on one day and selling on another later day. If no profit is possible, return 0.

### Approach:

The sliding window technique isn't directly used here, but the problem can be approached with a similar concept—by keeping track of the minimum price seen so far and calculating the potential profit for each price in the array.

### Steps:

1. Initialize two variables:
    
    * `minPrice` to store the minimum price encountered so far (initialized to a very large value).
        
    * `maxProfit` to store the maximum profit encountered so far (initialized to 0).
        
2. Iterate through the array of prices:
    
    * Update `minPrice` if the current price is lower than the `minPrice`.
        
    * Calculate the profit by subtracting the `minPrice` from the current price.
        
    * Update `maxProfit` if the calculated profit is greater than the current `maxProfit`.
        
3. Return `maxProfit`.
    

### Code

```javascript
const maxProfit = (prices) => {
  let maxProfit = 0;
  let minPrice = Infinity;
  for (let i = 0; i < prices.length; i++) {
    if (prices[i] < minPrice) {
      minPrice = prices[i];
    } else {
      let profit = prices[i] - minPrice;
      if (profit > maxProfit) {
        maxProfit = profit;
      }
    }
  }
  return maxProfit;
};

console.log(maxProfit([7, 1, 5, 3, 6, 4])); // 5
```