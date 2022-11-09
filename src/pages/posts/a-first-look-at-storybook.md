---
layout: ../../layouts/Post.astro
title: 'A first look at Storybook'
metaTitle: 'A first look at Storybook'
metaDesc: "Let's take a close look at Storybook and what it actually is"
ogImage: /images/18-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/ea23b208-b3bc-4c60-086d-61f405cb2a00
date: 2022-11-18T03:00:00.000Z
tags:
  - storybook
---

So you might have heard about Storybook, not children's stories, but the one for developers.

It's a frontend system (a workshop, they call it) for building UI components and pages.
This allows you to create more stable components and test and document them.

## Why is Storybook so great?

Storybook provides a way for developers to create components and pages in isolation. This means you can focus on how that individual element should behave, its options, and so on.

Eventually, you write your story for the component and define the different states it can be in.

After this, we get a couple of cool features:

- Spot test: Run your Storybook, and you'll be able to view the component and see if it is showing as expected.
- Visual tests: Automated tests to see if your component still renders as the previous test
- Interaction test: Test how it behaves on user interaction
- Accessibility test: Super cool to see there is an accessibility test on the component level!
- Snapshot testing: You can test on component dom level against snapshots to ensure nothing changes by accident.

You'll be able to reuse the test in Storybook in other testing frameworks as well.

Besides these points, it also provides documentation for your team. Colleagues can find components easily and see what they should look like.

## Do we always need it?

I'm super intrigued to give Storybook a try, as we use many custom components (like, really a lot!). This becomes a pain to maintain as some code someone else writes might accidentally impact a component.

I'm writing this series around Storybook to try it before implementing it.
I want to experience what it's like and if it can be helpful.

But, with that said, there will be times when it will be sheer overkill for your project.
For instance, when you rely solely on an external component library, you can use Storybook, but it will take longer to set up and doesn't really bring much value.

There is also another level of how long it will take to set up Storybook.
If your application is tiny, you may like to test it manually.
But in most cases, you'd be benefited from having some visual system in place.

I'm super hyped to try it and follow my newsletter if you are, too, as we will be exploring it in detail over the next couple of articles.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
