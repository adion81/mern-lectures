# Front-End Routing

<img src="https://raw.githubusercontent.com/reach/router/master/logo-horizontal.png" alt="routing" width="500px" />

### What is a Single Page Application?

<details>
  <summary>What is a SPA?</summary>
  <p>A single-page application (SPA) is a web application or website that interacts with the web browser by dynamically rewriting the current web page with new data from the web server, instead of the default method of the browser loading entire new page. -Wikipedia</p>
</details>

### Can a Single Page Application have routes?

<details>
  <summary>Routing a SPA?</summary>
  <p>Yes. While it will appear to the user that they are navigating to different pages, in fact they will be viewing the same <code>index.html</code> all along. We can change what is displayed for our user pased on what <code>url</code> the user is viewing.</p>
</details>

<hr>

## How to use @Reach/Router

#### Step 0 - Be sure to install it with each project

```
npm i @reach/router
```

#### Step 1 - Import it into the necessary files (App.js and others)

```js
import { Router, Link } from "@reach/router";
```

#### Step 2 - Place our "views" into the `<Router>`

Assuming we have components named `<IndexView />`, `<HomeView />`, and `<UserView />` we can add these as children into the `<Router>` component that we have imported above. 

```js
// this can go anywhere in our code, but for now place this in App.js
<Router>
  <IndexView path="/" />
  <HomeView path="/home" />
  <UserView path="/user" />
</Router>
```

#### Step 3 - Use `<Link>` components like you would `<a>` anchor tags

```js
// this can also go inside of App.js for now
<ul className="navbar">
  <li>
    <Link to="/">Index</Link>
  </li>
  <li>
    <Link to="/home">Home</Link>
  </li>
  <li>
    <Link to="/user">User</Link>
  </li>
</ul>
```

We can now click on the above links to change which component is being show to our user.

<img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/routing-nutshell.png" alt="front-end routing" width="926px" />

<hr>

## Route Parameters

We can also use Route parameters...

```js
// inside of App.js
const Dojo = (props) => {
  return <h1>Welcome to {props.city}!</h1>
}

function App() {
  <Link to="/dojo/Chicago">Chicago</Link>
  &nbsp;|&nbsp;
  <Link to="/dojo/Tulsa">Tulsa</Link>
  &nbsp;|&nbsp;
  <Link to="/dojo/DC">DC</Link>
  
  <Router>
    <Dojo path="/dojo/:city" />
  </Router>
}
```

In this example we can get the `:city` part of the `path` as a `prop` inside of the `Dojo` component.

We just need to be sure to use the `:` at the start of the path we want to be a variable.

<hr>

## The `navigate` function

Let's say we just submitted a form and we want to send the user to a different view

```js
import { navigate } from "@reach/router";

const SomeForm = (props) => {

  const submitHandler = (e) => {
    e.preventDefault();
    if(form_is_valid) {
      // do something with the data
      navigate("/success"); // success could be any route... you don't have to call it success in fact please don't
    } else {
      // display error messages to the user
    }
  }

  {/* rest of component omitted */}

}
```

we can use the navigate function to send the user to where we want them to go much like we would use `redirect` in the past.
