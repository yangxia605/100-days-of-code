# 100-days-of-code-study
## I will code for at least an hour a day for the next 100 days.[come on!!!]

#### Day 1:2018-01-20
####  sort()
The sort() method sorts the elements of an array in place and returns the array. The sort is not necessarily stable. The default sort order is according to string Unicode code points.
###### more details:
```html 
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/sort 
```

```js
var array = [1, 12, 21, 2];
array.sort(function(a, b) {
  return a - b;
});
```
###### this is my practise about this function in the freecodecamp.org
```html
https:www.freecodecamp.org/challenges/where-do-i-belong
```
#### filter()
The filter() method creates a new array with all elements that pass the test implemented by the provided function.
###### more details:
```html 
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Array/filter
```
###### this is my practise about this function in the freecodecamp.org
```html
https://www.freecodecamp.org/challenges/falsy-bouncer
```
____________________________________________________________________
#### Day 2:2018-01-21
#### learn ES6 in the udemy.com and yuanyifeng's blog
```html
https://www.udemy.com/es6-javascript-reloaded/learn/v4/t/lecture/8504648?start=0
http://es6.ruanyifeng.com/#docs/
```
#### let 和 const 命令
#### let 命令在代码块内有效
```js
{
  let a = 10;
  var b = 1;
}
a // ReferenceError: a is not defined.
b // 1
function checkScope() {
"use strict";
  let i = "function scope";
  if (true) {
    let i = "block scope";
    console.log("Block scope i is: ", i);
  }
  console.log("Function scope i is: ", i);
  return i;
}
```
#### let 不存在变量提升
```js
// var 的情况
console.log(foo); // 输出undefined
var foo = 2;

// let 的情况
console.log(bar); // 报错ReferenceError
let bar = 2;
```
#### const声明一个只读的常量。一旦声明，常量的值就不能改变。
###### const实际上保证的，并不是变量的值不得改动，而是变量指向的那个内存地址不得改动。对于简单类型的数据（数值、字符串、布尔值），值就保存在变量指向的那个内存地址，因此等同于常量。但对于复合类型的数据（主要是对象和数组），变量指向的内存地址，保存的只是一个指针，const只能保证这个指针是固定的，至于它指向的数据结构是不是可变的，就完全不能控制了。因此，将一个对象声明为常量必须非常小心。
```js
const foo = {};

// 为 foo 添加一个属性，可以成功
foo.prop = 123;
foo.prop // 123

// 将 foo 指向另一个对象，就会报错
foo = {}; // TypeError: "foo" is read-only
```
#### Default Parameters

解构复制允许指定默认值
_______________________________________________________________________________________________________________________

#### Day 3: 2018-01-22
###### Diff Two Arrays:learn to find a better way to improve that 算法（Algorithm） problem。
First of my mind :
```js
function diffArray(arr1, arr2) {
  var newArr = [];
  // Same, same; but different.
  arr1.filter(function(item){
    return arr2.indexOf(item) === -1 ? newArr.push(item) : "";
  });
  arr2.filter(function(item){
    return arr1.indexOf(item) === -1 ? newArr.push(item) : "";
  });
  return newArr;
}
```
 ###### 相关算法知识：Algorithm Complexity：2* n* n;


*****then I improved it
```js
function diffArray(arr1, arr2) {
  var newArr = [];
  // Same, same; but different.
newArr = arr1.concat(arr2).filter(function(v, i, arr) {
  return arr.indexOf(v) == arr.lastIndexOf(v);
});
   return newArr;
}
```
the amount of code is less,but I found the Algorithm Complexity is :(n + n) * (n + n),which is more bad than last answer.So I will continue to look for solutions.

_________________________________________________________________________________________________________________________

