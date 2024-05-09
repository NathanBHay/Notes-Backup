React is a popular [[JavaScript]] web framework. It was created by Facebook and is considered one of the most popular frameworks.

# JSX
JavaScript XML is a way to factor [[HTML]] snippets within JS code. This is declared with HTML tags found within JS code with brackets. It follows the form:
```jsx
const elem = (
	<div>Words</div>
);
```

[[CSS]] styles can also be used through JS objects. Elements can be chained together with the injection syntax `{var}`. These both can be done with:
```jsx
const style = { color:red; }
const title = <h1>Title</h1>
const elem = <div style='style'> {title} </div>;)
```

The `render` term can be used to display elements made from the JSX. This follows the syntax:
```jsx
const rootElement = document.getElementById('root')
ReactDOM.render(elem, rootElement)
```

# Components
A React component is a small reusable code snippet that is responsible for one part of the GUI. These components can be functional, or class based. They follow a life cycle which is defined as:
- **Mounting**, which is when a component is called and constructed for the first time.
- **Updating**, which is how the component is edited.
- **Unmounting**, which is when the component is destroyed ready to be mounted again.

Components can be called with the syntax `<var />`, where `var` is a functional component.

# Props
Props are a way to inject data from one component into another. A property is different from a component as it allows for... It can be done with the syntax:
```jsx
const elem = (props) => { 
	return(
		<div> {props.entry1} {props.entry2} </div>	
	)
}
<elem entry1 = 'val', entry2 = 'val' />
```

This will instantiate a component with the following props. Objects and arrays can be used within props as to allow for more succinct syntax. These

# Classes
React classes function similar to the functional approach to however allow for unique features such as state and inheritance. It is done through combining together rendered components and inheriting the props arguments. This is done through the syntax:
```jsx
import {Component} from 'react'
class App extends Component{
	constructor(props){
		super(props)
	}
	render() {
		<div> {this.props.entry} </div>
	}
}
```

This code can be destructured to simplify the `this` syntax. This is done by setting a variable to the *this* syntax with `const {entry} = this.props`.

The mounting process follows a procedure where `constructor` is executed before any other methods. This is then followed by the `getDerivedStateFromPos`, which derives a state from the props. This is then followed by the `render` and finally the `componentDidMount` which is used to interface with an API. This API interfacing is done with `fetch(url).then(...)`.

During the updating process `getDerivedStateFromPos` is executed first. This is then followed by `shouldComponentUpdate` which determines whether an update should happen. This will return a Boolean. The `render `operation will then be triggered again as to change the looks of the component. `componentDidUpdate` takes the arguments of the previous state and the current state and can run an operation.

States can be done by declaring a variable in class. This allows for the variable to be later changed with `this.setState({entry: val})`. These operations are commonly refractured as functions found within classes, and are the result of onclick actions.

# Exports
The file structure of a web page usually involves many pages. To achieve this the `export` operation is used as to allow for a function to be imported within another file. This can be done with the keyword `export` or `export default`.

# Events
Events are handled similar to traditional JS with the event linking together another function that triggers an effect.

A common event is the *onChange* event which is triggered by a change in a value field. When this happens the following code can be used to read an input:
```jsx
handeChange = (e) => { const val = e.target.value }
```

From this code an effect can be used to change a state. This code can also be destructured with `const {val1, val2} = e.target`, which allows all data to be collected.

# Routing
React Router allows for components to be connected together through domain address changes. This is done through a the `Route` component which allows for a `path` and `component` props to change the components. A `navLink` is another component that can be used to route messages. A `redirect` can also be used to route given a condition.

# Hooks
Hooks are a method of dealing with state through a more 'functional' approach. This is done with a new set of tools that are able to handle states on an individual, and global level.

## Use State
**Use State** is the most basic hook. It allows for the creation of a local state within the component as well as a function that can be used to set that state. It can be written with the syntax:
```jsx
const [val, func] = useState<Type>(default val)
```
Upon changing this value with the function call the component will re-render. When using the set state function a function can be called with a parameter of the previous state. This can provide greater clarity.

## Use Effect
**Use Effect** is another common hook which is used to apply side effects to your components. These effects include fetching data, updating the DOM or many other operations. It follows the syntax `useEffect(func, dependency)`. The first argument is the function that happens given the page is rendered again. The dependency is what forces the page to render which can be a change in props or state variable, etc. If the field is an empty list it will only happen once. Commonly a return case is used within the function as to minimize side effects.

**Use Layout Effect** is the same as use effect however fires before the re-render. This is commonly used to measure how a new layout which exists but hasn't been rendered fits. Therefore, allowing for changes to the layout before the new element renders. Another common use is when updating a [[React#Use Reference|reference]], before any other code runs.

## Use Context
**Use Context** is a hook which allows the management of global states. This can be used for themes, services and user settings. Context is handled by creating a context with `createContext`, and then using that context with `useContext`. This allows components to easily share state values without the need for prop drilling.

## Use Reference
**Use Reference** is a hook which is used to store values that persist through renders. This value can be changed without causing a re-render. It can be called with the command `useref(default val`. There are many common uses for the hook these include:
- **Accessing DOM elements** which is done by assigning an element's `ref={var}`, where var is the name of the variable made from the hook.
- **Keeping old states** which can be done by making a function that upon re-render records the last state.

## Use Reducer
**Use Reducer** is similar to [[React#Use State|use state]] however allows for a more complex reducer function to be used.

# States
Manipulating state is the key to dynamic websites. This can be done through either of the methods from the previous sections on [[React#Classes|classes]] and [[React#Hooks|hooks]]. The process of knowing what constitutes a state follows the simple logic of:
1. Identifying a component's different states.
2. Determining what triggers those states.
3. Represent all the states and in between states as separate variables.
4. Remove any non-essential states.
5. Connect event handlers to states

Some rules when creating states include:
- Group related states. If two states are updated at the same time most likely they can be merged.
- Avoid contradictions in states. Avoid making states that have the possibility to disagree with each other.
- Avoid redundant states. If you don't need a state, or the state is the same remove it.
- Avoid deeply hierarchical states. Prefer flat states over tall states.

Whenever two components need to access the same state, first try to lift the state up to the furthest in the hierarchy, and then use props to pass it down.
