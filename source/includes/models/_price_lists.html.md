# Price Lists

Price lists are used to charge different prices to different customers. Each price list has a currency, so they can also be used to support multi-currency ordering

## The Price List object

> Example price list

```json-doc
{
  "price_list": {
    "id": "pr_z0j7yjl2",
    "name": "Euros",
    "currency": "EUR",
    "conversion_rate": 100
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the price list</div>
	</li>
	<li>
		<h3><span class="name">name</span> <span class="type">string</span></h3>
		<div class="description">A unique name for the price list<div>
	</li>
	<li>
		<h3><span class="name">currency</span> <span class="type">string</span></h3>
		<div class="description">The three-letter ISO currency code representing the price list's currency</div>
	</li>
	<li>
		<h3><span class="name">conversion_rate</span> <span class="type number">number</span></h3>
		<div class="description">The conversion rate, as a percentage, applied to item prices if they don't have a specific price set for this price list<div>
	</li>
</ul>

## List price lists

> Example request with curl

```shell
curl "https://api.orderspace.com/v1/price_lists" \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "price_lists": [
    {
      "id": "pr_z0j7yjl2",
      "name": "Euros",
      "currency": "EUR",
      "conversion_rate": 100
    },
    {...},
    {...}
  ]
}
```

Retrieve a list of price lists. This endpoint does not support pagination

### HTTP Request

`GET https://api.orderspace.com/v1/price_lists`


### Response

`HTTP 200 Success` - A list of price lists in JSON format
