# Customers

A customer represents a company placing orders through your Orderspace site

## The Customer Object

> Example customer

```json-doc
{
  "customer": {
    "id": "cu_dnwz8gnx",
    "company_name": "Blue Sky",
    "created_at": "2021-03-09T13:08:51Z",
    "status": "active",
    "reference": "",
    "buyers": [
      {
        "name": "Emilia Jane Dogherty",
        "email_address": "sample@orderspace.com"
      }
    ],
    "phone": "12345",
    "email_addresses": {
      "orders": "sample@orderspace.com",
      "dispatches": "sample@orderspace.com",
      "invoices": "sample@orderspace.com",
    },
    "tax_number": "",
    "tax_rate_id": null,
    "addresses": [
      {
        "company_name": "Blue Sky",
        "contact_name": "Emilia Jane Dogherty",
        "line1": "12 Blue Sky Lane",
        "line2": "",
        "city": "Bristol",
        "postal_code": "BS1 2DF",
        "state": "",
        "country": "GB"
      }
    ],
    "minimum_spend": 150.0,
    "payment_terms_id": "pt_zkmqv8e0",
    "customer_group_id": "cg_w2n6ln8v",
    "price_list_id": "pr_3715yj58"
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the customer</div>
	</li>
	<li>
		<h3><span class="name">company_name</span> <span class="type">string</span></h3>
		<div class="description">The customer's company name</div>
	</li>
	<li>
		<h3><span class="name">created_at</span> <span class="type">string</span></h3>
		<div class="description">The UTC date and time the customer was created in ISO 8601 format</div>
	</li>
	<li>
		<h3><span class="name">status</span> <span class="type">string</span></h3>
		<div class="description">The status of the customer, one of <code>new</code>, <code>active</code> or <code>closed</code></div>
	</li>
	<li>
		<h3><span class="name">reference</span> <span class="type">string</span></h3>
		<div class="description">Your reference for this customer. Visible to the customer but not editable by them</div>
	</li>
	<li>
		<h3><span class="name">buyers</span> <span class="type li">list</span></h3>
		<div class="description">
			The buyer associated with this customer. This represents a user that can log in and access the ordering site. Currently Orderspace has a restriction of a single buyer per customer, but this parameter is a list to support multiple buyers per customer in the future. Adding more than one buyer to the list will currently fail.
			<div class="child-attributes">
				<h4>Child Attributes of Buyers</h4>
				<ul>
					<li>
						<h3><span class="parent-name">buyer.</span><span class="name">name</span> <span class="type">string</span></h3>
						<div class="description">The full name of the user</div>
					</li>				
					<li>
						<h3><span class="parent-name">buyer.</span><span class="name">email_address</span> <span class="type">string</span></h3>
						<div class="description">The email address associated with this user. This must be unique across all customers and buyers as it is used for logging in to the ordering site</div>
					</li>
				</ul>
			</div>
		</div>
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
		<h3><span class="name">tax_number</span> <span class="type">string</span></h3>
		<div class="description">The customer's sales tax or VAT number</div>
	</li>
	<li>
		<h3><span class="name">tax_rate_id</span> <span class="type">string</span></h3>
		<div class="description">Set to null to use the default tax rates set on each product, or the ID of a Tax Rate to use a specific rate. This should be set to null unless the customer needs to be assigned a specific rate, for example if they are in another country.</div>
	</li>
	<li>
		<h3><span class="name">addresses</span> <span class="type ha">list</span></h3>
		<div class="description">
			The customer's addresses
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
		<h3><span class="name">minimum_spend</span> <span class="type number">number</span></h3>
		<div class="description">The customer's minimum spend per order in the currency of the price list assigned to them or the account default currency if no price list is assigned. Set to <code>null</code> if there is no minimum spend</div>
	</li>
	<li>
		<h3><span class="name">payment_terms_id</span> <span class="type">string</span></h3>
		<div class="description">The ID of the Payment Terms assigned to this customer. Set to <code>null</code> if no Payment Terms are assigned</div>
	</li>
	<li>
		<h3><span class="name">customer_group_id</span> <span class="type">string</span></h3>
		<div class="description">The ID of the Customer Group assigned to this customer. Set to <code>null</code> if no Customer Group is assigned</div>
	</li>
	<li>
		<h3><span class="name">price_list_id</span> <span class="type">string</span></h3>
		<div class="description">The ID of the Price List assigned to this customer. Set to <code>null</code> if no Price List is assigned</div>
	</li>
</ul>

## Create a customer

> Example request with curl

```shell
curl -X POST https://api.orderspace.com/v1/customers \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
  "customer": {
    "company_name": "Blue Sky",
    "reference": "",
    "buyers": [
      {
        "name": "Emilia Jane Dogherty",
        "email_address": "sample@orderspace.com"
      }
    ],
    "phone": "12345",
    "email_addresses": {
      "orders": "sample@orderspace.com",
      "dispatches": "sample@orderspace.com",
      "invoices": "sample@orderspace.com",
    },
    "tax_number": "",
    "addresses": [
      {
        "company_name": "Blue Sky",
        "contact_name": "Emilia Jane Dogherty",
        "line1": "12 Blue Sky Lane",
        "line2": "",
        "city": "Bristol",
        "postal_code": "BS1 2DF",
        "state": "",
        "country": "GB"
      }
    ],
    "minimum_spend": 150.0,
    "payment_terms_id": "pt_zkmqv8e0",
    "customer_group_id": "cg_w2n6ln8v",
    "price_list_id": "pr_3715yj58"
    }
  }'
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "customer": {
    "id": "cu_dnwz8gnx",
    "company_name": "Blue Sky",
    "created_at": "2021-03-09T13:08:51Z",
    "status": "active",
    "reference": "",
    "buyers": [
      {
        "name": "Emilia Jane Dogherty",
        "email_address": "sample@orderspace.com"
      }
    ],
    "phone": "12345",
    "email_addresses": {
      "orders": "sample@orderspace.com",
      "dispatches": "sample@orderspace.com",
      "invoices": "sample@orderspace.com",
    },
    "tax_number": "",
    "tax_rate_id": null,
    "addresses": [
      {
        "company_name": "Blue Sky",
        "contact_name": "Emilia Jane Dogherty",
        "line1": "12 Blue Sky Lane",
        "line2": "",
        "city": "Bristol",
        "postal_code": "BS1 2DF",
        "state": "",
        "country": "GB"
      }
    ],
    "minimum_spend": 150.0,
    "payment_terms_id": "pt_zkmqv8e0",
    "customer_group_id": "cg_w2n6ln8v",
    "price_list_id": "pr_3715yj58"
  }
}
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
  "message": "Validation failed: Email address has already been taken"
}
```

Create a new customer

### HTTP Request

`POST https://api.orderspace.com/v1/customers`

