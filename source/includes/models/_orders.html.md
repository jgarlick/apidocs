# Orders
## The Order object

> Example object

```json-doc
{
	"id": "or_l5DYqeDn",
	"number": 1204,
	"customer": {
		"id": "cu_gpbOljAn",
		"company_name": "Sample Customer",
		"reference": "SC1",
		"phone": "07911 123456", 
		"email_orders": "sample@orderspace.com",
		"email_dispatches": "sample@orderspace.com",
		"email_invoices": "sample@orderspace.com"
	},
	"created": "2020-04-08T15:03:55Z",
	"status": "new",
	"reference": "",
	"po_number": "",
	"deliver_on": "2020-04-09",
	"net_total": 306.1,
	"gross_total": 366.1,
	"currency": "GBP",
	"internal_note": "",
	"customer_note": "",
	"shipping_type": "Special Delivery",
	"shipping_address": {
		 "name": "",
		 "company_name": "Sample Customer",
		 "line1": "34 Edgar Buildings",
		 "line2": "George Street",
		 "city": "Bath",
		 "postal_code": "BA1 2FJ",
		 "state": "",
		 "country": "United Kingdom"
	},
	"billing_address": {
		 "name": "",
		 "company_name": "Sample Customer",
		 "line1": "336 Hargrave Rd",
		 "line2": "Windsor",
		 "city": "New York",
		 "postal_code": "13865",
		 "state": "NY",
		 "country": "United States"
	},
	"order_lines": [
		{
			"id": "ol_NdOLvlpw",
			"sku": "AM-D-CHR-10",
			"name": "Amelia Dress",
			"options": "Colour: Charcoal, Size: 10",
			"quantity": 10,
			"unit_price": 30.0,
			"sub_total": 300.0,
			"tax_name": "Standard",
			"tax_rate": 20.0,
			"tax_amount": 60.0
		}
	]
}
```

