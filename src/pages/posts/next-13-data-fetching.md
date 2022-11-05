---
layout: ../../layouts/Post.astro
title: 'Next 13 - Data fetching'
metaTitle: 'Next 13 - Data fetching'
metaDesc: 'A closer look at data fetching in Next 13'
ogImage: /images/14-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/cff08d39-e8e0-40c5-5f50-dec26a811c00
date: 2022-11-14T03:00:00.000Z
tags:
  - nextjs
---

Data fetching is nothing new in Next, but they simplified how this works.

You might remember `getServerSideProps` and `getStaticProps` from the previous React versions. Those are no longer needed. In return, we get one uniform way of fetching data!

## Fetching data

The recommended way of fetching data is using [server components](https://daily-dev-tips.com/posts/next-13-sever-and-client-components/), as discussed in the previous article.

According to the docs, there are a lot of benefits from fetching from server components:

- Access to backend services like database and API that don't run on the client
- Keep your secure keys on the server so they don't leak to the client
- Fetch and render in the same environment
- Caching your renders on the server
- Send less JavaScript to bundle

One important note is that they recommend you refetch data over passing it down.
Underwater, they deduplicate your requests and return cached results.
So it's more efficient to have the server do the heavy lifting, and the client requests the data.

## How does the fetching work?

They changed to use the fetch Web API, which is fantastic. It's a super powerful API, so happy to see this choice.

Fetch will always return a promise so we can await the result; by default, it's a cached request/results.

Let's show you an example.

In our component, we can create a data fetching function that would look like this.

```js
async function getData() {
  const res = await fetch('https://jsonplaceholder.typicode.com/todos');

  return res.json();
}
```

Our component itself can then use this function like this.

```js
export default async function AccountPage() {
  const table = await getData();

  return (
    <ul>
      {table.map((todo) => (
        <li key={todo.id}>{todo.title}</li>
      ))}
    </ul>
  );
}
```

And yep, that's it, simple.
I like the abstraction of thought here to simplify everything using native APIs.

It's also a great abstraction to move towards a unique concern architecture by simply making the components as small and self-sufficient as possible.

We also get many options around the fetch API that we can leverage, but it might be best to review them once we need them.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
