---
layout: ../../layouts/Post.astro
title: 'Storybook - Using loaders'
metaTitle: 'Storybook - Using loaders'
metaDesc: "Let's take a look at Storybook's loaders and how they work"
ogImage: /images/24-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/c9f78209-cbc6-4f67-6331-c15dfc2a2900
date: 2022-11-24T03:00:00.000Z
tags:
  - storybook
---

Loaders are still an experimental function that can be used to add data for a story, and it's [decorators](https://daily-dev-tips.com/posts/storybook-using-decorators/).

The loaders are run before the story renders, and whatever is loaded gets injected into the render context.
You can use these loaders to load any asset or even fetch data from an API.

We get two ways of loading that we'll look into, one is for a specific story, and one is for your global system.

## Loading data for a story

Let's say we have a specific item that needs rendering instead of mocking the hard-coded data. We can opt to load it from a remote API.

This could be a mock API, as you'll see in the example, or your actual API if it's public data.

Let's take the example of a story that renders a blog item card.

```js
import React from 'react';

import fetch from 'node-fetch';

import { BlogItem } from './BlogItem';

export default {
  title: 'BlogItem'
  component: BlogItem,
};

export const Primary = (args, { loaded: { blogItem } }) => <BlogItem {...args} {...blogItem} />;
Primary.loaders = [
    async () => ({
      blogItem: await (await fetch('https://jsonplaceholder.typicode.com/posts/1')).json(),
    }),
];
```

Now our item will load whatever the API returns. This could be useful to try against a vast majority of randomized test items.

## Loading global data

In some cases, you might want to prepare a global loader, for instance, a logged-in user attribute.

We can add these loaders into our `.storybook/preview.js` file like this.

```js
import fetch from 'node-fetch';

export const loaders = [
  async () => ({
    currentUser: await (
      await fetch('https://jsonplaceholder.typicode.com/users/1')
    ).json(),
  }),
];
```

Now in every story, you can use the `loader.currentUser` value like this.

```js
export const Primary = (args, { loaded: { currentUser } }) => (
  <BlogItem {...args} {...currentUser} />
);
```

Loaders can be a super reliable way to set up reusable data that flows down to the excellent story without you having to do it repeatedly.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
