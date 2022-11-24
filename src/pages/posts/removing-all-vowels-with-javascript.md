---
layout: ../../layouts/Post.astro
title: 'Removing all vowels with JavaScript'
metaTitle: 'Removing all vowels with JavaScript'
metaDesc: 'Removing all vowels from a string with JavaScript'
ogImage: /images/03-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/85f72510-7db3-4898-bd8f-8f620b19f100
date: 2022-12-03T03:00:00.000Z
tags:
  - javascript
---

Today we'll look at a nifty solution to remove all vowels in a string using JavaScript.

The idea is that we get a string and have to return the string without the letters `aeiou`.

## JavaScript remove all vowels

Let's dive right into the solution.

```js
const input = 'daily dev tips';

const removeVowels = input.replace(/[aeiou]/gi, '');

console.log(removeVowels);

// 'dly dv tps'
```

It works!
And yep that's all the code we need, but let's take a closer look at how it works.

The first part is to use the JavaScript replace function to replace a specific match.
The first part is the match, for which we'll use a regular expression. And the second part is the replacement.

We could, say, replace the letter `i` with an empty string like this.

```js
const removeVowels = input.replace('i', '');

console.log(removeVowels);

// 'daly dev tips'
```

However, you'll notice it only replaced the first occurrence. And, of course, we can only target one letter at a time.
So this is where our regular expression comes in.

We start the regular expression by wrapping it in the `/ /` backslashes.
Then we open a pattern matcher with the `[]` brackets. And in between, we specify which letters should be matched.
The last part is to use `gi` at the end, which stands for `global ignore`.

- `global` meaning to apply it to each occurrence, not just the first one
- `ignore` means to perform a case-insensitive search

And that's it. I hope you learned something about removing vowels with JavaScript.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
