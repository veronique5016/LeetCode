# Longest Palindromic Substring

Given a string **s**, find the longest palindromic substring in **s**. You may assume that the maximum length of **s** is 1000.

## Example
- example 1
> Input: "babad"

> Output: "bab"

> Note: "aba" is also a valid answer.


- example 2

> Input: "cbbd"

> Output: "bb"

## Hint
- A palindromic substring mirrors around its center. Therefore, a palindrome can be expanded from its center.

## Solution
```
class Solution {
    private int lo, maxLen;
    public String longestPalindrome(String s) {
        int len = s.length();
        if (len<2)
            return s;
        for (int i=0; i<len-1; i++){
            extend(s, i, i);
            extend(s, i, i+1);
        }
        return s.substring(lo, lo+maxLen);
    }
    private void extend(String s, int j, int k){
        while (j>=0 && k<s.length() && s.charAt(j)== s.charAt(k)){
            j--;
            k++;
        }
        if (maxLen<k-j-1){
            lo = j+1;
            maxLen = k-j-1;
        }
    }
}
```
