# LeetCode20-Valid-Parentheses

This is a perfect an easy [problem](https://leetcode.com/problems/valid-parentheses/description/) to remember the stack data structure.
You can easily solve it by just read and apply the hints.

```java
class Solution {
    public boolean isValid(String s) {
        Stack<Character> stack = new Stack<>();

        for (char c : s.toCharArray()) {
            if (c == ')' || c == ']' || c == '}') {
                if (stack.empty()) return false;
                char closingPar = stack.peek();
                if (c == ')' && stack.peek() == '(') stack.pop();
                else if (c == ']' && stack.peek() == '[') stack.pop();
                else if (c == '}' && stack.peek() == '{') stack.pop();
                else return false;
            } else {
                 stack.push(c);
            }
        }

        if (!stack.empty()) return false;
    
        return true;
    }
}
```

We have the go through the whole string once and the stack has in the worst case a size of n with n the length of the string so both time and space complexity are O(n).
