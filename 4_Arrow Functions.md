# Arrow Functions - 

## Benefit 1 - Shorter Syntax

regular function syntax is - 

```javascript
function funcName(params) {
   return params + 2;
 }
funcName(2);
// 4
```

shorter syntax using Arrow function is - 

```javascript
var funcName = (params) => params + 2
funcName(2);
// 4
```

Arrow function syntax 

- `(parameters) => { statements }`
- without parameters : `() => { statements }`
- with one parameter the parathesis is optional : `parameter => { statements }`
- if returning an expression, remove the brackets : `parameter => expressions`

## Benefit 2 - No binding of `this`

Unlike regular function, an arrow function does not bind `this`. Instead, `this` is bound lexically (ie., `this` keeps its 
meaning from its original context).

```javascript
//regular function

function counter() {
  this.num = 0;
  this.timer = setInterval(function add() {
    this.num++;
    console.log(this.num);
  }, 1000);
}

var b = new counter();

//this after 10 iterations use to clear counter
clearInterval(b.timer); 

//output for the above logs 
//NaN
//every 1 sec
```

The issue is with the `this` in the setInterval which is bound to the global object, even though it is in the scope of
setInterval(). It was logging `NaN` because `this.num` was referring to the `num` property of the `window` object and not the
`b` object (`b.num`) we have created.

To fix this issue we use `Arrow` functions

```javascript
function counter() {
  this.num = 0;
  this.timer = setInterval(() => {
    this.num++;
    console.log(this.num);
  }, 1000);
}
var b = new counter();
//1
//2
//3

//this after 10 iterations use to clear counter
clearInterval(b.timer); 
```

The original this binding created by the Counter constructor function is preserved. 
Inside the setInterval function, this is still bound to our newly created b object!
