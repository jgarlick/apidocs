# Orders

## The Order Object

> Example order

```json-doc
{
  "order": {		
    "id": "or_l5DYqeDn",
    "number": 1204,
    "created": "2020-04-08T15:03:55Z",
    "status": "new",
    "customer_id": "cu_gpbOljAn"
    "company_name": "Sample Customer",
    "phone": "07911 123456", 
    "email_addresses": {
      "orders": "sample@orderspace.com",
      "dispatches": "sample@orderspace.com",
      "invoices": "sample@orderspace.com",
    }
    "delivery_date": "2020-04-09",
    "reference": "",
    "internal_note": "",
    "customer_po_number": "",
    "customer_note": "",
    "standing_order_id": "or_68ogydlx",
    "shipping_type": "Special Delivery",
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
    "billing_address": {
      "company_name": "Sample Customer",
      "contact_name": "",
      "line1": "336 Hargrave Rd",
      "line2": "Windsor",
      "city": "New York",
      "state": "NY",
      "postal_code": "13865",
      "country": "US"
    },
    "order_lines": [
      {
        "id": "ol_NdOLvlpw",
        "sku": "AM-D-CHR-10",
        "name": "Amelia Dress",
        "options": "Colour: Charcoal, Size: 10",
        "grouping_category": {
          "id": "ca_9n1klwr5",
          "name": "Dresses"
        },
        "shipping": false,
        "quantity": 10,
        "unit_price": 30.0,
        "sub_total": 300.0,
        "tax_name": "Standard",
        "tax_rate": 20.0,
        "tax_amount": 60.0,
				"on_hold": false,
				"invoiced": 0,
				"paid": 0,
				"dispatched": 0
      }
    ],
    "currency": "GBP",	
    "net_total": 306.1,
    "gross_total": 366.1
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the order</div>
	</li>
	<li>
		<h3><span class="name">number</span> <span class="type number">number</span></h3>
		<div class="description">Unique number identifying the order, shown to the customer</div>
	</li>
	<li>
		<h3><span class="name">created</span> <span class="type">string</span></h3>
		<div class="description">The date and time the order was placed in ISO 8601 format</div>
	</li>
	<li>
		<h3><span class="name">status</span> <span class="type">string</span></h3>
		<div class="description">The status of the order, one of <code>new</code>, <code>invoiced</code>, <code>released</code>, <code>part_fulfilled</code>, <code>preorder</code>, <code>fulfilled</code>, <code>standing_order</code> or <code>cancelled</code></div>
	</li>
	<li>
		<h3><span class="name">customer_id</span> <span class="type">string</span></h3>
		<div class="description">Internal identifier for the related customer resource</div>
	</li>				
	<li>
		<h3><span class="name">company_name</span> <span class="type">string</span></h3>
		<div class="description">The customer's company name</div>
	</li>
	<li>
		<h3><span class="name">phone</span> <span class="type">string</span></h3>
		<div class="description">The customer's phone number</div>
	</li>
	<li>
		<h3><span class="name">email_addresses</span> <span class="type ha">hash</span></h3>
		<div class="description">The customer's email addresses
			<div class="child-attributes">
				<h4>Child Attributes</h4>
				<ul>
					<li>
						<h3><span class="name">orders</span> <span class="type">string</span></h3>
						<div class="description">The customer's email address for order confirmations. Multiple email addresses may be present, separated by commas</div>
					</li>
					<li>
						<h3><span class="name">dispatches</span> <span class="type">string</span></h3>
						<div class="description">The customer's email address for dispatch confirmations. Multiple email addresses may be present, separated by commas</div>
					</li>
					<li>
						<h3><span class="name">invoices</span> <span class="type">string</span></h3>
						<div class="description">The customer's email address for invoices. Multiple email addresses may be present, separated by commas</div>
					</li>
				</ul>
			</div>
		</div>
	</li>
	<li>
		<h3><span class="name">delivery_date</span> <span class="type">string</span></h3>
		<div class="description">The customer requested delivery date in ISO 8601 format</div>
	</li>
	<li>
		<h3><span class="name">reference</span> <span class="type">string</span></h3>
		<div class="description">Your reference for this order. Visible to the customer but not editable by them</div>
	</li>
	<li>
		<h3><span class="name">internal_note</span> <span class="type">string</span></h3>
		<div class="description">Your internal note for this order, not visible to the customer</div>
	</li>
	<li>
		<h3><span class="name">customer_po_number</span> <span class="type">string</span></h3>
		<div class="description">The customer's purchase order number for this order</div>
	</li>
	<li>
		<h3><span class="name">customer_note</span> <span class="type">string</span></h3>
		<div class="description">The customer's note on this order</div>
	</li>
	<li>
		<h3><span class="name">standing_order_id</span> <span class="type">string</span></h3>
		<div class="description">Internal identifier for the standing order used to generate this repeat order. Set to null if this is not a repeat order. Only present if the standing orders feature is enabled</div>
	</li>
	<li>
		<h3><span class="name">shipping_type</span> <span class="type">string</span></h3>
		<div class="description">The name of the shipping option selected for this order</div>
	</li>
	<li>
		<h3><span class="name">shipping_address</span> <span class="type ha">hash</span></h3>
		<div class="description">
			The order's shipping address.
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
		<h3><span class="name">billing_address</span> <span class="type ha">hash</span></h3>
		<div class="description">The order's billing address
			<div class="child-attributes">
				<h4>Child Attributes</h4>
				<ul>
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">company_name</span> <span class="type">string</span></h3>
						<div class="description">Company name</div>
					</li>				
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">contact_name</span> <span class="type">string</span></h3>
						<div class="description">Contact name</div>
					</li>				
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">line1</span> <span class="type">string</span></h3>
						<div class="description">Address line 1</div>
					</li>				
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">line2</span> <span class="type">string</span></h3>
						<div class="description">Address line 2</div>
					</li>				
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">city</span> <span class="type">string</span></h3>
						<div class="description">City, town or village</div>
					</li>				
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">state</span> <span class="type">string</span></h3>
						<div class="description">State, county, province or region. U.S., Canadian and Australian addresses should use the abbreviated form of the state</div>
					</li>				
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">postal_code</span> <span class="type">string</span></h3>
						<div class="description">ZIP or postal code</div>
					</li>				
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">country</span> <span class="type">string</span></h3>
						<div class="description">Two-letter ISO 3166-1 country code</div>
					</li>				
				</ul>
			</div>
		</div>
	</li>
	<li>
		<h3><span class="name">order_lines</span> <span class="type li">list</span></h3>
		<div class="description">
			List of the individual lines that make up the order as <code>order lines</code>
			<div class="child-attributes">
				<h4>Child Attributes of Order Lines</h4>
				<ul>
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">id</span> <span class="type">string</span></h3>
						<div class="description">Internal identifier for the order line</div>
					</li>
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">sku</span> <span class="type">string</span></h3>
						<div class="description">The unique code for the ordered item</div>
					</li>
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">name</span> <span class="type">string</span></h3>
						<div class="description">The name of the ordered item</div>
					</li>
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">options</span> <span class="type">string</span></h3>
						<div class="description">The options (size/color etc) of the ordered item</div>
					</li>
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">grouping_category</span> <span class="type ha">hash</span></h3>
						<div class="description">
							The grouping category for this order line. Only present if the "group products on orders" feature is enabled
							<div class="child-attributes">
								<h4>Child Attributes of Grouping Category</h4>
								<ul>
									<li>
										<h3><span class="parent-name">order_line.grouping_category.</span><span class="name">id</span> <span class="type">string</span></h3>
										<div class="description">Internal identifier for the category</div>
									</li>
									<li>
										<h3><span class="parent-name">order_line.grouping_category.</span><span class="name">name</span> <span class="type">string</span></h3>
										<div class="description">The name of the category</div>
									</li>
								</ul>
							</div>
						</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">shipping</span> <span class="type">boolean</span></h3>
						<div class="description">Indicates whether the order line represents a shipping charge</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">quantity</span> <span class="type number">number</span></h3>
						<div class="description">The number of items ordered</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">unit_price</span> <span class="type number">number</span></h3>
						<div class="description">The unit price of each item on this line</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">sub_total</span> <span class="type number">number</span></h3>
						<div class="description">The line sub-total excluding tax</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">tax_name</span> <span class="type">string</span></h3>
						<div class="description">The name of the tax rate applied to this order line</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">tax_rate</span> <span class="type number">number</span></h3>
						<div class="description">The tax rate applied to this order line as a percentage</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">tax_amount</span> <span class="type number">number</span></h3>
						<div class="description">The total tax applied to this order line</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">on_hold</span> <span class="type number">boolean</span></h3>
						<div class="description">Indicates whether the items are on hold. If set to true, the items are preorders that should not have stock allocated to them or be fulfilled</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">invoiced</span> <span class="type number">number</span></h3>
						<div class="description">The number of items invoiced</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">paid</span> <span class="type number">number</span></h3>
						<div class="description">The number of items paid for via invoices</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">dispatched</span> <span class="type number">number</span></h3>
						<div class="description">The number of items dispatched</div>
					</li>				
				</ul>
			</div>
		</div>
	</li>
	<li>
		<h3><span class="name">currency</span> <span class="type">string</span></h3>
		<div class="description">The three-letter ISO currency code representing the order's currency</div>
	</li>
	<li>
		<h3><span class="name">net_total</span> <span class="type number">number</span></h3>
		<div class="description">The total cost of all items on the order excluding tax</div>
	</li>
	<li>
		<h3><span class="name">gross_total</span> <span class="type number">number</span></h3>
		<div class="description">The total cost of all items on the order including tax</div>
	</li>
</ul>

## List orders

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/orders \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -d limit=20 \
  -d starting_after=or_jl663xl1
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "orders": [
    {		
      "id": "or_l5DYqeDn",
      "number": 1204,
      "created": "2020-04-08T15:03:55Z",
      "status": "new",
      "customer_id": "cu_gpbOljAn"
      "company_name": "Sample Customer",
      "phone": "07911 123456", 
      "email_addresses": {
        "orders": "sample@orderspace.com",
        "dispatches": "sample@orderspace.com",
        "invoices": "sample@orderspace.com",
      }
      "delivery_date": "2020-04-09",
      "reference": "",
      "internal_note": "",
      "customer_po_number": "",
      "customer_note": "",
      "standing_order_id": null,
      "shipping_type": "Special Delivery",
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
      "billing_address": {
        "company_name": "Sample Customer",
        "contact_name": "",
        "line1": "336 Hargrave Rd",
        "line2": "Windsor",
        "city": "New York",
        "state": "NY",
        "postal_code": "13865",
        "country": "US"
      },
      "order_lines": [
        {
          "id": "ol_NdOLvlpw",
          "sku": "AM-D-CHR-10",
          "name": "Amelia Dress",
          "options": "Colour: Charcoal, Size: 10",
          "grouping_category": {
            "id": "ca_9n1klwr5",
            "name": "Dresses"
          },
          "shipping": false,
          "quantity": 10,
          "unit_price": 30.0,
          "sub_total": 300.0,
          "tax_name": "Standard",
          "tax_rate": 20.0,
          "tax_amount": 60.0,
					"on_hold": false,
					"invoiced": 0,
					"paid": 0,
					"dispatched": 0
        }
      ],
      "currency": "GBP",	
      "net_total": 306.1,
      "gross_total": 366.1
    },
    {...},
    {...}
  ],
  "has_more": true	
}
```

