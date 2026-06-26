---
title: "JavaScript in JSX with Curly Braces"
source: "https://react.dev/learn/javascript-in-jsx-with-curly-braces"
author:
published:
created: 2026-06-27
description: "The library for web and native user interfaces"
tags:
  - "clippings"
---
JSX lets you write HTML-like markup inside a JavaScript file, keeping rendering logic and content in the same place. Sometimes you will want to add a little JavaScript logic or reference a dynamic property inside that markup. In this situation, you can use curly braces in your JSX to open a window to JavaScript.

### You will learn

- How to pass strings with quotes
- How to reference a JavaScript variable inside JSX with curly braces
- How to call a JavaScript function inside JSX with curly braces
- How to use a JavaScript object inside JSX with curly braces

## Passing strings with quotes

When you want to pass a string attribute to JSX, you put it in single or double quotes:

export default function Avatar() {

return (

<img

className="avatar"

src="https://react.dev/images/docs/scientists/7vQD0fPs.jpg"

alt="Gregorio Y. Zara"

/>

);

}

<iframe title="Sandbox Preview" allow="accelerometer; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; clipboard-read; clipboard-write; xr-spatial-tracking;" src="https://786946de.sandpack-bundler-4bw.pages.dev/"></iframe>

Here, `"https://react.dev/images/docs/scientists/7vQD0fPs.jpg"` and `"Gregorio Y. Zara"` are being passed as strings.

But what if you want to dynamically specify the `src` or `alt` text? You could **use a value from JavaScript by replacing `"` and `"` with `{` and `}`**:

export default function Avatar() {

const avatar = 'https://react.dev/images/docs/scientists/7vQD0fPs.jpg';

const description = 'Gregorio Y. Zara';

return (

<img

className="avatar"

src={avatar}

alt={description}

/>

);

}

<iframe title="Sandbox Preview" allow="accelerometer; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; clipboard-read; clipboard-write; xr-spatial-tracking;" src="https://786946de.sandpack-bundler-4bw.pages.dev/"></iframe>

Notice the difference between `className="avatar"`, which specifies an `"avatar"` CSS class name that makes the image round, and `src={avatar}` that reads the value of the JavaScript variable called `avatar`. That’s because curly braces let you work with JavaScript right there in your markup!

## Using curly braces: A window into the JavaScript world

JSX is a special way of writing JavaScript. That means it’s possible to use JavaScript inside it—with curly braces `{ }`. The example below first declares a name for the scientist, `name`, then embeds it with curly braces inside the `<h1>`:

