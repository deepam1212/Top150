```swift
Given an array of strings strs, group the anagrams together. You can return the answer in any order.
```
 


**Example 1:**
```swift
Input: strs = ["eat","tea","tan","ate","nat","bat"]

Output: [["bat"],["nat","tan"],["ate","eat","tea"]]

Explanation:

There is no string in strs that can be rearranged to form "bat".
The strings "nat" and "tan" are anagrams as they can be rearranged to form each other.
The strings "ate", "eat", and "tea" are anagrams as they can be rearranged to form each other.
```
**Example 2:**
```swift
Input: strs = [""]

Output: [[""]]
```
**Example 3:**
```swift
Input: strs = ["a"]

Output: [["a"]]
```
**Constraints:**
```swift
1 <= strs.length <= 104
0 <= strs[i].length <= 100
strs[i] consists of lowercase English letters.
```

**Solution**

```swift
class Solution {
    func groupAnagrams(_ strs: [String]) -> [[String]] {
        //
        var dict: [[Int]: [String]] = [:]
        for str in strs {
            var arr: [Int] = Array(repeating: 0, count: 26)
            for char in str {
                arr[Int(char.asciiValue! - Character("a").asciiValue!)] += 1
            }
            dict[arr, default: []].append(str)
        }
        return Array(dict.values)
    }
}
```
