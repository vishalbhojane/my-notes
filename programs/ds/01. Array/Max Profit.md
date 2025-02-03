Create a function `maxProfit` that takes an array of stock prices and returns the maximum profit achievable by buying and selling a stock once. The function should:
1. Handle arrays of any length, including empty arrays.
2. Work with non-negative integers representing stock prices.
3. Ensure that buying occurs before selling.
4. Return 0 if no profit can be made or if the array is empty.
## Solution

```javascript
function maxProfit(prices) {
    let minPrice = Infinity;
    let maxProfit = 0;

    for (let price of prices) {
        if (price < minPrice) {
            minPrice = price;
        } else {
            let currentProfit = price - minPrice;
            if (currentProfit > maxProfit) {
                maxProfit = currentProfit;
            }
        }
    }

    return maxProfit;
}
```

Core Logic:
1. Keep track of the lowest price seen so far.
2. For each price, calculate the profit if we sell at that price after buying at the lowest price seen.
3. Update the maximum profit if the current profit is higher.

Usage

```javascript
console.log(maxProfit([7, 1, 5, 3, 6, 4])); // 5
console.log(maxProfit([5, 4, 3, 2, 1])); // 0
console.log(maxProfit([2, 2, 2, 2])); // 0
console.log(maxProfit([1])); // 0
console.log(maxProfit([])); // 0
console.log(maxProfit([2, 1, 4, 5, 2, 9, 7])); // 8
console.log(maxProfit([1, 2, 3, 4, 5])); // 4
```