#### Day 4: 2018-01-23
#### Title Case a Sentence
```js
function titleCase(str) {
 var convertToArray = str.toLowerCase().split(" "); //split the str into an array
 for(var i = 0;i < convertToArray.length;i++){ 
   var char = convertToArray[i].charAt(0); //find the first letter
   convertToArray[i]=convertToArray[i].replace(char,function replace(char){ 
     return char.toUpperCase(); }); //replace the first letter into UpperCase
 }
  return convertToArray.join(" ");
}
```
####  Mutate an Array Declared with const
```js
"use strict";
const s = [5, 6, 7];
s = [1, 2, 3]; // throws error, trying to assign a const
s[2] = 45; // works just as it would with an array declared with var or let
console.log(s); // returns [5, 6, 45]
```
####  Prevent Object Mutation:Object.freeze
Once the object is freezed, you can no longer add/update/delete properties from it. Any attempt at changing the object will be rejected without any error.
```js
let obj = {
  name: "mianmian"
  hobby:"coding"
  };
Object.freeze(obj);
obj.hobby = "bad"; //will be ignored. Mutation not allowed
obj.hobby = "Test"; // will be ignored. Mutation not allowed
console.log(obj); 
// { name: "mianmian", review:"coding"}
```
####  Use Arrow Functions to Write Concise Anonymous Functions
```js
const magic = () => new Date();
const myConcat = (arr1, arr2) => arr1.concat(arr2);
```
####  Write Higher Order Arrow Functions
Use arrow function syntax to compute the square of only the positive integers (fractions are not integers) in the array realNumberArray and store the new array in the variable squaredIntegers.
```js
const realNumberArray = [4, 5.6, -9.8, 3.14, 42, 6, 8.34];
const squareList = (arr) => {
  "use strict";
  // change code below this line
  let reg = /^[0-9]*[1-9][0-9]*$/;//正整数
  const squaredIntegers = arr.filter((item) => reg.test(item)).map((ele) => ele *ele);
  // change code above this line
  return squaredIntegers;
};
// test your code
const squaredIntegers = squareList(realNumberArray);
```
#### Use the Rest Operator with Function Parameters
```js
const sum = (function() {
  "use strict";
  return function sum(...args) {
    return args.reduce((a, b) => a + b, 0);
  };
})();
console.log(sum(1, 2, 3)); // 6
```
#### Use the Spread Operator to Evaluate Arrays In-Place
###### The ES5 code below uses apply() to compute the maximum value in an array:
```js
var arr = [6,89,3,45];
var maximus = Math.max.apply(null,arr);//returns 89
```
###### The spread operator makes this syntax much better to read and maintain.
```js
const arr = [6, 89, 3, 45];
const maximus = Math.max(...arr); // returns 89
```
####  Use Destructuring Assignment to Assign Variables from Objects
```js
Consider the following ES5 code:

var voxel = {x: 3.6, y: 7.4, z: 6.54 };
var x = voxel.x; // x = 3.6
var y = voxel.y; // y = 7.4
var z = voxel.z; // z = 6.54
```

