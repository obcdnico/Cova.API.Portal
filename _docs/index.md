---
title: Getting started with Cova APIs
permalink: /docs/home/
redirect_from: /docs/index.html
---
   
      
	  


![alt text](https://www.covasoftware.com/hs-fs/hubfs/Covasoft%20Jan2017/Images/cova_horiz_2col_tagline.png?t=1532104854154&width=1021&name=cova_horiz_2col_tagline.png "Logo Title Text 1")&nbsp;  

   
      
	  


COVA APIs are simple but powerful HTTP interfaces that are inspired by the REST architectural style. These are the same APIs that our internal development teams use to build products.

We are passionate about creating a great developer experience for you so please don’t hesitate to contact our API Support Team at apisupport@covasoftware.com with any feedback related to API design, usability, or features that you are interested to see.

# Onboarding Package

As part of the onboarding process, you will receive an onboarding package from the COVA API team.

This package provides you with credentials required to access COVA APIs.

If you need an onboarding package, contact apisupport@covasoftware.com

# Overview

In order to make authorized requests to COVA APIs, your application must first obtain an Access Token.
# Authentication
COVA APIs are protected by OAuth2.

# Rate Limiting

Requests to the COVA APIs are limited to help to manage server load, ensuring that high API request volumes do not impact overall performance.

They also help to protect from deliberate or accidental denial of service as a result of APIs being flooded with requests.

If you run into the 429 Too Many Requests error, please contact support.

## Rate Limit Policies
All rate limits are applied per service, not aggregated across all services.

There are three rate limit policies that are applied to the APIs.

## Authenticated Limit

The Authenticated Limit policy determines how many Authenticated Requests can be made during the Rate Limit Window.

Authenticated Requests are made to COVA APIs that require authentication, and include an in the HTTP Header.

To determine the limit, make an Authenticated Request to an COVA API, then check the X-RateLimit-Limit HTTP Header of the response.

## Anonymous Limit

The Anonymous Limit policy determines how many Anonymous Requests can be made during the Rate Limit Window.

Anonymous Requests are made to COVA APIs that do not require authentication.

To determine the limit, make an Anonymous Request to an COVA API, then check the X-RateLimit-Limit HTTP Header of the response.

## Rate Limit Window
The Rate Limit Window policy determines when the current rate limit will be reset.

To determine the limit, make a request to an COVA API, then check the X-RateLimit-Reset HTTP Header of the response.

## HTTP Headers
All responses from the COVA API’s have the following headers, which provide information about how many requests are remaining.

## HEADER NAME	DESCRIPTION
>X-RateLimit-Limit	The maximum number of requests allowed in the current rate limit window
X-RateLimit-Remaining	The number of requests remaining in the current rate limit window
X-RateLimit-Reset	The time when the rate limit window will reset in UTC
X-RateLimit-ResetSeconds	The number of seconds until the rate limit resets

## Checking a Rate Limit
To determine the Authenticated Rate Limit for an API, make an authenticated request to the API and check the HTTP headers in the response.

In the example below, a request is made to the Customers API with a valid in the Authorization header.

Example Request

>GET https://crmdemo.COVA.net/v1/Companies(14146)/Customers
Authorization: Bearer (Access Token)
Accept: application/json

Example Response

>HTTP 200 Content-Type: application/json
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 999
X-RateLimit-Reset: 2016-02-25T13:00:00.0000000Z
X-RateLimit-ResetSeconds: 59
{
    ...
}

Looking at the HTTP headers in the response, we can determine:

>Our rate limit window ends in 59 seconds or at precisely 2016-02-25T13:00:00.0000000Z UTC
In the next 59 seconds we can make 999 more requests
In 59 seconds, or at 2016-02-25T13:00:00.0000000Z UTC, the counter will reset and we will be able to make another 1000 requests


## Exceeding Rate Limit
If the rate limit is exceeded, the response will be 429 Too Many Requests and the service will not be able to make further requests until the quota resets.

Example

>HTTP/1.1 429 Too Many Requests
Content-Type: text/plain
X-RateLimit-Limit: 1000
X-RateLimit-Remaining: 0
X-RateLimit-Reset: 2015-04-16T17:46:00.0000000Z
X-RateLimit-ResetSeconds: 59
  
rate limit exceeded

# Supported Response Formats

Most COVA APIs support the json and hal+json response formats depending on the type of request. Documentation for each individual API will explicitly state which response formats are supported.

When sending an API request, you can select the format to return by defining the value in the HTTP Accept header, using the syntax Accept: {ResponseFormat}.

Example
>Accept: application/json

# Versioning
The API version is shown in the endpoint’s URL (e.g. /v1). Newer API versions will be highlighted in their respective API reference documentation.

Should there be a breaking change to an existing API, COVA will trigger a release of a newer version and notify stakeholders. Please take note that not all API versions will be backward compatible.
