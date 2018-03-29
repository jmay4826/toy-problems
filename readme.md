# Toy Problems

Just a simple collection of answers to toy problems from Codewars and other similar sites.

Current Codewars level: 5kyu, 359 points. (3/27)

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

### Control the Beast

https://www.codewars.com/kata/5a831574373c2e48cf00000d

In this kata you'll learn how to control Components with different kinds of beasts. Your goal is to tame and control a beast by building a controlled React component with the following criteria:

Create a component called Beast and its state name
The beast to control can be passed as a prop name
Render a textinput field with the id controlledName. Its value should be the name of the current beast.
Whenever this field's value is modified, the state should be updated as well
You should control the beast Yeti if name is not passed in

#### Solution:

```javascript
const React = require("react");

class Beast extends React.Component {
  constructor(props) {
    super(props);
    this.state = {
      name: props.name === undefined ? "Yeti" : props.name
    };
  }

  render() {
    const { name } = this.state;
    return (
      <input
        id="controlledName"
        value={name}
        onChange={e => this.setState({ name: e.target.value })}
      />
    );
  }
}
```

### United States of React

https://www.codewars.com/kata/5a830fa2373c2ec8eb00019d

You will be given a component called States. You will need to establish an initial state for the component called united and for it to be set to false.

Then write a unite function that changes this state to true.

Then conditionally render a bespoke message in the component.

If the States are united then display "Code for everyone"

If the States aren't united then display "Make America code again"

#### Solution:

```javascript
const React = require("react");

class States extends React.Component {
  constructor() {
    super();
    this.state = {
      united: false
    };
    this.unite = this.unite.bind(this);
  }

  unite() {
    this.setState({ united: true });
  }

  render() {
    return (
      <div className="status">
        {this.state.united ? "Code for everyone" : "Make America code again"}
      </div>
    );
  }
}
```

### Create Phone Number

Write a function that accepts an array of 10 integers (between 0 and 9), that returns a string of those numbers in the form of a phone number.

Example:

```javascript
createPhoneNumber([1, 2, 3, 4, 5, 6, 7, 8, 9, 0]); // => returns "(123) 456-7890"
```

The returned format must be correct in order to complete this challenge.
Don't forget the space after the closing parentheses!

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

### Word a10n (abbreviation)

https://www.codewars.com/kata/5375f921003bf62192000746

The word i18n is a common abbreviation of internationalization in the developer community, used instead of typing the whole word and trying to spell it correctly. Similarly, a11y is an abbreviation of accessibility.

Write a function that takes a string and turns any and all "words" (see below) within that string of length 4 or greater into an abbreviation, following these rules:

A "word" is a sequence of alphabetical characters. By this definition, any other character like a space or hyphen (eg. "elephant-ride") will split up a series of letters into two words (eg. "elephant" and "ride").
The abbreviated version of the word should have the first letter, then the number of removed characters, then the last letter (eg. "elephant ride" => "e6t r2e").

Example

```javascript
abbreviate("elephant-rides are really fun!") ===
  //          ^^^^^^^^*^^^^^*^^^*^^^^^^*^^^*
  // words (^):   "elephant" "rides" "are" "really" "fun"
  //                123456     123     1     1234     1
  // ignore short words:               X              X

  // abbreviate:    "e6t"     "r3s"  "are"  "r4y"   "fun"
  // all non-word characters (*) remain in place
  //                     "-"      " "    " "     " "     "!"
  "e6t-r3s are r4y fun!";
```

#### Solution:

```javascript
const abbreviate = str =>
  str
    .split(/([^a-z])/i)
    .map(
      w =>
        w.length >= 4
          ? w.substr(0, 1) + (w.length - 2) + w.substr(w.length - 1)
          : w
    )
    .join("");
```

### Find the Parity Outlier

https://www.codewars.com/kata/5526fc09a1bbd946250002dc

You are given an array (which will have a length of at least 3, but could be very large) containing integers. The array is either entirely comprised of odd integers or entirely comprised of even integers except for a single integer N. Write a method that takes the array as an argument and returns this "outlier" N.

Examples

```javascript
[2, 4, 0, 100, 4, 11, 2602, 36]
Should return: 11 (the only odd number)

[160, 3, 1719, 19, 11, 13, -21]
Should return: 160 (the only even number)
```

#### Solution:

```javascript
const findOutlier = integers =>
  integers.filter(n => n % 2).length === 1
    ? integers.find(n => n % 2)
    : integers.find(n => !(n % 2));
```

### Shortest Word

https://www.codewars.com/kata/57cebe1dc6fdc20c57000ac9

Simple, given a string of words, return the length of the shortest word(s).

String will never be empty and you do not need to account for different data types

#### Solution:

