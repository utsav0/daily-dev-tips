---
layout: ../../layouts/Post.astro
title: 'Have you tried React classnames?'
metaTitle: 'Have you tried React classnames?'
metaDesc: 'What is the classnames package for React and how can you use it.'
ogImage: /images/26-10-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/4b40e63e-b089-42e6-7512-07d008ceca00
date: 2022-10-26T03:00:00.000Z
tags:
  - react
---
Regarding classes in React, we get a lot of power out of the box.
However, we can enhance this power to make it even better.

We can leverage the [classnames](https://www.npmjs.com/package/classnames) package, which has been in the React ecosystem since 2015.

## Why React classnames rock

If all you do is write static classes like this:

```js
<div className='static-class'></div>
```

This article might not be for you. Not to disrespect you, but in that case, keep doing what you are doing.

React classnames rock when it comes to dynamic classes or combined classes.

A combined class, for instance, if we allow the [className to be passed](https://daily-dev-tips.com/posts/passing-classname-to-components-in-react/) from a parent component like this.

```js
<div className={`existing-class ${className}`}>
```

Or even classes that render conditionally.

```js
<div className={`existing-class ${success && 'bg-green'}`}>
```

Let's see how this would like with React classnames, but before we dive into that, we have to install it first.

```bash
npm install classnames
```

I tend to import it differently, so I never get confused with the default `className` by doing this.

```js
import classnames from 'classnames';
```

And now we can use it like this.

```js
<div className={classnames('foo', 'bar')}></div>
```

Or, in the more advanced examples, we can do stuff like this:

```js
<div className={classNames('existing-class', className)}>

<div className={classNames('existing-class', 'bg-green': success)}>
```

And this is where it shines. It's a great way to abstract, difficult class conditions to be more readable.

For the result of your output code, it doesn't matter which way you go. It will be the same.
However, this is way easier and more consistent across your code base from a maintainability point of view.

If you are an avid React user and use conditional classes, I would like you to try classnames.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)