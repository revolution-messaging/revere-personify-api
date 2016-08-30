# Uploads Resource

```
POST /uploads
```

## Description

Creates a new upload.

***

## Parameters

None

***

## Attributes

All attributes need to be sent in an `upload` object. See example request below for more details.

- **file_name** [String] &mdash; File key returned by Amazon after a successful file upload.

***

## Return format

An `upload` object with the following attributes:

- **id** [String] &mdash; ID of the upload resource.
- **status** [String] &mdash; File status of the upload.
- **file_name** [String] &mdash; File name of the upload.

For more information on uploading files directly to Amazon S3 check out the [file uploads section](https://github.com/revolution-messaging/revere-personify-api/blob/master/README.md#file-uploads) of the main Revere Personify API docs.

***

## Errors

- **422 Unprocessable Entity** &mdash; The system had trouble saving the record. Check response for error messages.

***

## Example

**Request** &mdash; Create upload (application/json)

```
POST /uploads
```

```json
{
  "upload": {
    "file_name": "1472573003000.csv"
  }
}
```

**Response** 201 (application/json)

```json
{
  "upload": {
    "id": "eb45ccbc-b581-47f3-b9bf-ae4b585d69c8",
    "status": "uploaded",
    "file_name": "1472573003000.csv",
    "created_at": "2016-08-30T15:59:34Z",
    "updated_at": "2016-08-30T15:59:34Z"
  }
}
```
