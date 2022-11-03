# Webhook Events

This section documents the events sent to webhook endpoints. Use the <a href="#webhooks">Webhooks</a> resource to create and manage event subscriptions.


## Expected Response

Events are sent as an `HTTP POST` request to your endpoint when they occur in Orderspace. 

An `HTTP 200 Success` response should be returned. If any other response is received, Orderspace will retry the request with an incremental backoff. After multiple failed attempts your webhook will be disabled.

## Validation

> Calculating the request signature in Ruby

```ruby
Base64.strict_encode64(OpenSSL::HMAC.digest('sha256', signing_key, request_payload))
```

> Calculating the request signature in NodeJS

```javascript
var crypto = require('crypto');
crypto.createHmac('sha256', signing_key).update(request_payload).digest("base64");
```

Every request sent to your endpoint is signed with an `X-Orderspace-Signature` HTTP header. To calculate the signature, the request payload is hashed using HMACSHA256 with the webhook `signing_key`, and then base64 encoded.

To validate that the request came from Orderspace, calculate the signature using the request payload and the stored `signing_key` and compare it to the one in the request header.


## Request Format

The payload of a request is a list of events in `JSON` format. A request will often contain a single event, but to reduce network traffic multiple events may be sent together. This is more likely on a bulk action such as a stock update. A single request can contain up to 50 events. Each event in the list is self-contained and events of different event types could be mixed together in the same request. Examples of each event type are shown below. 


## customer.created

> Example customer.created webhook request

```json-doc
[
  {
    "event": "customer.created",
    "data": {
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
  },
  {...},
  {...}
]
```

Triggered when a customer is created.

`data` contains the customer record.

## customer.deleted

> Example customer.deleted webhook request

```json-doc
[
  {
    "event": "customer.deleted",
    "data": {
      "customer": {
        "id": "cu_dnwz8gnx",
        "company_name": "Blue Sky",
        "deleted": true
      }
    }
  },
  {...},
  {...}
]
```

Triggered when a customer is deleted.

`data` contains fields to identify the customer.

## customer.updated

> Example customer.updated webhook request

```json-doc
[
  {
    "event": "customer.updated",
    "data": {
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
  },
  {...},
  {...}
]
```

Triggered when a customer is updated.

`data` contains the customer record with the updates applied.

## dispatch.created

> Example dispatch.created webhook request

```json-doc
[
  {
    "event": "dispatch.created",
    "data": {
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
          "company_name": "Blue Sky",
          "contact_name": "Emilia Jane Dogherty",
          "line1": "12 Blue Sky Lane",
          "line2": "",
          "city": "Bristol",
          "state": "",
          "postal_code": "BS1 2DF",
          "country": "GB"
        },
        "email_address": "sample@orderspace.com",
        "phone": "12345",
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
  },
  {...},
  {...}
]
```

Triggered when items on an order are dispatched.

`data` contains the dispatch record.

## inventory_level.updated

> Example inventory_level.updated webhook request

```json-doc
[
  {
    "event": "inventory_level.updated",
    "data": {
      "inventory_level": {
        "sku": "AD01-10",
        "on_hand": 20.0,
        "on_hand_adjustment": 10.0,
        "available": 20.0,
        "available_adjustment": 10.0
      }
    }
  },
  {...},
  {...}
]
```

Triggered when an inventory level is updated. 

If multiple inventory levels are changed in a bulk update there will be a separate event for each item, but multiple events may be sent in the same request.

`data` contains the inventory level update record.

## invoice.created

> Example invoice.created webhook request

```json-doc
[
  {
    "event": "invoice.created",
    "data": {
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
      }
    }
  },
  {...},
  {...}
]
```
Triggered when an invoice is created.

`data` contains the invoice record.

## invoice.deleted

> Example invoice.deleted webhook request

```json-doc
[
  {
    "event": "invoice.deleted",
    "data": {
      "invoice": {
        "id": "iv_7xg471xv",
        "number": "INV-1288",
        "deleted": true
      }
    }
  },
  {...},
  {...}
]
```

Triggered when an invoice is deleted.

`data` contains fields use to identify the invoice.

## payment.created

> Example payment.created webhook request

```json-doc
[
  {
    "event": "payment.created",
    "data": {
      "payment": {
        "invoice_id": "iv_7xg471xv",
        "invoice_number": "INV-1288",
        "amount": 26.7,
        "payment_date": "2021-04-24",
        "source": "card",
        "description": "Visa ending 3220",
        "reference": "pi_1IjW8KJzxI5C4d4qXkHyOFKZ"
      }
    }
  },
  {...},
  {...}
]
```

Triggered when a payment is made or recorded on an invoice.

`data` contains the payment record.

## product.created

> Example product.created webhook request

```json-doc
[
  {
    "event": "product.created",
    "data": {
      "product":{
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
      }
    }
  },
  {...},
  {...}
]
```

Triggered when a product is created.

`data` contains the product record.

## product.deleted

> Example product.deleted webhook request

```json-doc
[
  {
    "event": "product.deleted",
    "data": {
      "product": {
        "id": "pr_lj3pwm1n",
        "code": "AD01",
        "name": "Alexa Dress",
        "deleted": true
      }
    }
  },
  {...},
  {...}
]
```

Triggered when a product is deleted.

`data` contains fields used to identify the product.

## product.updated

> Example product.updated webhook request

```json-doc
[
  {
    "event": "product.updated",
    "data": {
      "product": {
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
      }
    }
  },
  {...},
  {...}
]
```

Triggered when a product is updated.

`data` contains the product record with the updates applied.

## order.created

> Example order.created webhook request

```json-doc
[
  {
    "event": "order.created",
    "data": {
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
  },
  {...},
  {...}
]
```

Triggered when an order is created.

`data` contains the order record.

## order.deleted

> Example order.deleted webhook request

```json-doc
[
  {
    "event": "order.deleted",
    "data": {
      "order": {
        "id": "or_l5DYqeDn",
        "number": 1204,
        "deleted": true
      }
    }
  },
  {...},
  {...}
]
```

Triggered when an order is deleted.

`data` contains fields used to identify the order.

## order.updated

> Example order.updated webhook request

```json-doc
[
  {
    "event": "order.updated",
    "data": {
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
  },
  {...},
  {...}
]
```

Triggered when an order is updated.

`data` contains the order record with the updates applied.
