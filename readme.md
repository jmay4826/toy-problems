# Toy Problems

Just a simple collection of answers to toy problems from Codewars and other similar sites.

Current Codewars level: 5kyu, 312 points. (3/14)

### Decode the Morse code

https://www.codewars.com/kata/decode-the-morse-code/train/javascript

#### Solution:

```javascript
const decodeMorse = morseCode =>
  morseCode
    .trim()
    .split("   ")
    .map(word =>
      word
        .split(" ")
        .map(letter => MORSE_CODE[letter])
        .join("")
    )
    .join(" ");
```

### Isograms

https://www.codewars.com/kata/isograms/train/javascript

An isogram is a word that has no repeating letters, consecutive or non-consecutive. Implement a function that determines whether a string that contains only letters is an isogram. Assume the empty string is an isogram. Ignore letter case.

```javascript
isIsogram("Dermatoglyphics") == true;
isIsogram("aba") == false;
isIsogram("moOse") == false; // -- ignore letter case
```

#### Solution:

```javascript
const isIsogram = str => new Set(str.toLowerCase()).size === str.length;
```

### Create Phone Number

https://www.codewars.com/kata/525f50e3b73515a6db000b83

#### Solution:

```javascript
const createPhoneNumber = n =>
  `(${n.slice(0, 3).join("")}) ${n.slice(3, 6).join("")}-${n
    .slice(6, 10)
    .join("")}`;
```

### Descending Order

https://www.codewars.com/kata/descending-order/train/javascript

Description:
Your task is to make a function that can take any non-negative integer as a argument and return it with its digits in descending order. Essentially, rearrange the digits to create the highest possible number.

#### Solution

```javascript
const descendingOrder = n =>
  +n
    .toString()
    .split("")
    .sort((a, b) => +b - +a)
    .join("");
```

### Two Joggers

https://www.codewars.com/kata/two-joggers/train/javascript
Your job is to complete the function nbrOfLaps(x, y) that, given the length of the laps for Bob and Charles, finds the number of laps that each jogger has to complete before they meet each other again, at the same time, at the start.

The function takes two arguments:

The length of Bob's lap (larger than 0)
The length of Charles' lap (larger than 0)

The function should return an array (Tuple<int, int> in C#) containing exactly two numbers:

The first number is the number of laps that Bob has to run
The second number is the number of laps that Charles has to run

Examples:

```javascript
nbrOfLaps(5, 3); // returns [3, 5]
nbrOfLaps(4, 6); // returns [3, 2]
```

#### Solution

```javascript
var nbrOfLaps = function(x, y) {
  let z = Math.min(x, y);
  while (z % x !== 0 || z % y !== 0) {
    z = z + Math.min(x, y);
  }
  return [z / x, z / y];
};
```

### Find the divisors

https://www.codewars.com/kata/find-the-divisors/train/javascript
Create a function named divisors/Divisors that takes an integer and returns an array with all of the integer's divisors(except for 1 and the number itself). If the number is prime return the string '(integer) is prime' (null in C#) (use Either String a in Haskell and Result<Vec<u32>, String> in Rust).

Example:

```javascript
divisors(12); // should return [2,3,4,6]
divisors(25); // should return [5]
divisors(13); // should return "13 is prime"
```

You can assume that you will only get positive integers as inputs.

#### Solution

```javascript
function divisors(integer) {
  let result = [];
  for (let i = 2; i < integer; i++) {
    integer % i === 0 && result.push(i);
  }

  return result.length ? result : `${integer} is prime`;
}
```

### Function Addition

https://www.codewars.com/kata/functional-addition/train/javascript

Create a function add(n)/Add(n) which returns a function that always adds n to any number

Note for Java: the return type and methods have not been provided to make it a bit more challenging.

```javascript
var addOne = add(1);
addOne(3); // 4

var addThree = add(3);
addThree(3); // 6
```

#### Solution:

```javascript
const add = n => y => n + y;
```
