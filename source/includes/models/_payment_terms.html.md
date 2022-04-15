# Payment Terms

Payment Terms represent the terms of payment offered on invoices. Each customer has one set of payment terms assigned to them which are used as the default payment terms for new invoices but specific terms can also be assigned to an invoice when it is created

## The Payment Terms object

> Example payment terms

```json-doc
{
  "payment_terms": {
    "id": "pr_z0j7yjl2",
    "name": "30 Days",
    "days_due": 30,
    "deposit_pecentage": 0.0,
    "deposit_days_due": 0
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the payment terms</div>
	</li>
	<li>
		<h3><span class="name">name</span> <span class="type">string</span></h3>
		<div class="description">A unique name for the payment terms<div>
	</li>
	<li>
		<h3><span class="name">days_due</span> <span class="type number">number</span></h3>
		<div class="description">The number of days after the invoice date that payment is due. Set to zero for immediate payment</div>
	</li>
	<li>
		<h3><span class="name">deposit_percentage</span> <span class="type number">number</span></h3>
		<div class="description">The percentage of the invoice total that is required to be paid as a deposit. Set to zero for no deposit</div>
	</li>
	<li>
		<h3><span class="name">deposit_days_due</span> <span class="type number">number</span></h3>
		<div class="description">The number of days after the invoice date that the deposit s due. Set to zero for immediate payment</div>
	</li>
</ul>

## List payment terms

> Example request with curl

```shell
curl "https://api.orderspace.com/v1/payment_terms" \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "payment_terms": [
    {
      "id": "pr_z0j7yjl2",
      "name": "30 Days",
      "days_due": 30,
      "deposit_pecentage": 0.0,
      "deposit_days_due": 0
    },
    {...},
    {...}
  ]
}
```

Retrieve a list of payment terms. This endpoint does not support pagination

### HTTP Request

`GET https://api.orderspace.com/v1/payment_terms`


### Response

`HTTP 200 Success` - A list of payment terms in JSON format
