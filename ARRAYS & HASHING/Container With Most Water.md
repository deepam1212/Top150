```swift
You are given an integer array height of length n. There are n vertical lines drawn such that the two endpoints of the ith line are (i, 0) and (i, height[i]).

Find two lines that together with the x-axis form a container, such that the container contains the most water.

Return the maximum amount of water a container can store.

Notice that you may not slant the container.
```
 
**Example 1:**

![asset](../assets/question_11.jpg)

```swift
Input: height = [1,8,6,2,5,4,8,3,7]
Output: 49
Explanation: The above vertical lines are represented by array [1,8,6,2,5,4,8,3,7]. In this case, the max area of water (blue section) the container can contain is 49.
```
**Example 2:**
```swift
Input: height = [1,1]
Output: 1
 ```

**Constraints:**
```swift
n == height.length
2 <= n <= 105
0 <= height[i] <= 104
```
**Solution**
```swift
class Solution {
    func maxArea(_ height: [Int]) -> Int {
        //
        var left: Int = 0
        var right: Int = height.count - 1
        var maxWater: Int = 0
        while(left <= right) {
            let minHeight: Int = min(height[left], height[right])
            let totalArea: Int = minHeight * (right - left)
            maxWater = max(maxWater, totalArea)
            if height[left] <= height[right] {
                left += 1
            } else {
                right -= 1
            }
        }
        return maxWater
    }
}
```
