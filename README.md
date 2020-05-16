# Longest Substring Without Repeating Characters
## https://leetcode.com/problems/longest-substring-without-repeating-characters

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
