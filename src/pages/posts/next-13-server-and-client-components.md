---
layout: ../../layouts/Post.astro
title: 'Next 13 - Server and Client components'
metaTitle: 'Next 13 - Server and Client components'
metaDesc: 'What is the difference between server and client components in Next 13'
ogImage: /images/13-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/d807b46d-29a7-4ebd-c907-03f054cd3200
date: 2022-11-13T03:00:00.000Z
tags:
  - nextjs
---

With Next 13 the team made quite big changes regarding how components render.
Not that it's all-new, but they seem to have simplified it and changed the defaults.

So let's take a closer look at how rendering works in Next 13.

## What is Server vs. Client?

We'll first have to address what is seen as the server and the client.

- **Server**: A actual server that hosts your code can receive a request, do some calculations and send back a response once those are complete.
- **Client**: The browser a user's device sends a request to the server and does some calculations in the browser to render the correct layout.

As you can see, the tipping point lies in where the calculations happen.

So what exactly did the ecosystem look like before Next 13?

In general, with React, everything happens on the client side. Next solve this by breaking your React components down into pages that could partially be rendered on the server.
However, this generated HTML on the server, which had to be hydrated on the client again, meaning we needed extra JavaScript.

With the introduction of the clear distinguishment between server and client-side components, React can render on the server OR the client.

The new default in all this is server-side rendering.

## Server side: Static or Dynamic rendering

With this addition of being Server side first, we get another two choices.
Either we render statically or dynamically.

Let's take a closer look at what that means.

- **Static**: Both server and client components can be prerendered on the server at build time. This will cache the result and reuse that cache on the following requests. (Equivalent of SSG and ISR in pre-13 terms)
- **Dynamic**: Server and client components are rendered on request and will not be cached. (Equivalent of SSR pre-13 terms)

## How to create client components?

You might wonder, if these server components are the new default, how do I use client components?

And Next makes this super simple by adding a directive at the top of your file.

```js
'use client';

export default function YourPage() {
  //Client-side code
}
```

Yep, that directive will take care of everything!

## When to use which one?

It might feel tricky to know which one to use at which stage, so let's look at Next's directive on this.

Let's break it down by what you might need.

- Fetching data? -> Server component
- Access backend resources -> Server component
- Keep sensitive information on the server -> Server component
- Reduce JavaScript code -> Server component

- Add interactivity (click/change listeners) -> Client component
- Use state or lifecycle effects -> Client component
- Browser-only APIs -> Client component
- Custom hooks that need any of the above -> Client components

You might think, ok but surely they need to mix and match, and indeed they do.

The advice given by Next is that we opt to make component server-side where possible and extract the ones that need client-side rendering.

This way, our server components only need to render that specific small component on the client.
But more on this later on when we try them out.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
