# HTML, CSS, JS
## HTML
React uses JSX(Javascript XML), a syntax extension for javascript, which looks similar to HTML but allows you to embed HTML within javascript.

Although JSX looks like javascript, it's not. JSX gets compiled to javascript, specially to `React.createElement` calls, which is why it can only be used within a React environment.

__Differences From HTML:__
- `className` instead of `class`
- camleCase for Attributes
- self-closing tags

## CSS
1. __External CSS:__
Just import external css file where you want those styles. Those style from the imported files are inherit to all the child component
2. __Inline Style:__
You can apply styles directly to elements using the `style` attribute which accepts a javascript object
3. __Modules:__
CSS modules are locally scoped CSS files, which means the styles defined in them are only applied to the component that imports them.. This prevents global name collisions.

# Fragments
It is a way to group multiple elements `without adding extra nodes` to the DOM. They allow to return multiple children from a component without the need to wrap them in an additional HTML like _div_.

__There are tow ways to use fragments:__

1. __Explict Syntax:__
```
<React.Fragment>
</React.Fragment>
```
2. __Shorthand Systax:__
```
<></>
```
The shorthand syntax is more concise and commonly used but doesn't support `key` or other attributes.

Render method can return only one elements. So when you need to return multiple element at a time but you don't want to add extra node to the DOM, use fragment.
# Hooks
Hooks are functions that allow functional components to manage state, perform side effects and other React features. 
- Call hooks at the top level.
- Call hooks in functional component.
- Can't be conditional(loop, condition, nested function).

## useState
It allow you to ad state to your compoents. When the state is updated, react automatically re-renders the component with the new state value, so the UI reflects the updated state.

State generally refers to data or properties that need tracking in an application.

It returs a pair, an array with current state and a function to update it.

## useEffect
It lets you perform side effect function(data fetching, timers, DOM manipulation) in functional components. Side effect refers to any operation that affects something outside of the components scope, interacting with external system, global state.

It takes two arguments
    - a function containing the side-effect logic which run after the render is committed to the screen.
    - an array of values that the effect depend on, when these values change, the effect is re-run.

If you omit the dependency array, the effect runs after every render, similar to `componentDidMount`, `componentDidUpdate` and `componentWillMount` in class component. Omitting the dependency array or referring a state that changes inside the effect can cause infinite loop of renders.

If you pass an empty array, the effect runs only once, similar to `componentDidMount`

If you pass an array of variables, the effect runs only when those variable change.

## Custom Hook
A function that allow you to `resue` stateful logic from your components.

- Name must start with `use`.
- It can return any type of data(array, object, function etc).

# Class Components
## Class Definition
A class component is defined as js class that `extends` `React.Component`. It must hve a `render()` method, which returns jsx to be rendered to the DOM.
```jsx
class MyApp extends Component{
    render(){
        return <h1>Hello World</h1>
    }
}
```
## State Management
Class component's have a built-in state object that can be used to store and manage data that affects the components rendering. The state can be updated using the `setState` method, which triggers a re-render of the component
```jsx
class Counter extends Component{
    constructor(props){
        super(props);
        this.state={count:0};
    }
    increment=()=>{
        this.setState({count:this.state.count+1});
    }
    render(){
        return(
            <>
            <p>Count: {this.state.count}</p>
            <button onClick={this.increment}>Increment</button>
            </>
        )
    }
}
```
## Props
Props are used to pass data from a parent component to a child component and access by `this.props`.
```jsx
class MyApp extends Component{
    render(){
        return <h1>Hello {this.props.name}</h1>
    }
}
```
