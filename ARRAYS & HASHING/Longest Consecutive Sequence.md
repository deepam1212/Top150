```swift
Given an unsorted array of integers nums, return the length of the longest consecutive elements sequence.

You must write an algorithm that runs in O(n) time.
```
 
**Example 1:**
```swift
Input: nums = [100,4,200,1,3,2]
Output: 4
Explanation: The longest consecutive elements sequence is [1, 2, 3, 4]. Therefore its length is 4.
```
**Example 2:**
```swift
Input: nums = [0,3,7,2,5,8,4,6,0,1]
Output: 9
```
**Example 3:**

```swift
Input: nums = [1,0,1,2]
Output: 3
``` 
**Constraints:**
```swift
0 <= nums.length <= 105
-109 <= nums[i] <= 109
```

**Solution**
```swift
class Solution {
    func longestConsecutive(_ nums: [Int]) -> Int {
        //
        var dict: [Int: Bool] = [:]
        var myNums = Set(nums)
        for num in myNums {
            dict[num] = true
        }
        //
        var longest: Int = 0
        for num in myNums {
            if dict[num - 1] == nil {
                var number: Int = num
                var length: Int = 1
                //
                while(dict[number + 1] != nil) {
                    number += 1
                    length += 1
                }
                //
                longest = max(longest, length)
            }
        }
        return longest
    }
}
```
