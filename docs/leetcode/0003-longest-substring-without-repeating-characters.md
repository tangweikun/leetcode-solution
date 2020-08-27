---
id: '0003'
title: 3.无重复字符的最长子串
sidebar_label: 3.无重复字符的最长子串
---

### [题目](https://leetcode-cn.com/problems/longest-substring-without-repeating-characters/)

给定一个字符串，请你找出其中不含有重复字符的 `最长子串` 的长度。

**示例 1**:

```
输入: "abcabcbb"
输出: 3
解释: 因为无重复字符的最长子串是 "abc"，所以其长度为 3。
```

**示例 2**:

```
输入: "bbbbb"
输出: 1
解释: 因为无重复字符的最长子串是 "b"，所以其长度为 1。
```

**示例 3**:

```
输入: "pwwkew"
输出: 3
解释: 因为无重复字符的最长子串是 "wke"，所以其长度为 3。
      请注意，你的答案必须是 `子串` 的长度，"pwke" 是一个子序列，不是子串。
```

### 方法一：滑动窗口

#### 解题思路

- 定义一个 map 数据结构存储 (k, v)，其中 key 值为字符，value 值为字符位置 +1，加 1 表示从字符位置后一个才开始不重复
- 我们定义不重复子串的开始位置为 start，结束位置为 end
- 随着 end 不断遍历向后，会遇到与 [start, end] 区间内字符相同的情况，此时将字符作为 key 值，获取其 value 值，并更新 start，此时 [start, end] 区间内不存在重复字符
- 无论是否更新 start，都会更新其 map 数据结构和结果 res

- 时间复杂度：`O(n)`

```js
/**
 * @param {string} s
 * @return {number}
 */
var lengthOfLongestSubstring = function (s) {
  const len = s.length;
  const map = new Map();
  let start = 0;
  let res = 0;

  for (let end = 0; end < len; end++) {
    if (map.has(s[end])) {
      start = Math.max(map.get(s[end]), start);
    }
    res = Math.max(res, end - start + 1);
    map.set(s[end], end + 1);
  }

  return res;
};
```
