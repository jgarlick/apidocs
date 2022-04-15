# Inventory Levels

An inventory level represents the quantity in stock and quantity available to order for a product variant. The endpoints for this resource allow stock levels to be retrieved and updated in bulk. For more details on how inventory works in Orderspace and the difference between on hand and available, see our help docs at <a href="https://docs.orderspace.com/article/48-about-inventory">https://docs.orderspace.com/article/48-about-inventory</a>

## The Inventory Level Object

> Example inventory level

```json-doc
{
  "inventory_level": {
    "sku": "AA-RED-XS",
    "on_hand": 5,
    "available": 5
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">sku</span> <span class="type">string</span></h3>
		<div class="description">Inventory levels use the SKU rather than an ID as a reference to a specific product variant</div>
	</li>
	<li>
		<h3><span class="name">on_hand</span> <span class="type number">number</span></h3>
		<div class="description">On hand represents the quantity in physically in stock</div>
	</li>
	<li>
		<h3><span class="name">available</span> <span class="type number">number</span></h3>
		<div class="description">Available represents the quantity available for customers to order</div>
	</li>
</ul>


## List inventory levels

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/inventory_levels \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -d limit=20 \
  -d starting_after=AD-08
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "inventory_levels": [
    {
      "sku": "AD-10",
      "on_hand": 10,
      "available": 4
    },
    {
      "sku": "AD-12",
      "on_hand": 45,
      "available": 45
    },
    {
      "sku": "AD-14",
      "on_hand": 0,
      "available": 0
    }
  ],
  "has_more": false
}
```

Retrieve a list of inventory levels. Inventory levels are returned in SKU order

### HTTP Request

`GET https://api.orderspace.com/v1/inventory_levels`


### Parameters

<ul class="attributes">
	<li>
		<h3><span class="name">starting_after</span> <span class="optional">optional</span></h3>
		<div class="description">A cursor used for pagination. Setting `starting_after` to the SKU of the last inventory level in the list will retrieve the next page of inventory levels</div>
	</li>
	<li>
		<h3><span class="name">limit</span> <span class="optional">optional</span></h3>
		<div class="description">A limit on the number of records returned. The default is 50 and the maximum limit is 200</div>
	</li>
	<li>
		<h3><span class="name">created_since</span> <span class="optional">optional</span></h3>
		<div class="description">Return records created since the given date and time in ISO 8601 format, e.g. <code>2019-10-29T21:00</code> </div>
	</li>
	<li>
		<h3><span class="name">updated_since</span> <span class="optional">optional</span></h3>
		<div class="description">Return inventory levels updated since the given date and time in ISO 8601 format, e.g. <code>2019-10-29T21:00</code> </div>
	</li>
	<li>
		<h3><span class="name">product_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return inventory levels for a specific product</div>
	</li>
	<li>
		<h3><span class="name">sku</span> <span class="optional">optional</span></h3>
		<div class="description">Return the inventory level for a specific SKU</div>
	</li>
</ul>

## Update inventory levels

> Example request with curl

```shell
curl -X POST https://api.orderspace.com/v1/inventory_levels \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
  "inventory_levels": [
    {
      "sku": "11106-WB-10",
      "on_hand": 30
    },
    {
      "sku": "11106-WB-12",
      "on_hand": 45
    },
    {
      "sku": "11106-WB-14",
      "on_hand": 20
    }
  ]
}'
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "inventory_levels": [
    {
      "sku": "11106-WB-10",
      "on_hand": 30,
      "available": 20
    },
    {
      "sku": "11106-WB-12",
      "on_hand": 45,
      "available": 45
    },
    {
      "sku": "11106-WB-14",
      "on_hand": 20,
      "available": 0
    }
  ]
}
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
  "message": "On Hand and Available can not be updated at the same
	 time because one is automatically calculated from the other"
}
```

Update the specified inventory levels. Unlike most update requests, multiple inventory levels can be updated at once, up to a maximum of 200 per request.

Update will accept either <code>on_hand</code> or <code>available</code>, but not both at the same time because one is calculated from the other. For example, if <code>on_hand</code> is increased from 10 to 15, <code>available</code> will be automatically increased by 5. 

See our help docs at <a href="https://docs.orderspace.com/article/48-about-inventory">https://docs.orderspace.com/article/48-about-inventory</a> for more details on the difference between On Hand and Available.

### HTTP Request

`POST https://api.orderspace.com/v1/inventory_levels`

### Response

`HTTP 200 Success` - A list of updated inventory levels in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors



