---
layout: ../../layouts/Post.astro
title: 'Vendure - Importing data'
metaTitle: 'Vendure - Importing data'
metaDesc: 'A first look at how we can import product data in Vendure'
ogImage: /images/15-12-2022.jpg
image: https://daily-dev-tips.com/cdn-cgi/imagedelivery/Bki7Af2hq0JKVFw1XYYMQg/22d9de6b-80fa-4812-e312-e0a021981c00
date: 2022-12-15T03:00:00.000Z
tags:
  - vendure
---

Product imports are an essential element that I found great when working with Vendure.
It was super important to me to be able to import products and their data.

Many people might have the exact needs as they often already have a webshop or system to keep track of these things.

In this article, we'll look at how we can use the data import feature of Vendure.

## Importing products

When importing products, Vendure accepts a flat `.csv` format, and it can hold products, assets, variants, and even custom fields.
These elements will be created during the import, which is excellent.

You can find an example of the CSV format on the [Vendure docs](https://www.vendure.io/docs/developer-guide/importing-product-data/#product-import-format)

The are multiple ways of doing the import, and I decided I wanted to be able to run it manually, so I created my script for it.

I called the script `populate-server.ts`.
It's important to note that this uses the Vendure core `populate` function, which takes two parameters, the first being the initial data and the second your import.

My complete file looks like this.

```js
// populate-server.ts
import { bootstrap } from '@vendure/core';
import { populate } from '@vendure/core/cli';
import path from 'path';

import { config } from './src/vendure-config';
import { initialData } from './my-initial-data';

const productsCsvFile = path.join(__dirname, 'import.csv');

populate(() => bootstrap(config), initialData, productsCsvFile)
  .then((app) => {
    return app.close();
  })
  .then(
    () => process.exit(0),
    (err) => {
      console.log(err);
      process.exit(1);
    }
  );
```

Let's go ahead and also create this `my-initial-data.ts` file.
This file can be used to set up the admin section of your Vendure server.

In my case, I limited quite a bit of the setup, and my file looks like this.

```js
import { InitialData, LanguageCode } from '@vendure/core';

export const initialData: InitialData = {
  paymentMethods: [],
  defaultLanguage: LanguageCode.en,
  countries: [],
  defaultZone: 'SA',
  taxRates: [],
  shippingMethods: [],
  collections: [],
};
```

You can find the complete object you can construct on the [Vendure docs](https://www.vendure.io/docs/developer-guide/importing-product-data/#initial-data).

> Note: Every time you run your import, these will be executed, so running it more than once will result in duplicates.

To run the actual import, we can use the following command:

```bash
yarn ts-node populate-server.ts
```

Depending on the number of products, it can take some time to finish.

I often ran the script for testing purposes to get the proper import set.
You might have to play around with your CSV format if importing many custom fields this way.

### Thank you for reading, and let's connect!

Thank you for reading my blog. Feel free to subscribe to my email newsletter and connect on [Facebook](https://www.facebook.com/DailyDevTipsBlog) or [Twitter](https://twitter.com/DailyDevTips1)
