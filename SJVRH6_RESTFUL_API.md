**Documents Restful API**

This API is used to create, modify and manage documents stored within the website. Users are able to look up documents by title, author, the date it was created or the date it was most recently modified.


**GET/documents**

Shows the all documents hosted on site, the following JSON is an example of this:
 
```json
HTTP/1.1 200 OK
Content-Type: application/json
[{
  "id": "234",
  "title": "Whales",
  "body": "Whales are mammals",
  "author": "Whale_Guy",
  "dateCreated": "2020-02-21",
  "dateUpdated": "2020-02-26"
},
{
  "id": "789",
  "title": "Zebras",
  "body": "Zebras are black and white",
  "author": "Ms_Zebra",
  "dateCreated": "2019-05-23",
  "dateUpdated": "2020-02-27"
}]
```

**POST/document**

Creates a new document that can be named and filled by the user. This is what will be shown by the users body input:
```json

{
  "title": "Lions",
  "body": "Lions are a type of cat",
  "author": "Mr_Lion"
}
```
This is what JSON will return:
```json

{
  "id": "123",
  "title": "Lions",
  "body": "Lions are a type of cat",
  "author": "Mr_Lion",
  "dateCreated": "2020-02-27",
  "dateUpdated": "2020-02-27"
}
```

**PATCH/document?id=234**

Allows users to modify an already existing document. This request changes the name of the author, title or body, and will change the date the document was updated, as shown in the following JSON:
```json
{
  "id": "234",
  "title": "Whales",
  "body": "Whales are mammals",
  "author": "Whale_Gal",
  "dateCreated": "2020-02-21",
  "dateUpdated": "2020-02-27"
}
```
**DELETE/document?title=Zebras**

Allows user to delete the document specified, which will return this JSON response:
```json
HTTP/1.1 202 Accepted
```



**GET/document?title=Whales**

Will return to the user the document titled "Whales" in similar style of this JSON example:

```json
HTTP/1.1 200 OK
Content-Type: application/json
{
  "id": "234",
  "title": "Whales",
  "body": "Whales are mammals",
  "author": "Whale_Gal",
  "dateCreated": "2020-02-21",
  "dateUpdated": "2020-02-27"
}
```

**GET/document?dateUpdated=2020-02-27**

Will return to the user all documents that are still hosted that were updated on February 27, 2020. Because "Zebras" was deleted, JSON returns this response:

```json
HTTP/1.1 200 OK
Content-Type: application/json
Content: 2
[{
  "id": "234",
  "title": "Whales",
  "body": "Whales are mammals",
  "author": "Whale_Gal",
  "dateCreated": "2020-02-21",
  "dateUpdated": "2020-02-27"
},
{
  "id": "123",
  "title": "Lions",
  "body": "Lions are a type of cat",
  "author": "Mr_Lion",
  "dateCreated": "2020-02-27",
  "dateUpdated": "2020-02-27"
}]
```