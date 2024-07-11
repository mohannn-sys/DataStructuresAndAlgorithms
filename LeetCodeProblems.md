# Reverse Substrings Between Each Pair of Parentheses
## Problem Statement:
You are given a string s that consists of lower case English letters and brackets.
Reverse the strings in each pair of matching parentheses, starting from the innermost one.
Your result should not contain any brackets.

> Example 1:
+ Input: s = "(abcd)"
+ Output: "dcba"

> Example 2:
+ Input: s = "(u(love)i)"
+ Output: "iloveu"
+ Explanation: The substring "love" is reversed first, then the whole string is reversed.
  
> Example 3:
+ Input: s = "(ed(et(oc))el)"
+ Output: "leetcode"
+ Explanation: First, we reverse the substring "oc", then "etco", and finally, the whole string.

> Constraints:
+ 1 <= s.length <= 2000
+ s only contains lower case English characters and parentheses.
+ It is guaranteed that all parentheses are balanced.

## Solution:
### Approach
To solve this problem, we can use a stack to keep track of the characters that need to be reversed. Here's the step-by-step approach:
1. Iterate through each character in the input string s.
2. Initialize an empty stack and an empty result string.
3. If the current character is an opening bracket (, push it onto the stack.
4. If the current character is a lowercase letter, append it to the result string.
5. If the current character is a closing bracket ), start popping characters from the stack and append them to the result string until the corresponding opening bracket is found.
6. After processing all characters, return the result string.

### Python Program

```
def reverseParentheses(s):
    stack = []
    result = ""
   
    for char in s:
        if char == "(":
            stack.append(result)
            result = ""
        elif char == ")":
            result = stack.pop() + result[::-1]
        else:
            result += char
    
    return result
```
### Analysis
1. ***Time Complexity:***
The time complexity of this solution is O(n), where n is the length of the input string s. This is because we iterate through the input string once, and each operation (pushing/popping from the stack and appending/reversing the result string) takes constant time.
2. ***Space Complexity:***
The space complexity of this solution is also O(n), where n is the length of the input string s. This is because, in the worst-case scenario, the entire string needs to be reversed (e.g., "(a(b(c)d)ef)"), and the stack will hold all the intermediate reversed strings.
 

