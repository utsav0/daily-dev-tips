---
layout: ../../layouts/Post.astro
title: 'A glance at Turbopack'
metaTitle: 'A glance at Turbopack'
metaDesc: 'What exactly is Turbopack and should we be looking at it?'
ogImage: /images/17-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/e2079e10-511d-4369-7502-3f80e5e04300
date: 2022-11-17T03:00:00.000Z
tags:
  - nextjs
---

Turbopack got announced with the release of Next 13, and is deemed to become the successor of Webpack.

If you're currently using Webpack for bundling, you might know the struggles of long first boots and generic slow bundling.
(I mean, slow is all relative)

But bundling certainly could happen faster, so the creators of Webpack, Vercel, and Next came together and introduced us to Turbpack.

At the time of writing, it's still in the alpha phase, so not ready for production, but a perfect time to explore it.

Turbopack can already be used with Next 13; in the future, you can also migrate your non-Next projects to it.

## Trying it out

To test out Turbopack, you can start an example code with the following command.

```bash
npx create-next-app --example with-turbopack
```

Now run the dev server by running:

```bash
npm run dev
```

Your startup and update time should be almost instant now!
They mention the bigger the application, the more you'll benefit from it.

## Background

So why is Turbopack so fast?

The first point is that it's built on Rust, which has proven to be a fast language.

For instance, you might have played around with Vite, which is already way faster than Webpack. However, Vite has one downside: it becomes slower for bigger applications.
This is due to how it bundles singular modules on a browser level.

With Turbopack, they choose to go for something called function-level caching. Which computes whether something called has to be refreshed or not.
Doing this and serving cache for partial functions that don't change your experience as a developer becomes way faster.

As a super high-level example, you change `file1` Turbopack receives the change file event and can compute the new combined files that use this file.

By doing this, it doesn't have to re-compute the entire application.

This all sounds very cool, but it's dependent on singular changes, so how do they get to start up time so fast?
And it's basically due to page-by-page rendering.
There's no point in bundling your entire application at run time as you only request one page at a time.
In Turbopack, they solved this by only rendering the pages when requested.

## What to expect

I hope they roll out the individual CLI soon, as allowing existing (non-Next) Webpack apps to migrate makes sense.

The benchmarks and initial feeling for it feels really good, and I have high hopes for Turbopack.

By the looks of their roadmap, they're taking a lot of inspiration from their SWC migration in how they will port essential Webpack plugins.

I'm pretty sure this will take a while to achieve.
The future of bundling does look promising 🙏.

How do you feel about Turbopack?

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
