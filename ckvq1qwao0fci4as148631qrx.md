---
title: "React state in class component"
seoTitle: "React state in class component"
datePublished: Mon Nov 08 2021 02:29:49 GMT+0000 (Coordinated Universal Time)
cuid: ckvq1qwao0fci4as148631qrx
slug: react-state-in-class-component
cover: https://cdn.hashnode.com/res/hashnode/image/upload/v1635232321389/GpniLUQ6a.png
tags: programming-blogs, web-development, webdev, reactjs, state

---

### State
- React components has a built-in state object. 
- The state object is where you store property values that belongs to the component.
- When the state object changes, the component re-renders.

### State updates are independent
The state object of a component may contain multiple attributes and React allows to use setState() function to update each attribute value independently. 

Example:
```jsx
class Car extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      brand: "Ford",
      model: "Mustang",
      color: "red",
      year: 1964
    };
  }
  changeColor = () => {
    this.setState({color: "blue"});
  }
  render() {
    return (
      <div>
        <h1>My {this.state.brand}</h1>
        <p>
          It is a {this.state.color}
          {this.state.model}
          from {this.state.year}.
        </p>
        <button
          type="button"
          onClick={this.changeColor}
        >Change color</button>
      </div>
    );
  }
}
``` 
### Updating state
setState is an asynchronous processing, if we try to use a value after setState then it may give as an undesirable value.

Example: 
```js
class State extends Component {
  constructor(props) {
    super(props);

    this.state = {
      count: 0,
    };
  }

  increment() {
    this.setState({ count: this.state.count + 1 });
    /* This console.log will print one count less then the state 
    because setState is async and before updating the state we are printing the value */
    console.log(this.state.count);
  }

  render() {
    return (
      <div>
        <div>
          <h1>{this.state.count}</h1>
          <button onClick={() => this.increment()}>
            Increment one
          </button>
        </div>
      </div>
    );
  }
}
```

to solve this problem we can use a callback function
```js
  increment() {
    this.setState({ count: this.state.count + 1 }, () => {
      console.log(this.state.count);
    });
  }
```
this will solve the problem but due to asynchronous processing, this.state.count may produce an undesirable result in some cases.

Example:
if we try to increment the value two times by calling increment() two times, then it will increment to 1 instead of 2 because react group multiple state updates into single update for better performance.
```js
class State extends Component {
  constructor(props) {
    super(props);

    this.state = {
      count: 0,
    };
  }

  increment() {
    this.setState({ count: this.state.count + 1 });
  }

  incrementTwo() {
    this.increment();
    this.increment();
  }

  render() {
    return (
      <div>
        <div>
          <h1>{this.state.count}</h1>
          <button onClick={() => this.incrementTwo()}>Increment two times</button>
        </div>
      </div>
    );
  }
}
```
To solve this problem we have to update the state based to previous state. we can pass a function as an argument and we can use the previous state as a parameter in setState. in this case it will update the state two times as we want.
```js
class State extends Component {
  constructor(props) {
    super(props);

    this.state = {
      count: 0,
    };
  }

  increment() {
    this.setState((prevState) => ({
      count: prevState.count + 1,
    }));
  }

  incrementTwo() {
    this.increment();
    this.increment();
  }

  render() {
    return (
      <div>
        <div>
          <h1>{this.state.count}</h1>
          <button onClick={() => this.incrementTwo()}>Increment two times</button>
        </div>
      </div>
    );
  }
}
```
setState can also take "props" as it's second parameter:
```js
this.setState(function(prevState, props){
    return {counter: prevState.count + props.diff};
});
```
**Reference: **
https://www.youtube.com/watch?v=QFaFIcGhPoM&list=PLC3y8-rFHvwgg3vaYJgHGnModB54rxOk3
