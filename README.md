# Kmurp62rulz's Javascript Cheat Sheet
#### This cheat sheet is a constant work in progress and covers some beginner/intermediate javascript topics as I learn them
#### There may be some gaps in the content here as I am adding topics everytime I find difficulty with them and have then learnt them

## Loops

### For Loop
```javascript
//prints numbers 0 to 9
for (let i = 0; i < 10; i += 1) {
  console.log(i);
};
```

### For...in Loop
```javascript
const object = { a: 1, b: 2, c: 3 };

for (const property in object) {
  console.log(`${property}: ${object[property]}`);
}

// prints:
// "a: 1"
// "b: 2"
// "c: 3"
```



## Functions

### Named Function
```javascript
function addNumbers(num1, num2) {
  return num1 + num2
}
```

### Anonymous Function
```javascript
const addNumbers = function(num1, num2) {
	return num1 + num2
}
```

### Arrow Function
```javascript
const addNumbers = (num1, num2) => {
	return num1 + num2
}

//One parameter
const oneParameter = num1 => {
	console.log(num1)
}

//No parameters
const noParameter = () => {
	console.log('Hello world')
}
```

### Concise Arrow Function
```javascript
const addNumbers1 = (num1, num2) => num1 + num2
```



## Array Methods

### array.map()
#### Returns a new array with some changes made in the callback function:
```javascript
const fruits = ['pineapple', 'apple', 'banana']
const smoothies = fruits.map(fruit => {
	return fruit + ' smoothie'
})

console.log(smoothies) //['pineapple smoothie', 'apple smoothie', 'banana smoothie']
```

## Array Destructuring

#### Array destructuring can be used to retrieve information from arrays in a convenient way: 
```javascript
const oldArray = ['A','B','C','D','E']

const [a,b] = oldArray //This line demonstrates array destructuring

console.log(a) //A
console.log(b) //B
```

#### It is also possible to skip values with empty fields between commas: 
```javascript
const oldArray = ['A','B','C','D','E']
 
const [a,,c] = oldArray //This line demonstrates array destructuring

console.log(a) //A
console.log(c) //C
```

#### The spread syntax is also useful in array/object destructuring to get an array of the remaining values: 
```javascript
const oldArray = ['A','B','C','D','E']

const [a,b, ...rest] = oldArray //This line demonstrates spread syntax

console.log(rest) //['C', 'D', 'E']
```

#### It is possible to combine two or more arrays with the spread operator:
```javascript
const letters = ['A','B','C','D','E']
const numbers = [1, 2, 3, 4, 5]

const newArray = [...letters, ...numbers] //This line demonstrates spread syntax

console.log(newArray) //['A','B','C','D','E', 1, 2, 3, 4, 5]
```

## Object Destructuring

#### Object destructuring is very similar to array destructuring except names are used to point to values instead of position
```javascript
const person = {
	first_name: 'Sarah',
	last_name: 'Person',
	age: 28,
	role: 'admin'
}

const {first_name, age} = person //This line demonstrates object destructuring

console.log(first_name) //'Sarah'
console.log(age) //28

```

#### It is possible to provide variable names for the destructured properties with a colon and the variable name after
```javascript
const person = {
	first_name: 'Sarah',
	last_name: 'Person',
	age: 28,
	role: 'admin'
}

const {first_name: name, age: years} = person //This line demonstrates object destructuring with named variables

console.log(name) //'Sarah'
console.log(years) //28

```

#### It is possible to provide default values for destructuring which will either carry the value from the object if it exists or just create a variable with the provided default value

```javascript
const person = {
	first_name: 'Sarah',
	last_name: 'Person',
	age: 28,
	role: 'admin'
}

const {first_name, age, favFood = 'Sushi'} = person //This line demonstrates object destructuring with default values

console.log(name) //'Sarah'
console.log(years) //28
console.log(favFood) // 'Sushi' //This line prints 'Sushi' because there is no favFood property of Person

```

#### When the value is found in the destructured object then it will return that value

```javascript
const person = {
	first_name: 'Sarah',
	last_name: 'Person',
	age: 28,
	role: 'admin',
	favFood: 'Pizza'
}

const {first_name, age, favFood = 'Sushi'} = person //This line demonstrates object destructuring with named variables

console.log(name) //'Sarah'
console.log(years) //28
console.log(favFood) // 'Pizza' // This line prints 'Pizza' because it found that value for the favFood property which exists this time within Person

```

## Value vs Reference

#### In Javascript, there are two types of data, primitive and non-primitive
#### Primitive data types: Number, String, Boolean, Undefined, Null and Symbol
#### Non-Primitive data types: Object. Arrays, Functions and mostly everything else in JavaScript belong to the ‘Object’ data type
#### 
#### When interacting with a variable, if it is a primitive data type then the value will be passed:
```javascript
let a = 1 //1
let b = a //1
b = b + 1 //2
console.log(a) //1
console.log(b) //2
```
#### A non-primitive type will pass a reference in memory to the value i.e 0x01, 0x02 etc
#### Creating a new variable `d`, that is based on `c` will mean that they both point to `0x01`, therefore any changes made to `d` will also happen to `c`:
```javascript
let c = [1,2,3] //0x01
let d = c //0x01
d.push(4) 
console.log(c) //[1,2,3,4]
console.log(d) //[1,2,3,4]
```

