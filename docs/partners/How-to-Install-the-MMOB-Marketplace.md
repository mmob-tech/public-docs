---
tags: [marketplace]
---
# How to install your Integration

## Requirements

### Before you install

Before you install the mmob Integration you have created through our platform, we will assign you an ID (referred to as  `cp_id`) to give you access to  [MMOB Production Dashboard](https://dashboard.mmob.com/)  and  [MMOB Staging Dashboard](https://dashboard.staging.mmob.com/).

> The same ID will be used to access both production and staging dashboards.

### Content

To install your mmob Integration, the following steps are required:

1.  Set up a CNAME on the domain your main website is operating from.
2.  Place mmob's JavaScript script in your header.
3.  Call the integration with your user information.

----------

## 1. Set up a CNAME on the domain your main website is operating from

Due to the latest advancements in browser security and tracking prevention, an mmob integration needs to be served under your domain. To do so, you need to add the following configuration to your DNS:

```
integration-staging.ef-hub.com   CNAME     integration-ingress.staging.mmob.com
integration.ef-hub.com           CNAME     integration-ingress.prod.mmob.com
```

----------

## 2. Place MMOB javascript script in your header

Add this javascript snippet in your header. This is only required on the page that will be displaying your new integration.

```
<!DOCTYPE html>
<html lang="en">
  <head>
    ...
    <script src="https://assets.mmob.com/js/mmob-snippet.min.js"></script>
  </head>
  ...
</html>
```

----------

## 3. Call the Integration with the right user configuration

#### Add a container for your integration

First, add a target DOM element to your page. This is the containing element that the integration will be injected into. It will be loaded using an iFrame that will have  `width: 100%`  and  `height: 100%`.

In the example below, we've created an empty div with the id  `#mmobIntegration`, this will be our target div.

```
<main class="your-page">
  <div id="mmobIntegration"></div>
</main>
```

> You can control the integration size by styling your containing `div`.

Let's say for example you want to have your integration at full page width and height. You could style your container like so:

```
width: 100%;
height: 100vh;
```

and if you need to accomodate a header:

```
width: 100%;
height: calc(100vh - 70px); // For a header that is 70px in height.
```


#### Load the integration into the container

Once the integration has been added into your HTML page, you will have to call the following script to load it.

```
mmob.init({
  customerInfo: {
    email: 'stephen.hayes@example.com',
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
#### Note that the above is an example snippet. To configure the data snippet, you will need to remove the example data

> -   `cp_id` and `cp_deployment_id` will be provided to you
> -   `location`  is the id of the DOM object that will contain your integration

## Available fields for `customerInfo` 

Field | Type | Information
---------|----------|---------
email | String | Max Length 255
title | String | Max Length 10
first_name | String | Max Length 255
surname | String | Max Length 255
dob | Datetime ISO 8601
phone_number | String | Max Length 15
mobile_number | String | Max Length 15
preferred_name | String | Max Length 255
passport_number | String | Max Length 50
national_insurance_number | String | Max Length 15
building_number | String | Max Length 50
address_1 | String | Max Length 50
address_2 | String | Max Length 50
address_3 | String | Max Length 50
town_city | String | Max Length 50
county | String | Max Length 50
postcode | String | Max Length 8
country_of_residence | String | Max Length 50
nationality | String | Max Length 50
gender | String | Max Length 15
relationship_status | String | Max Length 50
number_of_children | Integer
partner_first_name | String | Max Length 255
partner_surname | String | Max Length 255
partner_dob | Datetime ISO 8601
partner_sex | String | Max Length 15
relationship_to_partner | String | Max Length 50
smoker | String | "yes" / "no"
number_of_cigarettes_per_week | Integer
drinker | String | "yes" / "no"
number_of_units_per_week | Integer
meta | JSON | Snake Case key. For any custom data not defined in the field column eg. ```{ "custom_data": 10 }```

> In the snippet, customerInfo is required but all fields are optional. We do suggest however that you provide as much information as you can to allow users to join services without having to ask for missing fields whenever a provider requires them.

---

## Contact us

Contact us at [info@mmob.com](mailto:info@mmob.com)
