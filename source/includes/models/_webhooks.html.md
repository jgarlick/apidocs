# Webhooks

Orderspace will send a HTTP POST payload to the webhook’s configured URL when a subscribed event occurs

## The Webhook object

> Example webhook

```json-doc
{
  "webhook": {
    "id":"wh_1q4qn43v",
    "endpoint":"https://webhook.site/#!/6e3931ec-9f4b-4b3a-932f-42f73d1dc45f",
    "signing_key":"UNxdW7ugYl8PCKjVGkoXkHARkCoFT3eXpdpDsF1s",
    "events":["order.created", "dispatch.created"]
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the webhook</div>
	</li>
	<li>
		<h3><span class="name">endpoint</span> <span class="type">string</span></h3>
		<div class="description">The HTTPS URL where Orderspace will send a HTTP POST payload when a subscribed event occurs<div>
	</li>
	<li>
		<h3><span class="name">signing_key</span> <span class="type">string</span></h3>
		<div class="description">A key used to generate a hashed signature of the HTTP POST payload of each webhook request. This hashed signature is included in the request as header X-Orderspace-Signature. The signature and the signing key allow the receiving system to validate that the request originated from Orderspace</div>
	</li>
	<li>
		<h3><span class="name">events</span> <span class="type li">list</span></h3>
		<div class="description">
			The subscribed <a href="#events">events</a> that will trigger the webhook
		</div>
	</li>
</ul>

## Create a webhook

> Example request with curl

```shell
curl -X POST https://api.orderspace.com/v1/webhooks \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
  "webhook": {
    "endpoint":"https://webhook.site/#!/6e3931ec-9f4b-4b3a-932f-42f73d1dc45f",
    "events": ["order.created", "dispatch.created"]
  }
}'
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "webhook": {
    "id": "wh_nq479yz6",
    "endpoint": "https://webhook.site/#!/6e3931ec-9f4b-4b3a-932f-42f73d1dc45f",
    "signing_key": "7R2gNdE4GU8K06WXPV9lOXBic9mSs5LjKMsk46eW",
    "events": ["order.created","dispatch.created"]
  }
}
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
  "message": "Validation failed: Endpoint can't be blank, Endpoint must be a https url"
}
```

Create a new webhook

### HTTP Request

`POST https://api.orderspace.com/v1/webhooks`

### Response

`HTTP 200 Success` - The webhook object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors

## List webhooks

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/webhooks \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "webhooks": [
    {
      "id": "wh_o9ernm4p",
      "endpoint":"https://webhook.site/#!/6e3931ec-9f4b-4b3a-932f-42f73d1dc45f",
      "signing_key":"UNxdW7ugYl8PCKjVGkoXkHARkCoFT3eXpdpDsF1s",
      "events": ["order.created", "dispatch.created"]
    },
    {...},
    {...}
  ]
}
```

Retrieve a list of webhooks. Webhooks are returned in the order they are created with the most recently created listed first

### HTTP Request

`GET https://api.orderspace.com/v1/webhooks`

### Response

`HTTP 200 Success` - A list of webhooks in JSON format

## Events

### customer.created
> Example customer.created webhook request

```json-doc
{
  "event": "customer.created",
  "data": {
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
    ]
  }
}
```

Triggered when a customer is created. Could contain up to 50 customers

### customer.deleted
> Example customer.deleted webhook request

