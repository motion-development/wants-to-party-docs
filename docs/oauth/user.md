# User endpoints
These endpoints can be used if you recieve user data from a complete [oauth](/developers/docs/oauth) cycle.

<br>

## **GET** `/api/user`
Endpoint is used to get a users info. This will return a user object on success.
##### Example response
```json
{
  "user_id":1,                            // Only included with the user.read scope
  "user_name":"tech",                     // Only included with the user.read scope
  "email":"tech@motiondevelopment.top",   // Only included with the user.email scope
  "message":"ok"
}
```

<br>

## **GET** `/api/user/files`
Allowes you to see all the files the user uploads. This endpoint will only return the first 1000 files the user have uploaded.
**The `files.read` scope is required for this endpoint!**
##### Example response
```json
{
  "message": "ok", 
  "files": [...]
}
```
##### Example file object
```json
{
    "name": "12345.png",
    "extension": "png",
    "filename": "12345",
    "uploaded_at": 1633298777,
    "url": "https://tech.wants-to.party/12345.png"
}
```

<br>

## **POST** `/api/user/files`
Allowes you to upload files on the users behave. This required a `file` to be presend in the request.
**The `files.write` scope is required for this endpoint!**
##### Example response
```json
{
  "message": "ok", 
  "url": url
}
```

<br>

## **DELETE** `/api/user/files/:file_id`
Allowes you to delete a file on the users behave. The `file_id` is required in the url. The `file_id` must include the extension.
**The `files.delete` scope is required for this endpoint!**
