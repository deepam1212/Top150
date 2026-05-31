```swift
Given the root of a binary tree, return the length of the diameter of the tree.

The diameter of a binary tree is the length of the longest path between any two nodes in a tree. This path may or may not pass through the root.

The length of a path between two nodes is represented by the number of edges between them.
```
 https://leetcode.com/problems/diameter-of-binary-tree/description/

**Example 1:**
![assets](../assets/diamtree.jpg)


```swift
Input: root = [1,2,3,4,5]
Output: 3
Explanation: 3 is the length of the path [4,2,1,3] or [5,2,1,3].
```

**Example 2:**
```swift
Input: root = [1,2]
Output: 1
 ```

**Constraints:**
```swift
The number of nodes in the tree is in the range [1, 104].
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
    var diameter: Int = 0
    func diameterOfBinaryTree(_ root: TreeNode?) -> Int {
        let _ = diameterTree(root)
        return diameter
    }

    func diameterTree(_ root: TreeNode?) -> Int {
        guard let rootNode = root else {return 0}
        var left = diameterTree(rootNode.left)
        var right = diameterTree(rootNode.right)
        diameter = max(diameter, left + right)
        return (1 + max(left, right))
    }
}
```
