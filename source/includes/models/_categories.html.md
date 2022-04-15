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
    "parent_id": null
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
</ul>

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

