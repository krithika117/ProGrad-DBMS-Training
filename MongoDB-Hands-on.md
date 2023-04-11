# MongoDB Hands-on 11/04/2023

### Installation
```
https://www.mongodb.com/try/download/compass
```

## Database Commands
### Shows a list of all databases on the server
```
show dbs
```

### Switches to the specified database
```
use test_db
```

### Displays the current database
```
db
```

### Deletes the current database
```
db.dropDatabase()
```
  
## Collection Commands

### Shows a list of all collections in the current database
```
show collections
```

### Displays all documents in the Employee collection
```
db.Employee.find()
```

### Display particular fields in the Employee collection
```
db.Employee.find({}, {Name: 1, Age: 1, _id: 0})
```

### Displays the first document in the Employee collection
```
db.Employee.findOne()
```

### Inserts a single document into the Employee collection
```
db.Employee.insertOne({Name: "John", ID: 1234, Age: 30, Department: "Sales"})
```

### Inserts multiple documents into the Employee collection
```
db.Employee.insertMany([
{Name: "Jane", ID: 5678, Age: 25, Department: "Marketing"},
{Name: "Bob", ID: 91011, Age: 40, Department: "Finance"},
{Name: "Sarah", ID: 1213, Age: 35, Department: "Sales"},
{Name: "Mike", ID: 1415, Age: 45, Department: "Marketing"},
{Name: "Lisa", ID: 1617, Age: 28, Department: "Sales"}
])
```

### Updates a single document in the Employee collection that matches the filter
```
db.Employee.updateOne({ID: 1234}, {$set: {Age: 31}})
```

### Updates all documents in the Employee collection that match the filter
```
db.Employee.updateMany({Department: "Sales"}, {$set: {Department: "Marketing"}})
```

### Deletes a single document in the Employee collection that matches the filter
```
db.Employee.deleteOne({ID: 5678})
```

### Deletes all documents in the Employee collection that match the filter
```
db.Employee.deleteMany({Department: "Finance"})
```

## Querying Commands

### Displays all documents in the Employee collection where the Age is 30
```
db.Employee.find({Age: 30})
```

### Displays the first document in the Employee collection where the Name is John
```
db.Employee.findOne({Name: "John"})
```
### Displays names and departments in the Employee collection where the Age is greater than 30
```
db.Employee.find({Age: {$gte: 30}}, {Name: 1, Department:1, _id: 0})
```
### Returns a list of distinct values for the Department field in the Employee collection
```
db.Employee.distinct("Department")
```

### Returns the number of documents in the Employee collection where the Department is Sales
```
db.Employee.count({Department: "Sales"})
```

