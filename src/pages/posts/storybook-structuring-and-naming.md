---
layout: ../../layouts/Post.astro
title: 'Storybook - Structuring and naming'
metaTitle: 'Storybook - Structuring and naming'
metaDesc: 'Organizing and structuring our Storybook component hierarchy'
ogImage: /images/25-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/bc6e7c83-8532-4079-298f-a4cae558cb00
date: 2022-11-25T03:00:00.000Z
tags:
  - storybook
---

In our previous examples, you might have spotted that the test button component always gets added to the root of the Storybook structure.

In this article, I want to dive deeper into how you can organize and structure your components.

This means we'll look at giving them appropriate subcategories and even more explicit names.

## Adding structure to the hierarchy

The first thing we want to look at is the structural hierarchy. Our button shows up at the root, compared to the other samples with an "example" category.

![Structure starting point for Storybook](https://cdn.hashnode.com/res/hashnode/image/upload/v1668575445944/XCbyY5f01.png)

We can give the component story a better title split by `/` as the separator like this:

```js
export default {
  title: 'Components/Global/Button',
  component: Button,
};
```

With this setup, our Storybook will now look like this:

![Structured Storybook sample](https://cdn.hashnode.com/res/hashnode/image/upload/v1668575576555/pSNsMiwAP.png)

> Note: You can go as far as you like with the hierarchy here.

## Exporting only one story

What happens when you only have one story in the file? You can choose to export that in one go like this.

```js
export const Button = (args) => <ButtonComponent {...args} />;
```

This way, our story will be called the `Button`, only showing this version.

![Singular story](https://cdn.hashnode.com/res/hashnode/image/upload/v1668576315995/iQtlmihX2.png)

This can be super useful if you only have one state for a component.

## Sorting stories

There is also the option to sort your stories.
Everything related will happen in the `.storybook/preview.js` file.

We can provide a custom sorting method like this in the most basic option.

```js
export const parameters = {
  options: {
    storySort: (a, b) =>
      a[1].kind === b[1].kind
        ? 0
        : a[1].id.localeCompare(b[1].id, undefined, { numeric: true }),
  },
};
```

However, we have some cool options to work with that might help you better.

The basic configuration for sorting looks like this.

```js
export const parameters = {
  options: {
    storySort: {
      method: '',
      order: [],
      locales: '',
    },
  },
};
```

The method can be `alphabetical`, for example.

However, we are more interested in the `order`. We can provide an array of strings in which they should appear.

Take the example we have so far. We got "Example", then "Components".
If we wish to switch those around, we can provide an array as such:

```js
export const parameters = {
  options: {
    storySort: {
      order: ['Components', 'Example'],
    },
  },
};
```

This will now show the Components first.

![Storybook sorting](https://cdn.hashnode.com/res/hashnode/image/upload/v1668576628018/DIIJtagEY.png)

You don't have to explicitly mention all categories, just the ones you wish to order.
Using a wildcard like this, you can also say which one to always end with.

```js
export const parameters = {
  options: {
    storySort: {
      order: ['Components', 'Example', '*', 'WIP'],
    },
  },
};
```

This will show:

- Components
- Example
- _All other components_
- WIP

In some cases, you might also want to sort subcategories, for which we can use a subarray.
Let's say "Example" has multiple categories. We can sort them as such:

```js
export const parameters = {
  options: {
    storySort: {
      order: ['Components', 'Example', ['App', 'Introduction'], '*', 'WIP'],
    },
  },
};
```

You will see now we switched App and Introduction around.

![Sub sorting in Storybook](https://cdn.hashnode.com/res/hashnode/image/upload/v1668576815140/wPjgSMHhm.png)

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
