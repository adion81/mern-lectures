# Day 12 - Full MERN

<img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/React-icon.svg" width="256px" alt="React" />

## How does it all fit together?

| Front-End Technologies | Back-End Technologies |
|------------------------|-----------------------|
| React                  | Express               |
| @Reach/Router          | MongoDB / Mongoose    |
| Axios                  | cors                  |

<img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/MERN-req-res.png" alt="diagram" />

## Final Folder Structure

There are many ways we can organize our projects, but for now it's best to create our react app with the name of `client` and place it directly inside of our project folder.

```
├ disco-dogs/
    ├ client/
        ├ public/
            ├ index.html
        ├ src/
            ├ App.css
            ├ App.js
            ├ index.css
            ├ index.js
        ├ package.json
    ├ server/
        ├ config
            ├ database.config.js
        ├ controllers
            ├ dogs.controller.js
        ├ models
            ├ dog.model.js
            ├ move.model.js
        ├ routes
            ├ dogs.routes.js
    ├ server.js
    ├ package.json
```

## Full MERN Project Checklist

* create the initial folder and `cd` inside of it

``` 
mkdir disco-dogs
cd disco-dogs
```

* create server.js and initialize our project

```
touch server.js
npm init -y
```

* install our back-end dependancies 

```
npm i cors express mongoose
```

* create our back-end folder structure

```
mkdir server
cd server
mkdir config controllers models routes
cd ..
```

* create our front-end (make sure we're in the same folder as ```server/```

```
npx create-react-app client
```

* install our front-end dependancies

```
cd client
npm i axios @reach/router
cd ..
```

#### Now we're ready to get coding!
