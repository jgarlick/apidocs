---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ

toc_footers:

includes:
  - models/_customers.html.md
  - models/_orders.html.md
  - models/_dispatches.html.md
  - models/_products.html.md
  - models/_inventory_levels.html.md
  - models/_invoices.html.md
  - models/_categories.html.md
  - models/_customer_groups.html.md
  - models/_price_lists.html.md
  - models/_payment_terms.html.md
  - models/_tax_rates.html.md

search: false
---

# Orderspace API

Welcome to the Orderspace API reference. This document contains everything needed to access and use the API. 

<aside class="notice">
	Our API is currently in Beta. Breaking changes may be necessary but we will try to keep these to a minimum. If the API does not yet support something you need, contact us at support at orderspace.com and let us know your requirements.
</aside>

## Getting Started

To get started, contact us to enable API Access on your Orderspace site.

Once enabled, add an App from the Apps section of the Orderspace admin to provide access to the API.

The Orderspace API supports two types of App, Private and Public. 

### Private Apps

Private Apps are designed for custom integrations with a specific Orderspace site. Authentication is performed by exchanging the app's keys directly for an access token. This kind of app should be used when working directly with a trusted developer on an integration designed specifically for your site.

### Public Apps

Public Apps are designed for integrations with third-party products and services where the app can be used by any Orderspace site. Authentication uses OAuth2 Authorization Code grant flow, allowing the admin user of any Orderspace site to authorize the app through the web site.

Support for public apps is still under development and will be available soon. If you are developing an app for use by multiple Orderspace sites, start off with a Private App and we can upgrade it to a Public App when this feature becomes available.

## Request/Response Format

The Orderspace API is organised around REST using predicatable resource-oriented URLS and standard HTTP response codes. 

The base URL for all API requests is <code>https://api.orderspace.com/v1/</code>

Requests with a message body, such as create or update requests, use JSON in the message body and should have an HTTP header with <code>Content-Type: application/json</code>

Responses are returned in JSON format

Many endpoints accept optional parameters which can be passed as part of the HTTP query string. For example, <code>GET https://api.orderspace.com/v1/orders?created_since=2021-04-08</code>. The available parameters are detailed in the documentation for each endpoint.

Dates and times are in ISO 8601 format. Times are specified in UTC time regardless of the time zone set on the Orderspace account

IDs are provided for each resource as a unique, randomly generated string containing letters and numbers. IDs are prefixed with a two letter code representing the resource type, for example <code>cu_dnwz8gnx</code> represents a customer record.

## Pagination

Endpoints that return multiple records have a limit on the number of records returned. Cursor based pagination can be used to obtain additional records. The following HTTP query parameters are used:

- <code>limit</code> controls the number of records returned. For most endpoints the default is 50 and the maximum is 200 per page.
- <code>starting_after</code> is a cursor used to obtain the next page of records. This should be set to the ID of the last record in the list to obtain the next page of records. For example, when requesting orders, if the ID of the last order is <code>or_342q9r46</code>, <code>GET https://api.orderspace.com/v1/orders?starting_after=or_342q9r46</code> will return the next page of orders

## Errors

When an error occurs, an HTTP status code other than 200 will be used in the response. The message body will contain a JSON representation of the error message.

<table>
	<tr><th>Code</th><th>Description</th></tr>
	<tr><td><code>400 Bad Request</code></td><td>The request was unacceptable, often due to malformed JSON input or missing required parameters</td></tr>
	<tr><td><code>401 Unauthorized</code></td><td>The access token was invalid or missing</td></tr>
	<tr><td><code>404 Not Found</code></td><td>The requested endpoint or resource was not found</td></tr>
	<tr><td><code>422 Unprocessable Entity</code></td><td>The request could not be processed due to errors, for example validation errors when creating or updating a resource</td></tr>
	<tr><td><code>429 Too Many Requests</code></td><td>See the section on throttling</td></tr>
	<tr><td><code>500 Internal Server Error</code></td><td>Something went wrong at our end</td></tr>
</table>

## Throttling

API requests are limited to a maximum of 60 requests per minute. Clients exceeding this limit will receive an HTTP 429 response. We recommend spacing out requests to avoid hitting the limit. If an HTTP 429 response is received, wait at least 60 seconds before sending any additional requests.


# Authentication

## Private Apps

> Obtain an access token

```shell
curl -X POST https://identity.orderspace.com/oauth/token \
-d client_id=CLIENT_ID \
-d client_secret=CLIENT_SECRET \
-d grant_type=client_credentials
```

> Example response

```json
{
	"access_token": "WUECFd_Z1G02cxcKt2rFOy-Tn-zOAbjrCKUJB5S264U", 
	"token_type": "Bearer",
	"expires_in": 1800,
	"scope": "read write"
}
```

> Example of using an access token with an API request

```shell
curl https://api.orderspace.com/v1/customers \
-H "Authorization: Bearer WUECFd_Z1G02cxcKt2rFOy-Tn-zOAbjrCKUJB5S264U" 
```

Private Apps are authenticated using the OAuth2 Client Credentials grant flow.

To obtain an access token, post the app's Client ID and Client Secret to the identity server. This will return a JSON response with the access token. The token can be used to access the API using an HTTP Authorization header.

Access tokens are valid for 30 minutes. They should be stored and used for all requests to the API within the next 30 minutes. When an access token has expired, a new token can be requested by posting the client credentials to the identity server again. If an expired token is used to access the API, an HTTP 401 response will be returned.

