# Day 4 - Class Based Components

<img src="data:image/png;base64,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" alt="React" width="128px" />

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
        <p>Lorem ipsum dolor sit amet consectetur adipisicing elit. Rerum incidunt sunt minima quae? Ipsam, corporis!</p>
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
