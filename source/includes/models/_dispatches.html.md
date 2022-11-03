# Dispatches

Dispatches represent items being fulfilled

## The Dispatch Object

> Example JSON Response

```json-doc
{
  "dispatch": {
    "id": "di_4kzzxdk2",
    "order_id": "or_wlvzog4g",
    "order_number": 1289,
    "created": "2021-04-16T12:58:39Z",
    "comments": "Sent by Royal Mail using Next Day Delivery",
    "customer_note": "",
    "customer_po_number": "",
    "shipping_type": "Next Day Delivery",
    "shipping_address": {
      "company_name": "Sample Customer",
      "contact_name": "",
      "line1": "34 Edgar Buildings",
      "line2": "George Street",
      "city": "Bath",
      "state": "",
      "postal_code": "BA1 2FJ",
      "country": "GB"
    },
    "email_address": "sample@orderspace.com",
    "phone": "07911 123456",
    "dispatch_lines": [
      {
        "order_line_id": "ol_z1ow2pdm", 
        "sku": "ZAG-D-16",
        "name": "Angelica Dress",
        "options": "Size: 16",
        "quantity": 1
      },
      {
        "order_line_id": "ol_nm427o01", 
        "sku": "ZAG-D-18", 
        "name": "Angelica Dress",
        "options": "Size: 18",
        "quantity": 2
      },
      {
        "order_line_id": "ol_pmvznz21", 
        "sku": "ZAG-D-20", 
        "name": "Angelica Dress",
        "options": "Size: 20",
        "quantity": 3
      },
    ]	
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">order_id</span> <span class="type">string</span></h3>
		<div class="description">Internal identifier for the related order</div>
	</li>
	<li>
		<h3><span class="name">comments</span> <span class="type">string</span></h3>
		<div class="description">Comments to be shown on the delivery note and the dispatch email sent to the customer. This can contain courier details and tracking info, and anything else that the customer needs to know</div>
	</li>
	<li>
		<h3><span class="name">customer_po_number</span> <span class="type">string</span></h3>
		<div class="description">The customer's purchase order number for the related order</div>
	</li>
	<li>
		<h3><span class="name">customer_note</span> <span class="type">string</span></h3>
		<div class="description">The customer's note on the related order</div>
	</li>
	<li>
		<h3><span class="name">shipping_type</span> <span class="type">string</span></h3>
		<div class="description">The name of the shipping option selected for the related order</div>
	</li>
	<li>
		<h3><span class="name">shipping_address</span> <span class="type ha">hash</span></h3>
		<div class="description">
			The shipping address for the related order
			<div class="child-attributes">
				<h4>Child Attributes</h4>
				<ul>
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">company_name</span> <span class="type">string</span></h3>
						<div class="description">Company name</div>
					</li>
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">contact_name</span> <span class="type">string</span></h3>
						<div class="description">Contact name</div>
					</li>
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">line1</span> <span class="type">string</span></h3>
						<div class="description">Address line 1</div>
					</li>
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">line2</span> <span class="type">string</span></h3>
						<div class="description">Address line 2</div>
					</li>
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">city</span> <span class="type">string</span></h3>
						<div class="description">City, town or village</div>
					</li>
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">state</span> <span class="type">string</span></h3>
						<div class="description">State, county, province or region. U.S., Canadian and Australian addresses should use the abbreviated form of the state</div>
					</li>
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">postal_code</span> <span class="type">string</span></h3>
						<div class="description">ZIP or postal code</div>
					</li>
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">country</span> <span class="type">string</span></h3>
						<div class="description">Two-letter ISO 3166-1 country code</div>
					</li>
				</ul>
			</div>
		</div>
	</li>
	<li>
		<h3><span class="name">email_address</span> <span class="type">string</span></h3>
		<div class="description">The customer's email address for the related order</div>
	</li>
	<li>
		<h3><span class="name">phone</span> <span class="type">string</span></h3>
		<div class="description">The customer's phone number for the related order</div>
	</li>
	<li>
		<h3><span class="name">dispatch_lines</span> <span class="type li">list</span></h3>
		<div class="description">
			<div class="child-attributes">
				<h4>Child Attributes</h4>
				<ul>
					<li>
						<h3><span class="parent-name">dispatch_line.</span><span class="name">order_line_id</span> <span class="type">string</span></h3>
						<div class="description">Internal identifier for the order line being dispatched</div>
					</li>
					<li>
						<h3><span class="parent-name">dispatch_line.</span><span class="name">sku</span> <span class="type">string</span></h3>
						<div class="description">The SKU of the item being dispatched</div>
					</li>
					<li>
						<h3><span class="parent-name">dispatch_line.</span><span class="name">name</span> <span class="type">string</span></h3>
						<div class="description">The name of the item being dispatched</div>
					</li>
					<li>
						<h3><span class="parent-name">dispatch_line.</span><span class="name">options</span> <span class="type">string</span></h3>
						<div class="description">The options (size/color etc) of the item being dispatched</div>
					</li>
					<li>
						<h3><span class="parent-name">dispatch_line.</span><span class="name">quantity</span> <span class="type number">number</span></h3>
						<div class="description">The number of items being dispatched</div>
					</li>
				</ul>
			</div>
		</div>
	</li>
</ul>


## Create a dispatch

> Example request with curl

```shell
curl -X POST "https://api.orderspace.com/v1/dispatches" \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
    "dispatch": {
      "order_id": "or_wlvzog4g",
      "comments": "Sent by Royal Mail using Next Day Delivery",
      "dispatch_lines": [
        {"sku": "ZAG-D-16", "quantity": 1},
        {"sku": "ZAG-D-18", "quantity": 2},
        {"sku": "ZAG-D-20", "quantity": 3},
      ]
    }
  }'
