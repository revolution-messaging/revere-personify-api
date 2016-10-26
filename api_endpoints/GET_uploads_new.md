# Uploads Resource

```
GET /uploads/new
```

## Description

Returns a pre-signed URL and credentials for uploading files directly to Amazon S3. Uploaded files can then be submitted to be reviewed and queued for processing.

***

## Parameters

None

***

## Attributes

None

***

## Return format

Both a URL and fields object with the following attributes:

- **url** [String] &mdash; Amazon S3 bucket URL the file will be uploaded to.
- **fields** [Object] &mdash; List of key/value pairs that must be sent with the file upload request.

For more information on uploading files directly to Amazon S3 check out the [file uploads section](https://github.com/revolution-messaging/revere-personify-api/blob/master/README.md#file-uploads) of the main Revere Personify API docs.

***

## Errors

None

***

## Example

**Request** (application/json)

```
GET /uploads/new
```

**Response** 201 (application/json)

```json
{
  "url": "https://revere-personify.s3.amazonaws.com",
  "fields": {
    "key": "uploads/1e5c83b22223ab2a9848b01833129916/2016/1472570946.3263416.csv",
    "success_action_status": "201",
    "acl": "public-read",
    "policy": "eyJleHBpcmF0aW9uIjoiMjAxNi0wOC0zMFQxNjoyOTowNloiLCJjb25kaXRpb25zIjpbeyJidWNrZXQiOiJyZXZlcmUtcGVyc29uaWZ5LWRldmVsb3BtZW50In0seyJrZXkiOiJ1cGxvYWRzLzFlNWM4M2IyMjIyM2FiMmE5ODQ4YjAxODMzMTI5OTE2LzIwMTYvMTQ3MjU3MDk0Ni4zMjYzNDE2LmNzdiJ9LHsic3VjY2Vzc19hY3Rpb25fc3RhdHVzIjoiMjAxIn0seyJhY2wiOiJwdWJsaWMtcmVhZCJ9LHsieC1hbXotY3JlZGVudGlhbCI6IkFLSUFJUjVQRFJVQlJaN1hWMjJRLzIwMTYwODMwL3VzLWVhc3QtMS9zMy9hd3M0X3JlcXVlc3QifSx7IngtYW16LWFsZ29yaXRobSI6IkFXUzQtSE1BQy1TSEEyNTYifSx7IngtYW16LWRhdGUiOiIyMDE2MDgzMFQxNTI5MDZaIn1dfQ==",
    "x-amz-credential": "AKIAIR5PDRUBRZ7XV22Q/20160830/us-east-1/s3/aws4_request",
    "x-amz-algorithm": "AWS4-HMAC-SHA256",
    "x-amz-date": "20160830T152906Z",
    "x-amz-signature": "945806c0aa5a381f8cb183640c958ebdeefdc2d71c9456eba826a8706c2ad7cf"
  }
}
```
