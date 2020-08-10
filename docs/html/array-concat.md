---
id: concat
title: concat
sidebar_label: concat
---

```js
Array.prototype._concat = function () {
  if (this == null) {
    throw new TypeError('this is null or not defined');
  }

  const args = Array.prototype.slice.call(arguments);
  const len = args.length;
  const res = Array.prototype.slice.call(this);
  let k = 0;

  while (k < len) {
    if (Array.isArray(args[k])) {
      args[k].forEach((x) => res.push(x));
    } else {
      res.push(args[k]);
    }

    k++;
  }

  return res;
};
```

```js
Array.prototype._concat = function () {
  if (this == null) {
    throw new TypeError('this is null or not defined');
  }

  const args = Array.prototype.slice.call(arguments);

  return args.reduce(
    (acc, x) =>
      Array.isArray(x)
        ? x.reduce((res, curr) => (res.push(curr), res), acc)
        : (acc.push(x), acc),
    this
  );
};
```
