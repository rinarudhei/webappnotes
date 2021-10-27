# **React Lifecycle**
- source: [w3Schools](https://www.w3schools.com/react/react_lifecycle.asp)
- date: 27 October 2021

## React Lifecycle
3 phases: 
- [Mounting](#mounting)
- [Updating](#updating)
- [Unmounting](#unmounting)

## <a id="mounting"></a>**Mounting**
4 methods:
1. constructor()
2. getDerivedStateFromProps()
3. render()
4. componentDidMount()

### 1. constructor
- called before anything else. set up initial state. 
- called with props as its argument
- require to invoke "super(props)"  

### 2. getDerivedStateFromProps
- called right before rendering the element(s) in the DOM
- natural place to set the state object based on the initial props

### 3. render
- method that actually outputs the HTML to the DOM

### 4. componentDidMount
- called after the component is rendered

## <a id="updating"></a>**Updating**
A component is updated whenever there is a change in the component's ``state`` or ``props``.
5 methods :
1. getDerivedStateFromProps()
2. shouldComponentUpdate()
3. render()
4. getSnapshotBeforeUpdate()
5. componentDidUpdate()

### 1. getDerivedStateFromProps
- This is the first method that is called when a component gets updated.

### 2. shouldComponentUpdate
- return boolean value to allow or block any update

### 3. render
### 4. getSnapshotBeforeUpdate
- access ``props`` and ``state`` before the update
- If the getSnapshotBeforeUpdate() method is present, you should also include the componentDidUpdate() method, otherwise you will get an error.
### 5. componentDidUpdate
- called after the component is updated in the DOM

## <a id="unmounting"></a>**Unmounting**
- is when a component is removed from the DOM
1 method:
### componentWillUnmount
-  is called when the component is about to be removed








