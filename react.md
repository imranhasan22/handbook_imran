# Hooks
## useEffect
It lets you perform side effect function(data fetching, timers, DOM manipulation) in functional components. Side effect refers to any operation that affects something outside of the components scope, interacting with external system, global state.

It takes two arguments
    - a function containing the side-effect logic which run after the render is committed to the screen.
    - an array of values that the effect depend on, when these values change, the effect is re-run.

If you omit the dependency array, the effect runs after every render, similar to `componentDidMount`, `componentDidUpdate` and `componentWillMount` in class component. Omitting the dependency array or referring a state that changes inside the effect can cause infinite loop of renders.

If you pass an empty array, the effect runs only once, similar to `componentDidMount`

If you pass an array of variables, the effect runs only when those variable change.