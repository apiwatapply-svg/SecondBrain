---
title: "useDebugValue – React"
source: "https://react.dev/reference/react/useDebugValue"
author:
published:
created: 2026-06-27
description: "The library for web and native user interfaces"
tags:
  - "clippings"
---
## useDebugValue

`useDebugValue` is a React Hook that lets you add a label to a custom Hook in [React DevTools.](https://react.dev/learn/react-developer-tools)

```
useDebugValue(value, format?)
```

- [Reference](#reference)
	- [`useDebugValue(value, format?)`](#usedebugvalue)
- [Usage](#usage)

---

## Reference

### useDebugValue(value, format?)

Call `useDebugValue` at the top level of your [custom Hook](https://react.dev/learn/reusing-logic-with-custom-hooks) to display a readable debug value:

```
import { useDebugValue } from 'react';

function useOnlineStatus() {
  // ...
  useDebugValue(isOnline ? 'Online' : 'Offline');
  // ...
}
```

[See more examples below.](#usage)

#### Parameters

- `value`: The value you want to display in React DevTools. It can have any type.
- **optional** `format`: A formatting function. When the component is inspected, React DevTools will call the formatting function with the `value` as the argument, and then display the returned formatted value (which may have any type). If you don’t specify the formatting function, the original `value` itself will be displayed.

#### Returns

`useDebugValue` does not return anything.

## Usage

### Adding a label to a custom Hook

Call `useDebugValue` at the top level of your [custom Hook](https://react.dev/learn/reusing-logic-with-custom-hooks) to display a readable debug value for [React DevTools.](https://react.dev/learn/react-developer-tools)

```
import { useDebugValue } from 'react';

function useOnlineStatus() {
  // ...
isOnline ? 'Online' : 'Offline'
  // ...
}
```

This gives components calling `useOnlineStatus` a label like `OnlineStatus: "Online"` when you inspect them:

![A screenshot of React DevTools showing the debug value](https://react.dev/images/docs/react-devtools-usedebugvalue.png)

Without the `useDebugValue` call, only the underlying data (in this example, `true`) would be displayed.

```
import { useSyncExternalStore, useDebugValue } from 'react';

export function useOnlineStatus() {
  const isOnline = useSyncExternalStore(subscribe, () => navigator.onLine, () => true);
  useDebugValue(isOnline ? 'Online' : 'Offline');
  return isOnline;
}

function subscribe(callback) {
  window.addEventListener('online', callback);
  window.addEventListener('offline', callback);
  return () => {
    window.removeEventListener('online', callback);
    window.removeEventListener('offline', callback);
  };
}
```

<iframe title="Sandbox Preview" allow="accelerometer; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; clipboard-read; clipboard-write; xr-spatial-tracking;" src="https://786946de.sandpack-bundler-4bw.pages.dev/"></iframe>

### Note

Don’t add debug values to every custom Hook. It’s most valuable for custom Hooks that are part of shared libraries and that have a complex internal data structure that’s difficult to inspect.

---

### Deferring formatting of a debug value

You can also pass a formatting function as the second argument to `useDebugValue`:

```
date
```

Your formatting function will receive the debug value as a parameter and should return a formatted display value. When your component is inspected, React DevTools will call this function and display its result.

This lets you avoid running potentially expensive formatting logic unless the component is actually inspected. For example, if `date` is a Date value, this avoids calling `toDateString()` on it for every render.