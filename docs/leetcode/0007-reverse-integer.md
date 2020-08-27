---
id: '0007'
title: 7.整数反转
sidebar_label: 7.整数反转
---

### [题目](https://leetcode-cn.com/problems/reverse-integer/)

给出一个 `32` 位的有符号整数，你需要将这个整数中每位上的数字进行反转。

**示例 1**:

```
输入: 123
输出: 321
```

**示例 2**:

```
输入: -123
输出: -321
```

**示例 3**:

```
输入: 120
输出: 21
```

### 方法一

```js
/**
 * @param {number} x
 * @return {number}
 */
var reverse = function (x) {
  const sign = Math.sign(x);
  const n = Number(Math.abs(x).toString().split('').reverse().join(''));
  return n < Math.pow(-2, 31) || n > Math.pow(2, 31) - 1 ? 0 : sign * n;
};
```
