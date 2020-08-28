---
id: useHover
title: useHover
sidebar_label: useHover
---

Detect whether the mouse is hovering an element. The hook returns a ref and a boolean value indicating whether the element with that ref is currently being hovered. Just add the returned ref to any element whose hover state you want to monitor. One potential bug with this method: If you have logic that changes the element that hoverRef is added to then your event listeners will not necessarily get applied to the new element. If you need this functionality then use this alternate version that utilizes a callback ref.

### [Sandbox](https://codesandbox.io/s/usehover-forked-lk7o7)

### Hook

```js
// Hook
function useHover() {
  const [value, setValue] = useState(false);
  const ref = useRef(null);

  const handleMouseOver = () => setValue(true);
  const handleMouseOut = () => setValue(false);

  useEffect(
    () => {
      const node = ref.current;
      if (node) {
        node.addEventListener('mouseover', handleMouseOver);
        node.addEventListener('mouseout', handleMouseOut);

        return () => {
          node.removeEventListener('mouseover', handleMouseOver);
          node.removeEventListener('mouseout', handleMouseOut);
        };
      }
    },
    [ref.current] // Recall only if ref changes
  );

  return [ref, value];
}
```

### Usage

```js
import { useRef, useState, useEffect } from 'react';

// Usage
function App() {
  const [hoverRef, isHovered] = useHover();

  return <div ref={hoverRef}>{isHovered ? '😁' : '☹️'}</div>;
}
```
