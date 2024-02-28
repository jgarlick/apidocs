# Products

Products represent items for sale. Products contain product variants which represent a specific version of a product with unique properties, e.g. colors and sizes. Products with no variations contain a single product variant.

## The Product Object

> Example product

```json-doc
{
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
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the product</div>
	</li>
	<li>
		<h3><span class="name">code</span> <span class="type">string</span></h3>
		<div class="description">A unique code to represent the product</div>
	</li>
	<li>
		<h3><span class="name">name</span> <span class="type">string</span></h3>
		<div class="description">The name of the product</div>
	</li>
	<li>
		<h3><span class="name">description</span> <span class="type">string</span></h3>
		<div class="description">Details of the product shown on product pages</div>
	</li>
	<li>
		<h3><span class="name">active</span> <span class="type">boolean</span></h3>
		<div class="description">Controls the visibility of the product to customers</div>
	</li>
	<li>
		<h3><span class="name">minimum</span> <span class="type number">number</span></h3>
		<div class="description">The minimum order quantity required for this product. Set to null for no minimum. Minimums are set account-wide to either per product or per variant. This field is only present on the product when the setting is per product</div>
	</li>
	<li>
		<h3><span class="name">tariff_code</span> <span class="type">string</span></h3>
		<div class="description">The tariff code for commercial invoices. Set to null to use the default tariff code. Only visible if the commercial invoices feature is enabled</div>
	</li>
	<li>
		<h3><span class="name">country_of_origin</span> <span class="type">string</span></h3>
		<div class="description">The country of origin for commercial invoices. Set to null to use the default country of origin. Only visible if the commercial invoices feature is enabled</div>
	</li>
	<li>
		<h3><span class="name">composition</span> <span class="type">string</span></h3>
		<div class="description">The composition of the product for commercial invoices. Set to null to use the default composition. Only visible if the commercial invoices feature is enabled</div>
	</li>
	<li>
		<h3><span class="name">variant_options</span> <span class="type li">list</span></h3>
		<div class="description">A list of the ways in which the product varies (Color, Size etc). Products can have zero, one, two or three variant options. The order of the options in the list is significant as this controls how the products are displayed on ordering tables. The order should be the same throughout your products so that ordering tables are consistent. For example, if products vary by Color and Size, always list Color first and Size second.
	</li>
	<li>
		<h3><span class="name">product_variants</span> <span class="type li">list</span></h3>
		Product Variants represent a specific version of a product based on the variant options you have specified. For example, if the options are Color and Size, there should be one product variant for each specific color and size your product contains (for example Red, Small). Products with no variant options should have a single product variant with <code>options</code> left empty.
		<div class="description">
			<div class="child-attributes">
				<h4>Child Attributes</h4>
				<ul>
					<li>
						<h3><span class="name">id</span> <span class="type">string</span></h3>
						<div class="description">Unique auto-generated identifier for the product variant</div>
					</li>
					<li>
						<h3><span class="name">sku</span> <span class="type">string</span></h3>
						<div class="description">A unique code to represent the product variant. Often this is a combination of the product code and a suffix representing the unique variant, for example AD01-RED-S to represent product code AD01 with color red and size small.</div>
					</li>
					<li>
						<h3><span class="name">barcode</span> <span class="type">string</span></h3>
						<div class="description">Optional barcode number (EAN/UPC/GTIN) representing this product variant</div>
					</li>
					<li>
						<h3><span class="name">options</span> <span class="type ha">hash</span></h3>
						<div class="description">A hash listing the options that make this variant unique. The keys should match the product's <code>variant_options</code> and the combination of values must be unique to this variant. For example, if the variant options are Color and Size, a specific variant could be <code>{"Color": "Red", "Size": "Small"}</code></div>
					</li>
					<li>
						<h3><span class="name">unit_price</span> <span class="type number">number</span></h3>
						<div class="description">The wholesale price of the product variant</div>
					</li>
					<li>
						<h3><span class="name">price_list_prices</span> <span class="type li">list</span></h3>
						<div class="description">
							A list of price list prices set for this product variant. If a price is not listed here, the price will default to the standard unit price multiplied by the price list conversion rate
							<div class="description">
								<div class="child-attributes">
									<h4>Child Attributes</h4>
									<ul>
										<li>
											<h3><span class="name">id</span> <span class="type">string</span></h3>
											<div class="description">The ID of the price list</div>
										</li>
										<li>
											<h3><span class="name">unit_price</span> <span class="type number">number</span></h3>
											<div class="description">The unit price of the product variant for this price list. Set to <code>null</code> to remove the price set here and revert back to the calculated price of unit price multiplied by price list conversion rate</div>
										</li>
									</ul>
								</div>
						</div>
					</li>					
					<li>
						<h3><span class="name">rrp</span> <span class="type number">number</span></h3>
						<div class="description">The recommended retail price for the product variant</div>
					</li>
					<li>
						<h3><span class="name">backorder</span> <span class="type">boolean</span></h3>
						<div class="description">Determines if the product variant can be ordered when there is no stock available. Set to false, only the stock available can be ordered</div>
					</li>
					<li>
						<h3><span class="name">minimum</span> <span class="type number">number</span></h3>
						<div class="description">The minimum order quantity required for this variant. Set to null for no minimum. Minimums are set account-wide to either per product or per variant. This field is only present on variants when the setting is per variant</div>
					</li>
					<li>
						<h3><span class="name">multiple</span> <span class="type number">number</span></h3>
						<div class="description"></div>
					</li>
					<li>
						<h3><span class="name">weight</span> <span class="type number">number</span></h3>
						<div class="description">The weight of this variant in kg. Used for shipping price calculations</div>
					</li>
					<li>
						<h3><span class="name">tax_rate_id</span> <span class="type">string</span></h3>
						<div class="description">The tax rate id to be used for this item. Should be set to null to use the default tax rate unless a specific tax rate is required</div>
					</li>
					<li>
						<h3><span class="name">location</span> <span class="type">string</span></h3>
						<div class="description">A string representing the location of this item in the warehouse, used for picking. This field is only present if the stock locations feature is enabled</div>
					</li>
				</ul>
		</div>
	</li>
	<li>
		<h3><span class="name">categories</span> <span class="type li">list</span></h3>
		<div class="description">
			A list of categories the product is listed in
			<div class="child-attributes">
				<h4>Child Attributes</h4>
				<ul>
					<li>
						<h3><span class="name">id</span> <span class="type">string</span></h3>
						<div class="description">The ID of the category</div>
					</li>
					<li>
						<h3><span class="name">name</span> <span class="type">string</span></h3>
						<div class="description">The name of the category</div>
					</li>
				</ul>
		</div>
	</li>
	<li>
		<h3><span class="name">grouping_category_id</span> <span class="type">string</span></h3>
		<div class="description">The ID of the category used for grouping on orders. Only shown if "group products on orders" is enabled</div>
	</li>
</ul>

## Create a product

> Example request with curl

```shell
curl -X POST https://api.orderspace.com/v1/products \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
  "product": {
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
        "sku": "AD01-RED-10",
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
        "sku": "AD01-RED-12",
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
        "sku": "AD01-RED-14",
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
      {"id": "ca_x61lk8j7"},
      {"id": "ca_3xwy7mwo"}
    ],
    "grouping_category_id": "ca_x61lk8j7"
  }
}'
```

> Example success response [HTTP 200 Success]

```json-doc
{
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
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
  "message": "Validation failed: Product Code must be unique"
}
```

Create a new product

### HTTP Request

`POST https://api.orderspace.com/v1/products`

