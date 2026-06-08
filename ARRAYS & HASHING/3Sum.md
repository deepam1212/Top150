```swift
Given an integer array nums, return all the triplets [nums[i], nums[j], nums[k]] such that i != j, i != k, and j != k, and nums[i] + nums[j] + nums[k] == 0.

Notice that the solution set must not contain duplicate triplets.
```
 
**Example 1:**
```swift
Input: nums = [-1,0,1,2,-1,-4]
Output: [[-1,-1,2],[-1,0,1]]
Explanation: 
nums[0] + nums[1] + nums[2] = (-1) + 0 + 1 = 0.
nums[1] + nums[2] + nums[4] = 0 + 1 + (-1) = 0.
nums[0] + nums[3] + nums[4] = (-1) + 2 + (-1) = 0.
The distinct triplets are [-1,0,1] and [-1,-1,2].
Notice that the order of the output and the order of the triplets does not matter.
```
**Example 2:**

```swift
Input: nums = [0,1,1]
Output: []
Explanation: The only possible triplet does not sum up to 0.
```
**Example 3:**
```swift
Input: nums = [0,0,0]
Output: [[0,0,0]]
Explanation: The only possible triplet sums up to 0.
```
**Constraints:**
```swift
3 <= nums.length <= 3000
-105 <= nums[i] <= 105
```
**Solution**

```swift
class Solution {
    func threeSum(_ nums: [Int]) -> [[Int]] {
        //
        var sortedArr: [Int] = nums.sorted()
        var result: [[Int]] = []
        var n: Int = sortedArr.count
        //
        for i in 0..<n {
            if i > 0 && sortedArr[i] == sortedArr[i - 1] {
                continue
            }
            var left: Int = i + 1
            var right: Int = n - 1
            while(left < right) {
                let sum: Int = sortedArr[i] + sortedArr[left] + sortedArr[right]
                if sum == 0 {
                    result.append([sortedArr[i], sortedArr[left], sortedArr[right]])
                    left += 1
                    right -= 1
                    while(left < right && sortedArr[left] == sortedArr[left - 1]) {
                        left += 1
                    }
                    //
                    while(left < right && sortedArr[right] == sortedArr[right + 1]) {
                        right -= 1
                    }
                } else if sum < 0 {
                    left += 1
                } else {
                    right -= 1
                }
            }
        }
        //
        return result
    }
}
```
