---
id: lastIndexOf
title: lastIndexOf
sidebar_label: lastIndexOf
---

```js
Array.prototype._lastIndexOf = function (target) {
  'use strict';

  if (this == null) {
    throw new TypeError('this is null or not defined');
  }
  const objThis = Object(this);
  const len = objThis.length >>> 0;
  let k = len - 1;

  if (arguments.length > 1) {
    const temp = arguments[1] >> 0;
    k = temp < 0 ? Math.min(k, Math.max(temp + k, 0)) : Math.min(temp, k);
  }

  while (k >= 0) {
    if (k in objThis && objThis[k] === target) return k;
    k--;
  }

  return -1;
};
```
