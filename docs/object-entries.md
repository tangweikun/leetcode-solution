---
id: entries
title: entries
sidebar_label: entries
---

```js
Object._entries = function (obj) {
  const ownProps = Object.keys(obj);
  let i = ownProps.length;
  const resArray = new Array(i);

  while (i--) resArray[i] = [ownProps[i], obj[ownProps[i]]];

  return resArray;
};
```
