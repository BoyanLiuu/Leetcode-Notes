# 9.Subsets

## Summary:

This pattern aimed at solving problems about permutations and combinations of a given set of elements using BFS approach.

* Use deep copy when adding list

```text
result.add(new ArrayList<>(curList));
```



## Easy:



## Medium:

### [90. Subsets II](https://leetcode.com/problems/subsets-ii/)

### [78. Subsets](https://leetcode.com/problems/subsets/)

* 教程说是使用BFS但我认为是使用DFS，It add all the way to 1,5,3 and then backtrack and add \[1,3 \], \[5\],\[5,3\],\[3\]
* Generate all the subset is 2^N, and each time we need to use deep copy the list which cost O\(N\), the total time complexity is N\*2^N
* Space Complexity  is  we will have a total of O\(2^N\)subsets, and each subset can take up to O\(N\) space, therefore, the space complexity of our algorithm will be O\(N\*2^N\)

![](../.gitbook/assets/image%20%2818%29.png)

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




