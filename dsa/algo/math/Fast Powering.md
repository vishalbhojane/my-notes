**The power of a number** says how many times to use the number in a multiplication.

## Naive Algorithm Complexity

How to find `a` raised to the power `b`?

We multiply `a` to itself, `b` times. That
is, `a^b = a * a * a * ... * a` (`b` occurrences of `a`).

This operation will take `O(n)` time since we need to do multiplication operation
exactly `n` times.

## Fast Power Algorithm

Can we do better than naive algorithm does? Yes we may solve the task of
powering in `O(log(n))` time.

The algorithm uses divide and conquer approach to compute power. Currently the
algorithm work for two positive integers `X` and `Y`.

The idea behind the algorithm is based on the fact that:

For **even** `Y`:

```text
X^Y = X^(Y/2) * X^(Y/2)
```

For **odd** `Y`:

```text
X^Y = X^(Y//2) * X^(Y//2) * X
where Y//2 is result of division of Y by 2 without reminder.
```

**For example**

```text
2^4 = (2 * 2) * (2 * 2) = (2^2) * (2^2)
```

```text
2^5 = (2 * 2) * (2 * 2) * 2 = (2^2) * (2^2) * (2)
```

**Time Complexity**

Since each iteration we split the power by half then we will call function
recursively `log(n)` times. This the time complexity of the algorithm is reduced to:

```text
O(log(n))
```

```js
/**
 * Fast Powering Algorithm.
 * Recursive implementation to compute power.
 *
 * Complexity: log(n)
 *
 * @param {number} base - Number that will be raised to the power.
 * @param {number} power - The power that number will be raised to.
 * @return {number}
 */
export default function fastPowering(base, power) {
  if (power === 0) {
    // Anything that is raised to the power of zero is 1.
    return 1;
  }

  if (power % 2 === 0) {
    // If the power is even...
    // we may recursively redefine the result via twice smaller powers:
    // x^8 = x^4 * x^4.
    const multiplier = fastPowering(base, power / 2);
    return multiplier * multiplier;
  }

  // If the power is odd...
  // we may recursively redefine the result via twice smaller powers:
  // x^9 = x^4 * x^4 * x.
  const multiplier = fastPowering(base, Math.floor(power / 2));
  return multiplier * multiplier * base;
}
```
