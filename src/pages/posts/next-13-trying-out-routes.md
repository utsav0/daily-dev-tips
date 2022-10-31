---
layout: ../../layouts/Post.astro
title: 'Next 13 - Trying out routes'
metaTitle: 'Next 13 - Trying out routes'
metaDesc: 'Giving the new Next 13 routes a try'
ogImage: /images/09-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/83445073-afcb-4586-ef34-f90002ea1300
date: 2022-11-09T03:00:00.000Z
tags:
  - nextjs
---

If you are an avid reader of my blogs, you'll learn that I learn best by trying things out.

This article will look at the new Next 13 ways of routing.

To get started, we first have to install a new Next 13 app, which is created with the following command at the time of writing.

```bash
npx create-next-app@latest --experimental-app
```

## Creating routes

If we open up the project, we already see that inside our `app` directory, we get a `layout.tsx`, and `page.tsx` file.
The layout file is responsible for our layout and the page for our `/` home page.

We can go multiple routes to add a new page, but let's say we want to create the following pages.

- /dashboard/settings
- /dashboard/account

To achieve this, we have to start by creating our dashboard folder. This folder can eventually hold our global dashboard layout.
Create the `settings` and `account` folders in that folder.
And again, inside those, go ahead and create a `page.tsx` for each.

The whole structure will look like this:

- 🗂️ app
  - 🗂️ dashboard
    - 🗂️ settings
      - 📃 page.tsx
    - 🗂️ account
      - 📃 page.tsx

I do like how this makes every component very clear and explanatory of what it does.

Each page will return what it's on for now.
As for the `settings/page.tsx`, we use the following.

```js
export default function SettingsPage() {
  return <h1>This is my settings page</h1>;
}
```

And for the account page:

```js
export default function AccountPage() {
  return <h1>This is my account page</h1>;
}
```

Now, if you run your application with `npm run dev`, we will be able to visit both on:

- `http://localhost:3000/dashboard/settings`
- `http://localhost:3000/dashboard/account`

## Routing groups

Perhaps you like having combined layouts for the settings and account, but you don't want to include the `dashboard` param in the URL.

For this, we can leverage routing groups, which refer to a group of routes that can share a layout but doesn't get added to the URL.

To achieve this, rename `dashboard` to `(dashboard)`.

And now, we can visit our pages on the following URLs.

- `http://localhost:3000/settings`
- `http://localhost:3000/account`

## Conclusion

We can achieve a lot of excellent routing options with the new flows.
They make it super dynamic yet flexible to layout out from here.

In the following article, we'll look at how the layout will look and what will be shared between the pages.

If you are keen, I uploaded the code to [GitHub](https://github.com/rebelchris/next-13/tree/page-options), so you can look over it.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
