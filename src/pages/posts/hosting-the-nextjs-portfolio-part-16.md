---
layout: ../../layouts/Post.astro
title: 'Hosting the NextJS portfolio - part 16'
metaTitle: 'Hosting the NextJS portfolio - part 16'
metaDesc: 'Setting up the hosting on Vercel for our Next.js portfolio'
ogImage: /images/23-10-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/bbc95f7b-57b4-4e5f-7a4b-8fb656c8e300
date: 2022-10-23T03:00:00.000Z
tags:
  - nextjs
---

Now that we have our Next.js portfolio ready and working dynamically, it's time to look at hosting.

My advice with Next.js is to go with Vercel. They are the number one Next hosting.
And it's super easy (and free), so let's do this.

## Hosting a Next.js website on Vercel

To start, head over to [Vercel and create an account](https://vercel.com/login). The easiest way is to use your GitHub account to log in.

![Vercel new project](https://cdn.hashnode.com/res/hashnode/image/upload/v1665639275016/wt47V6vap.png)

Once logged in, click to add a new project here. It will pop up the option to import a git repository.
Please search for your Next.js portfolio repo and import it from the menu.

![Search the right project](https://cdn.hashnode.com/res/hashnode/image/upload/v1665639360791/8hu97AJMu.png)

The cool part about Vercel is that it will automatically know it's a Next project, so we don't need to do any other setup.
Pick a name and click "Deploy".

The deployment will start, and once it's done, you will see the following output stating it's ready.

![Deployment ready](https://cdn.hashnode.com/res/hashnode/image/upload/v1665639500595/jp-pjFl8h.png)

You might see that my preview shows the default next page, and this is because I've been working in branches.
And by default, Vercel will take only your main/master branch to deploy.

However, the cool part is that if we now make any changes to this branch, it will automatically trigger a new deployment.

So I headed to GitHub and merged the latest branch into the main one.

Once done with this deployment, my website is now visible on the Vercel domain!
Yes, we did it. Our portfolio is now hosted publicly online.

[View the portfolio](https://next-portfolio-kappa-lake.vercel.app/)

I'd also love to see your portfolios, so please share them with me 🤩.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
