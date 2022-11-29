---
layout: ../../layouts/Post.astro
title: 'Working with data attributes in CSS'
metaTitle: 'Working with data attributes in CSS'
metaDesc: 'Did you know you could style data-attributes in CSS?'
ogImage: /images/08-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/2bd97812-e404-4355-4e1a-e3e64d9f4400
date: 2022-12-08T03:00:00.000Z
tags:
  - css
---

We previously looked at using [data attributes in JavaScript](https://daily-dev-tips.com/posts/vanilla-javascript-data-attributes/). These data attributes are a fantastic way to store little bits of information on an element without using custom attributes.

However, we can also use them to style some aspects with specific attribute sets.

## CSS attributes in CSS

To paint a simple picture, let's create elements that hold a specific value like this.

```html
<div data-rating="1">Rating</div>
<div data-rating="5">Rating</div>
```

As you can see, our rating is only set as the custom attribute.

Let's first look at how we can style this object, which is very easy by simply using its name.

```css
[data-rating] {
  color: indigo;
}
```

With this, the rating text will be purple.

We can also make it more specific and add styling for particular values.

```css
[data-rating='1'] {
  color: red;
}
[data-rating='5'] {
  color: indigo;
}
```

And to top it off, we can inject the value with CSS!

```css
[data-rating]::after {
  content: attr(data-rating);
}
```

Which would result in the rating being added after our text.

You can play with these data attributes on the following CodePen.

<p class="codepen" data-height="300" data-default-tab="js,result" data-slug-hash="rNKrdGa" data-user="rebelchris" style="height: 300px; box-sizing: border-box; display: flex; align-items: center; justify-content: center; border: 2px solid; margin: 1em 0; padding: 1em;">
  <span>See the Pen <a href="https://codepen.io/rebelchris/pen/rNKrdGa">
  Untitled</a> by Chris Bongers (<a href="https://codepen.io/rebelchris">@rebelchris</a>)
  on <a href="https://codepen.io">CodePen</a>.</span>
</p>
<script async src="https://cpwebassets.codepen.io/assets/embed/ei.js"></script>

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
