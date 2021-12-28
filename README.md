# Kmurp62rulz's Javascript Cheat Sheet
#### This cheat sheet is a constant work in progress and covers some beginner/intermediate javascript topics as I learn them
#### There may be some gaps in the content here as I am adding topics everytime I find difficulty with them and have then learnt them

## Loops

### For Loop
```javascript

```

### For...in Loop
https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/for...in 
```javascript

```



## Functions

### Normal Function
```javascript

```

### Arrow Function
```javascript

```

### Anonymous Function
```javascript

```

### Const Function
```javascript

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



## Promises

#### Promises have 3 states: *pending, fulfilled, rejected*

#### A basic example of how a promise can be created and handled:
```javascript
let prom = new Promise((resolve, reject) => {
  let num = Math.random();
  if (num < .5 ){
    resolve('Yay!');
  } else {
    reject('Ohhh noooo!');
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



### Promise.first()
#### This will return the value of the first promise to come back as fulfilled
```javascript

```