### Response

`HTTP 200 Success` - The product object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors

## List products

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/products \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -d limit=20 \
  -d starting_after=pr_njgnve1o
```

> Example success response [HTTP 200 Success]

```json-doc
{
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
  ],
  "has_more": true
}
```

Retrieve a list of products. Products are returned in the order they are created with the most recently created listed first

### HTTP Request

`GET https://api.orderspace.com/v1/products`

### Parameters

<ul class="attributes">
	<li>
		<h3><span class="name">starting_after</span> <span class="optional">optional</span></h3>
		<div class="description">A cursor used for pagination. Setting `starting_after` to the ID of the last product in the list will retrieve the next page of products</div>
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
		<div class="description">Return records updated since the given date and time in ISO 8601 format, e.g. <code>2019-10-29T21:00</code> </div>
	</li>
	<li>
		<h3><span class="name">code</span> <span class="optional">optional</span></h3>
		<div class="description">Return products with the specified code. Should only return a single product as the codes are unique</div>
	</li>
	<li>
		<h3><span class="name">name</span> <span class="optional">optional</span></h3>
		<div class="description">Return products with the specified name</div>
	</li>
	<li>
		<h3><span class="name">active</span> <span class="optional">optional</span></h3>
		<div class="description">Return products with active set to the specified value, one of <code>true</code> or <code>false</code></div>
	</li>
	<li>
		<h3><span class="name">category_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return products in the specified category</div>
	</li>
</ul>

### Response

`HTTP 200 Success` - A list of products in JSON format


## Retrieve a product

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/products/pr_lj3pwm1n \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
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
```

Retrieve a single product by ID

### HTTP Request

`GET https://api.orderspace.com/v1/products/:product_id`

### Response

`HTTP 200 Success` - The product record in JSON format

`HTTP 404 Not Found` - A message describing the error


## Update a product

> Example request with curl

```shell
curl -X PUT https://api.orderspace.com/v1/products/pr_lj3pwm1n \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
  "product": {
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
        "sku": "AD01-RED-10",
        "barcode": "123456789",
        "options": {"Color": "Red", "Size": "10"},
        "unit_price": 32.0,
        "price_list_prices": [
          {"id": "pr_z0j7yjl2", "unit_price": 35.0},
          {"id": "pl_zyjgq19r", "unit_price": null}
        ],
        "rrp": 72.0,
        "backorder": true,
        "minimum": 4,
        "multiple": 3,
        "weight": 0.0,
      },
      {
        "id": "pv_xjz5xvjk",
        "sku": "AD01-RED-12",
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
        "sku": "AD01-RED-14",
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
      {"id": "ca_x61lk8j7"},
      {"id": "ca_3xwy7mwo"}
    ],
    "grouping_category_id": "ca_x61lk8j7"
  }
}'
```

> Example success response [HTTP 200 Success]

```json-doc
{
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
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
  "message": "Validation failed: Product Code must be unique"
}
```

Update an existing product. We recommend that you include all the fields and all the product variants in your update, not just the ones that are changing. Existing product variants should include their ID which can be obtained by retrieving the product through the API first.

### HTTP Request

`PUT https://api.orderspace.com/v1/products/:product_id`


### Response

`HTTP 200 Success` - The product object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors


