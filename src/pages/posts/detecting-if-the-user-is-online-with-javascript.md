---
layout: ../../layouts/Post.astro
title: 'Detecting if the user is online with JavaScript'
metaTitle: 'Detecting if the user is online with JavaScript'
metaDesc: 'How can we detect if the user is online or offline with JavaScript'
ogImage: /images/01-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/6bfe525b-c901-4340-8334-269164d5e700
date: 2022-12-01T03:00:00.000Z
tags:
  - javascript
---

Sometimes you might want to enhance your application to notify users they might have lost their internet connection.

Users might be visiting your website and receiving a cached version, so it can often appear that their internet is still working.
However, they lost a connection under the hood, and nothing new will load.

This is where it can be beneficial to show them some messages to let them know they should check their connection.

## Detecting connection status

We can leverage the `navigator.onLine` API to detect the connection status.
This will return a boolean to indicate whether the user is online.

> Note: Be aware browsers implement this [differently](https://developer.mozilla.org/en-US/docs/Web/API/Navigator/onLine#Example) so results may vary.

This would work great on the initial load so we could do something like this.

```js
window.addEventListener('load', () => {
  const status = navigator.onLine;
});
```

But we won't know if the network status changes after load, which is not ideal.

We can subscribe to offline and online events to listen to those specific changes.

```js
window.addEventListener('offline', (e) => {
  console.log('offline');
});

window.addEventListener('online', (e) => {
  console.log('online');
});
```

## Demo

Let's set up a quick demo to demonstrate this.
We'll be using a basic text element in the center of the screen, but you can, of course, style and implement this in whatever way you like.

> Note: I'm using SCSS to style this

```html
<div class="status">
  <div class="offline-msg">You're offline 😢</div>
  <div class="online-msg">You're connected 🔗</div>
</div>
```

We are building this with the premise that the default is a connected state.

Let's add some basic styling to the mix.

```css
.status {
  background: #efefef;
  display: flex;
  justify-content: center;
  align-items: center;
  min-height: 100vh;
  div {
    padding: 1rem 2rem;
    font-size: 3rem;
    border-radius: 1rem;
    color: white;
    font-family: Roboto, 'Helvetica Neue', Arial, sans-serif;
  }
  .online-msg {
    background: green;
    display: block;
  }
  .offline-msg {
    background: red;
    display: none;
  }
}
```

This would, by default, only show the online message ever.
Let's add a condition that if the status element has an offline class, we switch the two divs.

```css
.status {
  &.offline {
    .online-msg {
      display: none;
    }
    .offline-msg {
      display: block;
    }
  }
}
```

Now, if we add the offline class to the status div, we should see the offline message.

So how can we switch these based on the network status?

```js
const status = document.querySelector('.status');
window.addEventListener('load', () => {
  const handleNetworkChange = () => {
    if (navigator.onLine) {
      status.classList.remove('offline');
    } else {
      status.classList.add('offline');
    }
  };

  window.addEventListener('online', handleNetworkChange);
  window.addEventListener('offline', handleNetworkChange);
});
```

Yep, this piece of code does the trick!
We initialized this on the first load and created a new function to check the navigator status.

Then we add event listeners to listen to the changes so we can act based on them.
On change, it can add or remove the class name.

If we try it out, it looks like this.

<!-- ![JavaScript online, offline detection](https://cdn.hashnode.com/res/hashnode/image/upload/v1669095004521/StV1do9V2.gif) -->
<video autoplay loop muted playsinline>
  <source src="https://res.cloudinary.com/daily-dev-tips/video/upload/v1669095045/online-offline_jzu9z6.webm" type="video/webm" />
  <source src="https://res.cloudinary.com/daily-dev-tips/video/upload/v1669095044/online-offline_bpi0xn.mp4" type="video/mp4" />
</video>

Or give it a try on this [CodePen](https://codepen.io/rebelchris/pen/PoaQjqr).

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
