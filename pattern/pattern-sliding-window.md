# 1. Sliding Window

## Summary:

* It is usually dealing with an **`array`** or a **`linked list`** with its **`subarray`**.
* A problem can be solved by two pointers forming a range/window to help us **reduce the total cases we need to consider**, such that the corresponding **time complexity will reduce** too.
* **Rules** that holds a sliding window: 
  * TL;DR: every narrower area within the window is valid, the wider scope is invalid.
    * If a wider scope of the window is valid, the narrower scope of the window must be valid
    * If a narrower scope of the window is invalid, the wider scope of that window must be invalid
* When we finding no repeating character, we record its last index, When we finding K distinct characters, We record its occurrence.



## **Sliding window types:**

* **`Fixed Window Size (easy)`** :
  * Iteration time through n sized data structure:
    * **`(Length - K +1)`, K = window size**
  * **Start & end move at the same rate**
* **`Varied Window Size (complex)`**:
  * 🗝 Key Points:       **----------------------------------------------------**
    * Determining the **requirement of window movement** 
    * Determining **new starting/ending index**
    *  **----------------------------------------------------------------**
  * Behavior \(snail movement\)
    * Increment starting index **when exceeding** the requirement \(**shrink**\)
    * Increment ending index **when** the requirement is **not fulfilled \(expand\)**

## Easy:

### [643. Maximum Average Subarray I](https://leetcode.com/problems/maximum-average-subarray-i/) 

* 变种题目： 
  * Maximum Sum Subarray of Size K
  * [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)
* The brutal force is to calculate the sum of every 5 elements contiguous subarray of the given array and divide the sum by 5 to find the average.  O\(N\*K\)
* The inefficiency is that for any two consecutive subarrays of size ‘5’, the overlapping part \(which will contain four elements\) will be evaluated twice. There are four overlapping elements between the subarray.
* The efficient way to solve this problem would be to visualize each contiguous subarray as a sliding window of ‘5’ elements. This means that we will slide the window by one element when we move on to the next subarray. To reuse the sum from the previous subarray, we will subtract the element going out of the window and add the element now being included in the sliding window. This will save us from going through the whole subarray to find the sum and, as a result, the algorithm complexity will reduce to **O\(N\)**

![](../.gitbook/assets/image%20%282%29.png)

```text
    public double findMaxAverage(int[] nums, int k) {
        double  maxAverage = Integer.MIN_VALUE *1.0;
        int windowStart =0;
        double sum = 0;
        
        for(int windowEnd = 0;windowEnd < nums.length; windowEnd++){
            sum += nums[windowEnd];//add the element
            
            //when we reach to the limit
            if(windowEnd - windowStart + 1 == k){
                //calculate the average
                double temp =  (sum*1.0) / k;
                maxAverage =  Math.max(temp,maxAverage);
                //subtract the element going out
                sum -= nums[windowStart];
                //slide the window adhead
                windowStart ++;
            }
            
           
            
        }
        
        return maxAverage;
    }
```

### [209. Minimum Size Subarray Sum](https://leetcode.com/problems/minimum-size-subarray-sum/)

* We keep adding element till the sum &gt;= target
* We will shrink the window until the window’s sum is smaller than ‘S’ again. This is needed as we intend to find the smallest window. This shrinking will also happen in multiple steps; in each step, we will do two things:
  * Check if the current window length is the smallest so far, and if so, remember its length.
  * Subtract the first element of the window from the running sum to shrink the sliding window.

```text
 public int minSubArrayLen(int target, int[] nums) {
        int sum =0;
        int minimum = Integer.MAX_VALUE;
        
        int windowStart =0;
        
        for(int windowEnd =0; windowEnd < nums.length; windowEnd++){
            
            sum += nums[windowEnd];
            
            while(sum >= target){
                int length = windowEnd -windowStart +1;
                minimum = Math.min(length,minimum);
                sum -= nums[windowStart];
                windowStart++;
            }
            
            
        }
        return minimum == Integer.MAX_VALUE ? 0 : minimum;
        
    }
```

