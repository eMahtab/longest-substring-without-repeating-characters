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
        if(s == null || s.length() == 0)
            return 0;
        int maxSubstring = 1;
        for(int i = 0; i < s.length(); i++) {
            for(int j = i + 1; j <= s.length(); j++) {
                String substr = s.substring(i,j);
                if(isUnique(substr)) {
                    maxSubstring = Math.max(maxSubstring, j-i);
                } else {
                    break;
                }  
            }
        }
        return maxSubstring;
    }
    
    private boolean isUnique(String s) {
        Set<Character> set = new HashSet<>();
        for(int i = 0; i < s.length(); i++) {
            if(!set.contains(s.charAt(i)))
                set.add(s.charAt(i));
            else
                return false;
        }
        return true;
    }
}
```
# Implementation 2 : Sliding Window
```java
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if(s == null || s.length() == 0)
            return 0;
        int left = 0, right = 0;
        int max = 1;
        Set<Character> set = new HashSet<>();
        
        while(right < s.length()) {
               if(!set.contains(s.charAt(right))){
                   set.add(s.charAt(right++));
                   max = Math.max(max, set.size());
               } else {
                   set.remove(s.charAt(left++));
               }    
        }
        return max;
    }
    
}
```

# References :
1. https://leetcode.com/articles/longest-substring-without-repeating-characters
2. https://www.youtube.com/watch?v=3IETreEybaA
