
## Rest API Endpoint Formats
> https://api.example.com/v1/{{path}}

## Rest API Success Responses

1- GET - Get single item - HTTP Response Code: **200**
```javascript
    HTTP/2 200
    Content-Type: application/json

    {
        "id": 10,
        "name": "shirt",
        "color": "red"
    }
```
2- GET - Get item list - HTTP Response Code: **200**
```javascript
    HTTP/2 200
    Content-Type: application/json

    [
      {
        "id": 10,
        "name": "shirt",
        "color": "red",
        "price": "$123"
      },
      {
        "id": 11,
        "name": "coat",
        "color": "black",
        "price": "$2300"
      }
    ]
```

3- POST - Create a new item - HTTP Response Code: **201**
```javascript
    HTTP/2  201
    Content-Type: application/json

    {
      "message": "The item was created successfully"
    }
```
4- PATCH - Update an item - HTTP Response Code: **200/204**

> If updated entity is to be sent after the update

```javascript
    HTTP/2  200
    Content-Type: application/json

    {
        "id": 10,
        "name": "shirt",
        "color": "red",
        "price": "$23"
    }
```

> If updated entity is not to be sent after the update

```javascript
    HTTP/2  204
```

5- DELETE - Delete an item - HTTP Response Code: **204**
```javascript
    HTTP/2  204
```


## Rest API Error Responses

1- GET - HTTP Response Code: **404**

```javascript
    HTTP/2  404
    Content-Type: application/json

    {
      "message": "The item does not exist"
    }
```
2- DELETE - HTTP Response Code: **404**
```javascript
    HTTP/2  404
    Content-Type: application/json

    {
      "message": "The item does not exist"
    }
```
3- POST -  HTTP Response Code: **400**
```javascript
    HTTP/2  400
    Content-Type: application/json

    {
        "message": "Validation errors in your request",
        "errors": [
            {
                "message": "Oops! The value is invalid",
                "field": "email"
            },
            {
                "message": "Oops! The format is not correct",
                "field": "phoneNumber"
            }
        ]
    }
```
4- PATCH -  HTTP Response Code: **400/404**
```javascript
    HTTP/2  400
    Content-Type: application/json

    {
        "message": "Validation errors in your request",
        "errors": [
            {
                "message": "Oops! The format is not correct",
                "field": "phoneNumber"
            }
        ]
    }


    HTTP/2  404
    Content-Type: application/json

    {
      "message": "The item does not exist"
    }
```
5- VERB Unauthorized - HTTP Response Code: **401**
```javascript
    HTTP/2  401
    Content-Type: application/json

    {
      "message": "Authentication credentials were missing or incorrect"
    }
```
6- VERB Forbidden - HTTP Response Code: **403**
```javascript
    HTTP/2  403
    Content-Type: application/json

    {
      "message": "The request is understood, but it has been refused or access is not allowed"
    }
```
7- VERB Conflict - HTTP Response Code: **409**
```javascript
    HTTP/2  409
    Content-Type: application/json

    {
      "message": "Any message which should help the user to resolve the conflict"
    }
```
8- VERB Too Many Requests - HTTP Response Code: **429**
```javascript
    HTTP/2  429
    Content-Type: application/json

    {
      "message": "The request cannot be served due to the rate limit having been exhausted for the resource"
    }
```
9- VERB Internal Server Error - HTTP Response Code: **500**
```javascript
    HTTP/2  500
    Content-Type: application/json

    {
      "message": "Something is broken"
    }
```
10- VERB Service Unavailable - HTTP Response Code: **503**
```javascript
    HTTP/2  503
    Content-Type: application/json

    {
      "message": "The server is up, but overloaded with requests. Try again later!"
    }
```