```

> Example HTTP 200 success response

```json-doc
{
  "dispatch": {
    "id": "di_4kzzxdk2",
    "order_id": "or_wlvzog4g",
    "order_number": 1289,
    "created": "2021-04-16T12:58:39Z",
    "comments": "Sent by Royal Mail using Next Day Delivery",
    "customer_note": "",
    "customer_po_number": "",
    "shipping_type": "Next Day Delivery",
    "shipping_address": {
      "company_name": "Sample Customer",
      "contact_name": "",
      "line1": "34 Edgar Buildings",
      "line2": "George Street",
      "city": "Bath",
      "state": "",
      "postal_code": "BA1 2FJ",
      "country": "GB"
    },
    "email_address": "sample@orderspace.com",
    "phone": "07911 123456",
    "dispatch_lines": [
      {
        "order_line_id": "ol_z1ow2pdm", 
        "sku": "ZAG-D-16", 
        "name": "Angelica Dress",
        "options": "Size: 16",
        "quantity": 1
      },
      {
        "order_line_id": "ol_nm427o01", 
        "sku": "ZAG-D-18", 
        "name": "Angelica Dress",
        "options": "Size: 18",
        "quantity": 2
      },
      {
        "order_line_id": "ol_pmvznz21", 
        "sku": "ZAG-D-20", 
        "name": "Angelica Dress",
        "options": "Size: 20",
        "quantity": 3
      },
    ]	
  }
}
```

> Example HTTP 422 error response

```json-doc
{
  "message": "The order has already been fulfilled"
}
```

Create a dispatch. This will mark the order lines as dispatched and reduce the stock on hand representing the items leaving your warehouse. The status of the related order will change to <code>fulfilled</code> if all items on the order have been dispatched. A dispatch confirmation email will be sent to the customer if this setting is enabled

### HTTP Request

<code>POST https://api.orderspace.com/v1/dispatches</code>

### Response

`HTTP 200 Success` - The dispatch object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors

## List dispatches

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/dispatches \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -d limit=20 \
  -d starting_after=cu_53zjgvnm
```

> Example HTTP 200 success response

