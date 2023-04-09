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
