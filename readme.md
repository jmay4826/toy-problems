#Toy Problems

Just a simple collection of answers to toy problems from Codewars and other similar sites.

###Function Addition
https://www.codewars.com/kata/functional-addition/train/javascript

Create a function add(n)/Add(n) which returns a function that always adds n to any number

Note for Java: the return type and methods have not been provided to make it a bit more challenging.

```javascript
var addOne = add(1);
addOne(3); // 4

var addThree = add(3);
addThree(3); // 6
```

####Solution:

```javascript
const add = n => y => n + y;
```
