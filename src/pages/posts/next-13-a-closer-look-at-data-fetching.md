---
layout: ../../layouts/Post.astro
title: 'Next 13 - A closer look at data fetching'
metaTitle: 'Next 13 - A closer look at data fetching'
metaDesc: 'Taking a closer look at data fetching in Next 13'
ogImage: /images/15-11-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/52bef572-8f9e-48f0-7c07-11071b1dee00
date: 2022-11-15T03:00:00.000Z
tags:
  - nextjs
---

Yesterday we had our first introduction to [data fetching in Next 13](https://daily-dev-tips.com/posts/next-13-data-fetching/).

I want to take it one step further as the docs themselves have some interesting points they discuss.

## Types of fetching

The first point I want to discuss is the different types of fetching we can do.

This has a lot to do with whether the data is being saved or not, and we get the following options:

- Cache data: This is the default
- Dynamic data: No cache
- Revalidate: Cache for x time

They work by defining a caching strategy. As mentioned, the default one is always to cache everything.

You can also pass the flag like this:

```js
// This
fetch('https://...');

// Is the same as this
fetch('https://...', { cache: 'force-cache' });
```

The next one is to state that we always want to fetch new data from the server.
We achieve that by disabling the caching.

```js
fetch('https://...', { cache: 'no-store' });
```

And in the last option, we can specify how long we want to cache something.
This is basically what we previously had with ISR (Incremental Static Regeneration). We define this by adding a time in seconds for how long to cache something.

```js
fetch('https://...', { next: { revalidate: 10 } });
```

## Parallel vs. Sequential

Sometimes, you want to load data after we load another query.

For instance, we might want to load users and all their to-do items.

For these cases, you should use parallel fetching, which can query both calls at once and render once they are done.

It can look like this.

```js
async function getUser(username) {
  const res = await fetch(`https://api.example.com/user/${username}`);
  return res.json();
}

async function getUserTodos(username) {
  const res = await fetch(`https://api.example.com/user/${username}/todos`);
  return res.json();
}

async function Profile({ promise }) {
  // Wait for the albums...
  const albums = await promise;

  return (
    <ul>
      {albums.map((album) => (
        <li key={album.id}>{album.name}</li>
      ))}
    </ul>
  );
}

export default async function Page({ params: { username } }) {
  // Queue up the promises here...
  const _user = getUser(username);
  const _todos = getUserTodos(username);

  // Wait for the user...
  const user = await _user;

  return (
    <>
      <h1>{user.name}</h1>
      <Suspense fallback={<div>Loading...</div>}>
        <Todos promise={_todos} />
      </Suspense>
    </>
  );
}
```

This example demonstrates that we start the component by loading both calls simultaneously.
But only render the actual component once we have both results available.

Alternatively, you can opt for sequential loading, which will cause a waterfall of loads.
(But in some cases might be needed)

This way, incorporate fetching the first only and then fetching the second one.

```js
async function getUser(username) {
  const res = await fetch(`https://api.example.com/user/${username}`);
  return res.json();
}

async function getUserTodos(username) {
  const res = await fetch(`https://api.example.com/user/${username}/todos`);
  return res.json();
}

async function Todos({ userId }) {
  const todos = await getUserTodos(userId);

  return (
    <ul>
      {todos.map((todo) => (
        <li key={todo.id}>{todo.name}</li>
      ))}
    </ul>
  );
}

export default async function Page({ params: { username } }) {
  const user = await getUser(username);

  return (
    <>
      <h1>{user.name}</h1>
      <Suspense fallback={<div>Loading...</div>}>
        <Todos userId={user.id} />
      </Suspense>
    </>
  );
}
```

This will cause our page to load the user first, then try to render the `Todos` component and start loading the todos.

The result will be that two requests happen after each other.
However, by using this approach, we could already show the user page and a loader for the Todos.

## Conclusion

There are many different ways of using data fetching with Next 13. Which one you need to use will highly depend on what you are trying to achieve.

We should always aim to choose the one that unblocks the user as much as possible and cache wherever we can!

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
