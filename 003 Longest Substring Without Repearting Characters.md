# Longest Substring Without Repeating Characters
Given a string, find the length of the **longest substring** without repeating characters.

## Examples
> Given `abcabcbb`, the answer is `abc`, which the length is 3.

> Given `bbbbb`, the answer is `b`, with the length of 1.

> Given `pwwkew`, the answer is `wke`, with the length of 3. Note that the answer must be a **substring**, "pwke" is a *subsequence* and not a substring.

## Solution
```
class Solution {
    public int lengthOfLongestSubstring(String s) {
        if (s == null){
            return 0;
        }
        int length = 0;
        int start = 0;
        Map<Character, Integer> map = new HashMap<>(s.length());
        for (int i = 0; i<s.length(); i++){
            char ch = s.charAt(i);
            if (map.containsKey(ch) && map.get(ch) >= start){ 
                start = map.get(ch) + 1;
            }
            else {
                length = Math.max(length, i - start + 1);
            }
            map.put(ch, i);
        }
        return length;
    }
}
```
