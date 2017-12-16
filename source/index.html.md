---
title: Idea Box

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript

toc_footers:
  - <a href='#'>Sign Up for a Developer Key</a>
  - <a href='https://github.com/lord/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true
---

# Introduction

Welcome to Idea Box! Ideabox is a simple application that allows users to create a pool of ideas and promote collaboration. It has the following features:

* Creating an account
* Signing in a registered user
* Reset Password
* Edit user profile
* Create an Idea
* Edit an Idea
* Delete an Idea
* Comment on an Idea
* Reset password email
* Search for Idea
* Filter for ideas by category

# Authentication

## Sign-up

> Request Body:

```javascript
{
  {
    "firstname": "Ife",
    "lastname": "Tomiwa",
    "email": "tomiwa@gmail.com",
    "password": "Welcome3000#"
  }
}
```

> Sample Response:

```javascript
{
  {
    "user": {
        "userId": "5a35197c4ac189151504dc2c",
        "firstname": "funsho",
        "lastname": "ajayi",
        "email": "funso@andela.com",
        "token": ""
    },
    "message": "Signup successful",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiI1YTM1MTk3YzRhYzE4OTE1MTUwNGRjMmMiLCJlbWFpbCI6ImZ1bnNvQGFuZGVsYS5jb20iLCJpYXQiOjE1MTM0MjkzNzIsImV4cCI6MTUxMzU3MzgxNn0.B8-bRncbepKkxpp9BNUsA0Qit9n03hZ1SmeLbkibBxo"
  }
}
```

`**Sign-up[POST - /api/v1/user/signup]**`

This endpoint creates a new user

`**onSuccess - Status Code [201]**`
`**onError - Status Code [400, 409, 500]**`

## Sign-in

> Request Body:

```javascript
{
  {
    "firstname": "funsho",
    "lastname": "ajayi",
    "email": "funso@andela.com",
    "password": "Welcome3000#"
  }
}
```

> Sample Response:

```javascript
{
    "user": {
        "userId": "5a35197c4ac189151504dc2c",
        "firstname": "funsho",
        "lastname": "ajayi",
        "email": "funso@andela.com"
    },
    "message": "Login Successful",
    "token": "eyJhbGciOiJIUzI1NiIsInR5cCI6IkpXVCJ9.eyJ1c2VySWQiOiI1YTM1MTk3YzRhYzE4OTE1MTUwNGRjMmMiLCJlbWFpbCI6ImZ1bnNvQGFuZGVsYS5jb20iLCJpYXQiOjE1MTM0MzAzMzAsImV4cCI6MTUxMzU3NDc3NH0.gRBBuxw-xpCQ32TEDLg2ia7c10ka8MVDXLKjmDRienY"
}
```

`**Sign-in[POST - /api/v1/user/login]**`

This endpoint verifies if a user is registered and then logs the user if verified or throws the appropriate error if not verified. You can login with email

`**onSuccess - Status Code [200]**`
`**onError - Status Code [400, 401, 404, 500]**`

## Update Profile

> Request Body:

```javascript
{
  {
    "firstname": "funsho",
    "lastname": "Ajayi",
    "email": "funso@andela.com",
    "password": "Welcome3000#"
  }
}
```

> Sample Response:

```javascript
{
    "user": {
        "userId": "5a35197c4ac189151504dc2c",
        "firstname": "funsho",
        "lastname": "Ajayi",
        "email": "funso@andela.com"
    },
    "message": 'Your profile was updated successfully',,
}
```

`**Update Profile [PUT - /api/v1/user]**`

This endpoint updates a user profile

`**onSuccess - Status Code [200]**`
`**onError - Status Code [400, 404, 500]**`

## Forgot Password

> Request Body:

```javascript
{
  {
    "email": "funso@andela.com",
  }
}
```

> Sample Response:

```javascript
{
    "message": 'Check your email to continue resetting your password',,
}
```

`**Forgot Password [POST - /api/v1/resetpassword]**`

This endpoint generates a token and sends a reset link to the user via email

`**onSuccess - Status Code [200]**`
`**onError - Status Code [400, 404, 500]**`

## Reset Password

> Request Body:

```javascript
{
  {
    "email": "funso@andela.com",
  }
}
```

> Sample Response:

```javascript
{
    "message": 'Check your email to continue resetting your password',,
}
```

`**Forgot Password [PUT - /api/v1/resetpassword]**`

Upon reception of an email to reset password, this method receives the new password entered by the user and replaces the user's old password with the new one

