# 快速开始

## 数据结构与算法

### [示例 1：strStr](https://leetcode-cn.com/problems/implement-strstr/)

> 给定一个  haystack 字符串和一个 needle 字符串，在 haystack 字符串中找出 needle 字符串出现的第一个位置 (从 0 开始)。如果不存在，则返回  -1。

- 思路：核心点遍历给定字符串字符，判断以当前字符开头字符串是否等于目标字符串

```Python
class Solution:
    def strStr(self, haystack: str, needle: str) -> int:
        L, n = len(needle), len(haystack)

        for start in range(n - L + 1):
            if haystack[start:start + L] == needle:
                return start
        return -1
```

需要注意点

- 循环时，i 不需要到 len-1
- 如果找到目标字符串，len(needle) == j

### [示例 2：subsets](https://leetcode-cn.com/problems/subsets/)

> 给定一组不含重复元素的整数数组 nums，返回该数组所有可能的子集（幂集）。

- 思路：这是一个典型的应用回溯法的题目，简单来说就是穷尽所有可能性，算法模板如下

```go
result = []
func backtrack(选择列表,路径):
    if 满足结束条件:
        result.add(路径)
        return
    for 选择 in 选择列表:
        做选择
        backtrack(选择列表,路径)
        撤销选择
```

- 通过不停的选择，撤销选择，来穷尽所有可能性，最后将满足条件的结果返回。答案代码：

```Python
class Solution:
    def subsets(self, nums: List[int]) -> List[List[int]]:
        
        n = len(nums)
        result = []
        
        def backtrack(start, k, route=[]):
            if len(route) == k:
                result.append(route.copy())
                return
            
            for i in range(start, n):
                route.append(nums[i])
                backtrack(i + 1, k)
                route.pop()

            return
        
        for k in range(n + 1):
            backtrack(0, k)
        
        return result
```

## 练习

- [ ] [strStr](https://leetcode-cn.com/problems/implement-strstr/)
- [ ] [subsets](https://leetcode-cn.com/problems/subsets/)
