# Invoices

## The Invoice object

> Example invoice

```json-doc
{
  "invoice": {
    "id": "iv_7xg471xv",
    "number": "INV-1288",
    "invoice_date": "2021-04-24",
    "customer_id": "cu_pg34zo1x",
    "company_name": "BP Twelve",
    "email_address": "bp12@alliumstudios.com",
    "orders": [
      {
        "id": "or_e875r5l5",
        "number": 1288
      }
    ],
    "payment_terms": "15 Days",
    "due_date": "2021-05-09",
    "paid": true,
    "proforma": false,
    "deposit": {
      "percentage": 25.0,
      "due_date": "2021-04-24"
    },
    "comments": "",
    "address": {
      "company_name": "BP Twelve",
      "contact_name": "",
      "line1": "addr1",
      "line2": "",
      "city": "",
      "state": "",
      "postal_code": "NN14",
      "country": "GB"
    },
    "invoice_lines": [
      {
        "sku": "ZAG-D-16",
        "name": "Angelica Dress",
        "options": "Size: 16",
        "quantity": 1,
        "unit_price": 22.25,
        "sub_total": 22.25,
        "tax_rate": 20.0,
        "tax_amount": 4.45,
		"order_line_id": "ol_d16560mn"
      }
    ],
    "currency": "GBP",
    "net_total": 22.25,
    "gross_total": 26.7,
    "payments": [
      {
        "amount": 26.7,
        "payment_date": "2021-04-24",
        "source": "card",
        "description": "Visa ending 3220",
        "reference": "pi_1IjW8KJzxI5C4d4qXkHyOFKZ"
      }
    ]
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the invoice</div>
	</li>
	<li>
		<h3><span class="name">number</span> <span class="type">string</span></h3>
		<div class="description">Unique number identifying the invoice, shown to the customer. Can contain a prefix made of both letters and numbers</div>
	</li>
	<li>
		<h3><span class="name">invoice_date</span> <span class="type">string</span></h3>
		<div class="description">The date the invoice was issued in ISO 8601 format</div>
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
		<h3><span class="name">email_address</span> <span class="type">string</span></h3>
		<div class="description">The customer's email address for invoices. Multiple email addresses may be present, separated by commas</div>
	</li>
	<li>
		<h3><span class="name">orders</span> <span class="type li">list</span></h3>
		<div class="description">
			A list of orders associated with this invoice. Invoices are generated from orders and the items on an invoice correspond directly to items on the associated orders
			<div class="child-attributes">
				<h4>Child Attributes of orders</h4>
				<ul>
					<li>
						<h3><span class="parent-name">order.</span><span class="name">id</span> <span class="type">string</span></h3>
						<div class="description">Unique auto-generated identifier for the order</div>
					</li>				
					<li>
						<h3><span class="parent-name">order.</span><span class="name">number</span> <span class="type number">number</span></h3>
						<div class="description">Unique number identifying the order, shown to the customer</div>
					</li>
				</ul>
			</div>
		</div>
	</li>
	<li>
		<h3><span class="name">payment_terms</span> <span class="type">string</span></h3>
		<div class="description">A string representation of the payment terms offered on this invoice</div>
	</li>
	<li>
		<h3><span class="name">due_date</span> <span class="type">string</span></h3>
		<div class="description">The date payment is due in ISO 8601 format</div>
	</li>
	<li>
		<h3><span class="name">paid</span> <span class="type">boolean</span></h3>
		<div class="description">Set to <code>true</code> if the invoice has been paid in full</div>
	</li>
	<li>
		<h3><span class="name">proforma</span> <span class="type">boolean</span></h3>
		<div class="description">Set to <code>true</code> if this is a proforma invoice</div>
	</li>
	<li>
		<h3><span class="name">comments</span> <span class="type">string</span></h3>
		<div class="description">Comments to be shown on the invoice</div>
	</li>
	<li>
		<h3><span class="name">address</span> <span class="type ha">hash</span></h3>
		<div class="description">The customer's billing address
			<div class="child-attributes">
				<h4>Child Attributes</h4>
				<ul>
					<li>
						<h3><span class="parent-name">address.</span><span class="name">company_name</span> <span class="type">string</span></h3>
						<div class="description">Company name</div>
					</li>				
					<li>
						<h3><span class="parent-name">address.</span><span class="name">contact_name</span> <span class="type">string</span></h3>
						<div class="description">Contact name</div>
					</li>				
					<li>
						<h3><span class="parent-name">address.</span><span class="name">line1</span> <span class="type">string</span></h3>
						<div class="description">Address line 1</div>
					</li>				
					<li>
						<h3><span class="parent-name">address.</span><span class="name">line2</span> <span class="type">string</span></h3>
						<div class="description">Address line 2</div>
					</li>				
					<li>
						<h3><span class="parent-name">address.</span><span class="name">city</span> <span class="type">string</span></h3>
						<div class="description">City, town or village</div>
					</li>				
					<li>
						<h3><span class="parent-name">address.</span><span class="name">state</span> <span class="type">string</span></h3>
						<div class="description">State, county, province or region. U.S., Canadian and Australian addresses should use the abbreviated form of the state</div>
					</li>				
					<li>
						<h3><span class="parent-name">address.</span><span class="name">postal_code</span> <span class="type">string</span></h3>
						<div class="description">ZIP or postal code</div>
					</li>				
					<li>
						<h3><span class="parent-name">address.</span><span class="name">country</span> <span class="type">string</span></h3>
						<div class="description">Two-letter ISO 3166-1 country code</div>
					</li>				
				</ul>
			</div>
		</div>
	</li>
	<li>
		<h3><span class="name">invoice_lines</span> <span class="type li">list</span></h3>
		<div class="description">
			List of the individual lines that make up the invoice as <code>invoice lines</code>
			<div class="child-attributes">
				<h4>Child Attributes of Invoice Lines</h4>
				<ul>
					<li>
						<h3><span class="parent-name">invoice_line.</span><span class="name">sku</span> <span class="type">string</span></h3>
						<div class="description">The unique code for the item</div>
					</li>				
					<li>
						<h3><span class="parent-name">invoice_line.</span><span class="name">name</span> <span class="type">string</span></h3>
						<div class="description">The name of the item</div>
					</li>				
					<li>
						<h3><span class="parent-name">invoice_line.</span><span class="name">options</span> <span class="type">string</span></h3>
						<div class="description">The options (size/color etc) of the item</div>
					</li>				
					<li>
						<h3><span class="parent-name">invoice_line.</span><span class="name">quantity</span> <span class="type number">number</span></h3>
						<div class="description">The number of items ordered</div>
					</li>				
					<li>
						<h3><span class="parent-name">invoice_line.</span><span class="name">unit_price</span> <span class="type number">number</span></h3>
						<div class="description">The unit price of each item on this line</div>
					</li>				
					<li>
						<h3><span class="parent-name">invoice_line.</span><span class="name">sub_total</span> <span class="type number">number</span></h3>
						<div class="description">The line sub-total excluding tax</div>
					</li>				
					<li>
						<h3><span class="parent-name">invoice_line.</span><span class="name">tax_rate</span> <span class="type number">number</span></h3>
						<div class="description">The tax rate applied to this line as a percentage</div>
					</li>				
					<li>
						<h3><span class="parent-name">invoice_line.</span><span class="name">tax_amount</span> <span class="type number">number</span></h3>
						<div class="description">The total tax applied to this line</div>
					</li>				
					<li>
						<h3><span class="parent-name">invoice_line.</span><span class="name">order_line_id</span> <span class="type number">string</span></h3>
						<div class="description">The ID of the order line associated with this line</div>
					</li>
				</ul>
			</div>
		</div>
	</li>	
	<li>
		<h3><span class="name">currency</span> <span class="type">string</span></h3>
		<div class="description">The three-letter ISO currency code representing the invoice's currency</div>
	</li>
	<li>
		<h3><span class="name">net_total</span> <span class="type number">number</span></h3>
		<div class="description">The total cost of all items on the invoice excluding tax</div>
	</li>
	<li>
		<h3><span class="name">gross_total</span> <span class="type number">number</span></h3>
		<div class="description">The total cost of all items on the invoice including tax</div>
	</li>
	<li>
		<h3><span class="name">payments</span> <span class="type li">list</span></h3>
		<div class="description">
			A list of payments made against this invoice
			<div class="child-attributes">
				<h4>Child Attributes of Payments</h4>
				<ul>
					<li>
						<h3><span class="parent-name">payment.</span><span class="name">amount</span> <span class="type number">number</span></h3>
						<div class="description">The amount paid in the invoice's currency</div>
					</li>				
					<li>
						<h3><span class="parent-name">payment.</span><span class="name">payment_date</span> <span class="type">string</span></h3>
						<div class="description">The date the payment was made in ISO 8601 format</div>
					</li>				
					<li>
						<h3><span class="parent-name">payment.</span><span class="name">source</span> <span class="type">string</span></h3>
						<div class="description">The name of the payment source</div>
					</li>				
					<li>
						<h3><span class="parent-name">payment.</span><span class="name">description</span> <span class="type">string</span></h3>
						<div class="description">A description of the payment</div>
					</li>				
					<li>
						<h3><span class="parent-name">payment.</span><span class="name">reference</span> <span class="type">string</span></h3>
						<div class="description">A reference for the payment provided by the payment gateway</div>
					</li>				
				</ul>
			</div>
		</div>
	</li>
	
</ul>

## List invoices

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/invoices \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -d limit=20 \
  -d starting_after=iv_dmqjl0x8
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "invoices": [
    {
      "id": "iv_7xg471xv",
      "number": "INV-1288",
      "invoice_date": "2021-04-24",
      "customer_id": "cu_pg34zo1x",
      "company_name": "BP Twelve",
      "email_address": "bp12@alliumstudios.com",
      "orders": [
        {
          "id": "or_e875r5l5",
          "number": 1288
        }
      ],
      "payment_terms": "15 Days",
      "due_date": "2021-05-09",
      "paid": true,
      "proforma": false,
      "deposit": {
        "percentage": 25.0,
        "due_date": "2021-04-24"
      },
      "comments": "",
      "address": {
        "company_name": "BP Twelve",
        "contact_name": "",
        "line1": "addr1",
        "line2": "",
        "city": "",
        "state": "",
        "postal_code": "NN14",
        "country": "GB"
      },
      "invoice_lines": [
        {
          "sku": "ZAG-D-16",
          "name": "Angelica Dress",
          "options": "Size: 16",
          "quantity": 1,
          "unit_price": 22.25,
          "sub_total": 22.25,
          "tax_rate": 20.0,
          "tax_amount": 4.45,
          "order_line_id": "ol_d16560mn"
        }
      ],
      "currency": "GBP",
      "net_total": 22.25,
      "gross_total": 26.7,
      "payments": [
        {
          "amount": 26.7,
          "payment_date": "2021-04-24",
          "source": "card",
          "description": "Visa ending 3220",
          "reference": "pi_1IjW8KJzxI5C4d4qXkHyOFKZ"
        }
      ]
    },
    {...},
    {...}
  ]
}
```

Retrieve a list of invoices. Invoices are returned in the order they are created with the most recently created listed first

### HTTP Request

`GET https://api.orderspace.com/v1/invoices`

### Parameters

<ul class="attributes">
	<li>
		<h3><span class="name">starting_after</span> <span class="optional">optional</span></h3>
		<div class="description">A cursor used for pagination. Setting `starting_after` to the ID of the last invoice in the list will retrieve the next page of invoices</div>
	</li>
	<li>
		<h3><span class="name">limit</span> <span class="optional">optional</span></h3>
		<div class="description">A limit on the number of records returned. The default is 50 and the maximum limit is 200</div>
	</li>
	<li>
		<h3><span class="name">created_since</span> <span class="optional">optional</span></h3>
		<div class="description">Return records created since the given date and time in ISO 8601 format, e.g. <code>2021-10-29T21:00</code> </div>
	</li>
	<li>
		<h3><span class="name">invoice_date_after</span> <span class="optional">optional</span></h3>
		<div class="description">Return invoices with an invoice date after the given date in ISO 8601 format, e.g. <code>2019-10-29</code> </div>
	</li>
	<li>
		<h3><span class="name">invoice_date_before</span> <span class="optional">optional</span></h3>
		<div class="description">Return invoices with an invoice date before the given date in ISO 8601 format, e.g. <code>2021-10-29</code> </div>
	</li>
	<li>
		<h3><span class="name">due_date_after</span> <span class="optional">optional</span></h3>
		<div class="description">Return invoices with a due date after the given date in ISO 8601 format, e.g. <code>2019-10-29</code> </div>
	</li>
	<li>
		<h3><span class="name">due_date_before</span> <span class="optional">optional</span></h3>
		<div class="description">Return invoices with a due date before the given date in ISO 8601 format, e.g. <code>2021-10-29</code> </div>
	</li>
	<li>
		<h3><span class="name">number</span> <span class="optional">optional</span></h3>
		<div class="description">Return an invoice with the corresponding number</div>
	</li>
	<li>
		<h3><span class="name">customer_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return invoices for a specific customer</div>
	</li>
	<li>
		<h3><span class="name">paid</span> <span class="optional">optional</span></h3>
		<div class="description">Return invoices with a matching paid value. Set to either true or false</div>
	</li>
	<li>
		<h3><span class="name">proforma</span> <span class="optional">optional</span></h3>
		<div class="description">Return invoices with a matching proforma value. Set to either true or false</div>
	</li>
	
