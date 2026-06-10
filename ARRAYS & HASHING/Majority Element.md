```swift
Given an array nums of size n, return the majority element.

The majority element is the element that appears more than ⌊n / 2⌋ times. You may assume that the majority element always exists in the array.
```
 
**Example 1:**
```swift
Input: nums = [3,2,3]
Output: 3
```
**Example 2:**
```swift
Input: nums = [2,2,1,1,1,2,2]
Output: 2
```

**Constraints:**
```swift
n == nums.length
1 <= n <= 5 * 104
-109 <= nums[i] <= 109
The input is generated such that a majority element will exist in the array.
```

**Follow-up: Could you solve the problem in linear time and in O(1) space?**
**SOlution**

```swift
class Solution {
    func majorityElement(_ nums: [Int]) -> Int {
        //
        var dict: [Int: Int] = [:]
        var n: Int = nums.count / 2
        for num in nums {
            dict[num, default: 0] += 1
        }
        //
        for num in nums {
            if let dictNum = dict[num], dictNum > n {
                return num
            }
        }
        //
        return -1
    }
}
```


**Solution with O(1) space complexity**
**the optimal solution is Boyer-Moore Voting Algorithm.**
```swift
class Solution {
    func majorityElement(_ nums: [Int]) -> Int {
        //
        var candidate: Int = 0
        var count: Int = 0
        //
        for num in nums {
            if count == 0 {
                candidate = num
            }
            count += num == candidate ? 1 : -1
        }
        //
        return candidate
    }
}
```
