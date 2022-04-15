# Customer Groups

Customer groups represent a set of customers with shared settings. Each customer can belong to a single customer group

## The Customer Group object

> Example customer group

```json-doc
{
  "customer_group": {
    "id": "cg_mg5r89wo",
    "name": "Default"
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the customer group</div>
	</li>
	<li>
		<h3><span class="name">name</span> <span class="type">string</span></h3>
		<div class="description">A unique name for the customer group<div>
	</li>
</ul>

## List customer groups

> Example request with curl

```shell
curl "https://api.orderspace.com/v1/customer_groups" \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "customer_groups": [
    {
      "id": "cg_mg5r89wo",
      "name": "Default"
    },
    {...},
    {...}
  ]
}
```

Retrieve a list of customer groups. This endpoint does not support pagination

### HTTP Request

`GET https://api.orderspace.com/v1/customer_groups`

### Response

`HTTP 200 Success` - A list of customer groups in JSON format

