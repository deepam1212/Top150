```swift
You are given a string s and an integer k. You can choose any character of the string and change it to any other uppercase English character.
You can perform this operation at most k times.

Return the length of the longest substring containing the same letter you can get after performing the above operations.
```
 **Example 1:**
```swift
Input: s = "ABAB", k = 2
Output: 4
Explanation: Replace the two 'A's with two 'B's or vice versa.
```

**Example 2:**

```swift
Input: s = "AABABBA", k = 1
Output: 4
Explanation: Replace the one 'A' in the middle with 'B' and form "AABBBBA".
The substring "BBBB" has the longest repeating letters, which is 4.
There may exists other ways to achieve this answer too.
```

**Constraints:**
```swift
1 <= s.length <= 105
s consists of only uppercase English letters.
0 <= k <= s.length
```

**Solution**
**Brute-force Solution**
```swift
func doSomething() {
    let s: String = "AABABBBBBBBBBBBB"
    let k: Int = 1
    let charArr: [Character] = Array(s)
    var result: Int = 0
    //
    for left in 0..<charArr.count {
        //
        var dict: [Character: Int] = [:]
        var maxF: Int = 0
        //
        for right in left..<charArr.count {
            dict[charArr[right], default: 0] += 1
            maxF = max(maxF, dict[charArr[right]]!)
            if (right - left + 1) - maxF <= k {
                result = max(result, right - left + 1)
            }
        }
    }
    //
    print(result)
}
doSomething()
```
**Optimized Code**

```swift
class Solution {
    func characterReplacement(_ s: String, _ k: Int) -> Int {
        //
        let charArr = Array(s)
        var maxFrequency: Int = 0
        var frequency: [Character: Int] = [:]
        var left: Int = 0
        var result: Int = 0
        //
        for right in 0..<charArr.count {
            let myChar = charArr[right]
            frequency[myChar, default: 0] += 1
            maxFrequency = max(maxFrequency, frequency[myChar]!)
            while((right - left + 1 - maxFrequency) > k) {
                let charLeft = charArr[left]
                frequency[charLeft]! -= 1
                left += 1
            }
            result = max(result, right - left + 1)
        }
        //
        return result
    }
}
```
