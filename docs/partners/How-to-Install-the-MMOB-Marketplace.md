---
tags: [marketplace]
---

# How to Install your Marketplace

## Requirements

### Before you install the MMOB Marketplace

Before you install the MMOB Marketplace, we will create a Customer Partner ID (refered as `cp_id`) to give you access to [MMOB Dashboard production](https://dashboard.mmob.com) and [MMOB Dashboard staging](https://dashboard.staging.mmob.com).

<!-- theme: success -->

> The Customer Partner ID will be used to access both production and staging dashboards.

### Content

To install the MMOB marketplace, the following steps are required:

1. Set up a CNAME on the domain your main website is operating from.
2. Place MMOB JavaScript script in your header.
3. Call the marketplace with your user information.

---

## 1. Set up a CNAME on the domain your main website is operating from

Due to the latest advancements in browser security and tracking prevention, MMOB Marketplace needs to be served under your domain. To do so, you need to add the following configuration to your DNS:

```
marketplace-staging.example.com   CNAME     marketplace-ingress.staging.mmob.com
marketplace.example.com           CNAME     marketplace-ingress.prod.mmob.com
```

---

## 2. Place MMOB javascript script in your header

Add this javascript snippet in your header. This is only required on the page that will be displaying your new Marketplace.

```html
<!DOCTYPE html>
<html lang="en">
  <head>
    ...
    <script src="https://assets.mmob.com/js/mmob-snippet.min.js"></script>
  </head>
  ...
</html>
```

---

## 3. Call the marketplace with the right user configuration

#### Add a placeholder for your marketplace

First, add the placeholder DOM that will be containing the marketplace. The marketplace will be loaded using an iFrame that will have `width: 100%` and `height: 100%`.

Notice that we created an empty div with the id `#mmobMarketplace`

```html
<main class="main=-page">
  <div id="mmobMarketplace"></div>
</main>
```

<!-- theme: success -->

> You can control it's size by styling the `div`.

#### Load the marketplace into the placeholder

Once the marketplace has been added into your HTML page, you will have to call the following script to load it.

```js
mmob.init({
  customerInfo: {
    // required information
    email: 'stephen.hayes@example.com',

    // additional fields
    first_name: 'Stephen',
    surname: 'Hayes',
    gender: 'male',
    title: 'Mr',
    address_1: '1281 Miller Ave',
    town_city: 'Townsville',
    dob: '1968-05-30T21:12:22.275Z',
  },

  // marketplace configuration
  cp_id: 'cp_DhskfrQ5V0HLfcVwbl54Q',
  location: '#mmobMarketplace',
  marketplace_url: 'marketplace.example.com',
});
```

<!-- theme: info -->

> - `cp_id` is the id provided to you
> - `location` is the DOM object that will contain the marketplace

<!-- theme: info -->

> For a given customer, only the field `email`is required. We suggest to provide as much information you can to allow users to join services without having to ask missing fields whenever a provider requires them.

<!-- theme: warning -->

> In a future update, the Key "marketplace_url" will be removed from the snippet and placed in your CP settings in the dashboard.

---

## Contact us

Contact us at [info@mmob.com](mailto:info@mmob.com)
