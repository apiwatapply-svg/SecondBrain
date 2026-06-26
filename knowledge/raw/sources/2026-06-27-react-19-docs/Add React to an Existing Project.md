---
title: "Add React to an Existing Project"
source: "https://react.dev/learn/add-react-to-an-existing-project"
author:
published:
created: 2026-06-27
description: "The library for web and native user interfaces"
tags:
  - "clippings"
---
If you want to add some interactivity to your existing project, you don’t have to rewrite it in React. Add React to your existing stack, and render interactive React components anywhere.

### Note

**You need to install [Node.js](https://nodejs.org/en/) for local development.** Although you can [try React](https://react.dev/learn/installation#try-react) online or with a simple HTML page, realistically most JavaScript tooling you’ll want to use for development requires Node.js.

## Using React for an entire subroute of your existing website

Let’s say you have an existing web app at `example.com` built with another server technology (like Rails), and you want to implement all routes starting with `example.com/some-app/` fully with React.

Here’s how we recommend to set it up:

1. **Build the React part of your app** using one of the [React-based frameworks](https://react.dev/learn/creating-a-react-app).
2. **Specify `/some-app` as the *base path*** in your framework’s configuration (here’s how: [Next.js](https://nextjs.org/docs/app/api-reference/config/next-config-js/basePath), [Gatsby](https://www.gatsbyjs.com/docs/how-to/previews-deploys-hosting/path-prefix/)).
3. **Configure your server or a proxy** so that all requests under `/some-app/` are handled by your React app.

This ensures the React part of your app can [benefit from the best practices](https://react.dev/learn/build-a-react-app-from-scratch#consider-using-a-framework) baked into those frameworks.

Many React-based frameworks are full-stack and let your React app take advantage of the server. However, you can use the same approach even if you can’t or don’t want to run JavaScript on the server. In that case, serve the HTML/CSS/JS export ([`next export` output](https://nextjs.org/docs/advanced-features/static-html-export) for Next.js, default for Gatsby) at `/some-app/` instead.

## Using React for a part of your existing page

Let’s say you have an existing page built with another technology (either a server one like Rails, or a client one like Backbone), and you want to render interactive React components somewhere on that page. That’s a common way to integrate React—in fact, it’s how most React usage looked at Meta for many years!

You can do this in two steps:

1. **Set up a JavaScript environment** that lets you use the [JSX syntax](https://react.dev/learn/writing-markup-with-jsx), split your code into modules with the [`import`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import) / [`export`](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export) syntax, and use packages (for example, React) from the [npm](https://www.npmjs.com/) package registry.
2. **Render your React components** where you want to see them on the page.

The exact approach depends on your existing page setup, so let’s walk through some details.

### Step 1: Set up a modular JavaScript environment

A modular JavaScript environment lets you write your React components in individual files, as opposed to writing all of your code in a single file. It also lets you use all the wonderful packages published by other developers on the [npm](https://www.npmjs.com/) registry—including React itself! How you do this depends on your existing setup:

- **If your app is already split into files that use `import` statements,** try to use the setup you already have. Check whether writing `<div />` in your JS code causes a syntax error. If it causes a syntax error, you might need to [transform your JavaScript code with Babel](https://babeljs.io/setup), and enable the [Babel React preset](https://babeljs.io/docs/babel-preset-react) to use JSX.
- **If your app doesn’t have an existing setup for compiling JavaScript modules,** set it up with [Vite](https://vite.dev/). The Vite community maintains [many integrations with backend frameworks](https://github.com/vitejs/awesome-vite#integrations-with-backends), including Rails, Django, and Laravel. If your backend framework is not listed, [follow this guide](https://vite.dev/guide/backend-integration.html) to manually integrate Vite builds with your backend.

To check whether your setup works, run this command in your project folder:

```
npm install react react-dom
```

Then add these lines of code at the top of your main JavaScript file (it might be called `index.js` or `main.js`):

[Fork](https://codesandbox.io/api/v1/sandboxes/define?parameters=N4IgZglgNgpgziAXKOAnAxgeggOwCYwAeAdAFYLIjoD2OALjPUiBALYAO1qdABMD-lQwAhgwBK1arwC-PMKmqseAciHD0dALR5FmdFAiM6ygNwAdHBcyYeAYVjDUPOgAsYPIhDh1cAcx4AEgAqALIAMgK0DPQWOugArqxGxABG1HgAnsS4ODCoweE8ALwqADx4EABuPBB4RWYgwuzsDQB8pZgVla2mFlY2YowEThnU8U6D6rw0HLRGNTjeIngWNIu8ClLFAmriknQAFHGJyb4wdACisEn0AEIZAJJ4B8pN7MoAlB_mOJt0xEJ8HkDqUXABGVoBGBQKDUAA0PAA7lwoHgOuDWt8LCA4Sw4LdcI4MkgwMIoHAYNJcex1ABrYRnMhwWhIUBraJ0ZjACw8HgNHDCJINRB8kBqDTEAiVBpwnmiyp5OAQWjC0UABmIGrVMrlDVYwlwqoamDQWFwBBI5B1OF5DTgggg7DocFV3JtvNF3kcdCNYpEGk09tQjudPC93GtHtFKXi0BWSFF4q0QZDcB4MbjkY9DQY3l9ScDDqdadzvE0mkYlSK5B0rCztpAMFIMA0-f9yaLoabLZ9IDlVN1IAI7CGjHQhhdCbdUYaSd9AD0wQBOYgAJmIYPrifb2kUC-Xa43W9nO5TxYXAFZNZqGv3Ze6GlKACIwEdAnDj-Cu6QWaQ4vEEgKqDEogpLkpS1LxCkBhmkCJAuHQrBQKyVBREYzClAAhE-ADythBAAmgAChcPAIUhrQWKCiFQJR7qgss7Q-HQsCtCEGQ8G8HTMax6KMXKpRpJkdFRlh5Y8ARYxOJ43h-DwNJnJE9DzAcuDOC4XgeIQgrsLACIQLwZyhkIunqDAeAfDw5YiR65RVDUdSzvsbQdF0NkdEJGR0eiNF0f-XiAUSJJkhSVIgKaJp0BksBwMQ6BwBQbJoUwiAgAAVHwcppIQgYQAAXn4IppKgwyaNlPw_pYOCeZl7pgFEmikqw0AZCKcDCIsgZ5BAYA_Ly-qoL4uAiquarsIQfXycIeAVDgvgimqFV9Dg4K1f1jhDTgmh0NQ7ALZN9X0LleUwCNq7jUtVUuKua08ANm3bbt-1yodyb5adPCjRdv7LS4ADMt33bgj17Twi0vQ1SonSKYIABzfTglUWC4AAsgMbcDO2g-DdWQ-9MMAGwI0jK0Xujg2Y09YMHXj0M8GCKPE79BPkw9WPPbjR1Qx9YLnRNP1VTQBC3a9x082uMCsJdFjxFAt00jNfiaLgBi5IGdDeiNY384jy3-fihLAcF4HSGFDAcFAogwMwggiAwmgFm8IDSEAA&query=file%3D%252Fsrc%252Findex.js%26utm_medium%3Dsandpack&environment=create-react-app "Open in CodeSandbox")

```
import { createRoot } from 'react-dom/client';

// Clear the existing HTML content
document.body.innerHTML = '<div id="app"></div>';

// Render your React component instead
const root = createRoot(document.getElementById('app'));
root.render(<h1>Hello, world</h1>);
```

<iframe title="Sandbox Preview" allow="accelerometer; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; clipboard-read; clipboard-write; xr-spatial-tracking;" src="https://786946de.sandpack-bundler-4bw.pages.dev/"></iframe>

If the entire content of your page was replaced by a “Hello, world!”, everything worked! Keep reading.

### Note

Integrating a modular JavaScript environment into an existing project for the first time can feel intimidating, but it’s worth it! If you get stuck, try our [community resources](https://react.dev/community) or the [Vite Chat](https://chat.vite.dev/).

### Step 2: Render React components anywhere on the page

In the previous step, you put this code at the top of your main file:

```
import { createRoot } from 'react-dom/client';

// Clear the existing HTML content
document.body.innerHTML = '<div id="app"></div>';

// Render your React component instead
const root = createRoot(document.getElementById('app'));
root.render(<h1>Hello, world</h1>);
```

Of course, you don’t actually want to clear the existing HTML content!

Delete this code.

Instead, you probably want to render your React components in specific places in your HTML. Open your HTML page (or the server templates that generate it) and add a unique [`id`](https://developer.mozilla.org/en-US/docs/Web/HTML/Global_attributes/id) attribute to any tag, for example:

```
<!-- ... somewhere in your html ... -->
<nav id="navigation"></nav>
<!-- ... more html ... -->
```

This lets you find that HTML element with [`document.getElementById`](https://developer.mozilla.org/en-US/docs/Web/API/Document/getElementById) and pass it to [`createRoot`](https://react.dev/reference/react-dom/client/createRoot) so that you can render your own React component inside:

[Fork](https://codesandbox.io/api/v1/sandboxes/define?parameters=N4IgZglgNgpgziAXKOAnAxgeggOwCYwAeAdAFYLIjoD2OALjPUiBALYAO1qdABMD-lQwAhgwBK1arwC-PMKmqseAciHD0dALR5FmdFAiM6ygNwAdHBbABXHBoi0eAOWEA3CAHNRDnACFhqAAUAJR8Fjw8mJg8ACoA8gAicYg8AIIa1sJQUACePGzssKxGPMI8OG6e3o4ARgHhPEJ01qg4PAA8ABYAjAB8ABIw2dRyCkpiIhoAhO2YPb3mONIWFjQ4cLw6rE7UBDwAvDw66NbF9MQeMHQAokVGvjkAkniByhXuXnQ-ysGLaxuNSS8Q6CETiIGBLY7Ai_CwKKTEIT4GBBdouD7VPwBSK9WE4EAAGhYcF8uACOSQYCycBg0iJ7HUAGthJcyHBaEhQGsGExECBgA0zCAKsUhSkhWoNMQCK4hQTBSBXCi4D4xTwhQAGYhajVyhWsYS4NVCzBoLC4Agkch6trqkBwQQQdh0OBqgW2iJCjYBOjGkCSrQO1BOl08b3cG0RT0gGrWaB4P0BzRBkNwHix-ORqNChgbROTQOO51p3O8TSaRiufbkLZZ6MwUgwDT59SF4PFngNpu-kANOkKgjsRgEOyGV1IMIeu0Bv0APW6AE5iAAmYjdOvTgvaRRzxcrtcbiVblPFucAVm12qFffltqFMoSMCHyNH8DdyyWhOJpIqqApiCpKAaTpEB2GsGoDHNZESE6OhWCgTkqFoHk6GYdopiSABhGIAE0AAVrh4WD4N6CwujgqBSNtLoRDwXp2i-OhYF6ABZPJhHYdhZkY5jZk6WiqIidoal2HJBKjdp2F6GJOggNMGVQFlFPYTp8jTMoFN4agwB4foYhYgAZYhZikhohPefI8H2IV3iqL5aCFejMHecShKkmS5J4BSlI41TPOpEYNJ9HhtN0_SjJM8TZhEvAxLIuYKKor85J_clKWpWkiTNU06ByWA4GIdA4AoLlkKMZgACpJwiETCGTCAAC9cA8FIRNQAhUE0WrFg_CwYryd0IjAZDNCpVhoByFI4GEdZkxRCAwEWCIDVQDxcBSZcNXYQglq84Q8DwZqUg1HqVhwHpqp4Fa1pwTQ6Godhjt24b6HqhqYA25dttOyxzuXS7rtwO6HqehoXsDRqPp4TbvosXrzoAZgBgIbuBx6eBOsGRpVd6Um6AAOWGljOzoABZkdWoH7vRzHbXBt6oe6AA2In4c6M8KdR6nQbp7HIbx0nWZJpnOapkGMeevncZ4bovp2uGzpoPZBrkKXGZXGBWB-ixrCgS6GQO5rNFwAwcBgZM6B9Datvl4nfuSkkyT_dKgNpECGA4KBRBgZhQW9zQkw49gQGkIA&query=file%3D%252Fsrc%252Findex.js%26utm_medium%3Dsandpack&environment=create-react-app "Open in CodeSandbox")

```
import { createRoot } from 'react-dom/client';

function NavigationBar() {
  // TODO: Actually implement a navigation bar
  return <h1>Hello from React!</h1>;
}

const domNode = document.getElementById('navigation');
const root = createRoot(domNode);
root.render(<NavigationBar />);
```

Notice how the original HTML content from `index.html` is preserved, but your own `NavigationBar` React component now appears inside the `<nav id="navigation">` from your HTML. Read the [`createRoot` usage documentation](https://react.dev/reference/react-dom/client/createRoot#rendering-a-page-partially-built-with-react) to learn more about rendering React components inside an existing HTML page.

When you adopt React in an existing project, it’s common to start with small interactive components (like buttons), and then gradually keep “moving upwards” until eventually your entire page is built with React. If you ever reach that point, we recommend migrating to [a React framework](https://react.dev/learn/creating-a-react-app) right after to get the most out of React.

## Using React Native in an existing native mobile app

[React Native](https://reactnative.dev/) can also be integrated into existing native apps incrementally. If you have an existing native app for Android (Java or Kotlin) or iOS (Objective-C or Swift), [follow this guide](https://reactnative.dev/docs/integration-with-existing-apps) to add a React Native screen to it.