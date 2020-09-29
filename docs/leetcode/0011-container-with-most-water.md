---
id: '0011'
title: 11.盛最多水的容器
sidebar_label: 11.盛最多水的容器
---

### [题目](https://leetcode-cn.com/problems/container-with-most-water/)

### 方法一 双指针

- 时间复杂度：`O(n)`

- 空间复杂度：`O(1)`

```js
/**
 * @param {number[]} height
 * @return {number}
 */
var maxArea = function (height) {
  let left = 0;
  let right = height.length - 1;
  let res = 0;

  while (left < right) {
    res = Math.max(res, (right - left) * Math.min(height[left], height[right]));
    if (height[left] < height[right]) {
      left++;
    } else {
      right--;
    }
  }

  return res;
};
```
