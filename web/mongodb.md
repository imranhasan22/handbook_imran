# BSON
BSON (Binary JSON) is a binary-encoded serialization of JSON-like documents.

BSON supports all JSON types and includes additional data types such as:
- __Date__: Stores date-time values.
- __ObjectId__: A unique identifier generated by MongoDB for each document.
- __Binary Data__: Stores binary data like images or files.
- __MinKey/MaxKey__: Special types used for comparing BSON elements.
- __Int32, Int64, Double__: Different numeric types for storing integer and floating-point numbers.

In MongoDB, data is stored in a document format, which uses BSON for storing these documents, and for representing data it just uses JSON-like structure.

__Example:__
When you insert a JSON-like document into MongoDB, it converts it into BSON format for internal storage.

__JSON:__
```json
{
   "name": "Wireless Mouse",
   "price": 25.99,
   "inStock": true,
   "manufacturedDate": "2024-01-01T00:00:00Z",
   "specifications": {
      "color": "black",
      "weight": 0.1
   }
}
```
__BSON:__
```bson
{
   "_id": ObjectId("64b8d2e3e8c3bc7fbb9d3e45"),
   "name": "Wireless Mouse",
   "price": 25.99,
   "inStock": true,
   "manufacturedDate": ISODate("2024-01-01T00:00:00Z"),
   "specifications": {
      "color": "black",
      "weight": Double(0.1)
   }
}
```
# CRUD
## Create
### `insertOne()`
```shell
db.users.insertOne({
   "name": "Alice",
   "age": 28,
});
```
### `insertMany()`
```shell
db.users.insertMany([
   {
      "name": "Bob",
      "age": 32
   },
   {
      "name": "Charlie",
      "age": 25
   }
]);
```