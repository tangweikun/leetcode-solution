---
id: '0009'
title: 9.回文数
sidebar_label: 9.回文数
---

### [题目](https://leetcode-cn.com/problems/palindrome-number/)

判断一个整数是否是回文数。回文数是指正序（从左向右）和倒序（从右向左）读都是一样的整数。

**示例 1**:

```
输入: 121
输出: true
```

**示例 2**:

```
输入: -121
输出: false
解释: 从左向右读, 为 -121 。 从右向左读, 为 121- 。因此它不是一个回文数。
```

**示例 3**:

```
输入: 10
输出: false
解释: 从右向左读, 为 01 。因此它不是一个回文数。
```

### 方法一

#### 解题思路

将数字转换为字符串，并检查字符串是否为回文

```js
/**
 * @param {number} x
 * @return {boolean}
 */
var isPalindrome = function (x) {
  return x.toString() === x.toString().split('').reverse().join('');
};
```
