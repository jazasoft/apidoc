---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell

#toc_footers:
#  - <a href='#'>Sign Up for a Developer Key</a>
#  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - orders
  - fpo
  - loading
  - pieceInfo
  - bundleInfo
  - orderStatusDetails
  - rejectionDetails
  - lineBalancing
  - buyers
  - seasons
  - machines
  - machineTypes
  - products
  - departments
  - lines
  - errors

search: true
---

# Introduction

Welcome to the OptaFloor API! You can use our API to access OptaFloor API endpoints.

We have language bindings in Shell. You can view code examples in the dark area to the right, and you can switch the
programming language of the examples with the tabs in the top right.

# Authentication

In order to access OptaFloor API, you will need authenticate. We support two modes of authentication

- `OAuth 2.0`: When client is user who have user account and can enter username and password
- `API Key`: When client is Machine/Application etc.

## OAuth 2.0

> To authorize, use this code:

```shell
# With shell, you can just pass the correct header with each request
curl "{IAM_BASE_URL}/oauth/token?grant_type=password&appId=optafloor&username={username}&password={password}"
  -H "Authorization: Basic Y2xpZW50OnNlY3JldA=="
```

> Make sure to replace `IAM_BASE_URL` with actual IAM Url and `username`, `password` with your username and password.

> The above command returns JSON structured like this:

```json
{
  "access_token": "eyJhbGciOiJSUzI1NiIsInR5c...oXLVc6YA",
  "token_type": "bearer",
  "refresh_token": "eyJhbGciOiJSUzI1NiIsIn...zbi3zCTTniTpmbJ1KeA",
  "expires_in": 43199,
  "scope": "read,write",
  "application": "optafloor",
  "user_id": 7,
  "resources": {},
  "tenant": "dev",
  "jti": "62e24a85-1e53-4797-a3cc-4d0e3357be45"
}
```

### HTTP Request

`GET {IAM_BASE_URL}/oauth/token`

### Query Parameters

| Parameter  | Default | Description                 |
|------------|---------|-----------------------------|
| grant_type |         | value should be  `password` |
| appId      |         | value should be  `optafloor`  |
| username   |         | Your Username               |
| password   |         | Your Password               |

OptaFloor expects the Access Token to be included in all API requests to the server in a header that looks like the
following:

`Authorization: Bearer eyJhbGciOiJSUzI1NiIsInR5cCI6IkpXVCJ...oXLVc6YA`

## API Key

We will issue API Key with the appropriate privilege which can be used to access OptaFloor endpoints by including API Key
in
HTTP Request header which will look like:

`x-api-key: p4VXJhzNZVujvqX2l1d9IJp9.b3B0YWN1dA==`

# Pagination and Sort

> Response of Fetch all call looks like this

```json
{
  "content": [
    {
      "id": 1,
      "name": "Name 1"
    },
    {
      "id": 2,
      "name": "Name 2"
    }
  ],
  "pageable": {
    "sort": {
      "sorted": false,
      "unsorted": true,
      "empty": true
    },
    "offset": 0,
    "pageSize": 20,
    "pageNumber": 0,
    "paged": true,
    "unpaged": false
  },
  "totalPages": 1,
  "totalElements": 2,
  "last": true,
  "number": 0,
  "sort": {
    "sorted": false,
    "unsorted": true,
    "empty": true
  },
  "size": 20,
  "first": true,
  "numberOfElements": 2,
  "empty": false
}
```

All Fetch/Get API (with few exceptions) on each resource support pagination and sorting. Following parameters are used -

| Parameter | Default | Description                                                                               |                                                                               
|-----------|---------|-------------------------------------------------------------------------------------------|
| page      | 0       | `Zero` indexed page number                                                                |                                                                
| pageSize  | 20      | Number of records to fetch in one Page                                                    |                                                    
| sort      | id,desc | `id`: field on which sorting is applied, `desc`: Sort Direction. values - [`asc`, `desc`] | 

# Filter and Search

All Fetch/Get (with few exceptions) API on each resource support filtering and searching. Following parameters are
used -

| Parameter | Default | Description                                      |                                      
|-----------|---------|--------------------------------------------------|
| search    |         | filter and Search criteria using RSQL formating. | 

API uses `RSQL Parser` to achieve this. Refer [RSQL](https://github.com/jirutka/rsql-parser) documentation for more
details.

