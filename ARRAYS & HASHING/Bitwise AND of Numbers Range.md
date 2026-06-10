```swift
Given two integers left and right that represent the range [left, right], return the bitwise AND of all numbers in this range, inclusive.
```
 

**Example 1:**
```swift
Input: left = 5, right = 7
Output: 4
```
**Example 2:**
```swift
Input: left = 0, right = 0
Output: 0
```
**Example 3:**
```swift
Input: left = 1, right = 2147483647
Output: 0
```

**Constraints:**
```swift
0 <= left <= right <= 231 - 1
```
**Solution**
```swift
class Solution {
    func rangeBitwiseAnd(_ left: Int, _ right: Int) -> Int {
        //
        var shift: Int = 0
        var left = left
        var right = right
        while(left != right) {
            left >>= 1
            right >>= 1
            shift += 1
        }
        //
        return left << shift
    }
}
```
