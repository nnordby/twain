---
title: Product Service Readme
keywords: rpc, Product Service, product, vfs, service
last_updated: April 27, 2017
tags: [vfs, service, rpc]
summary: "Manages products within the VFS Product Library."
sidebar: product1_sidebar
permalink: vfs_productService.html
folder: product1
---

# RPC.ProductService

Manages products within the VFS Product Library.

## Quick Start

To run the service locally:

```bash
npm install
npm start -- --debug
```

For automatic code reloading in development:

```bash
npm install -g nodemon
nodemon -- --debug
```

To run on __AMQP__, omit the ```--debug``` option from either command.

<sup>_Note: You will need a running [RabbitMQ and ETCD2](https://github.com/nsnsolutions/rpcfw.env) environment._</sup>

# Interface

This section outlines the details you will need to use this service.

- [Methods](#methods)
- [Representations](#representations)

## Methods

- [Get Products (v1)](#get-products-v1) - Gets list of products
- [Get Product (v1)](#get-product-v1) - Gets product by ID
- [Create Product (v1)](#create-product-v1) - Creates a new product
- [Copy Product (v1)](#copy-product-v1) - Create a new product using another product's template.
- [Update Product (v1)](#update-product-v1) - Updates an existing product
- [Publish Template (v1)](#publish-template-v1) - Publishes version of a product's template
- [Get Token Manifest (v1)](#get-token-manifest-v1) - Retrieve the token manifest for a specific product.
- [Get Product Tags (v1)](#get-product-tags-v1) - Retrieve the list of tags associated with this product.

### Get Products (v1)

Gets a list of products.

##### API Request

```
GET /dev-product/products
Host: api.vfs.velma.com
Authorization: {{jwt-token}}
x-api-key: {{your-api-key}}
Cache-Control: no-cache
```

##### RPC Execution

```javascript
var args = { ... }
seneca.act('role:productService.Pub,cmd:getProductList.v1', args, (err, dat) => {
    /* Handle result */
});
```

##### HTTP Execution

```
POST /amqp/exec/productService/getProductList?version=v1 HTTP/1.1
Host: devel.rpc.velma.com
Content-Type: application/json
x-repr-format: RPC
Cache-Control: no-cache
```

##### Request

API Requests should be made with these parameters in the Query String. RPC requests accept these parameters in the POST body.

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| filterBy | String | (none) | String of filter parameters as described in the [FilterBy Parameter (v1)](https://github.com/nsnsolutions/RPC.Utils/blob/devel/README.md#staticmethod-parsefilterstring). |
| sortBy | String | id | Field name for sorting results |
| sortDir | String | asc | Sort order as ascending (asc) or descending (desc) |
| pageSize | Integer | 20 | Page size is the maximum number of results in each set |
| pageIndex | Integer | 1 | Page number of the requested results (one-based index). Ex. pageIndex=1, pageSize=20 will return records 1-20, pageIndex=2 will return 21-40. |

```
{
	"token": "jwt XXX",
    "filterBy": "title:BEGINSWITH:Buyer",
    "sortBy": "id",
    "sortDir": "asc",
    "pageSize": 20,
    "pageIndex": 1
}
```

##### Response

This method responds with an array of [Product Entities (v1)](#product-entity-v1).

```
{
  "items": [
    {
      "id": "0000",
      "title": "Your Product Title",
      "description": "Your Product Description",
      "preview": "https://vfs.url/preview.jpg",
      "template": "https://vfs.url/template.html?versionId=XXX",
      "thumb": "https://vfs.url/thumb.jpg?versionId=XXX"
    }
  ],
  "totalCount": 1,
  "pageIndex": 1,
  "itemPerPage": 20
}
```


##### Get Product (v1)

Gets product by ID.

##### API Request

```
GET /dev-product/products/:id
Host: api.vfs.velma.com
Authorization: {{jwt-token}}
x-api-key: {{your-api-key}}
Cache-Control: no-cache
```

##### RPC Execution

```javascript
var args = { ... }
seneca.act('role:productService.Pub,cmd:getProduct.v1', args, (err, dat) => {
    /* Handle result */
});
```

##### HTTP Execution

```
POST /amqp/exec/productService/getProduct?version=v1 HTTP/1.1
Host: devel.rpc.velma.com
Content-Type: application/json
x-repr-format: RPC
Cache-Control: no-cache
```

##### Request

API Requests should include the product's ID on the URL. RPC Requests should include the id value in the POST body.

```
{
	"token": "jwt XXX",
    "id": "0000"
}
```

##### Response

This method responds with a single [Product Entity (v1)](#product-entity-v1).

```
{
	"id": "0000",
	"title": "Your Product Title",
	"description": "Your Product Description",
	"template": "https://vfs.url/template.html?versionId=XXX",
	"thumb": "https://vfs.url/thumb.jpg?versionId=XXX",
	"preview": "https://vfs.url/preview.jpg"
}
```


#### Create Product (v1)

Creates a new product.

##### API Request

```
POST /dev-product/products
Host: api.vfs.velma.com
Authorization: {{jwt-token}}
x-api-key: {{your-api-key}}
Cache-Control: no-cache
```

##### RPC Execution

```javascript
var args = { ... }
seneca.act('role:productService.Pub,cmd:createProduct.v1', args, (err, dat) => {
    /* Handle result */
});
```

##### HTTP Execution

```
POST /amqp/exec/productService/createProduct?version=v1 HTTP/1.1
Host: devel.rpc.velma.com
Content-Type: application/json
x-repr-format: RPC
Cache-Control: no-cache
```

##### Request

| Field | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier for the entity. The requester is required to find a unique identifier for their own library. |
| productId | String | (Deprecated) Legacy identifier. Can still be used for GetProduct requests.
| title | String | Name of the product |
| description | String | Description of the product |
| templateData | String | Template data to store as the HTML content for this product. |

```
{
	"token": "jwt XXX",
	"id": "0000",
    "title": "Your Product Title",
    "description": "Your Product Description",
    "templateData": "XXX"
}
```

##### Response

This method responds with the newly created [Product Entity (v1)](#product-entity-v1).

```
{
	"id": "0000",
	"title": "Your Product Title",
	"description": "Your Product Description",
	"template": "https://vfs.url/template.html?versionId=XXX",
	"thumb": "https://vfs.url/thumb.jpg?versionId=XXX",
	"preview": "https://vfs.url/preview.jpg"
}
```

##### Copy Product (v1)

Create a new product using another product's template.

##### API Request

```
POST /dev-product/products/:fromProductId/copy
Host: api.vfs.velma.com
Authorization: {{jwt-token}}
x-api-key: {{your-api-key}}
Cache-Control: no-cache

{
  "id": "0000",
  "productId": "0000",
  "title": "New Product Title",
  "description": "New Product Description."
}
```

##### RPC Execution

```javascript
var args = { ... }
seneca.act('role:productService.Pub,cmd:copyProduct.v1', args, (err, dat) => {
    /* Handle result */
});
```

##### HTTP Execution

```
POST /amqp/exec/productService/copyProduct?version=v1 HTTP/1.1
Host: devel.rpc.velma.com
Content-Type: application/json
x-repr-format: RPC
Cache-Control: no-cache
```

##### Request

| Field | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier for the entity. The requester is required to find a unique identifier for their own library. |
| productId | String | (Deprecated) Legacy identifier. Can still be used for GetProduct requests.
| title | String | Name of the product |
| description | String | Description of the product |
| fromId | String | The product ID of an existing product who's template will be copied. |

```
{
	"token": "jwt XXX",
	"id": "0000",
    "title": "Your Product Title",
    "description": "Your Product Description",
    "fromId": "0000"
}
```

##### Response

This method responds with the newly created [Product Entity (v1)](#product-entity-v1).

```
{
	"id": "0000",
	"title": "Your Product Title",
	"description": "Your Product Description",
	"template": "https://vfs.url/template.html?versionId=XXX",
	"thumb": "https://vfs.url/thumb.jpg?versionId=XXX",
	"preview": "https://vfs.url/preview.jpg"
}
```

##### Update Product (v1)

Updates an existing product.

##### API Request

```
POST /dev-product/products/:id
Host: api.vfs.velma.com
Authorization: {{jwt-token}}
x-api-key: {{your-api-key}}
Cache-Control: no-cache
```

##### RPC Execution

```javascript
var args = { ... }
seneca.act('role:productService.Pub,cmd:updateProduct.v1', args, (err, dat) => {
    /* Handle result */
});
```

##### HTTP Execution

```
POST /amqp/exec/productService/updateProduct?version=v1 HTTP/1.1
Host: devel.rpc.velma.com
Content-Type: application/json
x-repr-format: RPC
Cache-Control: no-cache
```

##### Request

| Field | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier for the entity. |
| title | String | Name of the product |
| description | String | Description of the product |
| templateData | String | Template data to store as the HTML content for this product. |

```
{
	"token": "jwt XXX",
	"id": "0000",
    "title": "Your Product Title",
    "description": "Your Product Description",
    "templateData": "XXX"
}
```

##### Response

This method responds with the updated [Product Entity (v1)](#product-entity-v1).

```
{
	"id": "0000",
	"title": "Your Product Title",
	"description": "Your Product Description",
	"template": "https://vfs.url/template.html?versionId=XXX",
	"thumb": "https://vfs.url/thumb.jpg?versionId=XXX",
	"preview": "https://vfs.url/preview.jpg"
}
```


### Publish Template (v1)

Publishes version of the product's template.

#### API Request

```
POST /dev-product/products/:id/publish
Host: api.vfs.velma.com
Authorization: {{jwt-token}}
x-api-key: {{your-api-key}}
Cache-Control: no-cache
```

#### RPC Execution

```javascript
var args = { ... }
seneca.act('role:productService.Pub,cmd:publishTemplate.v1', args, (err, dat) => {
    /* Handle result */
});
```

#### HTTP Execution

```
POST /amqp/exec/productService/publishTemplate?version=v1 HTTP/1.1
Host: devel.rpc.velma.com
Content-Type: application/json
x-repr-format: RPC
Cache-Control: no-cache
```

#### Request

| Field | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier for the entity. For now, the requester is required to find their own unique identifier. |
| versionId | String | AWS-assigned version identifier. If not specified, the "latest" version will be published. |

```
{
	"token": "jwt XXX",
	"id": "0000",
    "versionId": "latest"
}
```

#### Response

This method responds with the updated asset URL's for the newly published template.

```
{
	"id": "0000",
	"template": "https://vfs.url/template.html?versionId=XXX",
	"thumb": "https://vfs.url/thumb.jpg?versionId=XXX",
	"preview": "https://vfs.url/preview.jpg"
}
```

### Get Token Manifest (v1)

Retrieve the token manifest for a specific product.

#### API Request

```
GET /dev-product/products/:id/manifest
Host: api.vfs.velma.com
Authorization: {{jwt-token}}
x-api-key: {{your-api-key}}
Cache-Control: no-cache
```

#### RPC Execution

```javascript
var args = { ... }
seneca.act('role:productService.Pub,cmd:getTokenManifest.v1', args, (err, dat) => {
    /* Handle result */
});
```

#### HTTP Execution

```
POST /amqp/exec/productService/getTokenManifest?version=v1 HTTP/1.1
Host: devel.rpc.velma.com
Content-Type: application/json
x-repr-format: RPC
Cache-Control: no-cache
```

#### Request

| Field | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier for the entity. For now, the requester is required to find their own unique identifier. |

```
{
	"token": "jwt XXX",
	"id": "0000"
}
```

#### Response

- [Error Response](error-response)
- [Token Manifest (v1)](token-manifest-v1)

### Get Product Tags (v1)

Retrieve a list of tags associated with this product.

#### API Request

```
GET /dev-product/products/:id/tags
Host: api.vfs.velma.com
Authorization: {{jwt-token}}
x-api-key: {{your-api-key}}
Cache-Control: no-cache
```

#### RPC Execution

```javascript
var args = { ... }
seneca.act('role:productService.Pub,cmd:getProductTags.v1', args, (err, dat) => {
    /* Handle result */
});
```

#### HTTP Execution

```
POST /amqp/exec/productService/getProductTags?version=v1 HTTP/1.1
Host: devel.rpc.velma.com
Content-Type: application/json
x-repr-format: RPC
Cache-Control: no-cache
```

#### Request

| Field | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier for the entity. For now, the requester is required to find their own unique identifier. |

```
{
	"token": "jwt XXX",
	"id": "0000"
}
```

#### Response

- [Error Response](error-response)
- [Tag List (v1)](tag-list-v1)


## Representations

A description of the various entities

### Product Entity (v1)

| Field | Type | Description |
| --- | --- | --- |
| id | String | Unique identifier for the entity |
| title | String | Name of the product |
| description | String | Description of the product |
| template | String | URL to the HTML content of this product |
| thumb | String | URL to the thumbnail image for this product |
| preview | String | URL to the preview image(s) for this product. If a multi-page product, this will be a reference to an image of the first page. |

```
{
	"id": "0000",
	"title": "Your Product Title",
	"description": "Your Product Description",
	"template": "https://vfs.url/template.html?versionId=XXX",
	"thumb": "https://vfs.url/thumb.jpg?versionId=XXX",
	"preview": "https://vfs.url/preview.jpg"
}
```

### Tag List (v1)

Returns a list of strings that represent the tags asoociated with a product.

```json
[
    "Tag1",
    "Tag2",
    "Tag3"
]
```

### Token Manifest (v1)

This is a passthrough from the token service. Please see
[documentation](https://github.com/nsnsolutions/RPC.TokenService/blob/master/README.md#representations)

### Error Response

```
{
	"code": 000,
    "message": "Description of error"
}
```

## Local Development

Initial Setup:

1. Configure [RabbitMQ and ETCD2](https://github.com/nsnsolutions/rpcfw.env) environment
2. Install [Prince](http://www.princexml.com) [www.princexml.com](http://www.princexml.com)
3. Run "npm install -g nodemon" to globally install Nodemon code monitoring utility
4. Repeat the following steps for RPC.Interface, RPC.AccountService, RPC.AssetService, RPC.Render, RPC.ProductService:

```bash
git clone git@github.com:nsnsolutions/[ProjectName].git
cd [ProjectName]
npm install
```

Steps for Running:

```bash
Start Docker

term 1 - Run RabbitMQ:
cd rpcfw.env
docker-compose --file local/docker-compose.yml up

term 2 - Run RPC Interface:
cd RPC.Interface
npm start

term 3 - Run RPC.AccountService:
cd RPC.AccountService
npm start

term 4 - Run RPC.AssetService:
cd RPC.AssetService
npm start

term 5 - Run RPC.Render:
cd RPC.Render
npm start

term 6 - Run Product Service:
cd RPC.ProductService
nodemon
```
