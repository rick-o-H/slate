---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - shell
  - javascript

toc_footers:
  - <p>HEY TEAM TRUFFLE - Rick</p>
  - <a href='https://github.com/slatedocs/slate'>Documentation Powered by Slate</a>

includes:
  - errors

search: true

code_clipboard: true
---

# Introduction

Welcome to the Hungry Bunch API! This API exposes the various ways you can interact with the back-end of the application.

The purpose of this documentation is to provide information about the following:
  - Endpoint names & descriptions
  - Parameter names, descriptions, & types
  - Example requests & responses
  - Status codes

Example requests in Shell and JavaScript using the axios library!


# Users

## Get a User

```shell
curl "http://localhost:3000/userInfo/itsme123" \
  -X GET \
```

```javascript
const axios = require('axios');

axios.get('http://localhost:3000/userInfo/itsme123');
```

> The above command returns JSON structured like this:

```json
{
  "_id": "itsme123",
  "username": "Max",
  "name": "unknown",
  "picture": "https://images.unsplash.com/photo-1476718406336-bb5a9690ee2a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80",
  "updated_at": "2020-12-29T21:28:15.625Z",
  "email": "frostedDonut123@gmail.com",
  "recipes": [
    {
      "owner": "itsme123",
      "recipeName": "Soupie Soup",
      "category": ["Dinner", "Soup"],
      "rating": 3.5,
      "shared": "Only me",
      "ingredients": ["carrot", "celery", "onion", "basil", "salt", "pepper", "potato", "tomato", "chicken broth"],
      "time": 45,
      "difficulty": "Easy",
      "favoritedBy": [2],
      "vegan": false,
      "steps": ["Chop veggies", "Combine in pot", "Add salt and pepper to taste", "Mix the rest of the ingredients", "Cook on stove for 25 min"],
      "imageUrl": "https://images.unsplash.com/photo-1476718406336-bb5a9690ee2a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80"
    },
    {
      "..."
    },
  ],
  "favoriteRecipes": ["array of recipe objects"],
  "friends": [
    {
      "_id": "friend234543",
      "username": "friendlyFriend",
      "name": "Mr.Friend",
      "..."
    }
  ]
}
```

This endpoint retrieves a specific user.

### HTTP Request

`GET http://localhost:3000/userInfo/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The id of the user to retrieve. This will eventually be available in the Redux store for the logged-in user.


<aside class="success">
The author of these docs is looking for a job :)
e-mail: rickhawley109@gmail.com
</aside>

## Add a User

```shell
curl "http://localhost:3000/addUser" \
  -X POST \
```

```javascript
const axios = require("axios");

axios.post("http://localhost:3000/addUser", {
  "username": "woolSocks",
  "name": "warm",
  "picture": "https://s.gravatar.com/avatar/6e785eb0726d6552198006f3bc03d4f6?s=480&r=pg&d=https%3A%2F%2Fcdn.auth0.com%2Favatars%2Fri.png"
  "updated_at": "2020-12-29T21:28:15.625Z",
  "email": "myFeetAreWarm@test.com"
});
```

> The above command returns JSON structured like this:

```json
{
  "_id": "DJFKVN324JSFK",
  "username": "woolSocks",
  "name": "warm",
  "picture": "https://s.gravatar.com/avatar/6e785eb0726d6552198006f3bc03d4f6?s=480&r=pg&d=https%3A%2F%2Fcdn.auth0.com%2Favatars%2Fri.png",
  "updated_at": "2020-12-29T21:28:15.625Z",
  "email": "myFeetAreWarm@test.com",
  "recipes": [],
  "favoriteRecipes": [],
  "friends": []
}
```

This endpoint adds a new user to the database and returns the newly added user.

### HTTP Request

`POST http://localhost:3000/addUser`

### Request Body

Field | Type | Description
----- | ---- | -----------
username | String | The username of the user.
name | String | The name of the user.
picture | String | The url of the users profile picture.
updated_at | String | Timestamp of when the user signed up.
email | String | The email of the user.

# Recipes

```shell
curl "http://localhost:3000/addRecipe" \
  -X POST \
```

```javascript
const axios = require("axios");

/* COMING SOON */

```

## Add a Recipe
This endpoint adds a new recipe for a specific user.

### HTTP Request

`POST http://localhost:3000/addRecipe`

### Request Body

Field | Type | Description
----- | ---- | -----------
id | String | The id of the user.
recipe | Object | The recipe object to add.



