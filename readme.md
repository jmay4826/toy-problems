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
