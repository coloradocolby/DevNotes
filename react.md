# React

## Stateless Functional Components

They are literally *functions*

Some info (can) go in, some JSX comes out.

```
const SearchBar = () => {
  return <input />;
};
```

They are faster because they have less baggage like lifecycle methods. Great for simple presentational ui

## Class-Based Components

Used when we want our component to have some sort of internal record keeping. Be aware of itself and what's happened to it since it's been rendered.

```
class SearchBar extends Component {

  constructor() {
    super(props);

  }

  render() {

  }
}

```

Every class-based component needs a render method

Functional Component -> (upgraded) -> Class Based Component

## Binding

```
constructor(props) {
  super(props);
  this.state = {isToggleOn: true}
  this.handleClick = this.handleClick.bind(this);
}

handleClick() {
  this.setState(prevState => ({
    isToggleOn: !prevState.isToggleOn
  }));
}

```

Is the same as using the public class fields syntax of

```
constructor(props) {
  super(props);
  this.state = {isToggleOn: true}
}

handleClick = () => {
  this.setState(prevState => ({
    isToggleOn: !prevState.isToggleOn
  }));
}

// note the arrow function

```

## React Router

Router is the workhorse of all things react-router

The Route component provides the configuration that says if the url looks like this, I want to show THIS component, if it looks like that, I want to show THAT component.


## Arrays in JSX

When JSX sees an array it renders each of the elements side by side, in other words
```
{[1,2,3]}

```
is no different than 
```
{1}{2}{3}
```

Which makes sense when you type:

```
<ol>
  {app.options.map((option, i) => <li key={i}>{option}</li>)}
</ol>
```
You are getting the three list items returned

## setState

This is the new way to setState

```
  plusOne() {
    this.setState((prevState) => { // current state values are the first param
      return {
        count: prevState.count + 1
      }
    });
  }
```

 This is the old way that will soon be done for!

```
  this.setState({
    count: this.state.count + 1
  });
```

Why? Calls to this.setState are ASYNCHRONOUS, in other words,
just because we change the state, it doesn't mean it will be changed
necesarilly by the time the next line runs!

This is also bad because sometimes React waits to batch state changes sometimes

## props

A component cannot mutate it's own props, but new props can be passed down to it.

...rest gives me everythings that was not destructured
```
{...rest}
```

## returning a object on one line arrow function

```
const num = () => {}
```
In this case, the {} is seen as the function body, so it returns undefined
Since we are actually trying to return an empty **object** we must wrap it in paranthesis

```
const num = () => ({})
```