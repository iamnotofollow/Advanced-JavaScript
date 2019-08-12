```html
<!DOCTYPE html>
<html>
<body>

<p>For each element in the array: multiply the value with 10 and update the element value:</p>

<p id="demo"></p>

<script>
var numbers = [65, 44, 12, 4];
//using forEach loop
numbers.forEach(myFunction)

function myFunction(item, index, arr) {
  arr[index] = item * 10;
}

//using map method
let mul = numbers.map((val, i) => {
	 return val * 10;
});

//using map method
let mul1 = numbers.map((val, i, arr) => val * 20);

document.getElementById("demo").innerHTML = mul;
</script>

</body>
</html>
```
