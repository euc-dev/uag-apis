---
layout: page
title: Getting Started Guide
hide:
  #- navigation
  - toc
---

This guide provides sample usage snippets to assist you in effectively utilizing the Unified Access Gateway REST APIs with the cURL command line client. API users may utilize any HTTP client to access the API.

For comprehensive information regarding each API, please refer to the Swagger API documentation.

**Base-Path** : https://[Management Interface IP address]:9443/rest

## 1. Login

The Login API is specifically designed to generate both the access_token and refresh_token. Please refer to the following cURL snippet for invoking the Login API, assuming it is executed from within the UAG virtual machine.

**HTTP request**

```markdown
POST https://[Management Interface IP address]:9443/rest/v1/jwt/login
```

**Input parameters**

| Parameter                         | Mandatory    | Description                                                         |
|-----------------------------------|--------------|---------------------------------------------------------------------|
| Management Interface IP address   | Yes (URL)    | IP of Management interface                                          |
| username                          | Yes (Body)   | Identifies the user                                                 |
| password                          | Yes (Body)   | Admin/Monitoring User password                                      |
| refreshTokenExpiryInHours         | No  (Body)   | Defines the refresh token expiry in hours. Minimum - 3 hours        |
| Accept                            | Yes (Header) | Accept: application/json                                            |
| Content-Type                      | Yes (Header) | Content-Type: application/json                                      |

> Note: The access token will have a time to live value of 2 hours by default. Once the token expires, you will need to get new access token.

To request an access token via shell:

*Request:*

```shell
curl -k -s -i -X 'POST' \
  'https://localhost:9443/rest/v1/jwt/login' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "username": "admin",
  "password": "password",
  "refreshTokenExpiryInHours": 3
}'
```

*Response:*

```json
HTTP/1.1 200 OK
… (other response headers)
  
{
    "access_token": "<access-token>",
    "accessTokenExpiryTime": "<access-token-expiry-timestamp>",
    "refreshToken": "<refresh-token>",
    "refreshTokenExpiryTime": "<refresh-token-expiry-timestamp>"
}
```

## 2. Refresh Token

The Access Token has limited lifetime. If your Token expires, request a new Access Token using the Refresh Token received in Login API response.

**HTTP Request**

```markdown
POST https://[Management Interface IP address]:9443/rest/v1/jwt/refreshToken
```

**Input parameters**

| Parameter                         | Mandatory    | Description                                                         |
|-----------------------------------|--------------|---------------------------------------------------------------------|
| Management Interface IP address   | Yes (URL)    | IP of Management interface                                          |
| refreshToken                      | Yes (Body)   | Refresh token received in Login API response along with access token|
| refreshTokenExpiryInHours         | No  (Body)   | Defines the refresh token expiry in hours. Minimum - 3 hours        |
| Accept                            | Yes (Header) | Accept: application/json                                            |
| Content-Type                      | Yes (Header) | Content-Type: application/json                                      |

To refresh the access token via shell:

*Request:*

```shell
curl -k -s -i -X 'POST' \
  'https://localhost:9443/rest/v1/jwt/refreshToken' \
  -H 'accept: application/json' \
  -H 'Content-Type: application/json' \
  -d '{
  "refreshToken": "<refresh-token>",
  "refreshTokenExpiryInHours": 4
}'
```

*Response:*

```json
HTTP/1.1 200 OK
… (other response headers)
  
{
    "access_token": "<access-token>",
    "accessTokenExpiryTime": "<access-token-expiry-timestamp>",
    "refreshToken": "<refresh-token>",
    "refreshTokenExpiryTime": "<refresh-token-expiry-timestamp>"
}
```

## 3. Logout/Invalidate token

The Invalidate API is designed to revoke the access_token and refresh_token that were previously generated. This process is akin to logging out a user

**HTTP Request**

```markdown
DELETE https://[Management Interface IP address]:9443/rest/v1/jwt/invalidate
```

**Input parameters**

| Parameter                         | Mandatory    | Description                                                         |
|-----------------------------------|--------------|---------------------------------------------------------------------|
| Management Interface IP address   | Yes (URL)    | IP of Management interface                                          |
| Accept                            | Yes (Header) | Accept: \*/\*                                                         |
| Authorization                     | Yes (Header) | Authorization: Bearer <access-token\>                               |

To refresh the access token via shell:

*Request:*

```shell
curl -k -s -i -X 'DELETE' \
  'https://localhost:9443/rest/v1/jwt/invalidate' \
  -H 'accept: */*' \
  -H 'Authorization: Bearer <access-token>'
```

*Response:*

```json
HTTP/1.1 200 OK
… (other response headers)
```