</ul>

### Response

`HTTP 200 Success` - A list of invoices in JSON format

## Retrieve an invoice

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/invoices/iv_7xg471xv \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "invoice": {
    "id": "iv_7xg471xv",
    "number": "INV-1288",
    "invoice_date": "2021-04-24",
    "customer_id": "cu_pg34zo1x",
    "company_name": "BP Twelve",
    "email_address": "bp12@alliumstudios.com",
    "orders": [
      {
        "id": "or_e875r5l5",
        "number": 1288
      }
    ],
    "payment_terms": "15 Days",
    "due_date": "2021-05-09",
    "paid": true,
    "proforma": false,
    "deposit": {
      "percentage": 25.0,
      "due_date": "2021-04-24"
    },
    "comments": "",
    "address": {
      "company_name": "BP Twelve",
      "contact_name": "",
      "line1": "addr1",
      "line2": "",
      "city": "",
      "state": "",
      "postal_code": "NN14",
      "country": "GB"
    },
    "invoice_lines": [
      {
        "sku": "ZAG-D-16",
        "name": "Angelica Dress",
        "options": "Size: 16",
        "quantity": 1,
        "unit_price": 22.25,
        "sub_total": 22.25,
        "tax_rate": 20.0,
        "tax_amount": 4.45,
		"order_line_id": "ol_d16560mn"
      }
    ],
    "currency": "GBP",
    "net_total": 22.25,
    "gross_total": 26.7,
    "payments": [
      {
        "amount": 26.7,
        "payment_date": "2021-04-24",
        "source": "card",
        "description": "Visa ending 3220",
        "reference": "pi_1IjW8KJzxI5C4d4qXkHyOFKZ"
      }
    ]
  }
}
```

Retrieve a single invoice by ID

### HTTP Request

`GET https://api.orderspace.com/v1/invoices/:invoice_id`

### Response

`HTTP 200 Success` - The invoice record in JSON format

`HTTP 404 Not Found` - A message describing the error

