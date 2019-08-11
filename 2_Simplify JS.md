## `.map()`, `.reduce()` and `.filter()`

###.map()

The `.map()` method is used to apply a function on every element in an array. A new array is then returned. You can think of 
`.map()` as a *for loop*, that is specifically for transforming values.

### .map() vs for loop

Using for loop,

```javascript
var arr = [1,2,3,4];
var plus5 = [];

for(var i = 0; i < arr.length; i++) {
  plus5[i] = arr[i] + 5;
}
console.log(plus5);
```

Much simpler way to achieve the same result is using `.map()` method.

```javascript
var arr = [1,2,3,4];
let plus5 = arr.map((val, i, arr) => {
  return val + 5;
});
```

###.filter()

The `.filter()` method returns a new array created from all elements that pass a certain test performed on original array.
You can think of filter() as a for loop, that is specifically for filtering in/out certain values from an array.

### .filter() vs for loop

Using for loop,

```javascript
var arr = [1,2,3,4,5];
var even = [];

for (var i = 0; i < arr.length; i++) {
  if(arr[i] % 2 === 0) even.push(arr[i]);
}
console.log(even);
```

Using `.filter()` method,

```javascript
var arr = [1,2,3,4,5];

let even = arr.filter(val => {
  return val % 2 === 0;
}
```

###.reduce()

The `.reduce()` method is used to apply a function to each of the element in the array to reduce the array to a single value.
You can think of reduce() as a for loop, that is specifically for using the values of an array to create *something new*.

### .filter() vs for loop

Using for loop,

```javascript
var arr = [1,2,3,4];
var sum = [];

for (var i = 0; i < arr.length; i++) {
  sum += arr[i];
}
console.log(sum);
```

Using `.reduce()` method,

```javascript
var arr = [1,2,3,4];

let sum = arr.reduce((acc, val) => {
  return acc + val;
}
```

We can use an optional initial value as second parameter, which makes the function execution to start from the specified value.

```javascript
var arr = [1,2,3,4];

let sum = arr.reduce((acc, val) => {
  return acc + val;
}, 100);
```
The above code will return **`110`**, the calculation will start at 100 and will add the callback function return value 10 to it.
