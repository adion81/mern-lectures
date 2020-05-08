# Day 6 - Mapping and Conditionals

<img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/React-icon.svg" width="256px" alt="React" />

## Iterating in React

We're probably familiar with using `for` loops to iterate through lists in our Views

#### SomeView.html
```html
<ul>
  {% for book in books %}
    <li>{{ book.title }} ({{ book.author }})</li>
  {% endfor %}
</ul>
```

But how should we do this in our React Components? We'll be using `Array.prototype.map()`.

#### BookList.jsx
```js
const BookList = props => {
  return (
    <ul>
      {props.books.map( (book, i) => 
        <li key={ i }>{ book.title } ({ book.author })</li>
      )}
    </ul>
  );
}
```

Here we're going to receive an array of books through props, and using these props we can map throug the array to display the books. If we give React a `<li>War and Peace (Tolstoy)</li>` or `[<li>War and Peace (Tolstoy)</li>]` it will be able to figure out how to display it. But when we give it an array, it will want each child (`<li>`) in the array to have a unique `key` property. We can get the loop index `i` from the `.map()` method and this can serve as a suitablly unique `key`.

## Conditionals in React

We're probably familiar with using `if` in our Views as well

#### SomeView.html
```html
{% if user.is_logged_in %}
  <div class="alert alert-primary">
    Welcome back, {{ user.username }}!
  </div>
{% else %}
  <div class="alert alert-danger">
    Hey there stranger!
  </div>
{% endif %}
```

In React we'll be making use of the [ternary opertor](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/Conditional_Operator)

#### Welcome.jsx
```js
const Welcome = (props) => {
  return (
    {
      props.isLoggedIn ?
      <div className="alert alert-primary">
        Welcome back, { props.username }!
      </div> : 
      <div className="alert alert-danger">
        Hey there stranger!
      </div>
    }
  );
}
```

## Thinking in React

When we approach creating a project in React, it's best to first start out by simply recreating the look of what we want to make. Let's say we start with a form and a table just hard coded into our `App.js`. 

#### App.js
```javascript
function App(props) {
  return (
    <div>
      <h1>Books</h1>
      <form>
        <div>
          <label>Title</label>
          <input type="text" name="title" />
        </div>
        <div>
          <label>Author</label>
          <input type="text" name="author" />
        </div>
        <input type="submit" value="add book" />
      </form>
      <table>
        <tbody>
          <tr>
            <th>Title</th>
            <th>Author</th>
          </tr>
          <tr>
            <td>War and Peace</td>
            <td>Leo Tolstoy</td>
          </tr>
          <tr>
            <td>To Kill a Mockingbird</td>
            <td>Harper Lee</td>
          </tr>
        </tbody>
      </table>
    </div>
  );
}
```

The next step that we can take is to decide what things we can store in state. In this case we have a form and we will always (I can't think of a case when we wouldn't) want our inputs to be stored in state. We should also create the table of books from an array of books that we can hold in state. An array has the benefit that when we create new books we can add them in.

We should add the following hooks to the top of the component

```javascript
const [title, setTitle] = useState("");
const [author, setAuthor] = useState("");
const [books, setBooks] = useState([
  {title: "War and Peace", author: "Leo Tolstoy"},
  {title: "To Kill a Mockingbird", author: "Harper Lee"}
]);
```

The form's inputs can be updated like so

```javascript
<div>
  <label>Title</label>
  <input 
    type="text" 
    name="title" 
    value={ title } 
    onChange={ (e) => setTitle(e.target.value) }
  />
</div>
<div>
  <label>Author</label>
  <input 
    type="text" 
    name="author" 
    value={ author } 
    onChange={ (e) => setAuthor(e.target.value) }
  />
</div>
```

And the table can be updated as well

```javascript
<tbody>
  <tr>
    <th>Title</th>
    <th>Author</th>
  </tr>
  {books.map( (book, i) =>
    <tr key={ i }>
      <td>{ book.title }</td>
      <td>{ book.author }</td>
    </tr>
  )}
</tbody>
```

Next we need to add in some code to handle submitting the form...

```javascript
const addBook = (e) => {
  e.preventDefault();
  const newBook = {title, author};
  setBooks( [...books, newBook ] );
  setTitle("");
  setAuthor("");
}
```

And this function needs to be run on submit in the form...


```javascript
<form onSubmit={ addBook }>
  {/* rest of form omitted */}
</form>
```

At this point our project fully works. We can think about modularizing it. The `<table>` and the `<form>` are both prime candidates to be made their own components.

The table is a fairly simple part of this project, all it is responsible for is displaying the books. It can be rewritten as it's own component, one that will expect to receive the array of books as a Prop.

#### Components/Table.jsx
```javascript
const Table = (props) => {
  return(
    <table>
      <tbody>
        <tr>
          <th>Title</th>
          <th>Author</th>
        </tr>
        {props.books.map( (book, i) =>
          <tr key={ i }>
            <td>{ book.title }</td>
            <td>{ book.author }</td>
          </tr>
        )}
      </tbody>
    </table>
  );
}
```

The form is a bit tricker. We need it to keep track of its `title` and `author`. But when a user goes to submit the form this information should be passed up to the parent `App` component. To make this happen we can pass a props to this `Form` component that is a function, one we can pass a newly created book into.

#### Components/Form.jsx
```javascript
const Form = (props) => {
  const [title, setTitle] = useState("");
  const [author, setAuthor] = useState("");
  
  const create = (e) => {
    e.preventDefault();
    const newBook = {title, author};
    props.addBook( newBook );
    setTitle("");
    setAuthor("");
  }
  
  return (
    <form onSubmit={ create }>
      <div>
        <label>Title</label>
        <input 
          type="text" 
          name="title" 
          value={ title } 
          onChange={ (e) => setTitle(e.target.value) }
         />
      </div>
      <div>
        <label>Author</label>
        <input 
          type="text" 
          name="author" 
          value={ author } 
          onChange={ (e) => setAuthor(e.target.value) }
        />
      </div>
      <input type="submit" value="add book" />
    </form>
  );
}
```

And now the `App` component can be rewritten like so. Don't forget to import the `Form` and `Table` components. Also don't forget to pass them their needed props.

#### App.js
```javascript
function App(props) {
  const [books, setBooks] = useState([
    {title: "War and Peace", author: "Leo Tolstoy"},
    {title: "To Kill a Mockingbird", author: "Harper Lee"}
  ]);

  return (
    <div>
      <h1>Books</h1>
      <Form addBook={ newBook => setBooks( [...books, newBook ] ) } />
      <Table books={ books } />
    </div>
  );
}
```