`**onSuccess - Status Code [200]**`
`**onError - Status Code [400, 500]**`

# Ideas

## Post an Idea

```javascript
{
   {
      "title": "Woman Abused",
      description: "So Many woman in africa are sexually abused",
      category: "engineering",
      ideaType: "Public",
      user: "5a35197c4ac189151504dc2c",
      modified: false,
   }
}
```

> Sample Response:

```javascript
{
    "newIdea": {
        "ideaId": "5a352870327a6e175d8232f1",
        "title": "Woman Abused",
        "description": "So Many woman in africa are sexually abused",
        "type": "Public",
        "userId": "5a35197c4ac189151504dc2c"
    },
    "message": "Idea created successfully"
}
```

This endpoint retrieves a specific idea.

### HTTP Request

`POST /api/v1/idea`

`**onSuccess - Status Code [201]**`
`**onError - Status Code [409, 500]**`

## Get All Ideas

```javascript
const kittn = require('kittn');

let api = kittn.authorize('meowmeowmeow');
let kittens = api.kittens.get();
```

> Sample Response:

```json
{
  "ideas": [
    {
      "_id": "5a35280add91fb174dcce01e",
      "title": "Help Help help",
      "description": "A study of Helpers hhk",
      "category": "Engineering",
      "user": {
        "_id": "5a35197c4ac189151504dc2c",
        "firstname": "funsho",
        "lastname": "ajayi",
        "email": "funso@andela.com",
        "password":
          "$2a$10$Sji81NvHqSaKPI1VH1FTw.UVea.EUB6XXOEc0NMzFDfE1Ka0TelSu",
        "token": "",
        "__v": 0,
        "updatedAt": "2017-12-16T13:02:52.690Z",
        "createdAt": "2017-12-16T13:02:52.690Z"
      },
      "modified": false,
      "__v": 0,
      "updatedAt": "2017-12-16T14:04:58.069Z",
      "createdAt": "2017-12-16T14:04:58.069Z",
      "ideaType": "Public"
    },
    {
      "_id": "5a352870327a6e175d8232f1",
      "title": "Woman Abused",
      "description": "So Many woman in africa are sexually abused",
      "category": "engineering",
      "user": {
        "_id": "5a35197c4ac189151504dc2c",
        "firstname": "funsho",
        "lastname": "ajayi",
        "email": "funso@andela.com",
        "password":
          "$2a$10$Sji81NvHqSaKPI1VH1FTw.UVea.EUB6XXOEc0NMzFDfE1Ka0TelSu",
        "token": "",
        "__v": 0,
        "updatedAt": "2017-12-16T13:02:52.690Z",
        "createdAt": "2017-12-16T13:02:52.690Z"
      },
      "modified": false,
      "__v": 0,
      "updatedAt": "2017-12-16T14:06:40.895Z",
      "createdAt": "2017-12-16T14:06:40.895Z",
      "ideaType": "Public"
    }
  ]
}
```

This endpoint retrieves all ideas.

### HTTP Request

`GET /api/v1/ideas`

## Get a Specific idea

> The above command returns JSON structured like this:

```json
{
  "_id": "5a352870327a6e175d8232f1",
  "title": "Woman Abused",
  "description": "So Many woman in africa are sexually abused",
  "category": "engineering",
  "user": {
    "_id": "5a35197c4ac189151504dc2c",
    "firstname": "funsho",
    "lastname": "ajayi",
    "email": "funso@andela.com",
    "password": "$2a$10$Sji81NvHqSaKPI1VH1FTw.UVea.EUB6XXOEc0NMzFDfE1Ka0TelSu",
    "token": "",
    "__v": 0,
    "updatedAt": "2017-12-16T13:02:52.690Z",
    "createdAt": "2017-12-16T13:02:52.690Z"
  },
  "modified": false,
  "__v": 0,
  "updatedAt": "2017-12-16T14:06:40.895Z",
  "createdAt": "2017-12-16T14:06:40.895Z",
  "ideaType": "Public"
}
```

This endpoint retrieves a specific idea.

### HTTP Request

`GET /api/v1/idea/<ID>`

### URL Parameters

| Parameter | Description                    |
| --------- | ------------------------------ |
| ID        | The ID of the idea to retrieve |

## Delete a Specific Idea

> Response:

```json
{
  "message": "Idea successfully deleted"
}
```

This endpoint deletes a specific Idea.

### HTTP Request

`DELETE api/v1/idea/<ID>`

### URL Parameters

| Parameter | Description                  |
| --------- | ---------------------------- |
| ID        | The ID of the idea to delete |
