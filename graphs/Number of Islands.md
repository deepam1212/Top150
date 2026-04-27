```swift
Given an m x n 2D binary grid grid which represents a map of '1's (land) and '0's (water), return the number of islands.

An island is surrounded by water and is formed by connecting adjacent lands horizontally or vertically. You may assume all four edges of the grid are all surrounded by water.
```
 

**Example 1:**

```swift
Input: grid = [
  ["1","1","1","1","0"],
  ["1","1","0","1","0"],
  ["1","1","0","0","0"],
  ["0","0","0","0","0"]
]
Output: 1
```

**Example 2:**
```swift
Input: grid = [
  ["1","1","0","0","0"],
  ["1","1","0","0","0"],
  ["0","0","1","0","0"],
  ["0","0","0","1","1"]
]
Output: 3
```

**Constraints:**
```swift
m == grid.length
n == grid[i].length
1 <= m, n <= 300
grid[i][j] is '0' or '1'.
```

**Solution**

```swift
class Solution {
    func numIslands(_ grid: [[Character]]) -> Int {
        //
        var grid = grid
        var rowCount: Int = grid.count
        var colCount: Int = grid[0].count
        var totalIsland: Int = 0
        func dfs(_ r: Int, _ c: Int) {
            //
            if r < 0 || c < 0 || r >= rowCount || c >= colCount || grid[r][c] == "0" {
                return
            }
            grid[r][c] = "0"
            dfs(r + 1, c)
            dfs(r - 1, c)
            dfs(r, c + 1)
            dfs(r, c - 1)
        }
        for i in 0..<rowCount {
            for j in 0..<colCount {
                if grid[i][j] == "1" {
                    totalIsland += 1
                    dfs(i, j)
                }
            }
        }
        //
        return totalIsland
    }
}
```

**Time Complexity: O(m * n)**
**Space Complexity: O(m * n) (worst case recursion stack for DFS)**
