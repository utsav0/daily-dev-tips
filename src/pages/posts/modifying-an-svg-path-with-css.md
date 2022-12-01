---
layout: ../../layouts/Post.astro
title: 'Modifying an SVG path with CSS'
metaTitle: 'Modifying an SVG path with CSS'
metaDesc: 'Did you know you can modify a SVG path with CSS?'
ogImage: /images/10-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/2602a028-f596-408e-f009-ec5af6eb6300
date: 2022-12-10T03:00:00.000Z
tags:
  - css
---

In the [previous article](https://daily-dev-tips.com/posts/animate-an-svg-path-with-css/), we learned that we could animate a CSS path, which led me to discover something even more mind-blowing!

We can modify the CSS path! (only supported in Chromium browsers).

Let's check this out and see how it works.

## Modifying SVG path with CSS

To start, we'll need an essential SVG element again. I started with this curved line.

```html
<svg viewBox="0 0 7 9">
  <path d="M1,3 C1,6 6,6 6,3" />
</svg>
```

Which would result in something like this:

![SVG Path](https://cdn.hashnode.com/res/hashnode/image/upload/v1669874220096/iPBShXlfO.png)

So how can we modify the path now?
And you'll be surprised, but it's accessible with CSS like this.

```css
svg:hover path {
  d: path('M1,6 C1,3 6,3 6,6');
}
```

It looks familiar, right? We can modify the path there. In my instance, I changed it to become the opposite angle of the curve, so it turned upside down.

I also added a transition effect on the path so it will animate smoothly.

```css
svg path {
  fill: transparent;
  stroke: indigo;
  stroke-linecap: round;
  stroke-linejoin: round;
  transition: 0.2s;
}
```

And now we're able to hover it and see the path change!
This blew my mind and is so cool.

You can see its effect here.

![SVG animation on hover](https://cdn.hashnode.com/res/hashnode/image/upload/v1669874548554/T_toH11sx.gif)

Or if you are on Chromium, check it out on [this CodePen](https://codepen.io/rebelchris/pen/vYrzqwe).

Let's hope this gets better browser support, as it's fantastic to have this ability.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
