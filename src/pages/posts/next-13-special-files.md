---
layout: ../../layouts/Post.astro
title: 'Next 13 - Special files'
metaTitle: 'Next 13 - Special files'
metaDesc: 'What are the new Next 13 special files and how do they work'
ogImage: /images/11-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/4b550cad-c2ba-4e2b-1a95-c9b83a52a400
date: 2022-11-11T03:00:00.000Z
tags:
  - nextjs
---

A super cool new addition to this new routing/layout style of Next 13 is the fact that we get a couple of special files that make our application more robust.

The concept of these files already existed, but we had to wrap many elements with Suspense to achieve the same manually.

Let's take a look at which ones we get:

- `page.tsx`: We already used this to create our pages.
- `layout.tsx`: Defined to create the layouts per folder.
- `loading.tsx`: Optional loading component can be used to show a loading state.
- `error.tsx`: Optional error state can be used only to show the error in a specific application part.
- `template.tsx`: Optional and very similar to layout, but this one will always remount on navigation, and the state is not shared.
- `head.tsx`: Optional to add a different `<head>` tag for a specific route.

For this article, we'll look into loading and error components.

## Next 13 loading component

Let's say you have a component that can initially take quite some time to load.
We will block the page until the load is done without any loading or handling of the load.

Since the loading only would happen in one of our components, we get the fantastic feature of loading components.
By adding these to our folder, we can show the time it takes to load.

The big benefit being it won't block the rest of the page or our navigation.

To add these files, add a `loading.tsx` file. Some example content could be:

```js
export default function Loading() {
  return <p>Loading account details</p>;
}
```

I placed this in the `app/dashboard/account/loading.tsx` spot. We'll work on testing it out in the following article.

## Next 13 error component

Like the loading component, it could be that only one element on the page gives us an error.
By default, this could crash out the entire application, but with this new error component, we can only show that piece of the puzzle as an error.

You can add this file by creating an `error.tsx` file in your component folder.

> Note: This has to be a client component!

An example error component would look like this.

```js
'use client';

export default function Error({
  error,
  reset,
}: {
  error: Error,
  reset: () => void,
}) {
  return (
    <div>
      <p>Something went wrong!</p>
      <button onClick={() => reset()}>Reset error boundary</button>
    </div>
  );
}
```

Now, we show this snippet whenever an error happens in this component, and the user can retry the component render.

I added these components on GitHub with some sample code we'll dive into later, but you can already check it out in [this branch](https://github.com/rebelchris/next-13/tree/special-files).

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
