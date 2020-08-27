---
id: '0005'
title: 5.最长回文子串
sidebar_label: 5.最长回文子串
---

### [题目](https://leetcode-cn.com/problems/longest-palindromic-substring/)

给定一个字符串 `s`，找到 `s` 中最长的回文子串。你可以假设 `s` 的最大长度为 `1000`。

**示例 1**:

```
输入: "babad"
输出: "bab"
注意: "aba" 也是一个有效答案。
```

**示例 2**:

```
输入: "cbbd"
输出: "bb"
```

### 方法一：动态规划

#### 解题思路

- 时间复杂度：`O(n^2)`

- 空间复杂度：`O(n^2)`

```js
/**
 * @param {string} s
 * @return {string}
 */

var longestPalindrome = function (s) {
  let n = s.length;
  let dp = Array.from({ length: n }, () => Array(n).fill(false));
  let start = 0;
  let end = 0;

  for (let i = n - 1; i >= 0; i--) {
    for (let j = i; j < n; j++) {
      dp[i][j] = s[i] === s[j] && (j - i < 2 || dp[i + 1][j - 1]);
      if (dp[i][j] && j - i > end - start) {
        start = i;
        end = j;
      }
    }
  }

  return s.slice(start, end + 1);
};
```