```json-doc
{
  "event": "customer.deleted",
  "data": {
    "customers": [
      {
        "id": "cu_dnwz8gnx",
        "company_name": "Blue Sky",
        "deleted": true
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when a customer is deleted. Could contain up to 50 customers

### customer.updated
> Example customer.updated webhook request

```json-doc
{
  "event": "customer.updated",
  "data": {
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
    ]
  }
}
```

Triggered when a customer is updated. Could contain up to 50 customers

### dispatch.created
> Example dispatch.created webhook request

```json-doc
{
  "event": "dispatch.created",
  "data": {
    "dispatches": [
      {
        "id": "di_4kzzxdk2",
        "order_id": "or_wlvzog4g",
        "order_number": 1289,
        "created": "2021-04-16T12:58:39Z",
        "comments": "Sent by Royal Mail using Next Day Delivery",
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
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when a dispatch is created. Could contain up to 50 dispatches

### inventory_level.updated
> Example inventory_level.updated webhook request

```json-doc
{
  "event": "inventory_level.updated",
  "data": {
    "inventory_levels": [
      {
        "sku": "AD01-10",
        "on_hand": 20.0,
        "on_hand_adjustment": 10.0,
        "available": 20.0,
        "available_adjustment": 10.0
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when a inventory_level is updated. Could contain up to 50 inventory level updates


### invoice.created
> Example invoice.created webhook request

```json-doc
{
  "event": "invoice.created",
  "data": {
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
            "tax_amount": 4.45
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
}
```
Triggered when an invoice is created. Could contain up to 50 invoices

### invoice.deleted
> Example invoice.deleted webhook request

```json-doc
{
  "event": "invoice.deleted",
  "data": {
    "invoices": [
      {
        "id": "iv_7xg471xv",
        "number": "INV-1288",
        "deleted": true
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when an invoice is deleted. Could contain up to 50 invoices

### payment.created
> Example payment.created webhook request

```json-doc
{
  "event": "payment.created",
  "data": {
    "payments": [
      {
        "invoice_id": "iv_7xg471xv",
        "invoice_number": "INV-1288",
        "amount": 26.7,
        "payment_date": "2021-04-24",
        "source": "card",
        "description": "Visa ending 3220",
        "reference": "pi_1IjW8KJzxI5C4d4qXkHyOFKZ"
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when a payment is created on an invoice. Cound contain up to 50 payments

### product.created
> Example product.created webhook request

```json-doc
{
  "event": "product.created",
  "data": {
    "products": [
      {
        "id": "pr_lj3pwm1n",
        "code": "AD01",
        "name": "Alexa Dress",
        "description": "Summer colours, fully lined",
        "active": true,
        "tariff_code": "0804.401",
        "country_of_origin": "India",
        "composition": "100% cotton",
        "variant_options": ["Color", "Size"],
        "product_variants": [
          {
            "id": "pv_v18kxq1e",
            "sku": "AD01-10",
            "barcode": "123456789",
            "options": {"Color": "Red", "Size": "10"},
            "unit_price": 32.0,
            "price_list_prices": [
              {"id": "pr_z0j7yjl2", "unit_price": 35.0}
            ],
            "rrp": 72.0,
            "backorder": true,
            "minimum": 4,
            "multiple": 3,
            "weight": 0.0,
          },
          {
            "id": "pv_xjz5xvjk",
            "sku": "AD01-12",
            "barcode": "1123456789",
            "options": {"Color": "Red", "Size": "12"},
            "unit_price": 32.0,
            "price_list_prices": [],
            "rrp": 72.0,
            "backorder": true,
            "minimum": 2,
            "multiple": 2,
            "weight": 0.0,
          },
          {
            "id": "pv_q1l2n634",
            "sku": "AD01-14",
            "barcode": "2123456789",
            "options": {"Color": "Red", "Size": "14"},
            "unit_price": 32.0,
            "price_list_prices": [],
            "rrp": 72.0,
            "backorder": true,
            "minimum": 4,
            "multiple": null,
            "weight": 1.0,
          }
        ],
        "categories": [
          {
            "id": "ca_x61lk8j7",
            "name": "Dresses"
          },
          {
            "id": "ca_3xwy7mwo",
            "name": "Spring / Summer 2022"
          }
        ],
        "grouping_category_id": "ca_x61lk8j7"
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when a product is created. Could contain up to 50 products

### product.deleted
> Example product.deleted webhook request

```json-doc
{
  "event": "product.deleted",
  "data": {
    "products": [
      {
        "id": "pr_lj3pwm1n",
        "code": "AD01",
        "name": "Alexa Dress",
        "deleted": true
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when a product is deleted. Could contain up to 50 products

### product.updated
> Example product.updated webhook request

```json-doc
{
  "event": "product.updated",
  "data": {
    "products": [
      {
        "id": "pr_lj3pwm1n",
        "code": "AD01",
        "name": "Alexa Dress",
        "description": "Summer colours, fully lined",
        "active": true,
        "tariff_code": "0804.401",
        "country_of_origin": "India",
        "composition": "100% cotton",
        "variant_options": ["Color", "Size"],
        "product_variants": [
          {
            "id": "pv_v18kxq1e",
            "sku": "AD01-10",
            "barcode": "123456789",
            "options": {"Color": "Red", "Size": "10"},
            "unit_price": 32.0,
            "price_list_prices": [
              {"id": "pr_z0j7yjl2", "unit_price": 35.0}
            ],
            "rrp": 72.0,
            "backorder": true,
            "minimum": 4,
            "multiple": 3,
            "weight": 0.0,
          },
          {
            "id": "pv_xjz5xvjk",
            "sku": "AD01-12",
            "barcode": "1123456789",
            "options": {"Color": "Red", "Size": "12"},
            "unit_price": 32.0,
            "price_list_prices": [],
            "rrp": 72.0,
            "backorder": true,
            "minimum": 2,
            "multiple": 2,
            "weight": 0.0,
          },
          {
            "id": "pv_q1l2n634",
            "sku": "AD01-14",
            "barcode": "2123456789",
            "options": {"Color": "Red", "Size": "14"},
            "unit_price": 32.0,
            "price_list_prices": [],
            "rrp": 72.0,
            "backorder": true,
            "minimum": 4,
            "multiple": null,
            "weight": 1.0,
          }
        ],
        "categories": [
          {
            "id": "ca_x61lk8j7",
            "name": "Dresses"
          },
          {
            "id": "ca_3xwy7mwo",
            "name": "Spring / Summer 2022"
          }
        ],
        "grouping_category_id": "ca_x61lk8j7"
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when a product is updated. Could contain up to 50 products

### order.created
> Example order.created webhook request

```json-doc
{
  "event": "order.created",
  "data": {
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
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when an order is created. Could contain up to 50 orders

### order.deleted
> Example order.deleted webhook request

```json-doc
{
  "event": "order.deleted",
  "data": {
    "orders": [
      {
        "id": "or_l5DYqeDn",
        "number": 1204,
        "deleted": true
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when an order is deleted. Could contain up to 50 orders

### order.updated
> Example order.updated webhook request

```json-doc
{
  "event": "order.updated",
  "data": {
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
      },
      {...},
      {...}
    ]
  }
}
```

Triggered when an order is updated. Could contain up to 50 orders
