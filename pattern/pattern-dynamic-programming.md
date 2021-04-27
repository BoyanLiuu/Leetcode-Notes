# 16. Dynamic Programming

## Summary:

Many recursive algorithms are brute-force in nature, i.e., they explore the entire solution space, which is exponential in terms of the problem size. Often, the recursive algorithms re-evaluate the same sub-problem over and over, which is inefficient. Dynamic programming is a technique that might be used to provide more efficient solutions to such problems

Dynamic programming is a technique to provide an efficient solution to a problem by avoiding recomputations. It only works on problems that have repeating subproblems







## Easy:

### 0/1 Knapsack:

Given the weights and profits of ‘N’ items, we are asked to put these items in a knapsack that has a capacity ‘C’. The goal is to get the maximum profit from the items in the knapsack. Each item can only be selected once, as we don’t have multiple quantities of any item.

Let’s take Merry’s example, who wants to carry some fruits in the knapsack to get maximum profit. Here are the weights and profits of the fruits:

**Items:** { Apple, Orange, Banana, Melon }  
**Weights:** { 2, 3, 1, 4 }  
**Profits:** { 4, 5, 3, 7 }  
**Knapsack capacity:** 5

Let’s try to put different combinations of fruits in the knapsack, such that their total weight is not more than 5:

Apple + Orange \(total weight 5\) =&gt; 9 profit  
Apple + Banana \(total weight 3\) =&gt; 7 profit  
Orange + Banana \(total weight 4\) =&gt; 8 profit  
Banana + Melon \(total weight 5\) =&gt; 10 profit

This shows that **Banana + Melon** is the best combination, as it gives us the maximum profit and the total weight does not exceed the capacity.

**Question:** Given two integer arrays to represent weights and profits of ‘N’ items, we need to find a subset of these items which will give us maximum profit such that their cumulative weight is not more than a given number ‘C’. Each item can only be selected once, which means either we put an item in the knapsack or skip it.

**Answer：**

* Brutal force: try all the kinds of combination, time Complexity: O\(2^N\)

```text
  public int solveKnapsack(int[] profits, int[] weights, int capacity) {
    return this.knapsackRecursive(profits, weights, capacity, 0);
  }

  private int knapsackRecursive(int[] profits, int[] weights, int capacity, int currentIndex) {
    // base checks
    if (capacity <= 0 || currentIndex >= profits.length)
      return 0;

    // recursive call after choosing the element at the currentIndex
    // if the weight of the element at currentIndex exceeds the capacity, we shouldn't process this
    int profit1 = 0;
    if( weights[currentIndex] <= capacity )
        profit1 = profits[currentIndex] + knapsackRecursive(profits, weights,
                capacity - weights[currentIndex], currentIndex + 1);

    // recursive call after excluding the element at the currentIndex
    int profit2 = knapsackRecursive(profits, weights, capacity, currentIndex + 1);

    return Math.max(profit1, profit2);
  }
```

* **DP:**
  * Using Top Down Dynamic Programming with memorization: 
    * We can use memorization to overcome the overlapping sub-problems. To reiterate, memorization is when we store the results of all the previously solved sub-problems and return the results from memory if we encounter a problem that has already been solved.
    * Since we have two changing values \(capacity and currentIndex\) in our recursive function knapsackRecursive\(\), we can use a two-dimensional array to store the results of all the solved sub-problems. As mentioned above, we need to store results for every sub-array \(i.e., for every possible index ‘i’\) and for every possible capacity ‘c’.
    * Time complexity:  Since our memorization array stores the results for all the subproblems, we can conclude that we will not have more than N\*C subproblems so it is O\(N\* C\)
    * Space-complexity: O\(N\*C +N\) 

```text
  public int solveKnapsack(int[] profits, int[] weights, int capacity) {
    Integer[][] dp = new Integer[profits.length][capacity + 1];
    return this.knapsackRecursive(dp, profits, weights, capacity, 0);
  }

  private int knapsackRecursive(Integer[][] dp, int[] profits, int[] weights, int capacity,
      int currentIndex) {

    // base checks
    if (capacity <= 0 || currentIndex >= profits.length)
      return 0;

    // if we have already solved a similar problem, return the result from memory
    if(dp[currentIndex][capacity] != null)
      return dp[currentIndex][capacity];

    // recursive call after choosing the element at the currentIndex
    // if the weight of the element at currentIndex exceeds the capacity, we shouldn't process this
    int profit1 = 0;
    if( weights[currentIndex] <= capacity )
        profit1 = profits[currentIndex] + knapsackRecursive(dp, profits, weights,
                capacity - weights[currentIndex], currentIndex + 1);

    // recursive call after excluding the element at the currentIndex
    int profit2 = knapsackRecursive(dp, profits, weights, capacity, currentIndex + 1);

    dp[currentIndex][capacity] = Math.max(profit1, profit2);
    return dp[currentIndex][capacity];
  }
```

* 






## Medium:



## Hard:



## The problem I  struggle with:

* * * 




* [139. Word Break](https://leetcode.com/problems/word-break/)



