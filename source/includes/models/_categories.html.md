# Categories

Categories are used to group related products together

## The Category object

> Example category

```json-doc
{
  "category": {
    "id": "ca_n51qpxjd",
    "name": "Dresses",
    "description": "",
    "active": true,
    "parent_id": null,
    "products": [
      {"product_id": "pr_r9x2mk1g", "product_name": "Alexa Dress"},
    ]
  }
}
```

<ul class="attributes">
	<li>
		<h3><span class="name">id</span> <span class="type">string</span></h3>
		<div class="description">Unique auto-generated identifier for the category</div>
	</li>
	<li>
		<h3><span class="name">name</span> <span class="type">string</span></h3>
		<div class="description">The name of the category<div>
	</li>
	<li>
		<h3><span class="name">description</span> <span class="type">string</span></h3>
		<div class="description">Text shown on the category page. Can contain HTML tags for formatting<div>
	</li>
	<li>
		<h3><span class="name">active</span> <span class="type">boolean</span></h3>
		<div class="description">Controls whether the categories is visible on the ordering site</div>
	</li>
	<li>
		<h3><span class="name">parent_id</span> <span class="type">string</span></h3>
		<div class="description">The identifier of the parent category if this category is a sub-category</div>
	</li>
  <li>
    <h3><span class="name">products</span> <span class="type li">list</span></h3>
    <div class="description">
      A list of products associated with the category
			<div class="child-attributes">
				<h4>Child Attributes of Products</h4>
				<ul>
					<li>
						<h3><span class="parent-name">product.</span><span class="name">product_id</span> <span class="type">string</span></h3>
						<div class="description">The id of the product</div>
					</li>
					<li>
						<h3><span class="parent-name">product.</span><span class="name">product_name</span> <span class="type">string</span></h3>
						<div class="description">The name of the product</div>
					</li>
				</ul>
			</div>
    </div>
  </li>
</ul>


## Create a category

> Example request with curl

```shell
curl -X POST https://api.orderspace.com/v1/categories \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
    "category": {
      "name": "Dresses",
      "description": "",
      "active": true,
      "parent_id": null,
      "products": [
        {"product_id": "pr_r9x2mk1g"},
        {"product_id": "pr_2rjlgp16"},
        {...},
        {...},
      ]
    }
  }'
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "category": {
    "id": "ca_n51qpxjd",
    "name": "Dresses",
    "description": "",
    "active": true,
    "parent_id": null,
    "products": [
      {"product_id": "pr_r9x2mk1g", "product_name": "Alexa Dress"},
      {"product_id": "pr_2rjlgp16", "product_name": "T-Shirt"},
      {...},
      {...},
    ]
  }
}
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
	"message": "Validation failed: Name is too long (maximum is 100 characters)"
}
```

Create a new category

### HTTP Request

`POST https://api.orderspace.com/v1/categories`

### Response

`HTTP 200 Success` - The category object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors


## List categories

> Example request with curl

```shell
curl https://api.orderspace.com/v1/categories \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -d limit=20 \
  -d starting_after=ca_57w9p7jz
```

> Example HTTP 200 success response

```json-doc
{
  "categories": [
    {
      "id": "ca_n51qpxjd",
      "name": "Dresses",
      "description": "",
      "active": true,
      "parent_id": null
    },
    {...},
    {...}
  ],
  "has_more": true
}
```
Retrieve a list of categories. Categories are returned based on their sort order on the web site

### HTTP Request

`GET https://api.orderspace.com/v1/categories`

### Parameters

<ul class="attributes">
	<li>
		<h3><span class="name">starting_after</span> <span class="optional">optional</span></h3>
		<div class="description">A cursor used for pagination. Setting `starting_after` to the ID of the last category in the list will retrieve the next page of categories</div>
	</li>
	<li>
		<h3><span class="name">limit</span> <span class="optional">optional</span></h3>
		<div class="description">A limit on the number of records returned. The default is 50 and the maximum limit is 200</div>
	</li>
	<li>
		<h3><span class="name">name</span> <span class="optional">optional</span></h3>
		<div class="description">Return categories matching this name</div>
	</li>
	<li>
		<h3><span class="name">parent_id</span> <span class="optional">optional</span></h3>
		<div class="description">Return sub-categories with this parent</div>
	</li>
</ul>

### Response

`HTTP 200 Success` - A list of categories in JSON format


## Retrieve a category

> Example request with curl

```shell
curl -X GET https://api.orderspace.com/v1/categories/ca_n51qpxjd \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "category": {
    "id": "ca_n51qpxjd",
    "name": "Dresses",
    "description": "",
    "active": true,
    "parent_id": null,
    "products": [
      {"product_id": "pr_r9x2mk1g", "product_name": "Alexa Dress"},
      {"product_id": "pr_2rjlgp16", "product_name": "T-Shirt"},
      {...},
      {...},
    ]
  }
}
```

Retrieve a single category by ID

### HTTP Request

`GET https://api.orderspace.com/v1/categories/:category_id`

### Response

`HTTP 200 Success` - The category record in JSON format

`HTTP 404 Not Found` - A message describing the error


## Update a category

> Example request with curl

```shell
curl -X PUT https://api.orderspace.com/v1/categories/ca_n51qpxjd \
  -H "Authorization: Bearer {ACCESS TOKEN}" \
  -H "Content-Type: application/json" \
  -d '{
    "category": {
      "name": "Dresses",
      "description": "",
      "active": true,
      "parent_id": null,
      "products": [
        {"product_id": "pr_r9x2mk1g"},
        {"product_id": "pr_2rjlgp16"},
        {...},
        {...},
      ]
    }
  }'
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "category": {
    "id": "ca_n51qpxjd",
    "name": "Dresses",
    "description": "",
    "active": true,
    "parent_id": null,
    "products": [
      {"product_id": "pr_r9x2mk1g", "product_name": "Alexa Dress"},
      {"product_id": "pr_2rjlgp16", "product_name": "T-Shirt"},
      {...},
      {...},
    ]
  }
}
```

> Example error response [HTTP 422 Unprocessable Entity]

```json-doc
{
	"message": "Validation failed: Name is too long (maximum is 100 characters)"
}
```

Update an existing category. Any fields not included in the update will remain the same.

### HTTP Request

`PUT https://api.orderspace.com/v1/categories/:category_id`


### Response

`HTTP 200 Success` - The category object in JSON format

`HTTP 422 Unprocessable Entity` - A message describing the errors
