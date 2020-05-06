# Day 4 - Class Based Components

<img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/React-icon.svg" width="256px" alt="React" />

## What is a Component?

A tale of 2 syntaxes

| React.createElement | Component |
|---------------------|-----------|
| <img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/create-element.png" /> | <img src="https://raw.githubusercontent.com/adion81/mern-lectures/master/assets/class-component.png" /> |

Components will be the building blocks of our react apps. We can define them in a few different ways, but for now we'll stick with this `class` syntax. 

A Component needs to return elements describing what should be displayed on the page. 

**Note:** When creating Components be sure to name them starting with a capital letter!

| ❌                                            | ✔️                                             |
|-----------------------------------------------|-----------------------------------------------|
| `class exampleComponent extends Component {}` | `class ExampleComponent extends Component {}` |

## Props

Props are properties that we can pass from a parent component to a child.

```javascript
class Title extends Component {
  render() {
    return (
      <h1>{ this.props.text }</h1>
    );
  }
}

class CardComponent extends Component {
  render() {
    return (
      <div>
        <Title text="This is a title" />
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
        <p>Rerum incidunt sunt minima quae? Ipsam, corporis!</p>
      </div>
    );
  }
}
```

In the `CardComponent` we can add in the child component using the name of its class `<Title />`. We are able to pass in a property called title by writing the component with `<Title text="This is a title" />` much like we would add a `src` to an `<img />` or an `href` to an `<a>` tag.

## Children

We've written our components so far as "self-closing" tags, if we write them with open and closing elements then we are allowed to pass in whatever we like as children.

If we add in `{ this.props.children }` into our `CardComponent`

```javascript
class CardComponent extends Component {
  render() {
    return (
      <div>
        <Title text="This is a title" />
        { this.props.children }
      </div>
    );
  }
}
```

Then in our `App` component (or any other parent component) we can write add in the component with both open and closing tags `<CardComponent></CardComponent>` and whatever we put between these tags will be children that we can pass in.

```javascript
class App extends Component {
  render() {
    return (
      <div>
        <CardComponent>
          <p>Lorem ipsum dolor sit amet consectetur adipisicing elit.</p>
          <p>Rerum incidunt sunt minima quae? Ipsam, corporis!</p>
        </CardComponent>
      </div>
    );
  }
}
```

This is really useful when we want to make components that are responsible for layout or navigation and may later on help us avoid having to "lift state" which will be a topic for another day.
