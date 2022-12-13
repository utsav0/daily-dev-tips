---
layout: ../../layouts/Post.astro
title: 'Vendure - Storefronts'
metaTitle: 'Vendure - Storefronts'
metaDesc: 'Looking at the Storefront options for Vendure'
ogImage: /images/14-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/d9fce0e2-c0f0-4d8e-b922-c51dc0e49000
date: 2022-12-14T03:00:00.000Z
tags:
  - vendure
---

When setting up a commerce website, you'll likely need a storefront. This will be what the end users will use to order your products.

In the case of Vendure, we are open to creating our own, but luckily for us, they have some fantastic starters already set up.

At the time of writing, they have official starters for:

- Remix
- Vue Storefront
- Next.js
- Angular

Since I started a [series on Remix](https://daily-dev-tips.com/tags/remix/), I have been eager to try that.

## Installing the Remix Storefront

To install the Storefront, we can clone the [Git repo](https://github.com/vendure-ecommerce/storefront-remix-starter) and install it.

```bash
git clone git@github.com:vendure-ecommerce/storefront-remix-starter.git

cd storefront-remix-starter

npm install
```

Then, create a `.env` file in the root and point it to our local Vendure server.

```js
VENDURE_API_URL=http://localhost:3001/shop-api
```

Now go ahead and run the Storefront with: `npm run dev`.

> Note: Make sure your Vendure server is running.

And visit the Storefront on [http://localhost:3000/](http://localhost:3000/).

![Remix Storefront example](https://cdn.hashnode.com/res/hashnode/image/upload/v1670909460542/tTALBNZ5F.png)

Play around with it and try to order some products. You'll see it's blazing fast!

## Other options

As mentioned, you can use some other supported Storefronts, which you can find on the [Vendure website](https://www.vendure.io/integration/).

And if you want to use something together, you can take inspiration from any of the existing integrations and create your own new integration.

Since, in the end, they query the API and have no concrete direct implementations in place.

I'm super stoked to see this freedom of front-end in a (headless) commerce system being so well demoed out.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