Retrieve a list of orders. Orders are returned in the order they are created with the most recently created listed first

### HTTP Request

`GET https://api.orderspace.com/v1/orders`

### Parameters

<ul class="attributes">
	<li>
		<h3><span class="name">starting_after</span> <span class="optional">optional</span></h3>
		<div class="description">A cursor used for pagination. Setting `starting_after` to the ID of the last order in the list will retrieve the next page of orders</div>
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
		<h3><span class="name">delivery_date_since</span> <span class="optional">optional</span></h3>
		<div class="description">Return records with a delivery date after the specified date in ISO 8601 format, e.g. <code>2019-10-29</code> </div>
	</li>
	<li>
		<h3><span class="name">delivery_date_before</span> <span class="optional">optional</span></h3>
		<div class="description">Return records with a delivery date before the specified date in ISO 8601 format, e.g. <code>2019-10-27</code> </div>
	</li>
	<li>
		<h3><span class="name">number</span> <span class="optional">optional</span></h3>
		<div class="description">Return records with the specified order number</div>
	</li>
	<li>
		<h3><span class="name">status</span> <span class="optional">optional</span></h3>
		<div class="description">Return records with the specified status, one of <code>new</code>, <code>invoiced</code>, <code>released</code>, <code>part_fulfilled</code>, <code>preorder</code>, <code>fulfilled</code>, <code>standing_order</code> or <code>cancelled</code></div>
	</li>
	<li>
		<h3><span class="name">reference</span> <span class="optional">optional</span></h3>
		<div class="description">Return records with the specified reference</div>
	</li>
	<li>
		<h3><span class="name">customer_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return records for the specified customer</div>
	</li>
	<li>
		<h3><span class="name">standing_order_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return repeat orders generated by the specified standing order. This option is only applicable if the standing orders feature is enabled</div>
	</li>	
