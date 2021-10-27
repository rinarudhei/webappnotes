# **React Lifecycle**
- source: [w3Schools](https://www.w3schools.com/react/react_hooks.asp)
- date: 27 October 2021


- [useState](#mounting)
- [useEffect](#updating)
- [useContext](#unmounting)
- [useReducer](#unmounting)
  - basically the same for useState, but allow us to make custom state logic. To make simple of a complex logic 
- [useRef](#unmounting)
  - persist values between renders.
  - to store a mutable value that does not cause a re-render when updated
  - to access a DOM element directly
- [useCallback](#unmounting)
  - Every time a component re-renders, its functions get recreated -> if the function is passed into a child component, the child component will be rerendered, we don't want that to happen.
  - use the useCallback hook to prevent the function from being recreated unless necessary
- [useMemo](#unmounting)
- [React Custom Hooks](#unmounting)

Hooks were added to React in version 16.8. Hooks allow us to "hook" into React features such as state and lifecycle methods.

3 rules for hooks: 
- Hooks can only be called inside React function components.
- Hooks can only be called at the top level of a component.
- Hooks cannot be conditional











