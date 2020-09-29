---
id: '0012'
title: 12.整数转罗马数字
sidebar_label: 12.整数转罗马数字
---

### [题目](https://leetcode-cn.com/problems/integer-to-roman/)

### 方法一

- 时间复杂度：`O(1)`

- 空间复杂度：`O(1)`

```js
/**
 * @param {number} num
 * @return {string}
 */
var intToRoman = function (num) {
  const numMap = [
    {
      key: 1000,
      value: 'M',
    },
    {
      key: 900,
      value: 'CM',
    },
    {
      key: 500,
      value: 'D',
    },
    {
      key: 400,
      value: 'CD',
    },
    {
      key: 100,
      value: 'C',
    },
    {
      key: 90,
      value: 'XC',
    },
    {
      key: 50,
      value: 'L',
    },
    {
      key: 40,
      value: 'XL',
    },
    {
      key: 10,
      value: 'X',
    },
    {
      key: 9,
      value: 'IX',
    },
    {
      key: 5,
      value: 'V',
    },
    {
      key: 4,
      value: 'IV',
    },
    {
      key: 1,
      value: 'I',
    },
  ];

  let res = '';
  const len = numMap.length;

  for (let i = 0; i < len; i++) {
    let item = numMap[i];

    while (num >= item.key) {
      num -= item.key;
      res += item.value;
    }
  }

  return res;
};
```
