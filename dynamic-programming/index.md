# Dynamic Programming
Dynamic programming is a technique to solve the recursive problems in more efficient manner. Many times in recursion we solve the sub-problems repeatedly.
In dynamic programming we store the solution of these sub-problems so that we do not have to solve them again, this is called **Memoization**.

Let's start with an example: finding the N-th Fibonacci number.
`Fibonacci(10) = Fibonacci(9) + Fibonacci(8)` with `Fibonacci(0) = 0` and `Fibonacci(1) = 1`.

A simple way to implement is via recursion to match the mathematical definition:
```java
class Fibonacci {
  static int fibonacci(int n) {
    if (n <= 1) { return n; }
    return fibonacci(n - 1) + fibonacci(n - 2);
  }
}
```

There's going to be a lot of duplicated work there. We can avoid it by starting from 0 and working our way up to N, storing the Fibonacci
numbers calculated so far:
```java
class Fibonacci {
  static int fibonacci(int n) {
    if (n == 0) { return 0; }
    int dp[] = new int[n +1];
    
    dp[0] = 0;
    dp[1] = 1;
    
    for (int i=2; i <= n; i++) {
      dp[i] = dp[i-1] + dp[i-2];
    }
    
    return dp[n];  
  }
}
```

## Approaches
Dynamic programming problems can often be tackled one of two ways:
* **Bottom-up.** More/less work your way up from 0 to N, storing the results along the way. This can make the solution fairly straightforward to implement.
* **Top-down.** Break the problem into sub-problems and solve them as needed and store the solution. This can often be more optimal by only solving the
sub-problems needed rather than all subproblems from 0 to N.

## Coin Change
The problem below was superbly explained at https://www.youtube.com/watch?v=jgiZlGzXMBw and the [Coin Change problem itself is found on
LeetCode](https://leetcode.com/problems/coin-change/).

> You are given coins of different denominations and a total amount of money *amount*.
> We are looking for an algorithm to compute the fewest number of coins that you need to make up that amount.
> If that amount of money cannot be made up by any combination of the coins, return `-1`.

> **NOTE:** the problem is not asking what these coins are, just how many coins are needed in total.

Here's a TypeScript dynamic programming implementation of it. 
```typescript
function coinChange(coins: number[], amount: number): number {
  const dp = new Array(amount +1);
  dp.fill(amount +1);
  dp[0] = 0;
  
  for (let i=1; i <= amount; i++) {
    for (let coin of coins) {
      if (coin <= i) {
        dp[i] = Math.min(dp[i], 1 + dp[i - coin]);
      }
    }
  }
  
  return dp[amount] === amount +1 ? -1 : dp[amount];
};
```