### Response

`HTTP 200 Success` - The customer object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors

## List customers

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/customers \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -d limit=20 \
  -d starting_after=cu_53zjgvnm
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "customers": [
    {
      "id": "cu_dnwz8gnx",
      "company_name": "Blue Sky",
      "created_at": "2021-03-09T13:08:51Z",
      "status": "active",
      "reference": "",
      "buyers": [
        {
          "name": "Emilia Jane Dogherty",
          "email_address": "sample@orderspace.com"
        }
      ],
      "phone": "12345",
      "email_addresses": {
        "orders": "sample@orderspace.com",
        "dispatches": "sample@orderspace.com",
        "invoices": "sample@orderspace.com",
      },
      "tax_number": "",
      "tax_rate_id": null,
      "addresses": [
        {
          "company_name": "Blue Sky",
          "contact_name": "Emilia Jane Dogherty",
          "line1": "12 Blue Sky Lane",
          "line2": "",
          "city": "Bristol",
          "postal_code": "BS1 2DF",
          "state": "",
          "country": "GB"
        }
      ],
      "minimum_spend": 150.0,
      "payment_terms_id": "pt_zkmqv8e0",
      "customer_group_id": "cg_w2n6ln8v",
      "price_list_id": "pr_3715yj58"
    },
    {...},
    {...}
  ],
  "has_more": true
}
```

Retrieve a list of customers. Customers are returned in the order they are created with the most recently created listed first

### HTTP Request

`GET https://api.orderspace.com/v1/customers`

### Parameters

<ul class="attributes">
	<li>
		<h3><span class="name">starting_after</span> <span class="optional">optional</span></h3>
		<div class="description">A cursor used for pagination. Setting `starting_after` to the ID of the last customer in the list will retrieve the next page of customers</div>
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
		<h3><span class="name">company_name</span> <span class="optional">optional</span></h3>
		<div class="description">Return customers with the specified company name</div>
	</li>
	<li>
		<h3><span class="name">buyers_email_address</span> <span class="optional">optional</span></h3>
		<div class="description">Return customers with the specified buyers email address</div>
	</li>
	<li>
		<h3><span class="name">status</span> <span class="optional">optional</span></h3>
		<div class="description">Return customers with the specified status, one of <code>new</code>, <code>active</code> or <code>closed</code></div>
	</li>
	<li>
		<h3><span class="name">reference</span> <span class="optional">optional</span></h3>
		<div class="description">Return customers with the specified reference</div>
	</li>
	<li>
		<h3><span class="name">payment_terms_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return customers with the specified payment terms</div>
	</li>
	<li>
		<h3><span class="name">customer_group_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return customers in the specified group</div>
	</li>
	<li>
		<h3><span class="name">price_list_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return customers with the specified price list</div>
	</li>
