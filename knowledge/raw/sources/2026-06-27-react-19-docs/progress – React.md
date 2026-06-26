---
title: "<progress> – React"
source: "https://react.dev/reference/react-dom/components/progress"
author:
published:
created: 2026-06-27
description: "The library for web and native user interfaces"
tags:
  - "clippings"
---
## \<progress>

The [built-in browser `<progress>` component](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress) lets you render a progress indicator.

```
<progress value={0.5} />
```

---

## Reference

### \<progress>

To display a progress indicator, render the [built-in browser `<progress>`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress) component.

```
<progress value={0.5} />
```

[See more examples below.](#usage)

#### Props

`<progress>` supports all [common element props.](https://react.dev/reference/react-dom/components/common#common-props)

Additionally, `<progress>` supports these props:

- [`max`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress#max): A number. Specifies the maximum `value`. Defaults to `1`.
- [`value`](https://developer.mozilla.org/en-US/docs/Web/HTML/Element/progress#value): A number between `0` and `max`, or `null` for indeterminate progress. Specifies how much was done.

---

## Usage

### Controlling a progress indicator

To display a progress indicator, render a `<progress>` component. You can pass a number `value` between `0` and the `max` value you specify. If you don’t pass a `max` value, it will assumed to be `1` by default.

If the operation is not ongoing, pass `value={null}` to put the progress indicator into an indeterminate state.

export default function App() {

return (

<>

\<progress value={0} />

\<progress value={0.5} />

\<progress value={0.7} />

\<progress value={75} max={100} />

\<progress value={1} />

\<progress value={null} />

</>

);

}

<iframe title="Sandbox Preview" allow="accelerometer; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; clipboard-read; clipboard-write; xr-spatial-tracking;" src="https://786946de.sandpack-bundler-4bw.pages.dev/"></iframe>