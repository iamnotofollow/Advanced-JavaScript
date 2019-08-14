# Callback

### What is a Callback?

* A Callback is a function that is to be executed after another function has finished executing. *

### Why do we need Callbacks?

Javascript is an event driven language. This means that instead of waiting for a response before moving on, javascript will keep
executing while listening for other events. 

```javascript
function first() {
  // simulate a code delay.
  setTimeout( function () {
    console.log(1);
  }, 500);
}

function second() {
  console.log(2);
}

first();
second();

// o/p shows
//2
//1
```
Javascript didn't wait for the response from **`first()`** before moving on to execute **`second()`**.

### Create a Callback

```javascript
function doHomework(subject, callback) {
  console.log(`Starting my ${subject} homework.`);
  callback();
}

function finishedHomework() {
  console.log(`I have finished my homework.`);
}

doHomework('Maths', finishedHomework);
```
