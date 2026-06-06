```swift
Given an integer array nums, return true if any value appears at least twice in the array, and return false if every element is distinct.
```
 

**Example 1:**
```swift
Input: nums = [1,2,3,1]

Output: true
```
**Explanation:**
```swift
The element 1 occurs at the indices 0 and 3.
```
**Example 2:**
```swift
Input: nums = [1,2,3,4]

Output: false
```
**Explanation:**
```swift
All elements are distinct.
```
**Example 3:**
```swift
Input: nums = [1,1,1,3,3,4,3,2,4,2]

Output: true
```
 


**Constraints:**
```swift
1 <= nums.length <= 105
-109 <= nums[i] <= 109
```

**Solution**

```swift
class Solution {
    func containsDuplicate(_ nums: [Int]) -> Bool {
       //
       var dict: [Int: Bool] = [Int: Bool]()
       //
        for num in nums {
            if let isContain = dict[num] {
                return isContain
            }
            //
            dict[num] = true
        }
        return false 
    }
}
```
