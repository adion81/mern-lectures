# Day 11 MongoDb

<img src="https://github.com/adion81/mern-lectures/blob/master/assets/mongoDb.png" alt="MongoDb" width="400px" />

## Mongo DB
Mongo DB is a noSQL database which means Not Only SQL.<br>
<br>
There is no relationship between our collections, and it allows us more flexibility with our database structure.<br>
This also means that there will be no joins, and can retrieve information faster.

### MySQL vs MongoDB

| MySQL  | MongoDB |
|---------------------|---------------------|
| schema | database |
| table  | collection |
| row    | document |

When you start up the mongo shell, you will notice that it is in JSON format.

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

// This will create a collection in the current database
db.createCollection("databaseName")

// This will drop a collection in the current database
db.{collectionName}.drop()

// This will show all documents in a certain collection in the current database.
db.users.find().pretty()
```
Running Mongo commands in the shell might sound like a fun time, but we want to be able to call and select information from our Express server.

## Mongoose

<img src="https://i.imgflip.com/41tay2.jpg" alt="Mongoose JS" width="300px" />

Mongoose will allow us to query our Mongo database to retrieve, create, update,and delete information.

In order to use . . .<br>
<br>
We must install it.

`npm install mongoose`<br>
<br>
We must also require it.<br>
`const mongoose = require('mongoose')`

### Database Connection
```javascript

mongoose.connect("mongodb://localhost/{databaseName},{
    useNewUrlParser: true,
    useUnifiedTopology: true
})
    .then(() =>  console.log("You're now inside the mainframe..."))
    .catch(err => console.log("MELTDOWN! MELTDOWN! MELTDOWN!",err))

```

### The Model Setup

```javascript
const mongoose = require("mongoose");

// Basic setup of the Mongoose Schema
const JokeSchema = new mongoose.Schema({
    setup: String,
    punchline: String
},{timestamps:true})

// This is how we register our schema.
const Joke = mongoose.model("Joke",JokeSchema);

// Finally we export it out of the file.
module.exports = User;
```

### Mongoose Queries

#### To find All(INDEX) . . .

```javascript
    Joke.find()
        .then( allJokes => res.json({jokes: allJokes}))
        .catch(err => res.json(err))
```

#### To find one(SHOW). . . 
```javascript
    Joke.find({_id:<SomeIDFromSomewhere>)
        .then( oneJoke => res.json({joke: oneJoke}))
        .catch(err => res.json(err))
```

#### Creating one(CREATE). . . 
```javascript
    Joke.create(req.body)
        .then( newJoke => res.json({joke: newJoke}))
        .catch(err => res.json(err))
```





