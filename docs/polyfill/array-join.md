---
id: join
title: join
sidebar_label: join
---

```js
Array.prototype._join = function (separator = ',') {
  if (this == null) {
    throw new TypeError('this is null or not defined');
  }
  return this.reduce((acc, x) => acc + separator + (x || ''));
};
```