```javascript
const findShort = s =>
  s.split(" ").sort((a, b) => a.length - b.length)[0].length;
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

### Multiply

https://www.codewars.com/kata/multiply/javascript

The code does not execute properly. Try to figure out why.

#### Solution:

```javascript
const multiply = (a, b) => a * b;
```

### ES2015: Build an object which can't be modified

https://www.codewars.com/kata/599a6aaf1924716c3000003f

Declare an variable which name is stone that cant't be modified.

The initial value of stone is under below.

```javascript
{
  feature: 'earth',
  style: {
    color: 'black'
  }
}
```

#### Solution:

```javascript
const stone = Object.freeze({
  feature: "earth",
  style: Object.freeze({
    color: "black"
  })
});
```

### Build Tower

https://www.codewars.com/kata/576757b1df89ecf5bd00073b

Build Tower by the following given argument:
number of floors (integer and always greater than 0).

Tower block is represented as \*

Python: return a list;
JavaScript: returns an Array;
C#: returns a string[];
PHP: returns an array;
C++: returns a vector<string>;
Haskell: returns a [String];
Ruby: returns an Array;
Have fun!

#### Solution:

```javascript
function towerBuilder(n) {
  let tower = [];
  for (var i = 0; i < n; i++) {
    tower.push(
      " ".repeat(Math.floor(n - i - 1)) +
        "*".repeat(2 * i + 1) +
        " ".repeat(Math.floor(n - i - 1))
    );
  }
  return tower;
}
```

### One Line Task: Count Down I

Task
Count down 3 times to an positive integer n, return these 3 numbers as a string, separated by exclamation mark(!).

Code Limit
Less than 30 characters.

Example
For n = 1, the output should be `"3!2!1".

count down from 3 to 1

For n = 10, the output should be `"12!11!10".

count down from 12 to 10

For n = 100, the output should be `"102!101!100".

count down from 102 to 100

#### Solution

```javascript
countDown = n => n + 2 + `!${n + 1}!` + n;
```

### Binary Addition

https://www.codewars.com/kata/551f37452ff852b7bd000139
Implement a function that adds two numbers together and returns their sum in binary. The conversion can be done before, or after the addition.

The binary number returned should be a string.

#### Solution

```javascript
function addBinary(a, b) {
  return (a + b).toString(2);
}
```

### Disemvowel Trolls

https://www.codewars.com/kata/52fba66badcd10859f00097e

Trolls are attacking your comment section!

A common way to deal with this situation is to remove all of the vowels from the trolls' comments, neutralizing the threat.

Your task is to write a function that takes a string and return a new string with all vowels removed.

For example, the string "This website is for losers LOL!" would become "Ths wbst s fr lsrs LL!".

Note: for this kata y isn't considered a vowel.

#### Solution:

```javascript
function disemvowel(str) {
  return str.replace(/[aeiou]/gi, "");
}
```

### Calculate Average

https://www.codewars.com/kata/calculate-average/javascript
Write function avg which calculates average of numbers in given list.

#### Solution

```javascript
const find_average = arr => arr.reduce((acc, cur) => acc + cur) / arr.length;
```

### Unique in Order

https://www.codewars.com/kata/unique-in-order/javascript

Implement the function unique_in_order which takes as argument a sequence and returns a list of items without any elements with the same value next to each other and preserving the original order of elements.

For example:

```javascript
uniqueInOrder("AAAABBBCCDAABBB") == ["A", "B", "C", "D", "A", "B"];
uniqueInOrder("ABBCcAD") == ["A", "B", "C", "c", "A", "D"];
uniqueInOrder([1, 2, 2, 3, 3]) == [1, 2, 3];
```

#### Solution:

```javascript
var uniqueInOrder = function(iterable) {
  //your code here - remember iterable can be a string or an array
  const arr = typeof iterable === "string" ? iterable.split("") : iterable;
  return arr.reduce(
    (acc, cur) => (cur === acc[acc.length - 1] ? [...acc] : [...acc, cur]),
    []
  );
};
```

### Bonus Time

https://www.codewars.com/kata/do-i-get-a-bonus/javascript

It's bonus time in the big city! The fatcats are rubbing their paws in anticipation... but who is going to make the most money?

Build a function that takes in two arguments (salary, bonus). Salary will be an integer, and bonus a boolean.

If bonus is true, the salary should be multiplied by 10. If bonus is false, the fatcat did not make enough money and must receive only his stated salary.

Return the total figure the individual will receive as a string prefixed with "£" (= "\u00A3", JS and Java) or "$" (C#, C++, Ruby, Clojure, Elixir, PHP and Python).

#### Solution:

```javascript
const bonusTime = (salary, bonus) => `£${salary * (bonus ? 10 : 1)}`;
```
