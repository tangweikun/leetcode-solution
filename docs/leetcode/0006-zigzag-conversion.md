---
id: '0006'
title: 6.Z 字形变换
sidebar_label: 6.Z 字形变换
---

### [题目](https://leetcode-cn.com/problems/zigzag-conversion/)

将一个给定字符串根据给定的行数，以从上往下、从左到右进行 Z 字形排列。

比如输入字符串为 "LEETCODEISHIRING" 行数为 `3` 时，排列如下：

```
L   C   I   R
E T O E S I I G
E   D   H   N
```

之后，你的输出需要从左往右逐行读取，产生出一个新的字符串，比如："LCIRETOESIIGEDHN"。

请你实现这个将字符串进行指定行数变换的函数：

```
string convert(string s, int numRows);
```

**示例 1**:

```
输入: s = "LEETCODEISHIRING", numRows = 3
输出: "LCIRETOESIIGEDHN"
```

**示例 2**:

```
输入: s = "LEETCODEISHIRING", numRows = 4
输出: "LDREOEIIECIHNTSG"
解释:

L     D     R
E   O E   I I
E C   I H   N
T     S     G

```

### 方法一

#### 解题思路

- 时间复杂度：`O(n)`

- 空间复杂度：`O(n)`

```js
/**
 * @param {string} s
 * @param {number} numRows
 * @return {string}
 */
var convert = function (s, numRows) {
  if (numRows === 1) return s;
  const res = [];
  let x = 0;
  let y = 0;
  let direction = 'DOWN';

  for (let i = 0; i < s.length; i++) {
    if (!res[y]) {
      res[y] = '';
    }
    res[y] += s[i];

    if (direction === 'DOWN') {
      if (y + 1 === numRows) {
        x++;
        y--;
        direction = 'RIGHT_UP';
      } else {
        y++;
      }

      continue;
    }

    if (direction === 'RIGHT_UP') {
      if (y === 0) {
        direction = 'DOWN';
        y++;
      } else {
        x++;
        y--;
      }

      continue;
    }
  }

  return res.reduce((acc, x) => acc + x, '');
};
```
