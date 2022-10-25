---
layout: ../../layouts/Post.astro
title: 'Adding Pages to Eleventy'
metaTitle: 'Adding Pages to Eleventy'
metaDesc: 'Lets add static pages to our Eleventy blog'
image: /images/23-04-2020.jpg
date: 2020-04-23T03:00:00.000Z
tags:
  - eleventy
---

Someone made an excellent comment recently that an about page would benefit my blog quite a bit.

So why not simultaneously explore how to add static pages to our dynamic-created blog?

We will create a static about page, which will sit on the URL `/about`.

## Adding the About page

Create an `about.njk` file in the root at the same level as the `index.njk` and insert the following code:

```html
---
layout: layouts/about.njk
permalink: /about/
---

<img src="/img/about.jpg" height="300" />

<h1>Hello world, I'm Chris! 🤟</h1>

<p>
  I'm Chris Bongers a web developer, solution architect, blogger, and lover of a
  beautiful wife and dog.
</p>
<p></p>
<p>
  I come from a mixed background being a full stack WordPress developer, a PHP
  Symfony developer and just your good old full-stack dev.
</p>
<p>
  On the web, I love beautiful things. They must look amazing, be blazing fast,
  and be innovative.
</p>
<p>
  I currently live in Cape Town, South Africa 🇿🇦, but my roots are in The The
  Netherlands 🇳🇱.
</p>
<br />
<p>
  Feel free to follow me on
  <a href="https://twitter.com/DailyDevTips1" target="_blank">Twitter</a>,
  <a href="https://www.linkedin.com/in/chrisbongers/" target="_blank"
    >LinkedIn</a
  >
  or
  <a href="https://www.facebook.com/DailyDevTipsBlog" target="_blank"
    >Facebook</a
  >
</p>
```

Here, we set the layout to a new one and added a permalink to `/about/`. This will create an `about` folder with an `index.html`.

Then we add an image and some text.

## Images in Eleventy

The image we just added won't work by default. We have to tell Eleventy to put it in our output folder.

We can add a `.eleventy` file in our root, and let's add the following code.

```js
module.exports = function (eleventyConfig) {
  // Copy `img/` to `_site/img`
  eleventyConfig.addPassthroughCopy('img');
};
```

Here we can change the default Eleventy settings; in this case, we say it must just be the `addPassthroughCopy` function to add the `img` folder to our output.

That being said, create the `img` folder in the root of our website and add your profile image in it as we set it in the `about.njk` page!

## The About template

```html
---
layout: layouts/base.njk
templateClass: tmpl-about
---

{{ content | safe }}
```

This layout is the same as our homepage, we could have re-used that one, but I like to keep things separate in case we want to add anything fancy later on.

## Testing and Deploying Netlify

As we saw in [building a static blog with 11ty](https://daily-dev-tips.com/posts/building-a-static-blog-with-11ty/) we can run the following command to test it locally:

```bash
npx eleventy --serve
```

Open up [http://localhost:8080](http://localhost:8080) to see what we got!

To deploy to Netlify, we can use our learnings from [Hosting on Netlify](https://daily-dev-tips.com/posts/hosting-a-static-blog-on-netlify/) and push them to our git main branch.

You can find this code in the following [GitHub repo](https://github.com/rebelchris/eleventy-demo/releases/tag/2.0), or view it online on [this link](https://romantic-torvalds-af350e.netlify.app/about/).

Or check out my newly created [about page](https://daily-dev-tips.com/about/).

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
