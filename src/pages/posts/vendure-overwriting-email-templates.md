---
layout: ../../layouts/Post.astro
title: 'Vendure - Overwriting email templates'
metaTitle: 'Vendure - Overwriting email templates'
metaDesc: 'A close look at overwriting and customizing email templates in Vendure'
ogImage: /images/19-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/2a38954f-58cd-4b8f-9b7c-2b423fb46c00
date: 2022-12-19T03:00:00.000Z
tags:
  - vendure
---

The previous article looked at [customizing Vendure](https://daily-dev-tips.com/posts/customizing-vendure/) on a data and process level.
In this article, we'll look at customizing emails, as they are often a big part of a webshop system.

We'll be looking at two different layers of customization for customizing these emails.

1. Globals
2. New email flows

## Changing email globals

We'll first have to add the email plugin, which we'll use to modify things.

```bash
npm install @vendure/email-plugin
```

Now we can open our `vendure-config.ts` file and load the plugin.

```js
export const config: VendureConfig = {
  plugins: [
    EmailPlugin.init({
      handlers: defaultEmailHandlers,
      templatePath: path.join(__dirname, '../static/email/templates'),
      globalTemplateVars: {
        fromAddress: '"example" <noreply@example.com`>',
      },
      transport: {
        type: 'smtp',
        host: 'smtp.example.com',
        port: 587,
        auth: {
          user: 'username',
          pass: 'password',
        },
      },
    }),
  ],
};
```

From this config, you can change quite a few variables. For a complete list, check out the [official documentation](https://www.vendure.io/docs/typescript-api/email-plugin/).

This config can change almost everything that has to do with the existing templates.
You can change the copy and format of each email by modifying them in `static/email/templates`.

## New email flows

At one stage, I needed to support a brand-new email flow.
By default, this was the email being sent on payment to give you an order confirmation, but I needed it to be sent pre-payment as payment instructions were manual for this shop.

So to add a new flow, we can create custom email event handlers on specific actions in our system.

This is the example of the order placed handler.

```js
const orderPlacedHandler = new EmailEventListener('order-placed')
    .on(OrderPlacedEvent)
    .loadData(async ({ event, injector }) => {
        transformOrderLineAssetUrls(event.ctx, event.order, injector);
        const shippingLines = await hydrateShippingLines(event.ctx, event.order, injector);
        return { shippingLines };
    })
    .setRecipient(event => event.order.customer!.emailAddress)
    .setSubject(`Order confirmation for #{{ order.code }}`)
    .setFrom(`{{ fromAddress }}`)
    .setTemplateVars(event => ({ order: event.order, shippingLines: event.data.shippingLines }));
```

And to use it, we return this handler in our config.

```js
EmailPlugin.init({
		...
    handlers: [orderPlacedHandler],
}),
```

When creating this new template, ensure that you add a new physical email in your template folder.
In this case, `static/email/templates/order-placed/body.hbs`.

> Note: You can also subscribe to your own [custom events](https://daily-dev-tips.com/posts/customizing-vendure/#customizing-the-order-process).

Pretty cool, as it's straightforward to create and customize email flows within Vendure.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
