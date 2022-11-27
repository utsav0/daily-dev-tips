---
layout: ../../layouts/Post.astro
title: 'Using CSS counters'
metaTitle: 'Using CSS counters'
metaDesc: 'What are CSS counters and how can we use them'
ogImage: /images/06-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/579ef66b-08a1-4c1e-1ac1-8e21590aab00
date: 2022-12-06T03:00:00.000Z
tags:
  - css
---

A while ago, we looked at [custom numbered list styling](https://daily-dev-tips.com/posts/css-custom-numbered-list-styling/), but we can use the concept of CSS counters to turn any element into a counter.

So what exactly are these CSS counters? We can look at them as variables maintained by CSS. CSS rules can increase the values, which will track how many times they are used.

## Using CSS counters

To use these counters, we must first create them with the counter-reset function. Wherever you call this reset from, it will reset the count for that counter (identified by its name).

Let's set up a counter on our body and count for each `p` element.

```css
body {
  counter-reset: paragraph;
}

p::before {
  counter-increment: paragraph;
  content: 'Paragraph ' counter(paragraph) ': ';
}
```

If we now create the following HTML:

```html
<p>Some text</p>
<p>Some text</p>
<p>Some text</p>
<p>Some text</p>
<p>Some text</p>
```

We end up with this result.

![CSS Counter](https://cdn.hashnode.com/res/hashnode/image/upload/v1669537433562/CrYHcAulv.png)

We can define these counters as we wish and reset them as we go.

## Custom reset

Let's take a look at custom resets.
For instance, we have `h2` elements as our main counter, and for each paragraph, inside of it, we want to showcase a different counter.
For the demo, we'll even combine the counter output.

Let's take the following HTML structure.

```html
<h2>First heading</h2>
<p>Some text</p>
<p>Some text</p>
<p>Some text</p>
<h2>Second heading</h2>
<p>Some text</p>
<p>Some text</p>
```

We could then easily create an index for each section like this.

```css
body {
  counter-reset: heading;
}
h2 {
  counter-reset: paragraph;
}
h2::before {
  counter-increment: heading;
  content: 'Section ' counter(heading) ': ';
}
p::before {
  counter-increment: paragraph;
  content: counter(heading) '.' counter(paragraph) ' ';
}
```

Which would result in the following:

![Multiple counters in CSS](https://cdn.hashnode.com/res/hashnode/image/upload/v1669537895892/PjJnU2kuS.png)

Pretty cool, right, It might be for sporadic use cases, but one day, you might need CSS counters.

You can also check them out on this [CodePen](https://codepen.io/rebelchris/pen/poKKdBg).

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