###### ES6 destructuring syntax:
```js
const { x, y, z } = voxel; // x = 3.6, y = 7.4, z = 6.54
```
If instead you want to store the values of voxel.x into a, voxel.y into b, and voxel.z into c, you have that freedom as well.
```js
const { x : a, y : b, z : c } = voxel // a = 3.6, b = 7.4, c = 6.54
```
#### sass(Syntactically Awesome StyleSheets)
#### Store Data with Sass Variables
```js
$main-fonts: Arial, sans-serif;
$headings-color: green;

//To use variables:
h1 {
  font-family: $main-fonts;
  color: $headings-color;
}
```
____________________________________________________________________________________________________________________
## Day 5:2018-01-24
#### Use Destructuring Assignment with the Rest Operator to Reassign Array Elements
```js
before :
Array.prototype.slice()
now:
const [a,b...arr]=[1,2,3,4,5];
console.log(arr) //[3,4,5]
```
#### Use Destructuring Assignment to Pass an Object as a Function's Parameters
```js
const profileUpdate = (profileData) => {
  const { name, age, nationality, location } = profileData;
  // do something with these variables
}
```
#### Create Strings using Template Literals
```js
const person = {
  name: "Zodiac Hasbro",
  age: 56
};
// string interpolation
const greeting = `Hello, my name is ${person.name}!`
```
####  Write Concise Object Literal Declarations Using Simple Fields
```js
Before:
const getMousePosition = (x, y) => ({
  x: x,
  y: y
});
Now:
const getMousePosition = (x, y) => ({ x, y });
```
####  Write Concise Declarative Functions with ES6
```js
Before:
const person = {
  name: "Taylor",
  sayHello: function() {
    return `Hello! My name is ${this.name}.`;
  }
};
Now:
const person = {
  name: "Taylor",
  sayHello() {
    return `Hello! My name is ${this.name}.`;
  }
};
```
#### Use class Syntax to Define a Constructor Function
```js
class SpaceShuttle {
  constructor(targetPlanet){
    this.targetPlanet = targetPlanet;
  }
}
const zeus = new spaceShuttle('Jupiter');
```
###### that the class keyword declares a new function, and a constructor was added, which would be invoked when new is called - to create a new object.
#### Use getters and setters to Control Access to an Object
```js
class Book {
  constructor(author) {
    this._author = author;
  }
  // getter
  get writer(){
    return this._author;
  }
  // setter
  set writer(updatedAuthor){
    this._author = updatedAuthor;
  }
}
const lol = new Book('anonymous');
console.log(lol.writer);
lol.writer = 'wut';
console.log(lol.writer);
```
#### Understand the Differences Between import and require
```js
import { countItems } from "math_array_functions"
```
###### Note
The whitespace surrounding the function inside the curly braces is a best practice - it makes it easier to read the import statement.
###### Note
In most cases, the file path requires a ./ before it; otherwise, node will look in the node_modules directory first trying to load it as a dependencie.
#### Use * to Import Everything from a File
```js
import * as myMathModule from "math_functions"
myMathModule.add(2,3);
myMathModule.subtract(5,3);
```
## React
#### Render a Class Component to the DOM
ReactDOM.render(componentToRender, targetNode). The first argument is the React component that you want to render. The second argument is the DOM node that you want to render that component within.
#### Pass Props to a Stateless Functional Component
```js
<App>
  <Welcome user='Mark' />
</App>

const Welcome = (props) => <h1>Hello, {props.user}!</h1>
```
####  Pass an Array as Props
```js
const List= (props) => {
  { /* change code below this line */ }
  return <p>{props.tasks.join(', ')}</p>
  { /* change code above this line */ }
};

class ToDo extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <h1>To Do Lists</h1>
        <h2>Today</h2>
        { /* change code below this line */ }
        <List tasks={["coding","codingAgain"]}/>
        <h2>Tomorrow</h2>
        <List tasks={["eadting","eatingAgain","sleep"]}/>
        { /* change code above this line */ }
      </div>
    );
  }
};
```
#### Use Default Props
```js
MyComponent.defaultProps = { location: 'San Francisco' }
```
#### Override Default Props
####  Use PropTypes to Define the Props You Expect
```js
MyComponent.propTypes = {
  handleclick: PropTypes.func.isRequired
}
```  
#### Access Props Using this.props
if an ES6 class component has a prop called data, you write {this.props.data} in JSX.
#### Stateless Functional Components
A stateless functional component is any function you write which accepts props and returns JSX. A stateless component, on the other hand, is a class that extends React.Component, but does not use internal state
```js
class CampSite extends React.Component {
  constructor(props) {
    super(props);
  }
  render() {
    return (
      <div>
        <Camper name={"yangxia"}/>
      </div>
    );
  }
};
// change code below this line
class Camper extends React.Component {
  constructor(props) {
    super(props);
  }
  render(){
    return (
    <div>
        <p>{this.props.name}</p>
        </div>
    )
  }
}
Camper.propTypes={
  name : PropTypes.string.isRequired
}
Camper.defaultProps = { name: 'CamperBot' }
```
#### Create a Stateful Component
```js
//You create state in a React component by declaring a state property on the component class in its constructor. This initializes the component with state when it is created. The state property must be set to a JavaScript object. Declaring it looks like this:

this.state = {
  // describe your state here
}
```
#### Set State with this.setState
```js
this.setState({
 username: 'Lewis'
});

```
#### Bind 'this' to a Class Method
```js
class MyComponent extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      itemCount: 0
    };
    // change code below this line
this.addItem = this.addItem.bind(this)
    // change code above this line
  }
  addItem() {
    this.setState({
      itemCount: this.state.itemCount + 1
    });
  }
  render() {
    return (
      <div>
        { /* change code below this line */ }
        <button onClick = {this.addItem}>Click Me</button>
        { /* change code above this line */ }
        <h1>Current Item Count: {this.state.itemCount}</h1>
      </div>
    );
  }
};
```
_________________________________________________________________________________________________________________
## Day 6:2018-01-26
#### learn the js utility library === lodash
#### A modern JavaScript utility library delivering modularity, performance & extras.
#### map an object
```js
_.forIn(new Foo, function(value, key) {
  console.log(key);
});
```
## Mobx 
Package with React component wrapper for combining React with MobX. Exports the observer decorator and some development utilities.
```js
import {observer} from 'mobx-react';//This package provides the bindings for MobX and React
```
#### The gist of MobX
###### 1. Define your state and make it observable
```js
import {observable} from 'mobx';

var appState = observable({
    timer: 0
});
```
###### 2. Create a view that responds to changes in the State
```js
import {observer} from 'mobx-react';

@observer
class TimerView extends React.Component {
    render() {
        return (<button onClick={this.onReset.bind(this)}>
                Seconds passed: {this.props.appState.timer}
            </button>);
    }

    onReset () {
        this.props.appState.resetTimer();
    }
};

ReactDOM.render(<TimerView appState={appState} />, document.body);
```
###### 3. Modify the State
```js
appState.resetTimer = action(function reset() {
    appState.timer = 0;
});

setInterval(action(function tick() {
    appState.timer += 1;
}), 1000);
```
________________________________________________________________________________________________________________
## Day 7:2018-01-27
React and MobX together are a powerful combination. React renders the application state by providing mechanisms to translate it into a tree of renderable components. MobX provides the mechanism to store and update the application state that React then uses.
```html
Events => Actions => State => Computed values => Reactions
```
#### 1.Events invoke actions.Actions are the only thing that modify state and may have other side effects
```js
@actions onClick = () => {
 this.props.todo.done = true;
 }
 ```
 #### 2. State is observable and minimally defined.Should not contain redudant or derivable data.
 ```js
 @observable todos =[{
 title:"learn Mobx",
 done:false,
 }]
 ```
 #### 3. Computed values are values that can be derived from the state using a pure function.
 ```js
 @computed get completedTodos(){
    return this.todos.filter(
      todo => todo.done
 ) }
 ```
 #### 4.Reactions are like computed values and react to state changes.But they produce a side effect instead of a value.like updating the UI
 ```js
 const Todos = observer({todos} => <ul> todos.map(todo => <TodoView .../> </ul>)
 ```
