# What is JSX? 
  - A syntax extension to JS, recommended to use with React to describe what the UI should look like.
  - `const name = 'Josh Perez';`
     `const element = <h1>Hello, {name}</h1>;`
  - It is also valid for expression inside the curly {name} ex: user.firstname, formatName(user)
  - For string literals, you should use quotes `const element = <div tabIndex="0"></div>;`
  - For JS expressions, curly braces `const element = <img src={user.avatarUrl}></img>;`
  - JSX is a special syntax to write React in a easier structures.
  
 ## Rendering Elements:
 - Rendering element desribes what you want to see on the screen `const element = <h1>Hello, world</h1>;`
 - `<div id="root"></div>` root DOM node is managed by React DOM, to render a React element into root DOM node, pass both to ReactDOm.render()
 - `const element = <h1>Hello, world</h1>;` passing element Hello world, to the root DOM
 - `ReactDOM.render(element, document.getElementById('root'));`

## Components:
- A collection of JS functions that produce HTML
- React component class is use to tell React what we want to see on the screen.
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
-  ` return <h1>Hello, {props.name}</h1>;`
- `}`
- `const element = <Welcome name="Sara" />;`  This is the element, we pass it thtough Wecome component and returns Hellow Sara
- `ReactDOM.render(`
- `element,`
-  `document.getElementById('root')`
 `);`
- All react components must act lke a pure functions, respect to their props. NO CHANGE 
- `function withdraw(amount) {` 
  `account total -=amounnt;`   AMOUNT cannot be change
  - PROPS are variables that you pass from the parent to the child, therefore child cannot modify. It's helpful because when bugs arise, you know the child didn't modify to begin with. 
  
  ## State: 
  - To remember things, components uses state.
  - Each class has its own state object, and state will force render to rerun if theres a state object
  - React components can have state by settting this.state in their constructors.
  - Requires to define a constructor and super, then a this.state.
  - In JS classes, you always call super when defining the constructor of a sublass. All React component classes that have a constructor should start it with a super(props) call.
  - `	class Square extends React.Component {`
 ` constructor(props) {`
    `super(props);`
    `this.state = {`
     ` value: null,`
  `  };`
`  }`
	`render() {`
    `return (`
      `<button className="square" onClick={event => this.setState({ term: event.target.value}>`
       ` {this.props.value}`
      `</button>`
   ` );`
 ` }`
  
  ## Array to List:
 - By using map(), we can convert array to a list
 - `const numbers = [1, 2, 3, 4, 5];`
 - `const doubled = numbers.map((number) => number * 2);`
 -  `console.log(doubled);`
 - A “key” is a special string attribute you need to include when creating lists of elements
 - Keys help React identify which items have changed, are added, or are removed.
 - By giving key an id of a list, we can identify which one needs update etc...
 - Use chrome browser inspect to find a key that we can use.
  ## HTML tags:
  - The `<div>` tag defines a division or a section in an HTML document.
  - The `<h1>` to `<h6>` tags are used to define HTML headings. Bigger to smaller font
  - The `<button>` tag defines a clickable button.
  - The `<ol>` tag defines an ordered list. An ordered list can be numerical or alphabetical.
  - The `<li>` tag defines a list item.
  - The <ul> tag defines an unordered (bulleted) list.
  
  ## Function to Class components 
  - Class has more functionality
  - `class Clock extends React.Component {
  - `render() {`
  - `return (`
  -    `<div>`
  -      `<h1>Hello, world!</h1>`
  -      `<h2>It is {this.props.date.toLocaleTimeString()}.</h2>`
  -    `</div>`
  
  ## Commandline:
  - npm install -g create-react-app: to install the react app 
  - create-react-app lottery-react: create the lottery react app 
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
  
