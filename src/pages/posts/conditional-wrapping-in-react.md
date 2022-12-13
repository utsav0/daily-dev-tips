---
layout: ../../layouts/Post.astro
title: 'Conditional wrapping in React'
metaTitle: 'Conditional wrapping in React'
metaDesc: 'Learning how to conditionally wrap a React element'
ogImage: /images/11-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/67448e0f-3eff-45f5-345e-16ef93795600
date: 2022-12-11T03:00:00.000Z
tags:
  - react
---

This is something you do not always need, but I wrote this article for those looking for it.

Sometimes we might have a generic element, a specific component that renders inside a modal.
When a specific flag is set, the component should get a parent wrapper to display it in a different variant.

We could use an if...else statement, but it looks messy.

## Conditional wrapping in React

Let's say we got specific service cards to make it a bit easier to follow. In some cases, they explain a service, but in others, they need to link to a detail page.

The component might look like this.

```js
const ServiceCard = ({ title, description, image, url }) => {
  return (
    <section>
      <h2>{title}</h2>
      <p>{description}</p>
      <img src={image} alt={title} />
    </section>
  );
};
```

As mentioned, what happens if we need to wrap this whole thing in a link element when the URL exists?
We could use the if...else loop.

```js
const ServiceCard = ({ title, description, image, url }) => {
  return (
    <section>
      {url ? (
        <a href={url}>
          <h2>{title}</h2>
          <p>{description}</p>
          <img src={image} alt={title} />
        </a>
      ) : (
        <>
          <h2>{title}</h2>
          <p>{description}</p>
          <img src={image} alt={title} />
        </>
      )}
    </section>
  );
};
```

But this shows duplicate code, so it's a bit silly. If we need to style each element, we must modify it in two places.

So how can we better wrap this conditionally?

We can create a generic component that handles this for us, the component will be named `ConditionalWrapper`, and it will take a condition, the wrapper, and the children it should wrap.

```js
const ConditionalWrapper = ({ condition, wrapper, children }) =>
  condition ? wrapper(children) : children;
```

With that in place, we can use it on our existing component to clean it up.

```js
const ServiceCard = ({ title, description, image, url }) => {
  return (
    <section>
      <ConditionalWrapper
        condition={url}
        wrapper={(children) => <a href={url}>{children}</a>}
      >
        <>
          <h2>{title}</h2>
          <p>{description}</p>
          <img src={image} alt={title} />
        </>
      </ConditionalWrapper>
    </section>
  );
};
```

And now, if we use our component, depending on whether we pass the URL. It will render with or without the href. And the best part is that we have no duplication in our elements.

For example, the following use case:

```js
<ServiceCard title='test' description='foo bar' img='img1.jpg' />
```

It would return the following HTML output:

```html
<section>
  <h2>test</h2>
  <p>foo bar</p>
  <img src="img1.jpg" alt="test" />
</section>
```

We will get the following output if we put the URL in the element.

```html
<section>
  <a href="url">
    <h2>test</h2>
    <p>foo bar</p>
    <img src="img1.jpg" alt="test" />
  </a>
</section>
```

Pretty cool, right?

The main magic, of course, happens in the ConditionalWrapper component and, to be precise, the wrapper argument.

Since we pass the children (which is a React default prop), we can see that the use case of our function as in `wrapper={children => <a href={url}>{children}</a>}` states.

- If the condition is met
- Wrap the children in this specific element

There will only be a handful of times when you might need this function, but it can be a huge lifesaver.

Note: big thanks to [Olivier](https://blog.hackages.io/conditionally-wrap-an-element-in-react-a8b9a47fab2) for the original idea!

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