</ul>

### Response

`HTTP 200 Success` - A list of orders in JSON format

## Retrieve an order

```shell
curl -X GET https://api.orderspace.com/v1/orders/or_l5DYqeDn \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "order": {		
    "id": "or_l5DYqeDn",
    "number": 1204,
    "created": "2020-04-08T15:03:55Z",
    "status": "new",
    "customer_id": "cu_gpbOljAn"
    "company_name": "Sample Customer",
    "phone": "07911 123456", 
    "email_addresses": {
      "orders": "sample@orderspace.com",
      "dispatches": "sample@orderspace.com",
      "invoices": "sample@orderspace.com",
    }
    "delivery_date": "2020-04-09",
    "reference": "",
    "internal_note": "",
    "customer_po_number": "",
    "customer_note": "",
    "shipping_type": "Special Delivery",
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
    "billing_address": {
      "company_name": "Sample Customer",
      "contact_name": "",
      "line1": "336 Hargrave Rd",
      "line2": "Windsor",
      "city": "New York",
      "state": "NY",
      "postal_code": "13865",
      "country": "US"
    },
    "order_lines": [
      {
        "id": "ol_NdOLvlpw",
        "sku": "AM-D-CHR-10",
        "name": "Amelia Dress",
        "options": "Colour: Charcoal, Size: 10",
        "grouping_category": {
          "id": "ca_9n1klwr5",
          "name": "Dresses"
        },
        "shipping": false,
        "quantity": 10,
        "unit_price": 30.0,
        "sub_total": 300.0,
        "tax_name": "Standard",
        "tax_rate": 20.0,
        "tax_amount": 60.0,
				"on_hold": false,
				"invoiced": 0,
				"paid": 0,
				"dispatched": 0				
      }
    ],
    "currency": "GBP",	
    "net_total": 306.1,
    "gross_total": 366.1
  }
}
```

Retrieve a single order by ID

### HTTP Request

`GET https://api.orderspace.com/v1/orders/:order_id`

### Response

`HTTP 200 Success` - The order record in JSON format

`HTTP 404 Not Found` - A message describing the error

