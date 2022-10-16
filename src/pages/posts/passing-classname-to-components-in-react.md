---
layout: ../../layouts/Post.astro
title: 'Passing className to components in React'
metaTitle: 'Passing className to components in React'
metaDesc: 'How to pass a className to a child component in React'
ogImage: /images/25-10-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/8c3319a4-a800-4c44-1d26-1a4e1e566b00
date: 2022-10-25T03:00:00.000Z
tags:
  - react
---

In React, we are familiar with the concepts of a `className` on components. It's the way React adds the class attribute to an element.
It looks like this:

```html
<div className="bg-red-200"></div>
```

However, what happens if we want to make our custom components have the option to allow dynamic classNames?

To give you an example, let's say we have a `CustomComponent` that can take a className from wherever it's imported.

```jsx
<CustomComponent className='bg-red-200` />
```

If we ran this in React, we would get shown an error as the CustomComponent doesn't know what a `className` is.
So let's fix that.

## Passing Classnames as props in React

In all honesty, I probably made it sounds like it was going to be very complicated, right?

Well, fear not, it's not that scary, as we can pass the `className` as a prop!

So in your child component, we would structure its receiving end like this.

```js
export default Child = ({ className }) => {
  return (
    <div className={className}>
      <h2>I'm the child component</h2>
    </div>
  );
};
```

And now, we can use this component like this.

```js
<Child className='bg-red' />
```

And that's it. Our component will now render this classname on its main div.

## Mixing classes

I also wanted to take a second to look at what happens if your child component always has certain classes and you want to add extra classes.

In that case, the props stay the same. However, we can dynamically render them like this.

```js
<div className={`existing-class ${className}`}>
```

Our component will always render `existing-class` as a class but add whatever we set on it.

So if we use it like this:

```js
<Child className='bg-red' />
```

Our result will be a div like this.

```html
<div class="existing-class bg-red"></div>
```

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
