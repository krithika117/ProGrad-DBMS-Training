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
db.Employee.insertMany([{Name: "Jane", ID: 5678, Age: 25, Department: "Marketing"}, {Name: "Bob", ID: 91011, Age: 40, Department: "Finance"}])
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

```
db.Employee.find({Age: 30})
```
displays all documents in the Employee collection where the Age is 30

```
db.Employee.findOne({Name: "John"})
```
displays the first document in the Employee collection where the Name is John

```
db.Employee.distinct("Department")
```
returns a list of distinct values for the Department field in the Employee collection

```
db.Employee.count({Department: "Sales"})
```
returns the number of documents in the Employee collection where the Department is Sales

## Index Commands


```
db.Employee.createIndex({ID: 1})
```
creates an index on the ID field in the Employee collection

```
db.Employee.getIndexes()
```
displays a list of all indexes in the Employee collection

```
db.Employee.dropIndex("ID_1")
```
deletes the ID index from the Employee collection
