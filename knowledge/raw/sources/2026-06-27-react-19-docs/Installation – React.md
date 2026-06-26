---
title: "Installation – React"
source: "https://react.dev/learn/installation"
author:
published:
created: 2026-06-27
description: "The library for web and native user interfaces"
tags:
  - "clippings"
---
## Installation

React has been designed from the start for gradual adoption. You can use as little or as much React as you need. Whether you want to get a taste of React, add some interactivity to an HTML page, or start a complex React-powered app, this section will help you get started.

## Try React

You don’t need to install anything to play with React. Try editing this sandbox!

[Fork](https://codesandbox.io/api/v1/sandboxes/define?parameters=N4IgZglgNgpgziAXKOAnAxgeggOwCYwAeAdAFYLIjoD2OALjPUiBALYAO1qdABMDwGU6qCOjoBZagR4BfHmFTVWPADohUMAIZi1AbhU42nbnx7oNmhgCVq1XnIVLV6rWIC0eJZnRQIjOnoGRly8asSYcHQAnrBwxOhwcIE4QRwhPACC7OzyisphmFnsyQY0OJE8inY8ALxmFta2dAAUnugArqz-xADmMHQAorBd9ABCUQCSeM1qVQEgAJQL-jhzxBr4MKgzODw8ADxCImKSBAB8Bnt7-0U8mBe7B5hHohJSMA_LIAA0LHCjuE0qCiSDAmigcBgMl-7G0AGtNH0yHBaEhQGUGExECBgJdnDhNF01IhnBYxMQCAA3NTfPFqSlbOAQWjE5wABmIHLZNLpIFYmlwrLUEQw2E2JHIPMeajg5gg7DoSSQfDxexldCB8xJs1cdDcspECrgPEimqlV2cACN2tA8EKXNo9Qb5YqeNbbearmoGJF7WSnXKjTwfbw3G5GJSauRPKxPWqQDBSDAdMqdY79YHXYnk_M8dDeQR2IwCDh0H4lSTcY94_77QA9ACMAE5iAAmYgNuOk3UeJT15ttjtdtPuZ1G-sAVk5nLUedp0pAVIAIjAi5tS-XWcAZAYZD8_gCCcDQeDIdCQOx2pbfFhcAQSAALOisKBoqi0TF0Zj7ACES4A8gAwgAKgAmgACgMPBPi-Dz7DBUA8FAmg4D0NRqIwahwQ-Wh4A81xdBqZgPkCkJ0OhIAAKrAQAYm4AAcWF4vshGaDwBJdBRlJ-AA7sY8xmB-_gUTxEB4HQD41FSogwG4oniQ-3w8LgEB0BA4IZuCMA1A2M4gPhBxqXQsBnEu1AdCMdD7JgRkmQY1k4ZoeH2ZaUhRAZ-x4BAlLKXgFFzFh1leZScGYK5eDufZmAIWc-4QP8gLHogYIQlCvxoFgRTIm-GL-MwYDtKWam0DwADiGj9LgPTNPwHEwLICwqo8Gh0O0qC7PBDZnAAEjAUBQNQSnAHVMgOV1Kw7ikOBEPxPAEGC7RQLwBVFcyuxFM0jVVnsLVtR15UwJVqHsYS2lqDxXBQHaIB3A8k1xQlR4gslp5pSAGURNEsTxIkOVCViIAAFRNXsrmEPqEAAF5VSSrmoAQqBuGDE0GAY4VRCD8gfm4YKsNAUQknAKFwPqWwQGAKx7PyqA9LgJKtmy7CEJTPCwngXmoSSbIo1ND4Npj1O0zgbh0NQ7BcyzYDY0ykMwPTrZMzzBgPq2AtAkLItixLeJS_QEOy_TjPM7uqM4A-ADMas07gmvizw3M69LUNyzwDb0YrJu8wALFbGui3bDuPLrTrOySDYAGwezgk3KxOvs2_72tB07Buu17Ucx2b4fx8Lif25LKcuw2CvG9Hps0NI21Y3rMtF22MCsErOCLZjbMcz0bi4L4036hq3CGxnpsPYeQLPSlZ7ngwHDIQwzDmFoDBuP6biaNkIAyEAA&query=file%3D%252Fsrc%252FApp.js%26utm_medium%3Dsandpack&environment=create-react-app "Open in CodeSandbox")

function Greeting({ name }) {

return \<h1>Hello, {name}\</h1>;

}

export default function App() {

return \<Greeting name="world" />

}

<iframe title="Sandbox Preview" allow="accelerometer; camera; encrypted-media; geolocation; gyroscope; hid; microphone; midi; clipboard-read; clipboard-write; xr-spatial-tracking;" src="https://786946de.sandpack-bundler-4bw.pages.dev/"></iframe>

You can edit it directly or open it in a new tab by pressing the “Fork” button in the upper right corner.

Most pages in the React documentation contain sandboxes like this. Outside of the React documentation, there are many online sandboxes that support React: for example, [CodeSandbox](https://codesandbox.io/s/new), [StackBlitz](https://stackblitz.com/fork/react), or [CodePen.](https://codepen.io/pen?template=QWYVwWN)

To try React locally on your computer, [download this HTML page.](https://gist.githubusercontent.com/gaearon/0275b1e1518599bbeafcde4722e79ed1/raw/db72dcbf3384ee1708c4a07d3be79860db04bff0/example.html) Open it in your editor and in your browser!

## Creating a React App

If you want to start a new React app, you can [create a React app](https://react.dev/learn/creating-a-react-app) using a recommended framework.

## Build a React App from Scratch

If a framework is not a good fit for your project, you prefer to build your own framework, or you just want to learn the basics of a React app you can [build a React app from scratch](https://react.dev/learn/build-a-react-app-from-scratch).

## Add React to an existing project

If want to try using React in your existing app or a website, you can [add React to an existing project.](https://react.dev/learn/add-react-to-an-existing-project)

### Note

#### Should I use Create React App?

No. Create React App has been deprecated. For more information, see [Sunsetting Create React App](https://react.dev/blog/2025/02/14/sunsetting-create-react-app).

## Next steps

Head to the [Quick Start](https://react.dev/learn) guide for a tour of the most important React concepts you will encounter every day.