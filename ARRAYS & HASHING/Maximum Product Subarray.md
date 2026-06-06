```swift
Given an integer array nums, find a subarray that has the largest product, and return the product.

The test cases are generated so that the answer will fit in a 32-bit integer.

Note that the product of an array with a single element is the value of that element.
```
 

**Example 1:**
```swift
Input: nums = [2,3,-2,4]
Output: 6
Explanation: [2,3] has the largest product 6.
```
**Example 2:**
```swift
Input: nums = [-2,0,-1]
Output: 0
Explanation: The result cannot be 2, because [-2,-1] is not a subarray.
 ```


**Constraints:**
```swift
1 <= nums.length <= 2 * 104
-10 <= nums[i] <= 10
The product of any subarray of nums is guaranteed to fit in a 32-bit integer.
```

**Solution**

```swift
class Solution {
    func maxProduct(_ nums: [Int]) -> Int {
        //
        var maxProduct: Int = nums[0]
        var minProduct: Int = nums[0]
        var output: Int = nums[0]
        //
        for (index, num) in nums.enumerated() where index > 0 {
            //
            if num < 0 {
                (maxProduct, minProduct) = (minProduct, maxProduct)
            }
            maxProduct = max(num, maxProduct * num)
            minProduct = min(num, minProduct * num)
            output = max(output, maxProduct)
        }
        //
        return output
    }
}
```
