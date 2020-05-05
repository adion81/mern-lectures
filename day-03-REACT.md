# Day 3 - REACT

<img src="https://github.com/adion81/mern-lectures/blob/master/assets/react.gif" alt="React" width="500px" />


## What is React?

React is a declarative JS library for building UIs.<br>
It's declarative because you have to tell it what to do, instead of it having it's own opinions about how to do things.<br>
<br>
React uses objects called `Componenets` to peice together our webpage, and we can build these components in a couple different ways.<br>

#### Initial Setup

To setup an initial React project type `npx create-react-app app-name`.

*MUST CALL YOUR PROJECT NAME LIKE SO `app-name`*<br>
<br>
When we run this command we will get a basic react appliction in the current folder.

##### Basic React App
```
├ my-react-app/
  ├ node_modules/
  ├ public/
    ├ index.html
  ├ src/
    ├ App.css
    ├ App.js
    ├ App.test.js
    ├ index.css
    ├ index.js
    ├ logo.svg
    ├ serviceWorker.js
    ├ setUpTests.js
  ├ package-lock.json
  ├ package.json
```

## Thinking in React

What does it mean to think in React? With React we are creating something called a Single Page Application. <br>
<br>
<details>
    <summary>Guidelines for Building Our UI</summary>
    <ul>
        <li>Divide the bigger UI into tiny pieces. You will always have child components inside parent components.</li>
        <li>Look for UI parts which are being used in more than one place within the application.</li>
        <li>See if they can live independently which means checking if they own their state or it’s being provided by their parent component.</li>
        <li>If they can live independently, try to see what are the rendering and event handling requirements.</li>
    </ul>
</details>
There will be many different ways that we can organize our react applictions.  But we must now start thinking in React, and that means there is only one page.