# Tax Rates

Tax Rates represent the different rates of tax that can be charged on items

## The Tax Rate object

> Example tax rate

```json-doc
{
  "tax_rate": {
    "id": "tr_xk7pe5kd",
    "name": "Standard",
    "rate": 20.0
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the tax rate</div>
	</li>
	<li>
		<h3><span class="name">name</span> <span class="type">string</span></h3>
		<div class="description">A unique name for the tax rate<div>
	</li>
	<li>
		<h3><span class="name">rate</span> <span class="type number">number</span></h3>
		<div class="description">The tax rate as a percentage</div>
	</li>
</ul>

## List tax rates

> Example request with curl

```shell
curl "https://api.orderspace.com/v1/tax_rates" \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "tax_rates": [
    {
      "id": "tr_xk7pe5kd",
      "name": "Standard",
      "rate": 20.0
    },
    {...},
    {...}
  ]
}
```

Retrieve a list of tax rates. This endpoint does not support pagination

### HTTP Request

`GET https://api.orderspace.com/v1/tax_rates`


### Response

`HTTP 200 Success` - A list of tax rates in JSON format