### Attributes
<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Internal identifier for the order</div>
	</li>
	<li>
		<h3><span class="name">number</span> <span class="type mi">integer</span></h3>
		<div class="description">Unique number identifying the order</div>
	</li>
	<li>
		<h3><span class="name">customer</span> <span class="type ha">hash</span></h3>
		<div class="description">
			The customer associated with this order
			<div class="child-attributes">
				<h4>Child Attributes</h4>
				<ul>
					<li>
						<h3><span class="parent-name">customer.</span><span class="name">id</span> <span class="type">string</span></h3>
						<div class="description">Internal identifier for the customer</div>
					</li>				
					<li>
						<h3><span class="parent-name">customer.</span><span class="name">company_name</span> <span class="type">string</span></h3>
						<div class="description">The customer's company name</div>
					</li>
					<li>
						<h3><span class="parent-name">customer.</span><span class="name">reference</span> <span class="type">string</span></h3>
						<div class="description">A custom reference for this customer</div>
					</li>
					<li>
						<h3><span class="parent-name">customer.</span><span class="name">phone</span> <span class="type">string</span></h3>
						<div class="description">The customer's phone number</div>
					</li>
					<li>
						<h3><span class="parent-name">customer.</span><span class="name">email_orders</span> <span class="type">string</span></h3>
						<div class="description">The customer's email address for order confirmations. Multiple email addresses may be present, separated by commas</div>
					</li>
					<li>
						<h3><span class="parent-name">customer.</span><span class="name">email_dispatches</span> <span class="type">string</span></h3>
						<div class="description">The customer's email address for dispatch confirmations. Multiple email addresses may be present, separated by commas</div>
					</li>
					<li>
						<h3><span class="parent-name">customer.</span><span class="name">email_invoices</span> <span class="type">string</span></h3>
						<div class="description">The customer's email address for invoices. Multiple email addresses may be present, separated by commas</div>
					</li>
				</ul>
			</div>
		</div>
	</li>
	<li>
		<h3><span class="name">created</span> <span class="type">string</span></h3>
		<div class="description">The date and time the order was placed in ISO 8601 format</div>
	</li>
	<li>
		<h3><span class="name">status</span> <span class="type">string</span></h3>
		<div class="description">The status of the order, one of <code>new</code>, <code>invoiced</code>, <code>released</code>, <code>part_fulfilled</code>, <code>on_hold</code>, <code>fulfilled</code>, <code>standing_order</code> or <code>cancelled</code></div>
	</li>
	<li>
		<h3><span class="name">reference</span> <span class="type">string</span></h3>
		<div class="description">A custom reference for this order</div>
	</li>
	<li>
		<h3><span class="name">po_number</span> <span class="type">string</span></h3>
		<div class="description">The customer's purchase order number for this order</div>
	</li>
	<li>
		<h3><span class="name">deliver_on</span> <span class="type">string</span></h3>
		<div class="description">The customer requested delivery date in ISO 8601 format</div>
	</li>
	<li>
		<h3><span class="name">net_total</span> <span class="type mf">number</span></h3>
		<div class="description">The total cost of all items on the order excluding tax</div>
	</li>
	<li>
		<h3><span class="name">gross_total</span> <span class="type mf">number</span></h3>
		<div class="description">The total cost of all items on the order including tax</div>
	</li>
	<li>
		<h3><span class="name">currency</span> <span class="type">string</span></h3>
		<div class="description">The three-letter ISO currency code representing the order's currency</div>
	</li>
	<li>
		<h3><span class="name">internal_note</span> <span class="type">string</span></h3>
		<div class="description">The internal note on this order, not visible to the customer</div>
	</li>
	<li>
		<h3><span class="name">customer_note</span> <span class="type">string</span></h3>
		<div class="description">The customer's note on this order</div>
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
						<h3><span class="parent-name">shipping_address.</span><span class="name">name</span> <span class="type">string</span></h3>
						<div class="description">Contact name</div>
					</li>				
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">company_name</span> <span class="type">string</span></h3>
						<div class="description">Company name</div>
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
						<h3><span class="parent-name">shipping_address.</span><span class="name">postal_code</span> <span class="type">string</span></h3>
						<div class="description">ZIP or postal code</div>
					</li>				
					<li>
						<h3><span class="parent-name">shipping_address.</span><span class="name">state</span> <span class="type">string</span></h3>
						<div class="description">State, county, province or region. U.S., Canadian and Australian addresses should use the abbreviated form of the state</div>
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
						<h3><span class="parent-name">billing_address.</span><span class="name">name</span> <span class="type">string</span></h3>
						<div class="description">Contact name</div>
					</li>				
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">company_name</span> <span class="type">string</span></h3>
						<div class="description">Company name</div>
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
						<h3><span class="parent-name">billing_address.</span><span class="name">postal_code</span> <span class="type">string</span></h3>
						<div class="description">ZIP or postal code</div>
					</li>				
					<li>
						<h3><span class="parent-name">billing_address.</span><span class="name">state</span> <span class="type">string</span></h3>
						<div class="description">State, county, province or region. U.S., Canadian and Australian addresses should use the abbreviated form of the state</div>
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
						<h3><span class="parent-name">order_line.</span><span class="name">quantity</span> <span class="type mf">number</span></h3>
						<div class="description">The number of items ordered</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">unit_price</span> <span class="type mf">number</span></h3>
						<div class="description">The unit price of each item on this line</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">sub_total</span> <span class="type mf">number</span></h3>
						<div class="description">The line sub-total excluding tax</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">tax_name</span> <span class="type">string</span></h3>
						<div class="description">The name of the tax rate applied to this order line</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">tax_rate</span> <span class="type mf">number</span></h3>
						<div class="description">The tax rate applied to this order line as a percentage</div>
					</li>				
					<li>
						<h3><span class="parent-name">order_line.</span><span class="name">tax_amount</span> <span class="type mf">number</span></h3>
						<div class="description">The total tax applied to this order line</div>
					</li>				
				</ul>
			</div>
		</div>
	</li>
</ul>
