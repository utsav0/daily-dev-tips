---
layout: ../../layouts/Post.astro
title: 'Storybook - Exploring the play function'
metaTitle: 'Storybook - Exploring the play function'
metaDesc: 'What is the play function in Storybook and how do we set it up?'
ogImage: /images/23-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/3c9ec4a2-7b14-4616-986d-46ceb6a3ae00
date: 2022-11-23T03:00:00.000Z
tags:
  - storybook
---

The play function is a part of Storybook I want to dive into quickly, but not too deeply.

You can add user interactions on the component render. This could be beneficial when constantly testing the same flow that requires such interaction.

## Setting up interaction addon

It's recommended to add an interactions addon plugin to make working with the play function easier.
Adding this addon gives you some extra interaction options that make it easier to use.

Start by installing the following packages.

```bash
npm install @storybook/testing-library @storybook/jest @storybook/addon-interactions --save-dev
```

We then have to update our storybook configuration to include this addon.
Open up `.storybook/main.js` and add the following.

```js
module.exports = {
  addons: ['@storybook/addon-interactions'],
};
```

## Writing a play action

If you keep the existing demo component, you can see a play-action in the wild.
It's added to the `Page.stories.jsx` file and included a button click simulation.

Here is what it looks like:

```js
export const LoggedIn = Template.bind({});
LoggedIn.play = async ({ canvasElement }) => {
  const canvas = within(canvasElement);
  const loginButton = await canvas.getByRole('button', { name: /Log in/i });
  await userEvent.click(loginButton);
};
```

When this story renders, we immediately find the login button and mimic a click.

You can also combine multiple events after each other. This can be super convenient to test out forms, for instance.

A lot of interaction looks like how we would interact with Jest test cases.

## Some examples

There are quite a few options we can test around with. Here are some examples.

Provider user input to a form and then submit that form.

```js
FilledForm.play = async ({ canvasElement }) => {
  const canvas = within(canvasElement);

  const emailInput = canvas.getByLabelText('email', {
    selector: 'input',
  });
  await userEvent.type(emailInput, 'example-email@email.com', {
    delay: 100,
  });

  const submitButton = canvas.getByRole('button');

  await userEvent.click(submitButton);
};
```

Another thing would be to mimic clicks, as we saw in the first example. For this, we can use multiple selectors.

```js
ClickExample.play = async ({ canvasElement }) => {
  const canvas = within(canvasElement);

  await userEvent.click(canvas.getByRole('button'));

  await fireEvent.click(canvas.getByTestId('data-testid'));
};
```

Or perhaps you are looking to mimic a select option choice.

```js
ExampleChangeEvent.play = async ({ canvasElement }) => {
  const canvas = within(canvasElement);

  const select = canvas.getByRole('listbox');

  await userEvent.selectOptions(select, ['One Item']);
  await sleep(2000);

  await userEvent.selectOptions(select, ['Another Item']);
  await sleep(2000);

  await userEvent.selectOptions(select, ['Yet another item']);
};
```

As you can see, technically, we can mimic everything the user would do as well.
This is an excellent addition for you to quickly see how the user flow would work for your component.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
