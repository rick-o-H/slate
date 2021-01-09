---
title: API Reference

language_tabs: # must be one of https://git.io/vQNgJ
  - javascript
  - shell

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

## Get a user

```shell
curl "http://localhost:3000/userInfo/5ff4903962127775787d7d8f" \
  -X GET \
```

```javascript
const axios = require('axios');

axios.get('http://localhost:3000/userInfo/5ff4903962127775787d7d8f');
```

> The above command returns JSON structured like this:

```json
{
  "_id": "5ff4903962127775787d7d8f",
  "username": "Rick",
  "name": "Rick",
  "picture": "https://images.unsplash.com/photo-1476718406336-bb5a9690ee2a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80",
  "updated_at": "2020-12-29T21:28:15.625Z",
  "email": "frostedDonut123@gmail.com",
  "recipes": [
    {
      "owner": "5ff4903962127775787d7d8f",
      "recipeName": "Soupie Soup",
      "category": ["Dinner", "Soup"],
      "rating": 3.5,
      "shared": "Only me",
      "ingredients": ["carrot", "celery", "onion", "basil", "salt", "pepper", "potato", "tomato", "chicken broth"],
      "time": 45,
      "difficulty": "Easy",
      "favoritedBy": ["5ff4f75dc00ca596bc43dae1"],
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
id | The id of the user to retrieve.


<aside class="success">
The author of these docs is looking for a job :)
e-mail: rickhawley109@gmail.com
</aside>

## Check and add user

```shell
curl "http://localhost:3000/checkUser" \
  -X POST \
```

```javascript
const axios = require("axios");

