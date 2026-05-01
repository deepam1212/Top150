**Given two strings s and t, return true if t is an anagram of s, and false otherwise.**

 
```swift
Example 1:

Input: s = "anagram", t = "nagaram"

Output: true
```
```swift
Example 2:

Input: s = "rat", t = "car"

Output: false
```
 

**Constraints:**
```swift
1 <= s.length, t.length <= 5 * 104
s and t consist of lowercase English letters.
``` 

**Follow up: What if the inputs contain Unicode characters? How would you adapt your solution to such a case?**
```swift
class Solution {
    func isAnagram(_ s: String, _ t: String) -> Bool {
        //
        if s.count != t.count {
            return false
        }
        var frequency: [Character: Int] = [:]
        for char in s {
            //
            frequency[char, default: 0] += 1
        }
        for char in t {
            if let count = frequency[char] {
                if count == 1 {
                    //
                    frequency.removeValue(forKey: char)
                } else {
                    frequency[char] = count - 1
                }
            } else {
                return false
            }
        }
        return frequency.isEmpty
    }
}
```
```swift
T.C.: O(max(s, t)) or better technically say O(n)
S.C.: O(s)
```
