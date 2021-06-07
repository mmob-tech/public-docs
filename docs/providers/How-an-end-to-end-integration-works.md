# How an end to end integration works

This document tracks a provider end to end implementation process.

First, a product needs to be created in our system. A product is anything a user can “purchase”, from tangible products to services offered by your company.

Since we need the flexibility of a service being offered at different price points, a product won’t include the price at the product creation stage, for that you need to create a price object attached to a product.

A single product can be assigned multiple prices.

## 1. Set up your products

### 1.1 Create the product

To create a product we are using the following information

`POST /products`

```json
{
	"name": "Your product",
	"description": "Your product description.",
	"enabled": true,
	"meta": {
		"your_extra_attributes": "value"
	}
	"product_type": "utilities_broadband"
}
```

- `product.name`: Name of the product to be displayed to end users.
- `product.description`: Name of the product to be displayed to customers
- `product.enabled`: Boolean. If disabled, the product won’t be available to be shown and acquired by end users.
- `product.meta`: A map of key string value string to store extra information. In this case the keys shown above are required to display the broadband tile on the marketplace.
- `product.type` one of the following categories

```
“insurance_car_insurance”
“insurance_home_insurance”
“insurance_travel_insurance”
“insurance_health_insurance”
“insurance_pet_insurance”
“insurance_gadget_insurance”
“investments”
“lending”
“insurance”
“rewards”
“utilities”
“insurance_life_insurance”
“insurance_business_insurance”
“investments_investment_account”
“investments_stocks_and_shares_isa”
“investments_sipp”
“investments_crowdfunding”
“investments_current_accounts”
“investments_savings_accounts”
“investments_cash_isas”
“lending_mortgages”
“lending_loans”
“lending_credit_cards”
“utilities_energy”
“utilities_broadband”
“utilities_tv”
“utilities_mobile_phones”
```

## 1.2. Create the price

`POST /products/{prod_id}/pricing`

```json
{
  "name": "Monhtly payment",
  "currency": "GBP",
  "amount": 3999
}
```

- `pricing.name` Name of the pricing item
- `currency` internal currency used for the pricing. Format is [ISO 4217](https://en.wikipedia.org/wiki/ISO_4217)
- `amount`: price, in pennies

Once your product is added and set as enabled you are ready to start receiving orders.

## 2. Dealing with orders

The best way to deal with orders is to consume them with a web hook.

When an end user places an order, our system register it as an order object with the following format.

```json
{
  "id": "po_xxxxxxxxxxx",
  "status": "Pending",
  "input": {
    "last_name": "Nichols",
    "sort_code": "11-22-33",
    "first_name": "Lisa",
    "account_number": "123456789"
  },
  "prod_id": "prod_EfeUDJnTVdDigaqQ9rMaC",
  "pricing_id": "price_xxxxxxxxxxx",
  "tpp_user_id": "tus_xxxxxxxxxxx"
}
```

The `input` information is captured on the UI and contains very specific details for the TPP. For now MMOB team is the one that will be manually adding the fields needed per integration until we have the system that will allow our partners to change and update it dynamically.

On the marketplace, for the first minute than an order is placed, it will display a spinner with the status “processing…” meanwhile our systems trigger the web hook and expect an update from our partners.

During that time, MMOB will post the new order to the designated TPP webhook. Our provider, will then do the following:

1. Parse the order information.
2. Use MMOB API to query extra information needed, like product, pricing and user details (address, postcode, etc.).
3. WIth that information, call MMOB API order update, and provide the status

<!-- theme: success -->

> If successful:

`POST /orders/{order_id}`

```json
{
  "status": "Succesful",
  "output": {
    "key": "Value"
  }
}
```

<!-- theme: warning -->

> If in the specific user more information is needed

```json
{
  "status": "Need_more_info",
  "output": {
    "required_fields": "engineer_appointment_date, engineer_apointment_time"
  }
}
```


<!-- theme: error -->

> If there's an error

```json
{
  "status": "Failed",
  "output": {
    "error": "PBX Over capacity"
  }
}
```

Once updated, the user will see on their screen an update with the final state of the order.

If for some reason the web hook system fails, our TPPs can go to the dashboard and process the orders manually. Although the polling will stop after a minute of the order creation, the user will be able to see the latest status when they refresh the screen.