axios.post("http://localhost:3000/checkUser", {
  "username": "woolSocks",
  "name": "warm",
  "picture": "https://s.gravatar.com/avatar/6e785eb0726d6552198006f3bc03d4f6?s=480&r=pg&d=https%3A%2F%2Fcdn.auth0.com%2Favatars%2Fri.png"
  "updated_at": "2020-12-29T21:28:15.625Z",
  "email": "myFeetAreWarm@test.com"
  "sub":
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
  "friends": [],
  "sub": "116155093460479402279"
}
```

This endpoint checks if a exists in the database, adds a new user to the database if they do not, and returns that user.

### HTTP Request

`POST http://localhost:3000/checkUser`

### Request Body

Field | Type | Description
----- | ---- | -----------
username | String | The username of the user.
name | String | The name of the user.
picture | String | The url of the users profile picture.
updated_at | String | Timestamp of when the user signed up.
email | String | The email of the user.
sub | String | The auth identifier of the user.

# Recipes

## Get a recipe

```shell
curl "http://localhost:3000/recipe/5ff6295bfbf23f210dad6ffb" \
  -X GET \
```

```javascript
const axios = require('axios');

axios.get('http://localhost:3000/recipe/5ff6295bfbf23f210dad6ffb');
```

> The above command returns JSON structured like this:

```json
{
    "ingredients": [
        "ice cream",
        "ice cream"
    ],
    "favoritedBy": [],
    "steps": [
        "scoop",
        "eat"
    ],
    "_id": "5ff6295bfbf23f210dad6ffb",
    "owner": "5ff4903962127775787d7d8f",
    "recipeName": "ice cream",
    "category": "breakfast",
    "shared": "Friends",
    "time": 1,
    "difficulty": "expert",
    "vegan": false,
    "imageUrl": "https://images.unsplash.com/photo-1476718406336-bb5a9690ee2a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80",
    "__v": 0
}
```

This endpoint retrieves a specific recipe.

### HTTP Request

`GET http://localhost:3000/recipe/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The id of the recipe to retrieve.

## Get all recipes for a specific user

```shell
curl "http://localhost:3000/userRecipes/5ff6295bfbf23f210dad6ffb" \
  -X GET \
```

```javascript
const axios = require('axios');

axios.get('http://localhost:3000/userRecipes/5ff6295bfbf23f210dad6ffb');
```

> The above command returns JSON structured like this:

```json
[
  {
    "ingredients": [
        "carrot",
        "celery",
        "onion",
        "basil",
        "salt",
        "pepper",
        "potato",
        "tomato",
        "chicken broth"
    ],
    "favoritedBy": [],
    "steps": [
        "Chop veggies",
        "Combine in pot",
        "Add salt and pepper to taste",
        "Mix the rest of the ingredients",
        "Cook on stove for 25 min"
    ],
    "_id": "5ff497858240870659b5889e",
    "owner": "5ff4903962127775787d7d8f",
    "recipeName": "Soupie Soup",
    "shared": "Only me",
    "time": 45,
    "difficulty": "Easy",
    "vegan": false,
    "imageUrl": "https://images.unsplash.com/photo-1476718406336-bb5a9690ee2a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80",
    "__v": 0
  },
  {
    "ingredients": [
        "Fish",
        "Chips"
    ],
    "favoritedBy": [],
    "steps": [
        "Fry the fish to golden brown on medium frying pan",
        "Make the chips",
        "Enjoy!"
    ],
    "_id": "5ff4a03da290d60695f324d1",
    "owner": "5ff4903962127775787d7d8f",
    "recipeName": "Fish and Chips",
    "shared": "Everyone",
    "time": 30,
    "difficulty": "Easy",
    "vegan": false,
    "imageUrl": "",
    "__v": 0
  },
  {
    "ingredients": [
        "Ribs",
        "BBQ sauce",
        "Salt",
        "Pepper"
    ],
    "favoritedBy": [],
    "steps": [
        "Cover ribs in BBQ sauce",
        "Add salt and pepper",
        "Smoke for 6 hours"
    ],
    "_id": "5ff4af204d815706c118db00",
    "owner": "5ff4903962127775787d7d8f",
    "recipeName": "Ribs",
    "shared": "Everyone",
    "time": 300,
    "difficulty": "Medium",
    "vegan": false,
    "imageUrl": "https://images.unsplash.com/photo-1476718406336-bb5a9690ee2a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80",
    "__v": 0
  },
  {
    "ingredients": [
        "Ground Beef",
        "Burger Bun",
        "Ketchup",
        "Mustard",
        "Tomato",
        "Onion"
    ],
    "favoritedBy": [],
    "steps": [
        "Flatten ground beef into burger patties",
        "Grill until fully cooked",
        "Add desired toppings"
    ],
    "_id": "5ff4afd54d815706c118db01",
    "owner": "5ff4903962127775787d7d8f",
    "recipeName": "Burger",
    "shared": "Everyone",
    "time": 45,
    "difficulty": "Easy",
    "vegan": false,
    "imageUrl": "https://images.unsplash.com/photo-1476718406336-bb5a9690ee2a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80",
    "__v": 0
  },
]
```

This endpoint retrieves all recipes that belong to a specific user.

### HTTP Request

`GET http://localhost:3000//userRecipes/:id`

### URL Parameters

Parameter | Description
--------- | -----------
id | The id of the user.


## Get all recipes

```shell
curl "http://localhost:3000/allRecipes" \
  -X GET \
```

```javascript
const axios = require('axios');

axios.get('http://localhost:3000/allRecipes');
```

> The above command returns JSON structured like this:

```json
[
    {
        "ingredients": [
            "pepper",
            "pasta",
            "salt",
            "butter",
            "sauce"
        ],
        "favoritedBy": [],
        "steps": [
            "do something",
            "then something"
        ],
        "_id": "5ff25a515e53a4ccb1d12e75",
        "owner": "5ff250aeabc667cae1ca4882",
        "recipeName": "PASTA YO",
        "shared": "yes",
        "time": 60,
        "difficulty": "EASY",
        "vegan": true,
        "imageUrl": "https://s.gravatar.com/avatar/6e785eb0726d6552198006f3bc03d4f6?s=480&r=pg&d=https%3A%2F%2Fcdn.auth0.com%2Favatars%2Fri.png",
        "__v": 0
    },
    {
        "ingredients": [
            "carrot",
            "celery",
            "onion",
            "basil",
            "salt",
            "pepper",
            "potato",
            "tomato",
            "chicken broth"
        ],
        "favoritedBy": [],
        "steps": [
            "Chop veggies",
            "Combine in pot",
            "Add salt and pepper to taste",
            "Mix the rest of the ingredients",
            "Cook on stove for 25 min"
        ],
        "_id": "5ff497858240870659b5889e",
        "owner": "5ff4903962127775787d7d8f",
        "recipeName": "Soupie Soup",
        "shared": "Only me",
        "time": 45,
        "difficulty": "Easy",
        "vegan": false,
        "imageUrl": "https://images.unsplash.com/photo-1476718406336-bb5a9690ee2a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80",
        "__v": 0
    },
    {
        "ingredients": [
            "Fish",
            "Chips"
        ],
        "favoritedBy": [],
        "steps": [
            "Fry the fish to golden brown on medium frying pan",
            "Make the chips",
            "Enjoy!"
        ],
        "_id": "5ff4a03da290d60695f324d1",
        "owner": "5ff4903962127775787d7d8f",
        "recipeName": "Fish and Chips",
        "shared": "Everyone",
        "time": 30,
        "difficulty": "Easy",
        "vegan": false,
        "imageUrl": "",
        "__v": 0
    },
    {
      "..."
    }
]
```

This endpoint retrieves all recipes.

### HTTP Request

`GET http://localhost:3000/allRecipe`


```shell
curl "http://localhost:3000/addRecipe" \
  -X POST \
```

```javascript
const axios = require('axios');

axios.get('http://localhost:3000/addRecipe');
```

## Add a recipe

```shell
curl "http://localhost:3000/addRecipe" \
  -X POST \
```

```javascript
const axios = require('axios');

axios.POST('http://localhost:3000/addRecipe', {
    "id": "5ff4cb0f5ad5ca479d398313",
    "recipe":
    {
        "recipeName": "ice cream",
        "category": "breakfast",
        "shared": "Friends",
        "ingredients": ["ice cream", "ice cream"],
        "time": 1,
        "difficulty": "expert",
        "favoritedBy": [3, 4, 10],
        "vegan": false,
        "steps": ["scoop", "eat"],
        "imageUrl": "https://images.unsplash.com/photo-1476718406336-bb5a9690ee2a?ixid=MXwxMjA3fDB8MHxwaG90by1wYWdlfHx8fGVufDB8fHw%3D&ixlib=rb-1.2.1&auto=format&fit=crop&w=634&q=80"
    }
});
```

> The above returns status code 200 upon completion.

This endpoint adds a new recipe for a specific user.

### HTTP Request

`POST http://localhost:3000/addRecipe`

### Request Body

Field | Type | Description
----- | ---- | -----------
id | String | The id of the user.
recipe | Object | The recipe object to add.

#### Recipe object

Field | Type | Description
----- | ---- | -----------
recipeName | String | The name for the recipe.
category | String | The category of the recipe (Breakfast, Lunch, Dinner, Snack, Beverage, Dessert).
shared | String | Visibility of the recipe (onlyMe, friends, everyone).
ingredients | Array | An array of strings that represent each individual ingredient of the recipe.
time | Number | The prep time for the recipe in minutes.
difficulty | String | A string representing the difficulty level for the recipe (easy, medium, hard, expert).
favoritedBy | Array | An array of strings representing the user id's that have favorited the recipe.
vegan | Boolean | True if recipe is vegan, false if not.
steps | Array | An array of string that represent each individual step required to prepare the recipe.
imageUrl | String | A String representing the url for the recipe's image.

# Friends

## Get all users that match a name search

```shell
curl "http://localhost:3000/friends/jo" \
  -X GET \
```

```javascript
const axios = require('axios');

axios.get('http://localhost:3000/friends/jo');
```

> The above command returns JSON structured like this:

```json
[
    {
        "recipes": [
            "5ff25a515e53a4ccb1d12e75",
            "5ff4af204d815706c118db00",
            "5ff4afd54d815706c118db01",
            "5ff497858240870659b5889e",
            "5ff4a03da290d60695f324d1",
            "5ff67130b77097471d0526f6",
            "5ff63ed23bfd6c7115e5c9d2",
            "5ff6298efbf23f210dad6ffc",
            "5ff66dc032598568b8053165"
        ],
        "favoriteRecipes": [],
        "friends": [
            "5ff2381f11fa42c5cd024b55",
            "5ff250aeabc667cae1ca4882",
            "5ff397ea240989274d88c370",
            "5ff4e3c635d52f0c150c7107",
            "5ff5f3cb784e008507853d69",
            "5ff4ae1ee313134de4f31ba4"
        ],
        "_id": "5ff4e292f9884a1aaebc1cae",
        "name": "Jonathan",
        "picture": "https://lh3.googleusercontent.com/a-/AOh14GigZeSo4fmuzlYR_oYon8vlnE7AzjFNTuUfl-Ek=s96-c",
        "updated_at": "2021-01-01T17:08:03.805Z",
        "email": "email7@gmail.com",
        "sub": "103370284414679082948",
        "__v": 0
    },
    {
      "..."
    }
]
```

This endpoint retrieves all users whose name partially matches the search term.

### HTTP Request

`GET http://localhost:3000/friends/:name`

### URL Parameters

Parameter | Description
--------- | -----------
name | The name of the user to search. Can be one letter, like B, to return all users with a B in their name.

## Add a friend

```shell
curl "http://localhost:3000/addFriend" \
  -X POST \
```

```javascript
const axios = require('axios');

axios.POST('http://localhost:3000/addFriend', {
  id: "5ff4903962127775787d7d8f",
  friendId: "5ff4f75dc00ca596bc43dae1"
});
```

> The above returns status code 200 upon completion.


This endpoint adds a friend to a user's friends list.

### HTTP Request

`POST http://localhost:3000/addFriend`

### Request Body

Field | Type | Description
----- | ---- | -----------
id | String | The id of the user that wants to add a friend.
friendID | String | The id of the friend to be added.



