# Leetcode Problem 1358 - Number of Substrings Containing All Three Characters

## Introduction

LeetCode problem 1358 asks us to find the number of substrings in a given string that contain all three characters a, b, and c. This problem tests our understanding of sliding windows and is a great way to improve our skills in string manipulation. In this article, we will go over the problem statement, provide examples, and walk through the thought process of solving the problem.

## Problem Statement

Given a string `s`, return the number of substrings that contain all three characters a, b and c. 

For example, given the string "abcabc", the answer is 10, as the substrings that contain all three characters are "abc", "bca", "cab", "abc", "bca", "cab", "abc", "bca", "cab" and "abc". 

The input string s, is a string (1 <= |s| <= $10^4$)  which contains only lowercase letters 'a', 'b', and 'c'. The output is a single integer, the number of substrings that contain all three characters.

## Approach

The idea is to use a sliding window approach where we maintain a window such that it contains all three characters. We can use a map (or an array) to keep track of the count of each character in the window. We can then slide the window to the right, updating the map (or array) as we go. 

We start by initializing the left and right pointers of the window to 0. We then iterate over the string, moving the right pointer to the right. For each character that

we encounter, we add 1 to its count in the map (or array). We then check if the count of all three characters is greater than 0. If it is, we increment our answer by 1. We then move the left pointer to the right and update the map (or array) accordingly.

## Implementation

Here's an example of how we can implement this approach in Python:
```python
def numberOfSubstrings(s: str) -> int:
    ans = 0
    left = 0
    right = 0
    count = {'a': 0, 'b': 0, 'c': 0}
    for right in range(len(s)):
        count[s[right]] += 1
        while count['a'] > 0 and count['b'] > 0 and count['c'] > 0:
            count[s[left]] -= 1
            left += 1
        ans += left
    return ans
#Java
class Solution {
    public int numberOfSubstrings(String s) {
        int count[] = {0, 0, 0}, res = 0, i = 0, n = s.length();
        for (int j = 0; j < n; ++j) {
            ++count[s.charAt(j) - 'a'];
            while (count[0] > 0 && count[1] > 0 && count[2] > 0)
                --count[s.charAt(i++) - 'a'];
            res += i;
        }
        return res;
    }
}
##Complexity Analysis

The time complexity of this solution is O(n), where n is the length of the string. This is because we iterate over the string once and make constant updates to the map (or array). The space complexity is O(1), as we are only using a fixed-size map (or array) to keep track of the character counts.

##Visual Explanation

A simple diagram showing how the sliding window works:
____________________
^                   ^
|                   |
left               right

At the start, both left and right pointers point to the first character of the string.
As we iterate through the string, we move the right pointer to the right and add 1 to the count of the current character in the map (or array).
Once we find a substring that contains all three characters, we move the left pointer to the right and subtract 1 from the count of the character at the new left pointer in the map (or array)
We continue sliding the window until we find a substring that contains all three characters again.

## Conclusion
In this article, we have discussed LeetCode problem 1358 - Number of Substrings Containing All Three Characters. We went over the problem statement, provided examples, walked through the thought process and implementation of the solution in Python, Java, and C++. We also analyzed the time and space complexity of the solution. I hope this article has helped you understand the problem better and improve your string manipulation skills. As a next step, I encourage you to try solving this problem on your own and then compare your solution to the one presented in this article.


