---
layout: ../../layouts/Post.astro
title: 'Submit button outside the form'
metaTitle: 'Submit button outside the form'
metaDesc: 'How to use a submit button outside a HTML form'
ogImage: /images/04-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/85f72510-7db3-4898-bd8f-8f620b19f100
date: 2022-12-04T03:00:00.000Z
tags:
  - html
---

The other day I had quite a weird scenario where we had a form inside a specific section, but the submit button was at the bottom.

At first, I tried to re-configure the HTML so that the button would be part of the form element. However, that quickly became an HTML soup.

So I decided to research other options and learned (after many years of being a developer) that you can place submit buttons outside a form!

Let's take a look at that.

## Submit button outside a form

To achieve this, we should use the following markup.

```html
<form id="newsletterForm">
  <label for="email">Email:</label>
  <input type="email" name="email" placeholder="Email" />
</form>

<button type="submit" form="newsletterForm">Submit!</button>
```

As you can see, the button is not part of the form, yet this will work.

This is because we used the `form` attribute on our button. In it, we define which form this button belongs to.

You can also try it out in [this CodePen](https://codepen.io/rebelchris/pen/MWXGoGj).

> Note: You will see a "Not Found" page, as our form doesn't go anywhere.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
