---
layout: ../../layouts/Post.astro
title: 'Making the site responsive - part 11'
metaTitle: 'Making the site responsive - part 11'
metaDesc: 'Making sure our Next.js portfolio website is fully responsive'
ogImage: /images/18-10-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/931d9b35-f4c3-4bd5-a0a4-81430d076900
date: 2022-10-18T03:00:00.000Z
tags:
  - nextjs
---

Now that we have our basic structure styled and working let's take some time to look at the responsive aspect.

We haven't considered it, so let's see what happens if we view the homepage on a mobile device.

![Responsive homepage no styling yet](https://cdn.hashnode.com/res/hashnode/image/upload/v1665225560634/FOZ9ce9OY.png)

I'm surprised by how well it already looks.
Some takeaways that we have to focus on.

- Header spacing left and right
- Pushing the profile image to its section
- Recent posts should show under each other

The rest is pretty much solid!
So let's get started.
If you wish to follow along for only the responsive part, use the following [GitHub branch](https://github.com/rebelchris/next-portfolio/tree/part-10) as your starting point.

## Making the homepage responsive

We'll start with the header, which needs more spacing on the sides.

Since we only want the padding to be added on the mobile version, we can "unset" it on the desktop.
So open the `header.js` file and add the following classes to the header element class list.

```html
<header className="px-6 md:px-0"></header>
```

Now let's move to the intro section, where we want the social image to be on its line.
However, I want the image to be on top of the text. Luckily for us, flexbox comes with a reverse option.

For this one, we need to modify the `introHeader.js` file and add the following options to the first div inside the header.

```html
<div className="flex-col-reverse md:flex-row"></div>
```

The last part we wanted to adjust was the recent post section. This simply needs to show the items under each other instead of next to each other.

Since we used a grid for this, we can define a different grid for the mobile view.
Then on the desktop, we modify it to show in the 2-column grid.

Open the `recentPosts.js` and modify the div wrapping the articles.

```html
<div className="grid grid-cols-1 md:grid-cols-2 gap-6">
  <article />
  <article />
</div>
```

Let's take another look at how it looks now.

![Responsive homepage](https://cdn.hashnode.com/res/hashnode/image/upload/v1665226199004/aGHXiYNoq.png)

And the best part is that because of the changes we made here, all other pages automatically look fantastic on mobile!

![Responsive webpages](https://cdn.hashnode.com/res/hashnode/image/upload/v1665226311521/5YC2xtYa0.png)

If you want to see the completed code check it out on this [GitHub branch](https://github.com/rebelchris/next-portfolio/tree/part-11)

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