[Fork](https://codesandbox.io/api/v1/sandboxes/define?parameters=N4IgZglgNgpgziAXKOAnAxgeggOwCYwAeAdAFYLIjoD2OALjPUiBALYAO1qdABMDwGU6qCOjoBZagR4BfHmFTVWPADohUMAIZi1AbhU42nbnx7oNmhgCVq1XnIVLV6rWIC0eJZnRQIjOnoGRly8asSYcHQAnrBwxOhwcIE4QRwhPACC7OzyisphmFnsyQY0OJE8inY8ALxmFta2dAAUnugArqz-xADmMHQAorBd9ABCUQCSeM1qVQEgAJQL-jhzxBr4MKgzODw8ADxCImKSBAB8Bnt7-0U8mBe7B5hHohJSMA_LIAA0LHCjuE0qCiSDAmigcBgMl-7G0AGtNH0yHBaEhQGUGExECBgJdnDhNF01IhnBYxMQCAA3NTfPFqSlbOAQWjE5wABmIHLZNLpIFYmlwrLUEQw2E2JHIPMeajg5gg7DoSSQfDxexldCB8xJs1cdDcspECrgPEimqlV2cACN2tA8EKXNo9Qb5YqeNbbearmoGJF7WSnXKjTwfbw3G5GJSauRPKxPWqQDBSDAdMqdY79YHXYnk_M8dDeQR2IwCDh0H4lSTcY94_77QA9ACMAE5iAAmYgNuOk3UeJT15ttjtdtPuZ1G-sAVk5nLUedp0pAVIAIjAi5tS-XWcAZAYZD8_gCCcDQeDIdCQOx2pbfFhcAQSAALOisKBoqi0TF0Zj7ACES4A8gAwgAKgAmgACgMPBPi-Dz7DBUA8FAmg4D0NRqIwahwQ-Wh4A81xdBqZgPkCkJ0OhIAAKrAQAYm4AAcWF4vshGaDwBJdBRlJ-AA7sY8xmB-_gUTxEB4HQD41FSogwG4oniQ-3w8LgEB0BA4IZuCMA1A2M4gPhBxqXQsBnEu1AdCMdD7JgRkmQY1k4ZoeH2ZaUhRAZ-x4BAlLKXgFFzFh1leZScGYK5eDufZmAIWc-4QP8gLHogYIQlCvxoFgRTIm-GL-MwRD8TwBBgu0UC8GA7SlmptA8MBUjUAAMvFLQLCqjxlBUHEwLUPAAOQAOIaD0XDMjwoHEDwABaQKaL1Kx7BodDtKguw7Ba8ENmcwBdTIvXGnVPBmTwTWRA5m14ssu4GHFCVHiCyWnmlIAZRE0SxPEiQ5UJWIgAAVG1eyuYQ-oQAAXrgPQkq5qAEKgbhAysO4pDg4VRAD8gfm4YKsNAUQknAKFwPqWwQGA808PyqA9LgJKtmy7CEOTsJ4F5qEkmyiMGAYD4NujlPUzgbh0NQ7Ds-TYCY0yoMwLTrYM5zyMPq2fNAgLQsi2LeIS_QIPS7T9OM1disAMwq1TuDq6LPAc1rktgzLPANvR8tG9zAAsZtq8LVs2482tOvbJINgAbC7OBI9zE6exb3ua37dt647bthxHOAPsH0eC7H1viwnDsNnLhvh1zpbvOj_u6_nbYwKwCsGKV6PM6zPRuLgvg4LJprcPrKclzdh5AvdKVnueDAcMhDDMOYWgMG4_puJo2QgDIQA&query=file%3D%252Fsrc%252FApp.js%26utm_medium%3Dsandpack&environment=create-react-app "Open in CodeSandbox")

```
export default function TodoList() {
  const name = 'Gregorio Y. Zara';
  return (
    <h1>{name}'s To Do List</h1>
  );
}
```

<iframe title="Sandbox Preview" allow="accelerometer; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; clipboard-read; clipboard-write; xr-spatial-tracking;" src="https://786946de.sandpack-bundler-4bw.pages.dev/"></iframe>

Try changing the `name` ’s value from `'Gregorio Y. Zara'` to `'Hedy Lamarr'`. See how the list title changes?

Any JavaScript expression will work between curly braces, including function calls like `formatDate()`:

```
const today = new Date();

function formatDate(date) {
  return new Intl.DateTimeFormat(
    'en-US',
    { weekday: 'long' }
  ).format(date);
}

export default function TodoList() {
  return (
    <h1>To Do List for {formatDate(today)}</h1>
  );
}
```

### Where to use curly braces

You can only use curly braces in two ways inside JSX:

1. **As text** directly inside a JSX tag: `<h1>{name}'s To Do List</h1>` works, but `<{tag}>Gregorio Y. Zara's To Do List</{tag}>` will not.
2. **As attributes** immediately following the `=` sign: `src={avatar}` will read the `avatar` variable, but `src="{avatar}"` will pass the string `"{avatar}"`.

## Using “double curlies”: CSS and other objects in JSX

In addition to strings, numbers, and other JavaScript expressions, you can even pass objects in JSX. Objects are also denoted with curly braces, like `{ name: "Hedy Lamarr", inventions: 5 }`. Therefore, to pass a JS object in JSX, you must wrap the object in another pair of curly braces: `person={{ name: "Hedy Lamarr", inventions: 5 }}`.

You may see this with inline CSS styles in JSX. React does not require you to use inline styles (CSS classes work great for most cases). But when you need an inline style, you pass an object to the `style` attribute:

```
export default function TodoList() {
  return (
    <ul style={{
      backgroundColor: 'black',
      color: 'pink'
    }}>
      <li>Improve the videophone</li>
      <li>Prepare aeronautics lectures</li>
      <li>Work on the alcohol-fuelled engine</li>
    </ul>
  );
}
```

Try changing the values of `backgroundColor` and `color`.

You can really see the JavaScript object inside the curly braces when you write it like this:

```
<ul style={
  {
    backgroundColor: 'black',
    color: 'pink'
  }
}>
```

The next time you see `{{` and `}}` in JSX, know that it’s nothing more than an object inside the JSX curlies!

### Pitfall

Inline `style` properties are written in camelCase. For example, HTML `<ul style="background-color: black">` would be written as `<ul style={{ backgroundColor: 'black' }}>` in your component.

## More fun with JavaScript objects and curly braces

You can move several expressions into one object, and reference them in your JSX inside curly braces:

```
const person = {
  name: 'Gregorio Y. Zara',
  theme: {
    backgroundColor: 'black',
    color: 'pink'
  }
};

export default function TodoList() {
  return (
    <div style={person.theme}>
      <h1>{person.name}'s Todos</h1>
      <img
        className="avatar"
        src="https://react.dev/images/docs/scientists/7vQD0fPs.jpg"
        alt="Gregorio Y. Zara"
      />
      <ul>
        <li>Improve the videophone</li>
        <li>Prepare aeronautics lectures</li>
        <li>Work on the alcohol-fuelled engine</li>
      </ul>
    </div>
  );
}
```

In this example, the `person` JavaScript object contains a `name` string and a `theme` object:

```
const person = {
  name: 'Gregorio Y. Zara',
  theme: {
    backgroundColor: 'black',
    color: 'pink'
  }
};
```

The component can use these values from `person` like so:

```
<div style={person.theme}>
  <h1>{person.name}'s Todos</h1>
```

JSX is very minimal as a templating language because it lets you organize data and logic using JavaScript.

## Recap

Now you know almost everything about JSX:

- JSX attributes inside quotes are passed as strings.
- Curly braces let you bring JavaScript logic and variables into your markup.
- They work inside the JSX tag content or immediately after `=` in attributes.
- `{{` and `}}` is not special syntax: it’s a JavaScript object tucked inside JSX curly braces.

## Try out some challenges

#### Challenge 1 of 3: Fix the mistake

This code crashes with an error saying `Objects are not valid as a React child`:

```
const person = {
  name: 'Gregorio Y. Zara',
  theme: {
    backgroundColor: 'black',
    color: 'pink'
  }
};

export default function TodoList() {
  return (
    <div style={person.theme}>
      <h1>{person}'s Todos</h1>
      <img
        className="avatar"
        src="https://react.dev/images/docs/scientists/7vQD0fPs.jpg"
        alt="Gregorio Y. Zara"
      />
      <ul>
        <li>Improve the videophone</li>
        <li>Prepare aeronautics lectures</li>
        <li>Work on the alcohol-fuelled engine</li>
      </ul>
    </div>
  );
}
```

Can you find the problem?