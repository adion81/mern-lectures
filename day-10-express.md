# Express and APIs

## Starting up a project

We need to make a folder for our back-end projects and create a file called `server.js`

```
mkdir games
cd games
touch server.js
```

## npm init

Next we want to let npm (Node Package Manager) know about our new project and fetch our needed packages...

```
npm init -y # the -y part just says `yes` to all of the prompts
npm i express cors
```

The `cors` package will help us overcome `Cross Origin Resource Sharing` related errors.

## simple express server

```js
const express = require("express");
const cors = require("cors");
const port = 8000;
const app = express();


app.use(cors());
app.use(express.json());

app.get("/", (req, res) => {
  res.json({"message": "ok"});
});

app.listen(port, () => console.log(`Listening on port ${port}`));
```

This will set up a really simple server that has one route... when we make a `GET` request to `localhost:8000` we will receive back a JSON response that says

```json
{"message": "ok"}
```
