---
title: Mobile App API Reference

language_tabs:
  - shell

toc_footers:
  - <a href='#'>API &copy; 2014 Apex Capital Corp</a>
  - <a href='http://github.com/tripit/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to the Apex Mobile App API! You can use our API to discover any mobile app endpoints you might need. Our endpoints are very loosely based on REST API. Ok not really. The endpoints are currently backed by Struts 2 actions. Hopefully
in the future we'll transition to a pure REST API.

Examples provided are for curl usage. You can view code examples in the dark area to the right.

# Authentication

## Login

```shell
curl "https://clients.apexcapitalcorp.com/m3clients/mobile/mobileLogin.action" \
  -d username=apextest \
  -d password=asdf1234
```

> EXAMPLE RESPONSE:

```json
{
    "accessedFrom": null,
    "name": "Apple Test User",
    "password": "",
    "requiredDocs": [ ],
    "sessionId": "NTU2MDIyNg==",
    "username": "appletest"
}
```

This endpoint returns a token based on successful authentication with Apex's servers. This token (currently referred to as sessionId) will be used with subsequent requests to identify the current signed in user.

### HTTP Request

`GET https://clients.apexcapitalcorp.com/m3clients/mobile/mobileLogin.action`

### Query Parameters

Parameter | Required | Description
--------- | -------- | -----------
username | true | your Apex username
password | true | your Apex password

# Kittens

## Get All Kittens

```shell
curl "http://example.com/api/kittens"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
[
  {
    "id": 1,
    "name": "Fluffums",
    "breed": "calico",
    "fluffiness": 6,
    "cuteness": 7
  },
  {
    "id": 2,
    "name": "Isis",
    "breed": "unknown",
    "fluffiness": 5,
    "cuteness": 10
  }
]
```

This endpoint retrieves all kittens.

### HTTP Request

`GET http://example.com/kittens`

### Query Parameters

Parameter | Default | Description
--------- | ------- | -----------
include_cats | false | If set to true, the result will also include cats.
available | true | If set to false, the result will include kittens that have already been adopted.

<aside class="success">
Remember — a happy kitten is an authenticated kitten!
</aside>

## Get a Specific Kitten

```shell
curl "http://example.com/api/kittens/3"
  -H "Authorization: meowmeowmeow"
```

> The above command returns JSON structured like this:

```json
{
  "id": 2,
  "name": "Isis",
  "breed": "unknown",
  "fluffiness": 5,
  "cuteness": 10
}
```

This endpoint retrieves a specific kitten.

<aside class="warning">If you're not using an administrator API key, note that some kittens will return 403 Forbidden if they are hidden for admins only.</aside>

### HTTP Request

`GET http://example.com/kittens/<ID>`

### URL Parameters

Parameter | Description
--------- | -----------
ID | The ID of the cat to retrieve
