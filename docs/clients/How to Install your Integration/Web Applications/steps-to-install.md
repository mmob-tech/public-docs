# Steps to Install your Integration

To install your mmob Integration, the following steps are required:

1.  Set up a CNAME on the domain your main website is operating from.
2.  Place mmob's JavaScript script in your header.
3.  Call the integration with your user information.

---

## 1. Set up a CNAME on the domain your main website is operating from

Due to the latest advancements in browser security and tracking prevention, an mmob integration needs to be served under your domain. To do so, you need to add the following configuration to your DNS:

```bash
integration-staging.ef-hub.com   CNAME     client-ingress.stag.mmob.com
integration.ef-hub.com           CNAME     client-ingress.prod.mmob.com
```

---

## 2. Place MMOB javascript script in your header

Add this javascript snippet in your header. This is only required on the page that will be displaying your new integration.

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

## 3. Call the Integration with the right user configuration

#### Add a container for your integration

First, add a target DOM element to your page. This is the containing element that the integration will be injected into. It will be loaded using an iFrame that will have `width: 100%` and `height: 100%`.

In the example below, we've created an empty div with the id `#mmobIntegration`, this will be our target div.

```html
<main class="your-page">
  <div id="mmobIntegration"></div>
</main>
```

> You can control the integration size by styling your containing `div`.

Let's say for example you want to have your integration at full page width and height. You could style your container like so:

```css
width: 100%;
height: 100vh;
```

and if you need to accommodate a header:

```css
width: 100%;
height: calc(100vh - 70px); // For a header that is 70px in height.
```

#### Load the integration into the container

Once the integration has been added into your HTML page, you will have to call the script to load it.
As an example:

```javascript
mmob.init({
  customerInfo: {
    email: {{customer email}},
    first_name: 'Stephen',
    surname: 'Hayes',
    gender: 'male',
    title: 'Mr',
    building_number: '81',
    address_1: 'Miller Street',
    town_city: 'Hull',
    postcode: 'HG45BU',
    dob: '1968-05-30T21:12:22.275Z',
  },

  // integration configuration
  cp_id: 'cp_XXXXXXXXXXXXXXXXXXXXX',
  cp_deployment_id: 'cpd_XXXXXXXXXXXXXXXXXXXXX',
  location: '#mmobMarketplace',
  marketplace_url: 'https://marketplace.example.com',
});
```

#### ??? Note that the above is an example snippet. To configure the data snippet, you will need to remove the example data

> - `cp_id` and `cp_deployment_id` will be provided to you
> - `location` is the id of the DOM object that will contain your integration

---

## Contact us

Contact us at [contact@mmob.com](mailto:contact@mmob.com)
