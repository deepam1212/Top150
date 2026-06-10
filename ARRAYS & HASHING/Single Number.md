```swift
Given a non-empty array of integers nums, every element appears twice except for one. Find that single one.

You must implement a solution with a linear runtime complexity and use only constant extra space.
```
 
**Example 1:**
```swift
Input: nums = [2,2,1]

Output: 1
```

**Example 2:**

```swift
Input: nums = [4,1,2,1,2]

Output: 4
```
**Example 3:**
```swift
Input: nums = [1]

Output: 1
```
***Constraints:**
```swift
1 <= nums.length <= 3 * 104
-3 * 104 <= nums[i] <= 3 * 104
Each element in the array appears twice except for one element which appears only once.
```
**Solution**

**0 XOR 100 i.e. 0 ^ 100 = 100; 100 ^ 100 = 0**
```swift
class Solution {
    func singleNumber(_ nums: [Int]) -> Int {
        //
        var outputNumber: Int = 0
        for num in nums {
            outputNumber ^= num
        }
        return outputNumber
    }
}
```
