---
layout: ../../layouts/Post.astro
title: "Next 13: What's new"
metaTitle: "Next 13: What's new"
metaDesc: 'A close look at the new and improved Next.js 13'
ogImage: /images/08-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/9ec722ab-020a-42b3-d837-be8fa110d700
date: 2022-11-08T03:00:00.000Z
tags:
  - nextjs
---

Last week we got introduced to Next 13, which got some mixed reviews from the public.
I won't go into detail about these reviews in this article, but let's look at what got introduced to us.

## Routing change

The first change we see is the way routing is handled.
Before, we were required to create a `pages` component for routing. However, everything inside the `app` folder becomes a route now.

The cool part is that we are not expected to upgrade all at once, as our `pages` structure will keep working.
We can migrate to the `app` layer as we go.

### Layouts

This new change in routing enabled us to create more complex interfaces.
For example, inside the `app` directory, we can create a dashboard folder with individual layout components.

The primary page inside this folder can have the main structure of the page, while next to it, we can have a `layout.js` file for the actual layout of this set of components.

Besides these two files, we get some other excellent special files we can use:

- `layout.js`: Defines the shared layout across multiple pages inside this folder.
- `page.js`: The specific UI for the page defined as the folder name.
- `loading.js`: A optional file to create a loading component for this specific app part.
- `template.js`: A optional file similar to the layout, but when navigating, a new component is mounted, and the state is not shared. It can be used when you need enter/exit animations on a page.
- `head.js`: A optional file can be used to define the `<head>` for this subsection of files.

We might dive into this perception of routing and layout in another article, as it's cool to explore more in-depth.

### Server components

Another cool new thing regarding the routing change is the ability to support server components.
The idea is that this will help to create a faster page load and less JavaScript on the end page.

All your components inside the `app` directory are server components. When a route is loaded, the Next and React runtime will be loaded, which is cacheable and predictable in size. The runtime won't increase in size, and it's loaded async. It enables your HTML to be loaded from the server and then enhanced by the client.

You can still mark components as client side only. This could be handy when you need interactivity, event listeners, or state.

More on these components later on.

### Streaming

We get a streaming-driven solution if we take the above two elements.

This means our app can render static elements without waiting for all the components that need data fetching or slow load.
Each server-rendered component can take time to render, but the client already sees the main layout and loading components for those server-side components that are still loading.

This powerful concept allows us to provide a better user experience.

## Data fetching

With the introduction of these server-side components, we also get a new and powerful way to fetch data inside parts.

A basic example of a component fetching data from some API.

```js
// app/page.js
async function getData() {
  const res = await fetch('https://api.example.com/...');
  // The return value is *not* serialized
  // You can return Date, Map, Set, etc.
  return res.json();
}

// This is an async Server Component
export default async function Page() {
  const data = await getData();

  return <main>{/* ... */}</main>;
}
```

They extended the native fetch API to React/Next, so it all used one flexible way of fetching data.
It comes down to all the benefits of the previous implementations into one.

## Turbopack

We also see a new Webpack alternative called Turbopack. It's being developed and maintained by the original creator of Webpack.

So far, their numbers don't lie, as it looks super impressive:

- 700x faster than Webpack
- 10x faster than Vite
- 4x faster cold start compared to webpack

Especially the cold start. I'm eager to try otu, as this was my biggest hurdle with Webpack.

Turbopack is written in Rust, which has proven to be the super-fast language on the block for other tools, so there are high hopes for this one.

## New plugins

There are also quite a few new/upgraded plugins, which we won't dive into too much detail, but here they are:

- `next/image`: Next 13 ships a new image component, which comes with many upgrades, less JavaScript, is easier to configure and is faster.
- `next/font`: A brand new font system that can be used to load optimized versions of fonts.
- `next/link`: Basically, an upgraded developer experience by needing less config.

## OG Images

We get a new integrated way of generating OG images, which could be a pain point due to the loading your pages would use.
This new plugin solves many of these pain points, and I'm eager to test it out and write more about it.

## Conclusion

Next 13 is packed with a lot of new and improved things. Keen to try out how they improved the speed of everything.

And keen to see how it all works in production apps.
So keep an eye out for upcoming articles.

To wrap it up: What was your favorite addition in Next 13?

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
