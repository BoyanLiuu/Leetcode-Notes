# 9.Subsets

## Summary:

This pattern aimed at solving problems about permutations and combinations of a given set of elements using BFS approach.



## Easy:



## Medium:

### [78. Subsets](https://leetcode.com/problems/subsets/)

### [90. Subsets II](https://leetcode.com/problems/subsets-ii/)

![](../.gitbook/assets/image%20%2817%29.png)

```text
public static List<List<Integer>> findSubsets(int[] nums) {
    List<List<Integer>> subsets = new ArrayList<>();
    // start by adding the empty subset
    subsets.add(new ArrayList<>());
    for (int currentNumber : nums) {
      // we will take all existing subsets and insert the current number in them to create new subsets
      int n = subsets.size();
      for (int i = 0; i < n; i++) {
        // create a new subset from the existing subset and insert the current element to it
        List<Integer> set = new ArrayList<>(subsets.get(i));
        set.add(currentNumber);
        subsets.add(set);
      }
    }
    return subsets;
  }
```

### [46. Permutations](https://leetcode.com/problems/permutations/)

![](../.gitbook/assets/image%20%2816%29.png)

```text
public static List<List<Integer>> findPermutations(int[] nums) {
    List<List<Integer>> result = new ArrayList<>();
    Queue<List<Integer>> permutations = new LinkedList<>();
    permutations.add(new ArrayList<>());
    for (int currentNumber : nums) {
      // we will take all existing permutations and add the current number to create new permutations
      int n = permutations.size();
      for (int i = 0; i < n; i++) {
        List<Integer> oldPermutation = permutations.poll();
        // create a new permutation by adding the current number at every position
        for (int j = 0; j <= oldPermutation.size(); j++) {
          List<Integer> newPermutation = new ArrayList<Integer>(oldPermutation);
          newPermutation.add(j, currentNumber);
          if (newPermutation.size() == nums.length)
            result.add(newPermutation);
          else
            permutations.add(newPermutation);
        }
      }
    }
    return result;
  }
```

### [784. Letter Case Permutation](https://leetcode.com/problems/letter-case-permutation/)

### [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)

### [320. Generalized Abbreviation](https://leetcode.com/problems/generalized-abbreviation/)🔓 

### [241. Different Ways to Add Parentheses](https://leetcode.com/problems/different-ways-to-add-parentheses/)

### [96. Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/)

### [95. Unique Binary Search Trees II](https://leetcode.com/problems/unique-binary-search-trees-ii/)

## Hard:



## The problem I  struggle with:

* * * 