```json-doc
{
  "dispatches": [
    {
      "id": "di_4kzzxdk2",
      "order_id": "or_wlvzog4g",
      "order_number": 1289,
      "created": "2021-04-16T12:58:39Z",
      "comments": "Sent by Royal Mail using Next Day Delivery",
      "customer_note": "",
      "customer_po_number": "",
      "shipping_type": "Next Day Delivery",
      "shipping_address": {
        "company_name": "Sample Customer",
        "contact_name": "",
        "line1": "34 Edgar Buildings",
        "line2": "George Street",
        "city": "Bath",
        "state": "",
        "postal_code": "BA1 2FJ",
        "country": "GB"
      },
      "email_address": "sample@orderspace.com",
      "phone": "07911 123456",
      "dispatch_lines": [
        {
          "order_line_id": "ol_z1ow2pdm", 
          "sku": "ZAG-D-16", 
          "name": "Angelica Dress",
          "options": "Size: 16",
          "quantity": 1
        },
        {
          "order_line_id": "ol_nm427o01", 
          "sku": "ZAG-D-18", 
          "name": "Angelica Dress",
          "options": "Size: 18",
          "quantity": 2
				},
        {
          "order_line_id": "ol_pmvznz21", 
          "sku": "ZAG-D-20", 
          "name": "Angelica Dress",
          "options": "Size: 20",
          "quantity": 3
        }
      ]	
    },
    {...},
    {...}
  ]
}
```

Retrieve a list of dispatches. Dispatches are returned in the order they are created with the most recently created listed first

### HTTP Request

`GET https://api.orderspace.com/v1/dispatches`

### Parameters

<ul class="attributes">
	<li>
		<h3><span class="name">starting_after</span> <span class="optional">optional</span></h3>
		<div class="description">A cursor used for pagination. Setting `starting_after` to the ID of the last dispatch in the list will retrieve the next page of dispatches</div>
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
		<h3><span class="name">created_before</span> <span class="optional">optional</span></h3>
		<div class="description">Return records created before the given date and time in ISO 8601 format, e.g. <code>2019-10-29T21:00</code> </div>
	</li>
	<li>
		<h3><span class="name">order_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return dispatches for the specified order</div>
	</li>
</ul>

## Retrieve a dispatch

```shell
curl -X GET https://api.orderspace.com/v1/dispaches/di_4kzzxdk2 \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example HTTP 200 success response

```json-doc
{
  "dispatch": {
    "id": "di_4kzzxdk2",
    "order_id": "or_wlvzog4g",
    "order_number": 1289,
    "created": "2021-04-16T12:58:39Z",
    "comments": "Sent by Royal Mail using Next Day Delivery",
    "customer_note": "",
    "customer_po_number": "",
    "shipping_type": "Next Day Delivery",
    "shipping_address": {
      "company_name": "Sample Customer",
      "contact_name": "",
      "line1": "34 Edgar Buildings",
      "line2": "George Street",
      "city": "Bath",
      "state": "",
      "postal_code": "BA1 2FJ",
      "country": "GB"
    },
    "email_address": "sample@orderspace.com",
    "phone": "07911 123456",
    "dispatch_lines": [
      {
        "order_line_id": "ol_z1ow2pdm", 
        "sku": "ZAG-D-16", 
        "name": "Angelica Dress",
        "options": "Size: 16",
        "quantity": 1
      },
      {
        "order_line_id": "ol_nm427o01", 
        "sku": "ZAG-D-18", 
        "name": "Angelica Dress",
        "options": "Size: 18",
        "quantity": 2
      },
      {
        "order_line_id": "ol_pmvznz21", 
        "sku": "ZAG-D-20", 
        "name": "Angelica Dress",
        "options": "Size: 20",
        "quantity": 3
      },
    ]	
  }
}
```

Retrieve a single dispatch by ID

### HTTP Request

`GET https://api.orderspace.com/v1/dispatches/:dispatch_id`

### Response

`HTTP 200 Success` - The dispatch record in JSON format

`HTTP 404 Not Found` - A message describing the error

