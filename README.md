# Longest Substring Without Repeating Characters
## https://leetcode.com/problems/longest-substring-without-repeating-characters

Given a string, find the length of the longest substring without repeating characters.
```
Example 1:

Input: "abcabcbb"
Output: 3 
Explanation: The answer is "abc", with the length of 3. 

Example 2:

Input: "bbbbb"
Output: 1
Explanation: The answer is "b", with the length of 1.

Example 3:

Input: "pwwkew"
Output: 3
Explanation: The answer is "wke", with the length of 3. 
             Note that the answer must be a substring, "pwke" is a subsequence and not a substring.
```
# Implementation 1 : Naive
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        int longest = 0;
        for(int i = 0; i < s.length(); i++) {
            for(int j = i+1; j < s.length() + 1; j++) {
                String substr = s.substring(i, j);
                longest = Math.max(longest, check(substr));
            }
        }
        return longest;
    }

    private int check(String str) {
        Set<Character> set = new HashSet<>();
        int length = 0;
        for(char ch : str.toCharArray()) {
            if(set.contains(ch))
              return 0;
            length++;
            set.add(ch);  
        }
        return length;
    }
}
```
# Implementation 2 : Sliding Window
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
       if(s == null || s.length() == 0)
         return 0;
       int i = 0, j = 0, max = 0;
       Set<Character> set = new HashSet<>();
       while(i < s.length()) {
         char ch = s.charAt(i);
         while(set.contains(ch)) {
            set.remove(s.charAt(j));
            j++;
         }
         set.add(ch);
         max = Math.max(max, i-j+1);
         i++;
       }
       return max;  
    }
}
```

# References :
1. https://leetcode.com/articles/longest-substring-without-repeating-characters
2. https://www.youtube.com/watch?v=4i6-9IzQHwo
