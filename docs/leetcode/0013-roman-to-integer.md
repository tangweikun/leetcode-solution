---
id: '0013'
title: 13.罗马数字转整数
sidebar_label: 13.罗马数字转整数
---

### [题目](https://leetcode-cn.com/problems/roman-to-integer/)

### 方法一

#### 解题思路

- 时间复杂度：`O(1)`

- 空间复杂度：`O(1)`

```js
/**
 * @param {string} s
 * @return {number}
 */
var romanToInt = function (s) {
  const hash = {
    I: 1,
    V: 5,
    X: 10,
    L: 50,
    C: 100,
    D: 500,
    M: 1000,
  };
  const arr = s.split('');
  let res = 0;

  for (let i = 0; i < arr.length; i++) {
    if (hash[arr[i]] < hash[arr[i + 1]]) {
      res -= hash[arr[i]];
    } else {
      res += hash[arr[i]];
    }
  }

  return res;
};
```
