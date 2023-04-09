# MongoDB Hands-on 10/04/2023
## Database Commands
Shows a list of all databases on the server
```
show dbs
```

Switches to the specified database
```
use test_db
```

Displays the current database
```
db
```

Deletes the current database
```
db.dropDatabase()
```
  
## Collection Commands

Shows a list of all collections in the current database
```
show collections
```

Displays all documents in the Employee collection
```
db.Employee.find()
```

Displays the first document in the Employee collection
```
db.Employee.findOne()
```

Inserts a single document into the Employee collection
```
db.Employee.insertOne({Name: "John", ID: 1234, Age: 30, Department: "Sales"})
```

Inserts multiple documents into the Employee collection
```
db.Employee.insertMany([
{Name: "Jane", ID: 5678, Age: 25, Department: "Marketing"},
{Name: "Bob", ID: 91011, Age: 40, Department: "Finance"},
{Name: "Sarah", ID: 1213, Age: 35, Department: "Sales"},
{Name: "Mike", ID: 1415, Age: 45, Department: "Marketing"},
{Name: "Lisa", ID: 1617, Age: 28, Department: "Sales"}
])
```

Updates a single document in the Employee collection that matches the filter
```
db.Employee.updateOne({ID: 1234}, {$set: {Age: 31}})
```

Updates all documents in the Employee collection that match the filter
```
db.Employee.updateMany({Department: "Sales"}, {$set: {Department: "Marketing"}})
```

Deletes a single document in the Employee collection that matches the filter
```
db.Employee.deleteOne({ID: 5678})
```

Deletes all documents in the Employee collection that match the filter
```
db.Employee.deleteMany({Department: "Finance"})
```

## Querying Commands

Displays all documents in the Employee collection where the Age is 30
```
db.Employee.find({Age: 30})
```

Displays the first document in the Employee collection where the Name is John
```
db.Employee.findOne({Name: "John"})
```

Returns a list of distinct values for the Department field in the Employee collection
```
db.Employee.distinct("Department")
```

Returns the number of documents in the Employee collection where the Department is Sales
```
db.Employee.count({Department: "Sales"})
```

## Index Commands

Creates an index on the ID field in the Employee collection
```
db.Employee.createIndex({ID: 1})
```

Displays a list of all indexes in the Employee collection
```
db.Employee.getIndexes()
```

Deletes the ID index from the Employee collection
```
db.Employee.dropIndex("ID_1")
```

## Aggreagate Function
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

