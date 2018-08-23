# What is JSX? 
  - A syntax extension to JS, recommended to use with React to describe what the UI should look like.
  - `const name = 'Josh Perez';`
     `const element = <h1>Hello, {name}</h1>;`
  - It is also valid for expression inside the curly {name} ex: user.firstname, formatName(user)
  - For string literals, you should use quotes `const element = <div tabIndex="0"></div>;`
  - For JS expressions, curly braces `const element = <img src={user.avatarUrl}></img>;`
  
 ## Rendering Elements:
 - An element desribes what you want to see on the screen `const element = <h1>Hello, world</h1>;`
 - `<div id="root"></div>` root DOM node is managed by React DOM, to render a React element into root DOM node, pass both to ReactDOm.render()
 - `const element = <h1>Hello, world</h1>;` passing element Hello world, to the root DOM
 - `ReactDOM.render(element, document.getElementById('root'));`

## Components:
- A component in React is like JS function. Always start component name with capital letter
- lowercase letter is for DOM tags, component requires capitilizae
- `function Welcome(props) {`
  `return <h1>Hello, {props.name}</h1>;}`
- `class Welcome extends React.Component {` 
  `render() {`
   ` return <h1>Hello, {this.props.name}</h1>;}}`
- One is a component and the second is ES6 class, quivalent.
- To render a component, React passes this as a single object, we call this object "props"
- `function Welcome(props) {`
 ` return <h1>Hello, {props.name}</h1>;`
`}`
`const element = <Welcome name="Sara" />;`  This is the element, we pass it thtough Wecome component and returns Hellow Sara
`ReactDOM.render(`
  `element,`
  `document.getElementById('root')`
`);`
-All react components must act lke a pure functions, respect to their props. NO CHANGE 
`function withdraw(amount) {` 
  `account total -=amounnt;`   AMOUNT cannot be change