## Index Commands
```
db.users.insertMany([
{ name: "Alice", age: 25, city: "New York" },
{ name: "Bob", age: 30, city: "Los Angeles" },
{ name: "Charlie", age: 35, city: "Chicago" },
{ name: "David", age: 40, city: "Houston" },
{ name: "Emma", age: 22, city: "Miami" },
{ name: "Frank", age: 27, city: "Seattle" },
{ name: "Grace", age: 33, city: "Boston" },
{ name: "Harry", age: 38, city: "Philadelphia" },
{ name: "Isabella", age: 26, city: "San Francisco" },
{ name: "Jack", age: 29, city: "Dallas" },
{ name: "Karen", age: 34, city: "Denver" },
{ name: "Luke", age: 39, city: "Phoenix" },
{ name: "Mary", age: 24, city: "Atlanta" },
{ name: "Nathan", age: 31, city: "San Diego" },
{ name: "Olivia", age: 36, city: "Washington" },
{ name: "Peter", age: 41, city: "Portland" },
{ name: "Quentin", age: 28, city: "San Antonio" },
{ name: "Rachel", age: 32, city: "Minneapolis" },
{ name: "Steve", age: 37, city: "Las Vegas" },
{ name: "Tina", age: 23, city: "Kansas City" },
{ name: "Uma", age: 30, city: "New Orleans" },
{ name: "Victor", age: 35, city: "Salt Lake City" },
{ name: "Wendy", age: 40, city: "Orlando" },
{ name: "Xavier", age: 27, city: "Austin" },
{ name: "Yolanda", age: 33, city: "Nashville" },
{ name: "Zach", age: 38, city: "Raleigh" },
{ name: "Amelia", age: 25, city: "New York" },
{ name: "Ben", age: 30, city: "Los Angeles" },
{ name: "Cathy", age: 35, city: "Chicago" },
{ name: "David", age: 40, city: "Houston" },
{ name: "Emily", age: 22, city: "Miami" },
{ name: "Frank", age: 27, city: "Seattle" },
{ name: "Grace", age: 33, city: "Boston" },
{ name: "Harry", age: 38, city: "Philadelphia" },
{ name: "Isabella", age: 26, city: "San Francisco" },
{ name: "Jack", age: 29, city: "Dallas" },
{ name: "Karen", age: 34, city: "Denver" },
{ name: "Luke", age: 39, city: "Phoenix" },
{ name: "Mary", age: 24, city: "Atlanta" },
{ name: "Nathan", age: 31, city: "New York"},
{ name: "Nora", age: 27, city: "Detroit" },
{ name: "Oscar", age: 32, city: "San Jose" },
{ name: "Penelope", age: 37, city: "Tucson" },
{ name: "Quincy", age: 24, city: "Charlotte" },
{ name: "Ryan", age: 31, city: "Memphis" },
{ name: "Samantha", age: 36, city: "Albuquerque" },
{ name: "Thomas", age: 41, city: "Sacramento" },
{ name: "Ursula", age: 28, city: "Virginia Beach" },
{ name: "Vincent", age: 33, city: "Milwaukee" },
{ name: "Wanda", age: 38, city: "Tampa" },{ name: "Xander", age: 29, city: "Oklahoma City" },
{ name: "Yara", age: 34, city: "Boise" },
{ name: "Zara", age: 39, city: "Anchorage" },
{ name: "Alex", age: 26, city: "New York" },
{ name: "Bella", age: 31, city: "Los Angeles" },
{ name: "Cameron", age: 36, city: "Chicago" },
{ name: "Derek", age: 41, city: "Houston" },
{ name: "Eliza", age: 28, city: "Miami" },
{ name: "Finn", age: 33, city: "Seattle" },
{ name: "Gina", age: 38, city: "Boston" },
{ name: "Henry", age: 25, city: "San Francisco" },
{ name: "Isaac", age: 30, city: "Dallas" },
{ name: "Julia", age: 35, city: "Denver" },
{ name: "Karl", age: 40, city: "Phoenix" },
{ name: "Lena", age: 27, city: "Atlanta" },
{ name: "Max", age: 32, city: "New York" },
{ name: "Nate", age: 37, city: "Detroit" },
{ name: "Owen", age: 24, city: "San Jose" },
{ name: "Paige", age: 29, city: "Tucson" },
{ name: "Quinn", age: 34, city: "Charlotte" },
{ name: "Riley", age: 39, city: "Memphis" },
{ name: "Sophie", age: 26, city: "Albuquerque" },
{ name: "Trevor", age: 31, city: "Sacramento" },
{ name: "Una", age: 36, city: "Virginia Beach" },
{ name: "Violet", age: 41, city: "Milwaukee" },
{ name: "Wade", age: 28, city: "Tampa" },
{ name: "Xena", age: 33, city: "Las Vegas" },
{ name: "Yvette", age: 38, city: "Kansas City" },
{ name: "Zane", age: 25, city: "New Orleans" },
{ name: "Adam", age: 30, city: "Salt Lake City" },
{ name: "Brittany", age: 35, city: "Orlando" },
{ name: "Chris", age: 40, city: "Austin" },
{ name: "Diana", age: 27, city: "Nashville" },
{ name: "Ethan", age: 32, city: "Raleigh" },
{ name: "Fiona", age: 37, city: "Charleston" },
{ name: "George", age: 24, city: "Savannah" },
{ name: "Haley", age: 29, city: "Asheville" },
{ name: "Ian", age: 34, city: "Portland" },
{ name: "Jasmine", age: 39, city: "San Antonio" },
{ name: "Keith", age: 26, city: "Minneapolis" }
])
```

