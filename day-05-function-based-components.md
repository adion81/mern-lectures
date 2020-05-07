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

```javascript
import React, {useState} from 'react;

const Form = (props) => {

    // Notice that we don't need the render method.
    // That's because we don't have access to it since it's a lifecycle method.
    return (
        <form onSubmit={(e) => handleSubmit(e)} >
            <input 
                type="text"
                name="firstName"
                value={firstName}
                onChange={ (e) => handleChange(e) }
            />
            <input 
                type="text"
                name="lastName"
                value={lastName}
                onChange={ (e) => handleChange(e) }
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
