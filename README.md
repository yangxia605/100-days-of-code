# 100-days-of-code-study
## I will code for at least an hour a day for the next 100 days.[common on!!!]

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
#### Days 2:2018-01-21
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

#### Days 3:
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
 ###### 相关算法知识：有数组 A，B 假设A的长度是 a假设B的长度是 b遍历a,需要执行：a次对A的每一个数字，需要遍历B看 B中是否存在这个数，比较的次数为 b复杂度 a * b 对B 同理有： b * a目前的算法总共的遍历次数是 2 * a * b

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
