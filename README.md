# Revere Personify API

This describes the resources that make up the official Revere Personify API. If you have any problems or requests please contact vip@revolutionmessaging.com.

All API access is over HTTPS, and accessed from the one of the domains listed below under the base endpoint section. All data payloads are sent and received as JSON unless otherwise noted.

***

Topics

- [Current Version](#current-version)
- [Authentication](#authentication)
- [Base Endpoint](#base-endpoint)
- [API Endpoints](#api-endpoints)
- [File Uploads](#file-uploads)

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

- [**`GET` /uploads/new**](https://github.com/revolution-messaging/revere-personify-api/blob/master/api_endpoints/GET_uploads_new.md)
- [**`POST` /uploads**](https://github.com/revolution-messaging/revere-personify-api/blob/master/api_endpoints/POST_uploads.md)

***

## File Uploads

Revere Personify **does not** store uploaded files to the local file system. This allows bigger files to be uploaded directly to Amazon for faster upload speed, and performance.

#### What is a pre-signed URL?

A pre-signed URL is Amazon's way to allow direct file uploads to S3 from any origin. Pre-signed URLs require a list of key/value pairs to be sent along with the file upload to verify the upload source.

#### How do I use uploads with Revere Personify?

Uploading files to Revere Personify is a three step process. It's important to understand each process to ensure your uploads are successfully stored to Amazon and reported to Revere Personify.

**Step 1 &mdash; Request the URL and fields**

Make a request to the `/uploads/new` endpoint to retrieve a URL and security credentials.

**Step 2 &mdash; Upload the file to S3**

Upload the file to the URL from the `/uploads/new` endpoint. When constructing the request make sure to send the `fields` key/value pairs along with the file to be uploaded. The file field needs to use the `file` param name. Below is an example of using CURL for the file upload.

```
curl -X "POST" "https://revere-personify.s3.amazonaws.com/" \
  -H "Content-Type: multipart/form-data; charset=utf-8;" \
  -F "policy=eyJleHBpcmF0aW9uIjoiMjAxNi0wOC0zMFQxODowNDowNVoiLCJjb25kaXRpb25zIjpbeyJidWNrZXQiOiJyZXZlcmUtcGVyc29uaWZ5LWRldmVsb3BtZW50In0seyJrZXkiOiJ1cGxvYWRzL2JlNjFlYzQwYmNiNzUxNDljZWE3ODJlZjZlMDE1MzJhLzIwMTYvMTQ3MjU3NjY0NTAwMC5jc3YifSx7InN1Y2Nlc3NfYWN0aW9uX3N0YXR1cyI6IjIwMSJ9LHsiYWNsIjoicHVibGljLXJlYWQifSx7IngtYW16LWNyZWRlbnRpYWwiOiJBS0lBSVI1UERSVUJSWjdYVjIyUS8yMDE2MDgzMC91cy1lYXN0LTEvczMvYXdzNF9yZXF1ZXN0In0seyJ4LWFtei1hbGdvcml0aG0iOiJBV1M0LUhNQUMtU0hBMjU2In0seyJ4LWFtei1kYXRlIjoiMjAxNjA4MzBUMTcwNDA1WiJ9XX0=" \
  -F "x-amz-signature=2562e9f2fb825cb7685d2d969d8bbd753deb11fec0425ea3b75f0d9474dc24b3" \
  -F "success_action_status=201" \
  -F "acl=public_read" \
  -F "x-amz-algorithm=AWS4-HMAC-SHA256" \
  -F "key=uploads/be61ec40bcb75149cea782ef6e01532a/2016/1472576645000.csv" \
  -F "file=member_id,msisdn,first_name,last_name,suffix,email,address,city,state,postal_code,postal_code_plus_4,afge_local,agency,afge_district,political_party,gender,congressional_district,retired,veteran,permission_to_text,permission_to_call_mobile,permission_to_text_confirmed_at,permission_to_call_mobile_confirmed_at
dc1b75d5-abfa-43cf-8a87-8c46247925a4,+7676060152,Zelma,Kulas,DDS,adrain@sanfordwilliamson.info,57913 Prohaska Trafficway,Claudefort,wa,86658,3320,65-5504230,Kuhlman-Fisher,24-2998185,green,female,682,false,true,false,false,2016-05-24T02:07:38Z,2016-05-25T01:26:14Z
b32865f0-4d0a-42e9-916c-bd85ef0332c3,+9510872181,Tyrel,Jakubowski,Sr.,nasir_berge@schuster.io,95447 Wilson Greens,North Sallie,me,80589,7530,61-0215689,\"Daugherty, King and Schuster\",49-6812064,green,female,87,true,false,true,true,2016-05-20T12:04:05Z,2016-05-24T23:23:52Z
769b3a82-cbaa-4cd1-8d17-3b26b1ebd721,+6294798344,Jarrell,Towne,I,dane@donnelly.net,234 Wuckert Brooks,Port Estelfort,ma,96987,2622,99-7956478,Johns LLC,59-9005734,independent,male,570,true,true,true,false,2016-05-24T13:26:14Z,2016-05-24T21:41:14Z
9c8a1199-3a05-41a7-ae7c-85a0127a0676,+9941917162,Adrain,Monahan,IV,orpha_wunsch@turner.info,87897 Barbara Plains,Stantonland,tx,24106,7493,91-1093179,\"Ruecker, Littel and Zboncak\",53-2599878,green,male,155,true,true,false,false,2016-05-25T14:52:08Z,2016-05-25T03:54:09Z
fe4b7424-1785-44a2-94ee-76a5fe746d0c,+7306827348,Layne,Smitham,II,raymundo@kutch.com,466 Douglas Station,Lake Lysanne,ca,43535,7487,28-7670206,\"Hills, Quigley and Simonis\",27-6810844,independent,male,422,true,false,true,true,2016-05-22T01:57:13Z,2016-05-25T15:52:30Z
" \
  -F "x-amz-credential=AKIAIR5PDRUBRZ7XV22Q/20160830/us-east-1/s3/aws4_request" \
  -F "x-amz-date=20160830T170405Z"
```

**Step 3 &mdash; Create the upload**

Upon a successful file upload to Amazon, you'll get an XML response that looks like the following:

```xml
<PostResponse>
  <Location>https://revere-personify.s3.amazonaws.com/uploads%2Fbe61ec40bcb75149cea782ef6e01532a%2F2016%2F1472576645000.csv</Location>
  <Bucket>revere-personify-development</Bucket>
  <Key>uploads/be61ec40bcb75149cea782ef6e01532a/2016/1472576645000.csv</Key>
  <ETag>"6cb34290b4cc5bd37ccfe895f02587ce"</ETag>
</PostResponse>
```

Use the value of the `<Key>` to send the correct `file_name` to Revere Personify using the `POST /uploads` endpoint. If you do not send the value exactly as it is returned from Amazon, the file will not be parsed and processed.
