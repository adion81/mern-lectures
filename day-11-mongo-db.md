# Day 11 MongoDb

<img src="https://github.com/adion81/mern-lectures/blob/master/assets/mongoDb.png" alt="MongoDb" width="400px" />

## Mongo DB

### MySQL vs MongoDB

| MySQL  | MongoDB |
|---------------------|---------------------|
| schema | database |
| table  | collection |
| row    | document |

### Commands

```
// This will show you all the databases 
show dbs

// This will show you the current database
db

// This will create/switch to a database
use {database name}

// This will drop the current database
db.dropDatabase()

// This will show all collections in the current database
db.showCollections()

// This will show all documents in a certain collection in the current database.
db.users.find().pretty()
```

## Mongoose

