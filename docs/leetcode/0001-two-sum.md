---
id: '0001'
title: 1.Two sum
sidebar_label: 1.Two sum
---

### [题目](https://leetcode-cn.com/problems/two-sum/)

给定一个整数数组 `nums`  和一个目标值 `target`，请你在该数组中找出和为目标值的那两个整数，并返回他们的数组下标。

你可以假设每种输入只会对应一个答案。但是，数组中同一个元素不能使用两遍。

**示例**:

```
给定 nums = [2, 7, 11, 15], target = 9

因为 nums[0] + nums[1] = 2 + 7 = 9
所以返回 [0, 1]
```

### 方法一：暴力法

#### 解题思路

- 遍历每个元素 `x`，并查找是否存在一个值与 `target - x` 相等的目标元素

- 时间复杂度：O(n^2)
- 空间复杂度：O(1)

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function (nums, target) {
  for (let i = 0; i < nums.length; i++) {
    for (let j = i + 1; j < nums.length; j++) {
      if (nums[j] === target - nums[i]) {
        return [i, j];
      }
    }
  }
};
```

### 方法二：哈希表

#### 解题思路

- 在进行迭代并将元素插入到表中的同时，我们还会回过头来检查表中是否已经存在当前元素所对应的目标元素。如果它存在，那我们已经找到了对应解，并立即将其返回。

- 时间复杂度：O(n)
- 空间复杂度：O(n)

```js
/**
 * @param {number[]} nums
 * @param {number} target
 * @return {number[]}
 */
var twoSum = function (nums, target) {
  const hash = new Map();
  for (let i = 0; i < nums.length; i++) {
    const complement = target - nums[i];
    if (hash.has(complement)) {
      return [hash.get(complement), i];
    }

    hash.set(nums[i], i);
  }
};
```

#### 相关标签

数组、哈希表
