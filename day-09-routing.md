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

```
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

{{ Diagram here }}


## Route Parameters



## The `navigate` function
