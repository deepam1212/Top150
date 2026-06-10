**Given an integer array of size n, find all elements that appear more than ⌊ n/3 ⌋ times.**

 
**Example 1:**
```swift
Input: nums = [3,2,3]
Output: [3]
```

**Example 2:**
```swift
Input: nums = [1]
Output: [1]
```

**Example 3:**
```swift
Input: nums = [1,2]
Output: [1,2]
```

**Constraints:**
```swift
1 <= nums.length <= 5 * 104
-109 <= nums[i] <= 109
```
**Follow up: Could you solve the problem in linear time and in O(1) space?**
**Use the Boyer-Moore Voting Algorithm with two candidates and two counters.**
```swift
class Solution {
    func majorityElement(_ nums: [Int]) -> [Int] {
        //
        var candidate1: Int = 0
        var candidate2: Int = 0
        var count1: Int = 0
        var count2: Int = 0
        //
        for num in nums {
            if num == candidate1 {
                count1 += 1
            } else if num == candidate2 {
                count2 += 1
            } else if count1 == 0 {
                candidate1 = num
                count1 = 1
            } else if count2 == 0 {
                candidate2 = num
                count2 = 1
            } else {
                count1 -= 1
                count2 -= 1
            }
        }
        //
        count1 = 0
        count2 = 0
        //
        for num in nums {
            if num == candidate1 {
                count1 += 1
            } else if num == candidate2 {
                count2 += 1
            }
        }
        //
        var threshold: Int = nums.count / 3
        var result: [Int] = []
        //
        if count1 > threshold {
            result.append(candidate1)
        }
        //
        if count2 > threshold {
            result.append(candidate2)
        }
        //
        return result
    }
}
```