</ul>

### Response

`HTTP 200 Success` - A list of customers in JSON format


## Retrieve a customer

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/customers/cu_dnwz8gnx \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "customer": {
    "id": "cu_dnwz8gnx",
    "company_name": "Blue Sky",
    "created_at": "2021-03-09T13:08:51Z",
    "status": "active",
    "reference": "",
    "buyers": [
      {
        "name": "Emilia Jane Dogherty",
        "email_address": "sample@orderspace.com"
      }
    ],
    "phone": "12345",
    "email_addresses": {
      "orders": "sample@orderspace.com",
      "dispatches": "sample@orderspace.com",
      "invoices": "sample@orderspace.com",
    },
    "tax_number": "",
    "tax_rate_id": null,
    "addresses": [
      {
        "company_name": "Blue Sky",
        "contact_name": "Emilia Jane Dogherty",
        "line1": "12 Blue Sky Lane",
        "line2": "",
        "city": "Bristol",
        "postal_code": "BS1 2DF",
        "state": "",
        "country": "GB"
      }
    ],
    "minimum_spend": 150.0,
    "payment_terms_id": "pt_zkmqv8e0",
    "customer_group_id": "cg_w2n6ln8v",
    "price_list_id": "pr_3715yj58"
  }
}
```

Retrieve a single customer by ID

### HTTP Request

`GET https://api.orderspace.com/v1/customers/:customer_id`

### Response

`HTTP 200 Success` - The customer record in JSON format

`HTTP 404 Not Found` - A message describing the error


## Update a customer

> Example request with curl

```shell
curl -X PUT https://api.orderspace.com/v1/customers/cu_53zjgvnm \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
	"customer": {
		"company_name": "Blue Sky",
		"status": "active",
		"reference": "",
		"buyers": [
			{
		  	"name": "Emilia Jane Dogherty",
		  	"email_address": "sample@orderspace.com"
			}
		],
		"phone": "12345",
		"email_addresses": {
			"orders": "sample@orderspace.com",
			"dispatches": "sample@orderspace.com",
			"invoices": "sample@orderspace.com",
		},
		"tax_number": "",
		"addresses": [
			{
		    "company_name": "Blue Sky",
		    "contact_name": "Emilia Jane Dogherty",
		    "line1": "12 Blue Sky Lane",
		    "line2": "",
		    "city": "Bristol",
		    "postal_code": "BS1 2DF",
		    "state": "",
		    "country": "GB"
		  }
		],
		"minimum_spend": 150.0,
		"payment_terms_id": "pt_zkmqv8e0",
		"customer_group_id": "cg_w2n6ln8v",
		"price_list_id": "pr_3715yj58"
	}
}'
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "customer": {
    "id": "cu_dnwz8gnx",
    "company_name": "Blue Sky",
    "created_at": "2021-03-09T13:08:51Z",
    "status": "active",
    "reference": "",
    "buyers": [
      {
        "name": "Emilia Jane Dogherty",
        "email_address": "sample@orderspace.com"
      }
    ],
    "phone": "12345",
    "email_addresses": {
      "orders": "sample@orderspace.com",
      "dispatches": "sample@orderspace.com",
      "invoices": "sample@orderspace.com",
    },
    "tax_number": "",
    "tax_rate_id": null,
    "addresses": [
      {
        "company_name": "Blue Sky",
        "contact_name": "Emilia Jane Dogherty",
        "line1": "12 Blue Sky Lane",
        "line2": "",
        "city": "Bristol",
        "postal_code": "BS1 2DF",
        "state": "",
        "country": "GB"
      }
    ],
    "minimum_spend": 150.0,
    "payment_terms_id": "pt_zkmqv8e0",
    "customer_group_id": "cg_w2n6ln8v",
    "price_list_id": "pr_3715yj58"
  }
}
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
  "message": "Validation failed: Email address has already been taken"
}
```

Update an existing customer. Any fields not included in the update will remain the same.

### HTTP Request

`PUT https://api.orderspace.com/v1/customers/:customer_id`


### Response

`HTTP 200 Success` - The customer object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors
