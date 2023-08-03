# PIAIC-simple-book-api-project
- This is a Practice project of PIAIC Web 3.0 and Metaverse developer course
- Assignment-04 from gitrepo: https://github.com/panaverse/learn-nextjs/blob/main/assignment04_simple_book_api/readme.md

- the simple book API is not working now, so I used JSON Placehoders -> Todos api ("https://jsonplaceholder.typicode.com/todos") for practice
- This JSON Placeholds API has variety of dummy content over to use for practice purposes (/posts & /comments & /albums & /photos & /todos & /users) 
- You may use any of your API that you feel easy to use.
- 


# Simple Books API using Next.js 13 and Neon

Develop a REST API that allows you to reserve a book. This API should be fully founctional with SQL calls to Neon Database.

The API should mirror the funtionality available at: 

https://simple-books-api.glitch.me

Deploy your REST API is available on Vercel.

Note: Study Steps 11, 12, and 13 to learn how to build APIs. Note middleware (Step 13) should be used to implement authentication.  

## Endpoints ##

### Status ###

GET `/status`

Returns the status of the API.

### List of books ###

GET `/books`

Returns a list of books.

Optional query parameters:

- type: fiction or non-fiction
- limit: a number between 1 and 20.


### Get a single book ###

GET `/books/:bookId`

Retrieve detailed information about a book.


### Submit an order ###

POST `/orders`

Allows you to submit a new order. Requires authentication.

The request body needs to be in JSON format and include the following properties:

 - `bookId` - Integer - Required
 - `customerName` - String - Required

Example
```
POST /orders/
Authorization: Bearer <YOUR TOKEN>

{
  "bookId": 1,
  "customerName": "John"
}
```

The response body will contain the order Id.

### Get all orders ###

GET `/orders`

Allows you to view all orders. Requires authentication.

### Get an order ###

GET `/orders/:orderId`

Allows you to view an existing order. Requires authentication.

### Update an order ###

PATCH `/orders/:orderId`

Update an existing order. Requires authentication.

The request body needs to be in JSON format and allows you to update the following properties:

 - `customerName` - String

 Example
```
PATCH /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>

{
  "customerName": "John"
}
```

### Delete an order ###

DELETE `/orders/:orderId`

Delete an existing order. Requires authentication.

The request body needs to be empty.

 Example
```
DELETE /orders/PF6MflPDcuhWobZcgmJy5
Authorization: Bearer <YOUR TOKEN>
```

## API Authentication ##

To submit or view an order, you need to register your API client.

POST `/api-clients/`

The request body needs to be in JSON format and include the following properties:

 - `clientName` - String
 - `clientEmail` - String

 Example

 ```
 {
    "clientName": "Postman",
    "clientEmail": "valentin@example.com"
}
 ```

The response body will contain the access token. The access token is valid for 7 days.

**Possible errors**

Status code 409 - "API client already registered." Try changing the values for `clientEmail` and `clientName` to something else.
