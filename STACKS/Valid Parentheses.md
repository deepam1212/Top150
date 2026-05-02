```swift
Given a string s containing just the characters '(', ')', '{', '}', '[' and ']', determine if the input string is valid.

An input string is valid if:

Open brackets must be closed by the same type of brackets.
Open brackets must be closed in the correct order.
Every close bracket has a corresponding open bracket of the same type.
```

**Example 1:**
```swift
Input: s = "()"

Output: true
```
**Example 2:**
```swift
Input: s = "()[]{}"

Output: true
```
**Example 3:**
```swift
Input: s = "(]"

Output: false
```
**Example 4:**
```swift
Input: s = "([])"

Output: true
```
**Example 5:**
```swift
Input: s = "([)]"

Output: false
```
 **Constraints:**
```swift
1 <= s.length <= 104
s consists of parentheses only '()[]{}'.
```

**Solution**

```swift
class Solution {
    func isValid(_ s: String) -> Bool {
        //
        var dict: [Character: Character] = [")": "(", "]": "[", "}": "{"]
        var stack: [Character] = []
        //
        for char in s {
            if stack.isEmpty || char == "(" || char == "[" || char == "{" {
                stack.append(char)
            } else {
                if let value = dict[char], value == stack.last {
                    stack.removeLast()
                } else {
                    return false
                }
            }
        }
        //
        return stack.isEmpty
    }
}
```
```swift
T.C.: O(N)
S.C.: O(N)
```