### Creates an index on the ID field in the Employee collection
```
db.users.createIndex({ city: 1 })
```

### Displays a list of all indexes in the Employee collection
```
db.users.getIndexes()
```

### Deletes the ID index from the Employee collection
```
db.users.dropIndex("ID_1")
```

### View Stats
```
db.users.find({ city: "New York" }).explain()
```
```
db.users.find({city: "New York"}).explain("executionStats")
```
## Aggregate Function
### To produce an aggregate of all the price totals
```
db.orders.insertMany([
   { _id: 1, cust_id: "Ant O. Knee", ord_date: new Date("2020-03-01"), price: 25, items: [ { sku: "oranges", qty: 5, price: 2.5 }, { sku: "apples", qty: 5, price: 2.5 } ], status: "A" },
   { _id: 2, cust_id: "Ant O. Knee", ord_date: new Date("2020-03-08"), price: 70, items: [ { sku: "oranges", qty: 8, price: 2.5 }, { sku: "chocolates", qty: 5, price: 10 } ], status: "A" },
   { _id: 3, cust_id: "Busby Bee", ord_date: new Date("2020-03-08"), price: 50, items: [ { sku: "oranges", qty: 10, price: 2.5 }, { sku: "pears", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 4, cust_id: "Busby Bee", ord_date: new Date("2020-03-18"), price: 25, items: [ { sku: "oranges", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 5, cust_id: "Busby Bee", ord_date: new Date("2020-03-19"), price: 50, items: [ { sku: "chocolates", qty: 5, price: 10 } ], status: "A"},
   { _id: 6, cust_id: "Cam Elot", ord_date: new Date("2020-03-19"), price: 35, items: [ { sku: "carrots", qty: 10, price: 1.0 }, { sku: "apples", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 7, cust_id: "Cam Elot", ord_date: new Date("2020-03-20"), price: 25, items: [ { sku: "oranges", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 8, cust_id: "Don Quis", ord_date: new Date("2020-03-20"), price: 75, items: [ { sku: "chocolates", qty: 5, price: 10 }, { sku: "apples", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 9, cust_id: "Don Quis", ord_date: new Date("2020-03-20"), price: 55, items: [ { sku: "carrots", qty: 5, price: 1.0 }, { sku: "apples", qty: 10, price: 2.5 }, { sku: "oranges", qty: 10, price: 2.5 } ], status: "A" },
   { _id: 10, cust_id: "Don Quis", ord_date: new Date("2020-03-23"), price: 25, items: [ { sku: "oranges", qty: 10, price: 2.5 } ], status: "A" }
])
```
```
db.orders.aggregate([
   { $group: { _id: "$cust_id", value: { $sum: "$price" } } },
   { $out: "summation" }
])
```
### View Output
```
db.summation().find().sort({value: 1})
```

## Foreign Key Implementation
Unlike relational databases, MongoDB does not have the concept of primary and foreign keys. However, we can simulate these concepts using document references.
```
db.customers.insertMany([
  { _id: 1, name: "John Doe", email: "johndoe@example.com" },
  { _id: 2, name: "Jane Smith", email: "janesmith@example.com" },
  { _id: 3, name: "Bob Johnson", email: "bobjohnson@example.com" }
])
```
```
db.orders.insertMany([
  { _id: 1, order_number: "123", customer_id: 1 },
  { _id: 2, order_number: "456", customer_id: 2 },
  { _id: 3, order_number: "789", customer_id: 1 }
])
```
```
db.orders.aggregate([
  {
    $lookup: {
      from: "customers",
      localField: "customer_id",
      foreignField: "_id",
      as: "customer_info"
    }
  },
  { $out: "join_demo" }
])
```
