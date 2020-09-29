---
id: '0014'
title: 14.最长公共前缀
sidebar_label: 14.最长公共前缀
---

### [题目](https://leetcode-cn.com/problems/longest-common-prefix/)

### 方法一 纵向扫描

#### 解题思路

- 时间复杂度：`O(mn)`，其中 m 是字符串数组中的字符串的平均长度，n 是字符串的数量。最坏情况下，字符串数组中的每个字符串的每个字符都会被比较一次

- 空间复杂度：`O(1)`

```js
/**
 * @param {string[]} strs
 * @return {string}
 */
var longestCommonPrefix = function (strs) {
  let firstLetter = strs[0];
  let res = '';
  if (!firstLetter) return res;

  for (let i = 0; i < firstLetter.length; i++) {
    const flag = strs.every((item) => item[i] === firstLetter[i]);

    if (!flag) {
      return res;
    }

    res += firstLetter[i];
  }

  return res;
};
```