________________________________________________________________________________________________________________
## Day 8:2018-01-28
#### Provider and inject
Provider is a component that can pass stores (or other stuff) using React's context mechanism to child components. This is useful if you have things that you don't want to pass through multiple layers of components explicitly.

inject can be used to pick up those stores. It is a higher order component that takes a list of strings and makes those stores available to the wrapped component.
```js
@inject("color") @observer
class Button extends React.Component {
  render() {
    return (
      <button style={{background: this.props.color}}>
        {this.props.children}
      </button>
    );
  }
}

class Message extends React.Component {
  render() {
    return (
      <div>
        {this.props.text} <Button>Delete</Button>
      </div>
    );
  }
}

class MessageList extends React.Component {
  render() {
    const children = this.props.messages.map((message) =>
      <Message text={message.text} />
    );
    return <Provider color="red">
        <div>
            {children}
        </div>
    </Provider>;
  }
}
```
________________________________________________________________________________________________________
## Day 9:2018-01-29
 learn the react component lifecycle from freeCodeCamp
 #### componentWillReceiveProps()
  which is called whenever a component is receiving new props. This method receives the new props as an argument, which is usually written as nextProps. You can use this argument and compare with this.props and perform actions before the component updates. For example, you may call setState() locally before the update is processed.
  ```js
  class Dialog extends React.Component {
  constructor(props) {
    super(props);
  }
  componentWillUpdate() {
     console.log('Component is about to update...');
}
  // change code below this line
componentWillReceiveProps(nextProps) {
  console.log(this.props);
 console.log(nextProps);
}
componentDidUpdate(nextProps) {
     console.log('Component is didUpdate...');
}
  // change code above this line
  render() {
    return <h1>{this.props.message}</h1>
  }
};

class Controller extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      message: 'First Message'
    };
    this.changeMessage = this.changeMessage.bind(this);
  }
  changeMessage() {
    this.setState({
      message: 'Second Message'
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.changeMessage}>Update</button>
        <Dialog message={this.state.message}/>
      </div>
    );
  }
};
```
#### shouldComponentUpdate()
can call when child components receive new state or props, and declare specifically if the components should update or not
and it takes nextProps and nextState as parameters.
```js
class OnlyEvens extends React.Component {
  constructor(props) {
    super(props);
  }
  shouldComponentUpdate(nextProps, nextState) {
    console.log('Should I update?');
     // change code below this line
    console.log(nextProps)
    var odd = (nextProps.value)%2;
    console.log("odd"+odd);
    if(!odd ){
      return true;
    } 
     // change code above this line
  }
  componentWillReceiveProps(nextProps) {
    console.log('Receiving new props...');
  }
  componentDidUpdate() {
    console.log('Component re-rendered.');
  }
  render() {
    return(  <div>
      <h1>{this.props.value}</h1>
    </div>) 
  
  }
};

class Controller extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      value: 0
    };
    this.addValue = this.addValue.bind(this);
  }
  addValue() {
    this.setState({
      value: this.state.value + 1
    });
  }
  render() {
    return (
      <div>
        <button onClick={this.addValue}>Add</button>
        <OnlyEvens value={this.state.value}/>
      </div>
    );
  }
};
```
_____________________________________________________________________________________________________________
## Day 10: 2018-01-30
#### React: Use Array.map() to Dynamically Render Elements
https://beta.freecodecamp.org/en/challenges/react/use-arraymap-to-dynamically-render-elements
>
I'm confused about the "dynamically return an unordered list" and not solve the problem.But I have asked the forum for help.
and I will keep track of this problem until solve it.
the code like as below:
```js
const textAreaStyles = {
  width: 235,
  margin: 5
};

class MyToDoList extends React.Component {
  constructor(props) {
    super(props);
    // change code below this line
this.state = {
  userInput : '',
  toDoList : []
}
    // change code above this line
    this.handleSubmit = this.handleSubmit.bind(this);
    this.handleChange = this.handleChange.bind(this);
  }
  handleSubmit() {
    const itemsArray = this.state.userInput.split(',');
    this.setState({
      toDoList: itemsArray
    });
  }
  handleChange(e) {
    this.setState({
      userInput: e.target.value
    });
  }
  render() {
    const items =this.state.toDoList.map(function(item,index){
      return <li key={index}> {item} </li>
    })
    return (
      <div>
        <textarea
          onChange={this.handleChange}
          value={this.state.userInput}
          style={textAreaStyles}
          placeholder="Separate Items With Commas" /><br />
        <button onClick={this.handleSubmit}>Create List</button>
        <h1>My "To Do" List:</h1>
        <ul>
          {items}
        </ul>
      </div>
    );
  }
};
```
___________________________________________________________________________________________________________________
## Day 11: 2018-01-31 [REDUX]
## Redux: Create a Redux Store
【ps】：yesterDay's question has been solved after my feedback.My code is not modified,but the case passed.
```js
const reducer = (state = 5) => {
  return state;
}

// Redux methods are available from a Redux object
// For example: Redux.createStore()
// Define the store here:
const store = Redux.createStore(reducer);
```
## Get State from the Redux Store
```js
const store = Redux.createStore(
  (state = 5) => state
);

// change code below this line
const currentState = store.getState();
```
## Redux Action
 Redux actions as messengers that deliver information about events happening in your app to the Redux store. The store then conducts the business of updating state based on the action that occurred.
 ```js
 const action = {
  type:'LOGIN',
}
```
## an Action Creator
After creating an action, the next step is sending the action to the Redux store so it can update its state. In Redux, you define action creators to accomplish this. An action creator is simply a JavaScript function that returns an action. In other words, action creators create objects that represent action events.
```js
const action = {
  type: 'LOGIN'
}
// Define an action creator here:
function actionCreator(action) {
  return action
}
```
## Dispatch an Action Event
```js
const store = Redux.createStore(
  (state = {login: false}) => state
);

const loginAction = () => {
  return {
    type: 'LOGIN'
  }
};

// Dispatch the action here:
store.dispatch(loginAction());
```
## Handle an Action in the Store
After an action is created and dispatched, the Redux store needs to know how to respond to that action. This is the job of a reducer function.  A reducer takes state and action as arguments, and it always returns a new state.Another key principle in Redux is that state is read-only. In other words, the reducer function must always return a new copy of state and never modify state directly. 
```js 
const defaultState = {
  login: false
};

const reducer = (state = defaultState, action) => {
  // change code below this line
if(action.type == 'LOGIN'){
  return Object.assign({}, state, {
      login: true
      })
}
  return state
  // change code above this line
};

const store = Redux.createStore(reducer);

const loginAction = () => {
  return {
    type: 'LOGIN'
  }
};
```
_________________________________________________________________________________________________________
## Day 12:2018-02-01
## Redux: Use a Switch Statement to Handle Multiple Actions
```js
const defaultState = {
  authenticated: false
};

const authReducer = (state = defaultState, action) => {
  // change code below this line
switch (action.type){
    case 'LOGIN':
      return Object.assign({},state,{authenticated: true})
    case 'LOGOUT':
     return  Object.assign({},state,{authenticated: false})
    default:
      return state
}
  // change code above this line
};

const store = Redux.createStore(authReducer);

const loginUser = () => {
  return {
    type: 'LOGIN'
  }
};

const logoutUser = () => {
  return {
    type: 'LOGOUT'
  }
};
```
##  Combine Multiple Reducers [  all app state is held in a single state object in the store.  ]
```js
const rootReducer = Redux.combineReducers({
  auth: authenticationReducer,
  notes: notesReducer
});
```
##  Send Action Data to the Store
```js
const ADD_NOTE = 'ADD_NOTE';

const notesReducer = (state = 'Initial State', action) => {
  switch(action.type) {
    // change code below this line
    case ADD_NOTE:
      return action.text 
    // change code above this line
    default:
      return state;
  }
};

const addNoteText = (note) => {
  // change code below this line
return {
  type: ADD_NOTE,
  text: note
}
  // change code above this line
};

const store = Redux.createStore(notesReducer);

console.log(store.getState());
store.dispatch(addNoteText('Hello!'));
console.log(store.getState());
```
##  Use Middleware to Handle Asynchronous Actions
##  Write a Counter with Redux
```js
const INCREMENT = 'INCREMENT';
const DECREMENT = 'DECREMENT';

const counterReducer = (state=0, action) => {
  switch(action.type){
    case INCREMENT:
      return state+1;
    case DECREMENT:
      return state-1;
    default:
      return state;
  }
}

const incAction = () => {
  return  {
    type: INCREMENT
  }
};

const decAction = () => {
  return {
    type: DECREMENT
  }
};
const store = Redux.createStore(counterReducer);
```
##  Never Mutate State
```js
const ADD_TO_DO = 'ADD_TO_DO';

// A list of strings representing tasks to do:
const todos = [
  'Go to the store',
  'Clean the house',
  'Cook dinner',
  'Learn to code',
];

const immutableReducer = (state = todos, action) => {
  switch(action.type) {
    case ADD_TO_DO:
      // don't mutate state here or the tests will fail
      return [
        ...state,
        action.todo
      ]
    default:
      return state;
  }
};

// an example todo argument would be 'Learn React',
const addToDo = (todo) => {
  return {
    type: ADD_TO_DO,
    todo
  }
}

const store = Redux.createStore(immutableReducer);
```
______________________________________________________________________________________________________
## Day 13:2018-02-02
## Getting Started with React Redux
#### React is a view library that you provide with data, then it renders the view in an efficient, predictable way
#### Redux is a state management framework that you can use to simplify the management of your application's state.
## Manage State Locally First
```js
class DisplayMessages extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      messages: []
    }
  }
  // add handleChange() and submitMessage() methods here
handleChange(e){
  this.setState({
    input:e.target.value
  })
}
  submitMessage(){
    const itemInput = this.state.input
    this.setState({
       messages: this.state.messages.concat(itemInput),
        input: ''})
  }
  render() {
    const items = this.state.messages.map((item,index) => {
      return <li key={index}>{item}</li>
    })
    return (
      <div>
        <h2>Type in a new Message:</h2>
        { /* render an input, button, and ul here */ }
        <input value={this.state.input} onChange={(e)=> this.handleChange(e)}/>
        <button onClick={() => this.submitMessage() }>Add message</button>
        <ul>
          {items}
        </ul>
        { /* change code above this line */ }
      </div>
    );
  }
};
```
## Use Provider to Connect Redux to React
#### React Redux provides its react-redux package to help accomplish providing React access to the Redux store and the actions it needs to dispatch updates.
####  The Provider is a wrapper component from React Redux that wraps your React app. This wrapper then allows you to access the Redux store and dispatch functions throughout your component tree
```js
<Provider store={store}>
  <App/>
</Provider>
```
```js
// Redux Code:
const ADD = 'ADD';

const addMessage = (message) => {
  return {
    type: ADD,
    message
  }
};

const messageReducer = (state = [], action) => {
  switch (action.type) {
    case ADD:
      return [
        ...state,
        action.message
      ];
    default:
      return state;
  }
};



const store = Redux.createStore(messageReducer);

// React Code:

class DisplayMessages extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      input: '',
      messages: []
    }
    this.handleChange = this.handleChange.bind(this);
    this.submitMessage = this.submitMessage.bind(this);
  }
  handleChange(event) {
    this.setState({
      input: event.target.value
    });
  }
  submitMessage() {
    const currentMessage = this.state.input;
    this.setState({
      input: '',
      messages: this.state.messages.concat(currentMessage)
    });
  }
  render() {
    return (
      <div>
        <h2>Type in a new Message:</h2>
        <input
          value={this.state.input}
          onChange={this.handleChange}/><br/>
        <button onClick={this.submitMessage}>Submit</button>
        <ul>
          {this.state.messages.map( (message, idx) => {
              return (
                 <li key={idx}>{message}</li>
              )
            })
          }
        </ul>
      </div>
    );
  }
};

const Provider = ReactRedux.Provider;

class AppWrapper extends React.Component {
  // render the Provider here
  render() {
    return (
        <Provider store={store}>
          <DisplayMessages />
        </Provider>
    )
  }
   
  // change code above this line
};
```
##  Map State to Props
#### The Provider component allows you to provide state and dispatch to your React components, but you must specify exactly what state and actions you want. This way, you make sure that each component only has access to the state it needs. You accomplish this by creating two functions: mapStateToProps() and mapDispatchToProps().In these functions, you declare what pieces of state you want to have access to and which action creators you need to be able to dispatch. Once these functions are in place, you'll see how to use the React Redux connect method to connect them to your components in another challenge.
```js
const state = [];

// change code below this line
const mapStateToProps =(state) => {
  return {
    messages: state
  }
}
```
##  Map Dispatch to Props
```js
const addMessage = (message) => {
  return {
    type: 'ADD',
    message: message
  }
};

// change code below this line

const mapDispatchToProps =(dispatch) => {

  return {

    submitNewMessage: (message) => {

      dispatch(addMessage(message))
    }
  }
}
```
## Connect Redux to React
#### Now that you've written both the mapStateToProps() and the mapDispatchToProps() functions, you can use them to map state and dispatch to the props of one of your React components. The connect method from React Redux can handle this task. This method takes two optional arguments, mapStateToProps() and mapDispatchToProps(). They are optional because you may have a component that only needs access to state but doesn't need to dispatch any actions, or vice versa.To use this method, pass in the functions as arguments, and immediately call the result with your component. This syntax is a little unusual and looks like:connect(mapStateToProps, mapDispatchToProps)(MyComponent)Note: If you want to omit one of the arguments to the connect method, you pass null in its place.
```js
const addMessage = (message) => {
  return {
    type: 'ADD',
    message: message
  }
};

const mapStateToProps = (state) => {
  return {
    messages: state
  }
};

const mapDispatchToProps = (dispatch) => {
  return {
    submitNewMessage: (message) => {
      dispatch(addMessage(message));
    }
  }
};

class Presentational extends React.Component {
  constructor(props) {
    super(props);
  }
  
  render() {
     console.log(this.props);
    return <h3>This is a Presentational Component</h3>
  }
};

const connect = ReactRedux.connect;
// change code below this line
const ConnectedComponent = connect(mapStateToProps, mapDispatchToProps)(Presentational)
```
#### By contrast, container components are connected to Redux. 
________________________________________________________________________________________________________________
## Day 16 2018-02-05
## Converts a timestamp to a date format.
```js
var date = new Date(timestamp); //获取一个时间对象
date.getFullYear();  // 获取完整的年份(4位,1970)
date.getMonth();  // 获取月份(0-11,0代表1月,用的时候记得加上1)
date.getDate();  // 获取日(1-31)
date.getTime();  // 获取时间(从1970.1.1开始的毫秒数)
date.getHours();  // 获取小时数(0-23)
date.getMinutes();  // 获取分钟数(0-59)
date.getSeconds();  // 获取秒数(0-59)
```
```js
example:you want to have :yyyy-MM-dd hh:mm:ss
var date = new Date(1398250549490);
Y = date.getFullYear() + '-';
M = (date.getMonth()+1 < 10 ? '0'+(date.getMonth()+1) : date.getMonth()+1) + '-';
D = date.getDate() + ' ';
h = date.getHours() + ':';
m = date.getMinutes() + ':';
s = date.getSeconds(); 
console.log(Y+M+D+h+m+s);//2014-04-23 18:55:49
```
## Converts the date format to a timestamp.
```js
var strtime = '2014-04-23 18:55:49:123';
var date = new Date(strtime); [or var date = new Date(strtime.replace(/-/g, '/'));]
// 有三种方式获取，在后面会讲到三种方式的区别
time1 = date.getTime();//精确到毫秒 1398250549123
time2 = date.valueOf();//精确到毫秒 1398250549123
time3 = Date.parse(date);//精确到秒，毫秒将用0来代替  1398250549000                         

```
## Moment.js 
#### Parse, validate, manipulate, and display dates and times in JavaScript.
__________________________________________________________________________________________________________________
## DAY 17:2018-02-06 go through the jest+enzyme and learn the js design mordern
## DAY 18:2018-02-07 finish set up the jest_enzyme test framework into my react project
__________________________________________________________________________________________________________________
## DAY 19:2018-02-08 
## CSS Latout Centering Techniques
#### Centering elements with CSS sometimes can be tricky. There are plenty of techniques that you could use but what technique you should use depends on the element and the content. Some questions that you might ask yourself when trying to center an element could be:
###### 1.Is it an inline or a block element?
###### 2.Is it just one line of text or multiple lines
###### 3.Does it have a fixed width and height or its size is unknown?
## Horizontal Centering(水平居中)
#### Text-aglign
#### In case you want to center an inline element you should apply it on its parent and not directly on that element:
```js
.parent { text-align: center; };
<div class="parent">
 <strong>I'm Centered</strong>
</div>
```
#### In case we have an inline-block element we could make it full width and apply text-align: center; on it directly instead of it's parent.
```js
strong {
 display: inline-block; 
 width: 100%;
 text-align: center;
}
```
## Absolute Position
```js
.parent { position: relative; }
.centered-element {
 position: absolute;
 left: 50%;
 transform: translateX(-50%);
}
```
#### An alternative to that, -if you have elements of known width- would be to use a negative margin-left instead of translateX:
```js
.centered-element { 
 position: absolute;
 width: 600px;
 left: 50%;
 margin-left: -300px; // Shift it back by half of it's size.
}
```
## Flex
```js
.parent { 
 display: flex; 
 justify-content: center;
 height: 100vh;
}
```
## Vertical Centering
#### Absolute Position
```js
.parent { position: relative; }
.centered-element {
 position: absolute;
 top: 50%;
 transform: translateY(-50%);
}
```
#### Table Cell
```js
.parent { 
 display: table;
 height: 100vh; 
}

.centered-element {
 display: table-cell;
 vertical-align: middle;
}
```
#### Line-height
```js
.box { 
 width: 600px;
 height: 600px;
 line-height: 600px;
}
<div class="box">
 <strong>I'm Centered</strong>
</div>
```
#### The Ghost Element
```js
.container { font-size: 0; }
.container::before {
  content: '';
  display: inline-block;
  height: 100%;
  vertical-align: middle;
}
.container strong {
 display: inline-block;
 vertical-align: middle;
 font-size: 1rem;
}
```
#### flex 垂直居中
```js
.vertical-container {
  height: 300px;
  display: -webkit-flex;
  display:         flex;
  -webkit-align-items: center;
          align-items: center;
  -webkit-justify-content: center;
          justify-content: center;
}
```
______________________________________________________________________________________________________________________
#### [day 20]:]i learned how to use the css to draw triangle.semicircle.circle .and also study the BFC.
______________________________________________________________________________________________________________________
#### [day 21]:moved the original css part over the "beta freecodecamp" @freeCodeCamp 
_____________________________________________________________________________________________________________________
#### [day 22]:Basic Algorithm has completed.
_____________________________________________________________________________________________________________________
#### [day 23]: learnt the typescript.first.i learned the concepts of typescript.then i try to code follow the example of https://github.com/Microsoft/TypeScript-React-Starter.git.but … i failed to compiled it.and has submit issue
______________________________________________________________________________________________________________________
#### [day 24]:i enrolled the lesson of "Build Front-End Web Applications from Scratch"  @Codecademy.which use react components. Today.i completed the basic of variables. Although i've already known the basics.i think lay a solid foundation will let me easier later.
________________________________________________________________________________________________________________________
#### [day 25]:the exercises of 'Create the Minesweeper Project' 
__________________________________________________________________________________________________________________________
#### manually created an empty game board and a simulated game board.
```js
const blankLine = '  |   |  ';
console.log('This is what an empty board would look like:');
console.log(blankLine);
console.log(blankLine);
console.log(blankLine);

const guessLine = '1 |   |  ';
const bombLine = '  | B |  ';
console.log('This is what a board with a guess and a bomb on it would look like: ');
console.log(guessLine);
console.log(bombLine);
console.log(blankLine);
```
_____________________________________________________________________________________________________________________
#### [day 26]:use function and array to print player boards and bomb boards.
```js
const printBoard = board => {
console.log('Current Board: ');
console.log(board[0].join(' | '));
console.log(board[1].join(' | '));
console.log(board[2].join(' | '));
};
let board = [[' ',' ',' '],[' ',' ',' '],[' ',' ',' ']];
printBoard(board);
board[0][1]='1';
board[1][0]='B';
printBoard(board);
```
______________________________________________________________________________________________________________________
#### [day 27]:use iterators and function to dynamically generate player board
###### 1.Used nested arrays to manually create a game board
###### 2.Wrote a function to neatly log the game board
###### 3.Accessed the nested arrays to set a guess and a bomb on the game board
______________________________________________________________________________________________________________________
#### 【day 28】Do my codeCademy course.PS:next days code in my github project.but the record is on my twitter:https://twitter.com/mianmian605 and https://beta.freecodecamp.org/en/challenges/react-and-redux/map-dispatch-to-props

_______________________________________________________________________________________________________________________
#### Responsive Web Design Principles: Create a Media Query
###### Media Queries are a new technique introduced in CSS3 that change the presentation of content based on different viewport sizes. The viewport is a user's visible area of a web page, and is different depending on the device used to access the site.
###### an example of a media query that returns the content when the device's width is less than or equal to 100px:and the following media query returns the content when the device's height is more than or equal to 350px:
```js
@media (max-width: 100px) { /* CSS Rules */ }
@media (min-height: 350px) { /* CSS Rules */ }
```
###### !!!Remember, the CSS inside the media query is applied only if the media type matches that of the device being used.
####  Responsive Web Design Principles: Make an Image Responsive
```js
Making images responsive with CSS is actually very simple. Instead of applying an absolute width to an element:

img { width: 720px; }

You can use:

img {
  max-width: 100%;
  display: block;
  height: auto;
}
```js
