---
title: "createRef – React"
source: "https://react.dev/reference/react/createRef"
author:
published:
created: 2026-06-27
description: "The library for web and native user interfaces"
tags:
  - "clippings"
---
## createRef

### Pitfall

`createRef` is mostly used for [class components.](https://react.dev/reference/react/Component) Function components typically rely on [`useRef`](https://react.dev/reference/react/useRef) instead.

`createRef` creates a [ref](https://react.dev/learn/referencing-values-with-refs) object which can contain arbitrary value.

```
class MyInput extends Component {
  inputRef = createRef();
  // ...
}
```

- [Reference](#reference)
	- [`createRef()`](#createref)
- [Usage](#usage)
	- [Declaring a ref in a class component](#declaring-a-ref-in-a-class-component)
- [Alternatives](#alternatives)
	- [Migrating from a class with `createRef` to a function with `useRef`](#migrating-from-a-class-with-createref-to-a-function-with-useref)

---

## Reference

### createRef()

Call `createRef` to declare a [ref](https://react.dev/learn/referencing-values-with-refs) inside a [class component.](https://react.dev/reference/react/Component)

```
import { createRef, Component } from 'react';

class MyComponent extends Component {
  intervalRef = createRef();
  inputRef = createRef();
  // ...
```

[See more examples below.](#usage)

#### Parameters

`createRef` takes no parameters.

#### Returns

`createRef` returns an object with a single property:

- `current`: Initially, it’s set to the `null`. You can later set it to something else. If you pass the ref object to React as a `ref` attribute to a JSX node, React will set its `current` property.

#### Caveats

- `createRef` always returns a *different* object. It’s equivalent to writing `{ current: null }` yourself.
- In a function component, you probably want [`useRef`](https://react.dev/reference/react/useRef) instead which always returns the same object.
- `const ref = useRef()` is equivalent to `const [ref, _] = useState(() => createRef(null))`.

---

## Usage

### Declaring a ref in a class component

To declare a ref inside a [class component,](https://react.dev/reference/react/Component) call `createRef` and assign its result to a class field:

```
import { Component, createRef } from 'react';

class Form extends Component {
  inputRef = createRef();

  // ...
}
```

If you now pass `ref={this.inputRef}` to an `<input>` in your JSX, React will populate `this.inputRef.current` with the input DOM node. For example, here is how you make a button that focuses the input:

```
import { Component, createRef } from 'react';

export default class Form extends Component {
  inputRef = createRef();

  handleClick = () => {
    this.inputRef.current.focus();
  }

  render() {
    return (
      <>
        <input ref={this.inputRef} />
        <button onClick={this.handleClick}>
          Focus the input
        </button>
      </>
    );
  }
}
```

### Pitfall

`createRef` is mostly used for [class components.](https://react.dev/reference/react/Component) Function components typically rely on [`useRef`](https://react.dev/reference/react/useRef) instead.

---

## Alternatives

### Migrating from a class with createRef to a function with useRef

We recommend using function components instead of [class components](https://react.dev/reference/react/Component) in new code. If you have some existing class components using `createRef`, here is how you can convert them. This is the original code:

```
import { Component, createRef } from 'react';

export default class Form extends Component {
  inputRef = createRef();

  handleClick = () => {
    this.inputRef.current.focus();
  }

  render() {
    return (
      <>
        <input ref={this.inputRef} />
        <button onClick={this.handleClick}>
          Focus the input
        </button>
      </>
    );
  }
}
```

When you [convert this component from a class to a function,](https://react.dev/reference/react/Component#alternatives) replace calls to `createRef` with calls to [`useRef`:](https://react.dev/reference/react/useRef)

```
import { useRef } from 'react';

export default function Form() {
  const inputRef = useRef(null);

  function handleClick() {
    inputRef.current.focus();
  }

  return (
    <>
      <input ref={inputRef} />
      <button onClick={handleClick}>
        Focus the input
      </button>
    </>
  );
}
```