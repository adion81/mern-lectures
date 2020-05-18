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
    setup: {
        type: String,
        required:[true,"This is how we validate"],
        minlength: [3,"Setup has to be more than 2 characters"]
    },
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
        .then( allJokes => res.json(allJokes))
        .catch(err => res.json(err))
```

#### To find one(SHOW). . . 
```javascript
    Joke.find({_id:req.params.id)
        .then( oneJoke => res.json(oneJoke))
        .catch(err => res.json(err))
```

#### Creating one(CREATE). . . 
```javascript
    Joke.create(req.body)
        .then( newJoke => res.json(newJoke))
        .catch(err => res.json(err))
```

We know by now that we can't relate our database objects together, but what if we want to have a one to many relationship?<br>

### Nested Documents

```javascript
const mongoose = require("mongoose")

const MessageSchema = new mongoose.Schema({
    message:{
        type:String,
        minlength:[3,"Message must be at least 3 characters."]
    }
},{timestamps:true})

const UserSchema = new mongoose.Schema({
    name:{
        type: String,
        required:[true,"A user must have a name"]
    },
    messages:[MessageSchema]
},{timestamps:true})

const Message = mongoose.model("Message",MessageSchema);
const User = mongoose.model("User",UserSchema);

```

To actually create a message and nest it in the UserSchema, we need to do something like this.

```javascript

Message.create(req.body)
    .then(newMessage => {
        User.findByIdAndUpdate({_id:req.params.id},{$push:{messages:newMessage}})
    })
    .catch(err => res.json(err))

```

## Modularization
Finally we want our Express server to not look like the mountains of Mordor.

<img src="https://i.pinimg.com/originals/44/12/d6/4412d6e2a2328c631e71d68e14da600c.jpg" alt="Mordor" width="300px">
Meaning that everything is in one file, but more like the rolling hills of the Shire.
<img src="https://i.pinimg.com/originals/3a/73/5f/3a735fcfb6f4bd6c37b9f10477a449f3.jpg" alt="Shire" width="300px">

#### The Folder Structure

```
├ jokes-api/
    ├ node_modules/
    ├ server/
        ├ config
            ├ database.config.js
        ├ controllers
            ├ jokes.controllers.js
        ├ models
            ├ joke.model.js
        ├ routes
            ├ jokes.routes.js
    ├ server.js
    ├ package.json
```