# Price Lists

Price lists are used to charge different prices to different customers. Each price list has a currency, so they can also be used to support multi-currency ordering

## The Price List object

> Example price list

```json-doc
{
  "price_list": {
    "id": "pl_y3157jxp",
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


## Create a price list

> Example request with curl

```shell
curl -X POST https://api.orderspace.com/v1/price_lists \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
    "price_list": {
      "name": "Euros",
      "currency": "EUR",
      "conversion_rate": 100
    }
  }'
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "price_list": {
    "id": "pl_y3157jxp",
    "name": "Euros",
    "currency": "EUR",
    "conversion_rate": 100
  }
}
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
	"message": "Validation failed: Name has already been taken"
}
```

Create a new price list

### HTTP Request

`POST https://api.orderspace.com/v1/price_lists`

### Response

`HTTP 200 Success` - The price list object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors


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
      "id": "pl_y3157jxp",
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



## Retrieve a price list

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/price_lists/pl_y3157jxp \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "price_list": {
    "id": "pl_y3157jxp",
    "name": "Euros",
    "currency": "EUR",
    "conversion_rate": 100
  }
}
```

Retrieve a single price list by ID

### HTTP Request

`GET https://api.orderspace.com/v1/price_lists/:price_list_id`

### Response

`HTTP 200 Success` - The price list record in JSON format

`HTTP 404 Not Found` - A message describing the error


## Update a price list

> Example request with curl

```shell
curl -X PUT https://api.orderspace.com/v1/price_lists/pl_y3157jxp \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
    "price_list": {
      "name": "Euros",
      "currency": "EUR",
      "conversion_rate": 100
    }
  }'
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "price_list": {
    "id": "pl_y3157jxp",
    "name": "Euros",
    "currency": "EUR",
    "conversion_rate": 100
  }
}
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
	"message": "Validation failed: Name has already been taken"
}
```

Update an existing price list. Any fields not included in the update will remain the same.

### HTTP Request

`PUT https://api.orderspace.com/v1/price_lists/:price_list_id`


### Response

`HTTP 200 Success` - The price list object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors


## Delete a price list

> Example request with curl

```shell
curl -X DELETE https://api.orderspace.com/v1/price_lists/pl_y3157jxp \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "price_list": {
      "id": "pl_y3157jxp",
      "deleted": true
    }
}
```

Delete a price list.

### HTTP Request

`DELETE https://api.orderspace.com/v1/price_lists/:price_list_id`

### Response

`HTTP 200 Success` - A short representation of the price list in JSON format

`HTTP 404 Success` - A message describing the error

