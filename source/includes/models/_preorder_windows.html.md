# Preorder Windows

Preorder Windows represent a specific season or drop that customers are buying for. In Orderspace you can take orders for multiple preorder windows and also sell from stock on the same items at the same time. Preorders allow you to take forward orders on items that have not yet been made. Preordered items are held back and do not reduce stock levels or appear in the Dispatch area for fulfilment until they are released.

## The Preorder Window object

> Example preorder window

```json-doc
{
  "preorder_window": {
    "id": "pw_y1pj71pk",
    "name": "Spring/Summer 2021",
    "deadline": "2021-05-21",
    "due": "2021-06-01",
    "categories": [
      { "id": "ca_kj6mz919", "name": "Spring/Summer 2021" }
    ]
  }
}
```

<ul class="attributes">
  <li>
    <h3><span class="name">id</span> <span class="type">string</span></h3>
    <div class="description">Unique auto-generated identifier for the preorder window</div>
  </li>
  <li>
    <h3><span class="name">name</span> <span class="type">string</span></h3>
    <div class="description">A short name describing the preorder window such as Spring/Summer 2021 or SS21 Drop 1<div>
  </li>
  <li>
    <h3><span class="name">deadline</span> <span class="type">string</span></h3>
    <div class="description">The deadline date for this preorder window in ISO 8601 format. This will be shown to customers and preordering will automatically stop after this day</div>
  </li>
  <li>
    <h3><span class="name">due</span> <span class="type">string</span></h3>
    <div class="description">The due date for this preorder window in ISO 8601 format. This will be shown to customers to inform them when the preordered items are due to arrive. Shown for information only</div>
  </li>
  <li>
    <h3><span class="name">categories</span> <span class="type li">list</span></h3>
    <div class="description">
      The categories associated with this preorder window. Products in the selected categories will become preorderable in this preorder window
      <div class="child-attributes">
        <h4>Child Attributes of Categories</h4>
        <ul>
          <li>
            <h3><span class="name">id</span> <span class="type">string</span></h3>
            <div class="description">Unique auto-generated identifier for the category</div>
          </li>
          <li>
            <h3><span class="name">name</span> <span class="type">string</span></h3>
            <div class="description">The name of the category</div>
          </li>
        </ul>
      </div>
    </div>
  </li>
</ul>

## List preorder windows

> Example request with curl

```shell
curl "https://api.orderspace.com/v1/preorder_windows" \
  -H "Authorization: Bearer {ACCESS TOKEN}"
```

> Example success response [HTTP 200 Success]

```json-doc
{
  "preorder_windows": [
    {
      "id": "pw_y1pj71pk",
      "name": "Spring/Summer 2021",
      "deadline": "2021-05-21",
      "due": "2021-06-01",
      "categories": [
        { "id": "ca_kj6mz919", "name": "Spring/Summer 2021" }
      ]
    },
    {...},
    {...}
  ]
}
```

Retrieve a list of preorder windows. This endpoint does not support pagination

### HTTP Request

`GET https://api.orderspace.com/v1/preorder_windows`


### Response

`HTTP 200 Success` - A list of preorder windows in JSON format
