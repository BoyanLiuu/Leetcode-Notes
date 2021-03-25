# 9.Subsets

## Summary:\(Not very familiar\)

This pattern aimed at solving problems about permutations and combinations of a given set of elements using BFS approach.

* 2^N permutation
* N！for all the combination of subset
* Use deep copy when adding list

```text
result.add(new ArrayList<>(curList));
```



## Easy:



## Medium:

### [90. Subsets II](https://leetcode.com/problems/subsets-ii/)

* Follow subset pattern, First we sort the array
* Follow the same BFS approach but whenever we are about to process a duplicate \(i.e., when the current and the previous numbers are same\), _**instead of adding the current number \(which is a duplicate\) to all the existing subsets, only add it to the subsets which were created in the previous step.**_

![](../.gitbook/assets/image%20%2820%29.png)

```text
    public List<List<Integer>> subsetsWithDup(int[] nums) {
    // sort the numbers to handle duplicates
    Arrays.sort(nums);
    List<List<Integer>> subsets = new ArrayList<>();
    subsets.add(new ArrayList<>());
    int startIndex = 0, endIndex = 0;
    for (int i = 0; i < nums.length; i++) {
        startIndex = 0;
        // if current and the previous elements are same, create new subsets only from the subsets 
        // added in the previous step
        if (i > 0 && nums[i] == nums[i - 1])
            startIndex = endIndex + 1;
        
        
        endIndex = subsets.size() - 1;
        for (int j = startIndex; j <= endIndex; j++) {
            // create a new subset from the existing subset and add the current element to it
            List<Integer> set = new ArrayList<>(subsets.get(j));
            set.add(nums[i]);
            subsets.add(set);
        }
    }
    return subsets;
}
```

To handle this instead of adding cur item to all the existing subsets, we only add it to the new subsets which were created in the previous step:

### [78. Subsets](https://leetcode.com/problems/subsets/)

* 教程说是使用BFS但我认为是使用DFS，It add all the way to 1,5,3 and then backtrack and add \[1,3 \], \[5\],\[5,3\],\[3\]
* Generate all the subset is 2^N, and each time we need to use deep copy the list which cost O\(N\), the total time complexity is N\*2^N
* Space Complexity  is  we will have a total of O\(2^N\)subsets, and each subset can take up to O\(N\) space, therefore, the space complexity of our algorithm will be O\(N\*2^N\)

![](../.gitbook/assets/image%20%2818%29.png)

![](../.gitbook/assets/image%20%2817%29.png)

```text

//This solution looks like above graph
    public List<List<Integer>> subsets(int[] nums) {
        List<List<Integer>> subsets = new ArrayList<>();
        subsets.add(new ArrayList<>());
        int startIndex = 0, endIndex = 0;
        for (int i = 0; i < nums.length; i++) {
          startIndex = 0;
          endIndex = subsets.size() - 1;
          for (int j = startIndex; j <= endIndex; j++) {
            // create a new subset from the existing subset and add the current element to it
            List<Integer> set = new ArrayList<>(subsets.get(j));
            set.add(nums[i]);
            subsets.add(set);
          }
        }
        return subsets;
    }

//This solution does not looks like above graph
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

*  we add current item in all the index of current list

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

* Same idea as subset

### [22. Generate Parentheses](https://leetcode.com/problems/generate-parentheses/)

* Follow permutations pattern46
* Two rules:
  * We can’t add more than ‘N’ open parenthesis.
  * To keep the parentheses balanced, we can add a close parenthesis \) only when we have already added enough open parenthesis \(. For this, we can keep a count of open and close parenthesis with every combination.
* Algorithm: N=3
  * Start with an empty combination: “”,
  * At every step, let’s take all combinations of the previous step and add \( or \) keeping the above-mentioned two rules in mind.
  * For the empty combination, we can add \( since the count of open parenthesis will be less than ‘N’. We can’t add \) as we don’t have an equivalent open parenthesis, so our list of combinations will now be: “\(”
  * For the next iteration, let’s take all combinations of the previous set. For “\(” we can add another \( to it since the count of open parenthesis will be less than ‘N’. We can also add \) as we do have an equivalent open parenthesis, so our list of combinations will be: “\(\(”, “\(\)”
  * In the next iteration, for the first combination “\(\(”, we can add another \( to it as the count of open parenthesis will be less than ‘N’, we can also add \) as we do have an equivalent open parenthesis. This gives us two new combinations: “\(\(\(” and “\(\(\)”. For the second combination “\(\)”, we can add another \( to it since the count of open parenthesis will be less than ‘N’. We can’t add \) as we don’t have an equivalent open parenthesis, so our list of combinations will be: “\(\(\(”, “\(\(\)”, \(\)\("
  * Following the same approach, next we will get the following list of combinations: “\(\(\(\)”, “\(\(\)\(”, “\(\(\)\)”, “\(\)\(\(”, “\(\)\(\)”
  * Next we will get: “\(\(\(\)\)”, “\(\(\)\(\)”, “\(\(\)\)\(”, “\(\)\(\(\)”, “\(\)\(\)\(”
  * Finally, we will have the following combinations of balanced parentheses: “\(\(\(\)\)\)”, “\(\(\)\(\)\)”, “\(\(\)\)\(\)”, “\(\)\(\(\)\)”, “\(\)\(\)\(\)”

![](../.gitbook/assets/image%20%2821%29.png)

### [320. Generalized Abbreviation](https://leetcode.com/problems/generalized-abbreviation/)🔓 

* This can follow Blanaced Parentheses  question
* **At each step we have two option:**
  * Abbreviate the current character or
  * Add the current character to the output and skip abbreviation
* Algorithm: BAT

  * Start with an empty word: “”
  * At every step, we will take all the combinations from the previous step and apply the two abbreviation rules to the next character.
  * Take the empty word from the previous step and add the first character to it. We can either abbreviate the character or add it \(by skipping abbreviation\). This gives us two new words: \_, B.
  * and so on

![](../.gitbook/assets/image%20%2822%29.png)

### [241. Different Ways to Add Parentheses](https://leetcode.com/problems/different-ways-to-add-parentheses/)

* This question follow  question 22 , 
* Algorithm: 1 +2 \*3
  * We can iterate through the expression character-by-character.
  * we can break the expression into two halves whenever we get an operator \(+, -, \*\).
    * Simulate adding \(\) at this character
  * The two parts can be calculated by recursively calling the function.
  * Once we have the evaluation results from the left and right halves, we can combine them to produce all results.

### [96. Unique Binary Search Trees](https://leetcode.com/problems/unique-binary-search-trees/)

### [95. Unique Binary Search Trees II](https://leetcode.com/problems/unique-binary-search-trees-ii/)

## Hard:



## The problem I  struggle with:

* 90
* 78
* 全部都不会。。。 
* 784 略微写出来一点了





