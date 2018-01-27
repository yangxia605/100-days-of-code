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
 )
 }
 ```