### [340. Longest Substring with At Most K Distinct Characters](https://leetcode.com/problems/longest-substring-with-at-most-k-distinct-characters/)

* Use hashmap to track the occurrence of each character

### [904. Fruit Into Baskets](https://leetcode.com/problems/fruit-into-baskets/)

* Same as finding the longest substring with at most 2 distinct characters

## Medium:

### [3.longest Substring Without Repeating Characters](https://leetcode.com/problems/longest-substring-without-repeating-characters/)

* We can use a HashMap to remember the **last index of each character** we have processed. Whenever we get a repeating character, we will shrink our sliding window to ensure that we always have distinct characters in the sliding window

### [424. Longest Repeating Character Replacement](https://leetcode.com/problems/longest-repeating-character-replacement/)

* We’ll iterate through the string to add one letter at a time in the window.
* We’ll also keep track of the count of the maximum repeating letter in any window \(let’s call it maxRepeatLetterCount\).
* So, at any time, we know that we can have a window that has one letter repeating maxRepeatLetterCount times; this means we should try to replace the remaining letters.
* If we have more than `k` remaining letters, we should shrink the window as we are not allowed to replace more than `k` letters.

```text
class Solution {
    public int characterReplacement(String s, int k) {
        int windowStart =0, maxLength  = 0, maxRepeatLetterCount = 0;
        HashMap<Character,Integer> map =  new HashMap<>();
        
        for(int windowEnd = 0; windowEnd< s.length(); windowEnd++){
            char rightChar = s.charAt(windowEnd);
            map.put(rightChar,map.getOrDefault(rightChar,0)+1);
            maxRepeatLetterCount =  Math.max(maxRepeatLetterCount, map.get(rightChar));
            
            // in the range,we have more than k element need to swap, then we shrink window
            if(windowEnd - windowStart -maxRepeatLetterCount +1 > k){
                char leftChar =  s.charAt(windowStart);
                map.put(leftChar, map.get(leftChar) - 1);
                windowStart ++;
                
            }
            maxLength = Math.max(maxLength,windowEnd - windowStart +1 );
            
        }
        return maxLength;
    }
}
```

### [487. Max Consecutive Ones II](https://leetcode.com/problems/max-consecutive-ones/)

* 424 with k equal to 1



### [1004. Max Consecutive Ones III](https://leetcode.com/problems/max-consecutive-ones-iii/)

* exact same idea as 424

### [1100. Find K-Length Substrings With No Repeated Characters](https://leetcode.com/problems/find-k-length-substrings-with-no-repeated-characters/)

* We need to worry about repeated character and keep track of window range
* Use hash map to record character last index 

### [1438. Longest Continuous Subarray With Absolute Diff Less Than or Equal to Limit ](https://leetcode.com/problems/longest-continuous-subarray-with-absolute-diff-less-than-or-equal-to-limit/)

### [1151. Minimum Swaps to Group All 1's Together](https://leetcode.com/problems/minimum-swaps-to-group-all-1s-together/)

### [395. Longest Substring with At Least K Repeating Characters](https://leetcode.com/problems/longest-substring-with-at-least-k-repeating-characters/)

### [1423. Maximum Points You Can Obtain from Cards](https://leetcode.com/problems/maximum-points-you-can-obtain-from-cards/)

## Hard:

### [567. Permutation in String](https://leetcode.com/problems/permutation-in-string/)

* Create a HashMap to calculate the frequencies of all characters in the pattern.
* Iterate through the string, adding one character at a time in the sliding window.
* If the character being added matches a character in the HashMap, decrement its frequency in the map. If the character frequency becomes zero, we got a complete match.
* If at any time, the number of characters matched is equal to the number of distinct characters in the pattern \(i.e., total characters in the HashMap\), we have gotten our required permutation.
* If the window size is greater than the length of the pattern, shrink the window to make it equal to the pattern’s size. At the same time, if the character going out was part of the pattern, put it back in the frequency HashMap.

