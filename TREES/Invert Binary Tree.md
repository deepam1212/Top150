```swift
Given the root of a binary tree, invert the tree, and return its root.
```

https://leetcode.com/problems/invert-binary-tree/description/

**Example 1:**

![Trapping Rain Water Example](../assets/invert1-tree.jpg)
```swift
Input: root = [4,2,7,1,3,6,9]
Output: [4,7,2,9,6,3,1]
```


**Example 2:**
![Trapping Rain Water Example](../assets/invert2-tree.jpg)

```swift
Input: root = [2,1,3]
Output: [2,3,1]
```

**Example 3:**
```swift
Input: root = []
Output: []
```

**Constraints:**
```swift
The number of nodes in the tree is in the range [0, 100].
-100 <= Node.val <= 100
 ```

**Solution**

```swift
/**
 * Definition for a binary tree node.
 * public class TreeNode {
 *     public var val: Int
 *     public var left: TreeNode?
 *     public var right: TreeNode?
 *     public init() { self.val = 0; self.left = nil; self.right = nil; }
 *     public init(_ val: Int) { self.val = val; self.left = nil; self.right = nil; }
 *     public init(_ val: Int, _ left: TreeNode?, _ right: TreeNode?) {
 *         self.val = val
 *         self.left = left
 *         self.right = right
 *     }
 * }
 */
class Solution {
    func invertTree(_ root: TreeNode?) -> TreeNode? {
        //
        guard let rootNode = root else {return nil}
        //
        let temp = rootNode.left
        rootNode.left = rootNode.right
        rootNode.right = temp

        invertTree(rootNode.left)
        invertTree(rootNode.right)
        //
        return rootNode
    }
}
```