#### Creating two variables with the same array seperately will mean that they are referencing two sepearate references in memory and won't affect each other:
```javascript
let c = [1,2,3] //0x01
let d = [1,2,3] //0x02
d.push(4) 
console.log(c) //[1,2,3]
console.log(d) //[1,2,3,4]
```

## Truthy vs Falsy
#### In Javascript, values that evaluate to `true` are known as 'truthy' and values that evaluate to `false` are known as 'falsy'
#### Obviously a variable with the boolean value of `false` is falsy but so are the following variables: 
```javascript
//All the following evaluate to false when used in an if statement
let a = false
let b = 0
let c = -0
let d = ""
let e = null
let f = undefined
let g = NaN
```
#### All other values will evaluate to `true` also known as a 'truthy' value

## == vs ===
####
```javascript

```

## Promises

#### Promises have 3 states: *pending, fulfilled, rejected*
#### A promise takes in 1 parameter called the executor function, which has 2 parameters in its constructor `resolve` and `reject`
```javascript
const executorFunction = (resolve, reject) => {
  if (someCondition) {
      resolve('Resolved :)');
  } else {
      reject('Rejected :('); 
  }
}
const myFirstPromise = new Promise(executorFunction);
```

#### A basic example of how a promise can be created and handled:
```javascript
let prom = new Promise((resolve, reject) => {
  let num = Math.random();
  if (num < .5 ){
    resolve('Bigger');
  } else {
    reject('Smaller');
  }
});
 
const handleSuccess = (resolvedValue) => {
  console.log(resolvedValue);
};
 
const handleFailure = (rejectionReason) => {
  console.log(rejectionReason);
};
 
prom.then(handleSuccess, handleFailure);
```

#### `.then()` to handle a fulfilled promise
#### `.catch()` to handle a rejected promise

#### A basic example of how a promise can be handled using `.then()` and `.catch()`:
```javascript
function gotData(data) {
    console.log(data)
}

function gotErr(data) {
    console.log(data)
}

fetch(url).then(gotData).catch(gotErr);
```

#### `.then()` can handle both success and failure when there is only 1 `.then()`
```javascript
fetch(url).then(gotData,gotErr);
```


#### This can be simplified using arrow functions in the actual `.then()` and `.catch()` after the function call:
```javascript
fetch(url)
	.then((data) => {
		console.log(data)
	})
	.catch((err) => {
		console.log(err)
	})
```


#### And these arrow functions can be simplified again:
```javascript
fetch(url)
	.then(data => console.log(data))
	.catch(err => console.log(err))
```


#### `.catch()` will handle errors from any of the `.then()`s above it

```javascript
fetch(url)
	.then()
	.then()
	.then()
	.then()
	.catch() //this would handle any of the errors no matter how early or late
```


### Promise.all()
#### This will return all the promises' values if *all* of the promises called come back as fulfilled 
#### An array of promises needs to be provided and an array will be returned with the results in the same order as the inputted array
#### If any of the promises resolve as rejected, then `Promise.all()` will resolve as rejected and the `.catch()` will be invoked
```javascript
let promises = [promise1, promise2, promise3]

Promise.all(promises)
	.then((results) => {
		for (let i = 0; i < results.length; i++) {
			console.log(results[i])
		}
	})
	.catch((err) => {
		console.log(err)
	});
```

#### The array of promises can also be directly provided when calling `Promise.all()`:
```javascript
Promise.all([promise1, promise2, promise3])
```



### Promise.first()
#### This will return the value of the first promise to come back as fulfilled
```javascript
let promises = [promise1, promise2, promise3]

Promise.first(promises)
	.then((result) => {
		console.log(result)
	})
	.catch((err) => {
		console.log(err)
	});
```

## Async/Await

#### Async/Await was added in ES8, and adds syntactic sugar to the existing ES6 promises, however doesn't add any new functionality
#### `async` is called before a function is defined and `await` is called within the function for a value that will take time to resolve
```javascript
async function urlReader(url) {
	let result = await fetch(url)
	return result
}
```

#### An `async` function will always return a `promise` which means when it can be called with `.then()` and `.catch()`:
```javascript
urlReader(url)
	.then((result) => {
		console.log(result)
	})
	.catch((err) => {
		console.log(err)
	});
```

#### An `async` function is most useful when calling multiple services that take time to resolve but don't need require each other to be called in any order
#### Basically, all the `await`s within an `async` function will run next to each other and save time (asynchronously) instead of one after another (synchronously)
#### If one line is slower than the rest, the program won't be slowed down because the rest of the code will execute at the same time:

```javascript
async function urlsReader(urls) {
	let resultOne = await fetch(urls[0]) //slow
	let resultTwo = await fetch(urls[1]) //fast
	let resultThree = await fetch(urls[2]) //fast
	let resultFour = await fetch(url[3]) //fast
}
```

## AJAX - Asynchronous JavaScript And XML

#### AJAX is a set of tools that are used together to take advantage of JavaScript’s asynchronous capabilities
#### In a nutshell, it is the use of the XMLHttpRequest object to communicate with servers. 
#### It can send and receive information in various formats, including JSON, XML, HTML, and text files