```text
class Solution {
    public boolean checkInclusion(String s1, String s2) {

    int windowStart = 0, matched = 0;
    Map<Character, Integer> charFrequencyMap = new HashMap<>();
    for (char chr :  s1.toCharArray())
      charFrequencyMap.put(chr, charFrequencyMap.getOrDefault(chr, 0) + 1);

    // our goal is to match all the characters from the 'charFrequencyMap' with the current window
    // try to extend the range [windowStart, windowEnd]
    for (int windowEnd = 0; windowEnd <  s2.length(); windowEnd++) {
      char rightChar =  s2.charAt(windowEnd);
      if (charFrequencyMap.containsKey(rightChar)) {
        // decrement the frequency of the matched character
        charFrequencyMap.put(rightChar, charFrequencyMap.get(rightChar) - 1);
        if (charFrequencyMap.get(rightChar) == 0) // character is completely matched
          matched++;
      }

      if (matched == charFrequencyMap.size()) // have to use map.size() for duplicated field
        return true;
      // shrink the window by one character ,If the window size is greater than the length of the pattern
      if (windowEnd -windowStart +1 >=  s1.length()) { 
        char leftChar =  s2.charAt(windowStart++);
        if (charFrequencyMap.containsKey(leftChar)) {
          if (charFrequencyMap.get(leftChar) == 0)
            matched--; // before putting the character back, decrement the matched count
          // put the character back for matching
          charFrequencyMap.put(leftChar, charFrequencyMap.get(leftChar) + 1);
        }
      }
  }
        
        return false;
    }
}
```

### [438. Find All Anagrams in a String](https://leetcode.com/problems/find-all-anagrams-in-a-string/)

* Same idea as 567

### [76. Minimum Window Substring](https://leetcode.com/problems/minimum-window-substring/)

* Same idea as 567

### [30. Substring with Concatenation of All Words](https://leetcode.com/problems/substring-with-concatenation-of-all-words/)

* Keep the frequency of every word in a HashMap.
* Starting from every index in the string, try to match all the words.
* In each iteration, keep track of all the words that we have already seen in another HashMap.
* If a word is not found or has a higher frequency than required, we can move on to the next character in the string.
* Store the index if we have found all the words.

```text
class Solution {
    public List<Integer> findSubstring(String s, String[] words) {
        Map<String, Integer> wordFrequencyMap = new HashMap<>();
        //Keep the frequency of every word in a HashMap.
        for (String word : words)
          wordFrequencyMap.put(word, wordFrequencyMap.getOrDefault(word, 0) + 1);

        List<Integer> resultIndices = new ArrayList<Integer>();
        int wordsCount = words.length, wordLength = words[0].length();

        for (int i = 0; i <= s.length() - wordsCount * wordLength; i++) {
                //In each iteration, keep track of all the words that we have already seen in another HashMap.
              Map<String, Integer> wordsSeen = new HashMap<>();
              for (int j = 0; j < wordsCount; j++) {
                int nextWordIndex = i + j * wordLength;
                // get the next word from the string
                String word = s.substring(nextWordIndex, nextWordIndex + wordLength);
                if (!wordFrequencyMap.containsKey(word)) // break if we don't need this word
                  break;

                wordsSeen.put(word, wordsSeen.getOrDefault(word, 0) + 1); // add the word to the 'wordsSeen' map

                // no need to process further if the word has higher frequency than required 
                if (wordsSeen.get(word) > wordFrequencyMap.getOrDefault(word, 0))
                  break;

                if (j + 1 == wordsCount) // store index if we have found all the words
                  resultIndices.add(i);
              }
        }

    return resultIndices;
    }
}
```





## Ivy's Marked Problems w/ Notes:

 



## Boyan's Marked Problems:

* Trouble List:
  * 3
  * 424
  * 487
  * 1100
  * 567
  * 30

