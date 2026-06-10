```swift
Given an integer array nums where every element appears three times except for one, which appears exactly once. Find the single element and return it.

You must implement a solution with a linear runtime complexity and use only constant extra space.
```
 
**Example 1:**
```swift
Input: nums = [2,2,3,2]
Output: 3
```
**Example 2:**
```swift
Input: nums = [0,1,0,1,0,1,99]
Output: 99
```

**Constraints:**

```swift
1 <= nums.length <= 3 * 104
-231 <= nums[i] <= 231 - 1
Each element in nums appears exactly three times except for one element which appears once.
```

**Solution**
```swift
class Solution {
    func singleNumber(_ nums: [Int]) -> Int {
        //
        var result: Int = 0
        for bit in 0..<32 {
            var count: Int = 0
            for num in nums {
                if (num & (1 << bit)) != 0 {
                    count += 1
                }
            }
            if count % 3 != 0 {
                result |= (1 << bit)
            }
        }
        //
        if result >= (1 << 31) {
            result -= (1 << 32)
        }
        //
        return result
    }
}
```
