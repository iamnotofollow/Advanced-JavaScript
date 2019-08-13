# this

The value of `this` is usually determined by *how* a function is called.

## Global Object

When you write the below js code in browser console it will return `Window{...}` object.

```javascript
console.log(this)
```

The `window` object! That’s because in the global scope, `this` refers to the global object. 
In a browser, the global object is the `window` object.

```javascript
console.log(this);
```

## Declared Object

When the keyword `this` is used inside of a declared object, the value of `this` is 
set to the closest parent object the method is called on.

```javascript
var person = {
  first: 'John',
  last: 'Smith',  
  full: function() {
    console.log(this.first + ' ' + this.last);
  }
};
person.full();
// logs => 'John Smith'
```
This is also called as scope level.

## The `New` Keyword

When the `new` keyword is used(a constructor), `this` is bound to the new object being created.

```javascript
var myCar = new Car('Ford', 'Escape');
console.log(myCar);
// logs => Car {make: "Ford", model: "Escape"}

function Car(make, model) {
  this.make = make;
  this.model = model;
};
```

## Call, Bind, Apply

We can actually set `this` explicitly using `call()`, `bind()` and `apply()`. Call and Apply are invoked immediately. 
Call takes any number of parameters, `this` followed by additional arguments. Apply takes two parameters, `this` followed by
an array of additional arguments.

```javascript
function add(c, d) {
  console.log(this.a + this.b + c + d);
}
var ten = {a: 1, b: 2};
add.call(ten, 3, 4);
// logs => 10
add.apply(ten, [3,4]);
// logs => 10
```

Bind is not invoked immediately. `bind()` returns a function with the context of `this` bound already.

```javascript
var small = {
  a: 1,
  go: function(b,c,d){
    console.log(this.a+b+c+d);
  }
}
var large = {
  a: 100
}

small.go(2,3,4);
// logs 1+2+3+4 => 10

small.go.call(large,2,3,4);
// logs 100+2+3+4 => 109

var bindTest = small.go.bind(large,2);
console.log(bindTest);
// logs => function (b,c,d){console.log(this.a+b+c+d);}
```

## Arrow Functions

`Not in this scope, explained as a separate topic`

## Conclusion - 
- The value of this is usually determined by a functions execution context.
- In the global scope, this refers to the global object (the window object).
- When the new keyword is used(a constructor), this is bound to the new object being created.
- We can set the value of this explicitly with call(), bind(), and apply()
- Arrow Functions don’t bind this — instead this is bound lexically (i.e. based on the original context)
