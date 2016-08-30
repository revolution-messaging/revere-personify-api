# Revere Personify API

This describes the resources that make up the official Revere Personify API. If you have any problems or requests please contact vip@revolutionmessaging.com.

All API access is over HTTPS, and accessed from the one of the domains listed below under the base endpoint section. All data payloads are sent and received as JSON unless otherwise noted.

***

Topics

- [Current Version](#current-version)
- [Authentication](#authentication)
- [Base Endpoint](#base-endpoint)
- [API Endpoints](#api-endpoints)

***

## Current Version

By default, all requests receive the v1 version of the API. We encourage you to explicitly request this version via the Accept header.

```
Accept: application/vnd.revere-personify-v1+json
```

***

## Authentication

All API endpoints are protected via an API key. API keys are distributed on a per client account basis, meaning every client account is allowed one active API key unless noted otherwise. API keys need to be sent in via the X-Auth-Token request header.

```
X-Auth-Token: 47bcd71c5991338eb48cf935f87e46ce
```

***

## Base Endpoint

Production

```
https://personify.reverehq.com/api
```

Staging

```
https://stagingpersonify.reverehq.com/api
```

***

## API Endpoints

Click on an API endpoint for more detailed information.

#### Uploads Resources

- GET /uploads/new
- POST /uploads
