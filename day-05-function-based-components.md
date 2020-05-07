# Day 5 - Function Based Components

<img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/React-icon.svg" width="256px" alt="React" />

## Class Components vs. Function Components

|   |Class Components | Function Components |
|-------------------|---------------------|---------------------|
|  state  | &#9989; | &#10060; |
| LifeCyle Methods | &#9989; | &#10060;  |
|  props | &#9989; |  &#9989; |

### What are Lifecyle Methods?

There are 3 different stages in the life of a React component.
<details>
    <summary>Mounting</summary>
    <ol>
        <li>constructor()</li>
        <li>render()</li>
        <li>componenetDidMount()</li>
    </ol>
</details>
<details>
    <summary>Updating</summary>
    <ol>
        <li>shouldComponentUpdate()</li>
        <li>render()</li>
        <li>componenetDidUpdate()</li>
    </ol>
</details>
<details>
    <summary>UnMounting</summary>
    <ol>
        <li>componentWillUnmount()</li>
    </ol>
</details>

With Functional / Stateless  components we do not have access to these wonderful React tools.<br>

## React Hooks

React hooks allow us to 'hook' into React's state and lifecycle methods and still keep our functional components.<br>
*The syntax will also look alot cleaner.*

### useState

useState is a React hook that allows us to hook into the state functionality of React, but first we must import it at the top.

`import React, {useState} from 'react';`
<br>
useState has two variables `state` and `setState`, but it also should take in an initial state value.<br>
`const [count,setCount] = useState(1);`

```javascript
import React, {useState} from 'react;

const Form = (props) => {
    const [firstName,setFirstName] = useState("");
    const [lastName,setLastName] = useState("");

    // This function will be called when we submit the form.
    const handleSubmit = (e) => {
        e.preventDefault();
        // This is where we will eventually send our form data to a server.
    }
    // Notice that we don't need the render method.
    // That's because we don't have access to it since it's a lifecycle method.
    return (
        <form onSubmit={(e) => handleSubmit(e)} >
            <input 
                type="text"
                name="firstName"
                value={form.firstName}
                onChange={ (e) => setFirstName(e.target.value) }
            />
            <input 
                type="text"
                name="lastName"
                value={form.lastName}
                onChange={ (e) => setLastName(e.target.value) }
            />
            <input 
                type="submit"
                value="Submit"
            />
        </form>
    );


}

export default Form;
```

## Lifting State

<img src="https://i.imgflip.com/40hcej.jpg" alt="Lifting State" width="400px" />

Sometimes we need sibling components to share information, but if one sibling say a `Form.js` is managing it's state, the other `DisplayInfo.js` cannot access it.<br>
<br>
In this case we would need to lift up our state to the common parent component.

```javascript
function App(){
    const [firstName,setFirstName] = useState("");
    const [lastName,setLastName] = useState("");

    const handleSubmit = (e) => {
        e.preventDefault();
        // This is where we will eventually send our form data to a server.
    }
    
    return(
        <div>
            <Form 
                fName={firstName}
                lName={lastName}
                handleFirst={setFirstName}
                handleLast={handleLastName}
                handleFormSubmit={handleSubmit}
            />
            <Display 
                fName={firstName} 
                lName={lastName} 
            />
        </div>
    );
}


const Form = ({fName,lName,handleFirst,handleLast,handleFormSubmit}) => {
    return(
        <form onSubmit={(e) => handleFormSubmit(e)} >
            <input 
                type="text"
                name="firstName"
                value={fName}
                onChange={ (e) => handleFirst(e.target.value) }
            />
            <input 
                type="text"
                name="lastName"
                value={lName}
                onChange={ (e) => handleLast(e.target.value) }
            />
            <input 
                type="submit"
                value="Submit"
            />
        </form>
    );
}

```