---
layout: ../../layouts/Post.astro
title: 'Storybook - Args, and Parameters'
metaTitle: 'Storybook - Args, and Parameters'
metaDesc: 'Working with args and parameters in Storybook stories'
ogImage: /images/21-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/efba6bfd-c961-4d8a-b2a2-e89896c60800
date: 2022-11-21T03:00:00.000Z
tags:
  - storybook
---

Now that we have [written our first story](https://daily-dev-tips.com/posts/storybook-writing-stories/), which renders a relatively static component let's see how we can make it a bit more interactive.

For this, we have two elements to take a closer look at, the one being `args` and the other `parameters`.

## Storybook args

Args are a set of arguments that define how the component should render. Args are Storybook's way of describing those. The cool part is that we can change them on the fly within Storybook.

Let's see how we can add some args to the Button component, for instance.

The first thing we'll have to add is a template. This is our component with the args added.

```js
const Template = (args) => <Button {...args} />;
```

We can start by adding the first story, where we can add these args.

```js
export const Primary = Template.bind({});
Primary.args = {
  primary: true,
  label: 'Button',
};
```

And now, if we run our Storybook, you'll see the component rendered with these arguments, but at the bottom, we get the option to change those!

![Storybook args](https://cdn.hashnode.com/res/hashnode/image/upload/v1668230911672/p4pNBNRcj.png)

We can reuse those for any other stories in this file.

```js
export const Secondary = Template.bind({});
Secondary.args = {
  ...Primary.args,
  primary: false,
};
```

This will render the same component with the label, but the default primary value will now be false.

Alternatively, you can define the args on a component level like this.

```js
export default {
  title: 'Button',
  component: Button,
  args: {
    primary: true,
    label: 'Button',
  },
};

const Template = (args) => <Button {...args} />;

export const Primary = Template.bind({});

export const Secondary = Template.bind({});
Secondary.args = {
  primary: false,
};
```

And in this example, each story we define will start with the primary state. In the secondary case, we overwrite that value.

## Storybook parameters

Next to args, we also get parameters, which say something about the story's environment.

A typical example would be the theme.

Again we can add it to a singular story like this.

```js
Primary.parameters = {
  backgrounds: {
    values: [
      { name: 'red', value: '#f00' },
      { name: 'green', value: '#0f0' },
      { name: 'blue', value: '#00f' },
    ],
  },
};
```

This will now show up at the Storybook top menu like this.

![Storybook story parameters](https://cdn.hashnode.com/res/hashnode/image/upload/v1668231420107/FTViKAYUk.png)

However, more common would probably be to set it for the whole story like this.

```js
export default {
  title: 'Button',
  component: Button,
  parameters: {
    backgrounds: {
      values: [
        { name: 'red', value: '#f00' },
        { name: 'green', value: '#0f0' },
        { name: 'blue', value: '#00f' },
      ],
    },
  },
};
```

Besides these methods, we also get an option to set these elements for all components.

We can create a `preview.js` file in our `.storybook` file and add it like this.

```js
export const parameters = {
  backgrounds: {
    values: [
      { name: 'red', value: '#f00' },
      { name: 'green', value: '#0f0' },
      { name: 'blue', value: '#00f' },
    ],
  },
};
```

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
