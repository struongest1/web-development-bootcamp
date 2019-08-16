# Programming Fundamentals

We will be learning how to work with JavaScript. JavaScript runs most of the internet today, and allows us to use the same language for both the front-end (user interfaces seen in the browser)

## This lesson covers
* REPL
* Declaring Functions
* Storing values
* Objects
* Comparison Operators
* Logical Operators
* Conditional statements

## REPL
REPL stands for "read evaluate print loop" and allows us to do things with JavaScript interactively in our terminal. It's a great way to test things out.

To access the NodeJs REPL, use the command `node` in your terminal 

## Declaring Functions
To declare a function there are two basic ways:

```js
function superCoolFunction() {
  return 'I am such a cool function... wow';
};

const superCoolFunction = () => {
  return 'I am such a cool function... wow';
};
```

To load a file into the REPL, get into REPL mode by using the `node` command in your terminal, then use the command `.load [filename]` to load the file (you have to be in the same directory as the file, or give it the correct path). Allow me to demonstrate!

## Storing Values
One of the basic concepts in programming is storing values. There are values which change, or **variables** and those that don't, **constants**. Let's go through some examples.

```js
// This variable is called "a" and stores the character "A"
// The value's type is "string"
// You can change the value for this *variable* - it's expected to change
var a = 'A'
// If you try to use 'a' below, having used *const*, it won't work - it's a *constant* and
// it isn't expected to change
const a = 'A' 

// Below is a way to declare a *variable* which is similar to `var` but has different *scope*
// We'll learn more about scope in later lessons
let c = "see"

// This variable is called "b" and stores the number 1 
// The **type** of this value is "integer"
var b = 1

// The type of this value is "decimal"
var c = 0.001

// The type of this value is "array"
var d = [1, 2, 3, 4]
var e = ["banana", "apple", "dolphin"]

// The type of this value is "boolean"
var f = true

// The type of this value is "object"
var d = {
  first_name: 'Tuna',
  last_name: 'Bigum',
  race: 'fish',
}
```

The concept of types goes very deep in [type theory](https://en.wikipedia.org/wiki/Type_theory) but that's outside of the scope of this class. It's enough to know the following **primitive types**: **string**, **integer**, **float**, **boolean**, and **object**. There are a few others but we don't need to worry about those for now.

### Null and undefined
Sometimes you may try to use a value which doesn't exist, and you will run into an error saying that the value you're trying to use is `undefined`. This means that you haven't created the value or that you assigned the `undefined` value to an existing variable.

Similarly, a variable or constant may have the value of `null`. This means that the value doesn't exist! In other words, you have an empty variable.

Both `undefined` and `null` are similar, but are used in slightly different contexts. If you want to set a variable to an empty value, use `null`. Undefined is usually the result of a bug which needs to be fixed!

## Objects
Objects are the bread and butter of OOP. They allow us to model real life objects and manipulate them using methods in order to build an idea. For example. If we wanted to model a car, one of the ways we can do this is like so:

```js
  const car = {
    speed: 40,
    color: 'red',
    horsePower: 400,
    get sound() {
      return "wrooom";
    }
  };
```

We are now able to **get** and **set** different properties of this object.

```js
car.speed // returns 40
car.sound // returns "wrooom"
```

We can also update the different properties, or add new ones.

```js
car.speed = 160
car.make = 'Tesla'
```

## Basic Arithmetic
Programming is often about doing arithmetic. Here are some basic things you can do in JavaScript.

```js
// Adding strings (string concatenation)
const myName = 'Tuna'
"Hello " + myName // => "Hello Tuna"

// Another syntax for string concatenation uses *backticks*
const greeting = "Hey there"
const name = "Bruno"
`${greeting} ${name}, my old friend`

// Addition
3 + 1 // => 4
3 + 0.1 // => 3.1

// Subtraction
4 - 1 = 3

// Multiplication
3 * 1 = 3
3 * 0 = 0

// Division
1 / 0 = Infinity
0 / 1 = 0
3 / 1 = 3

// Modulo
10 % 2 = 0
10 % 3 = 1 // Add up as many 3s as you can before going over 10, and then see how far from 10 you are; 3 + 3 + 3 = 9. 10 - 9 = 1 so our remainer is 1. If we do 3 + 3 + 3 + 3 = 12 we have gone over 10, so that's no good

```

## [Comparisons Operators](https://www.w3schools.com/js/js_comparisons.asp)
In programming, we often look at the **state** of our program to figure out what should happen next. This is done through **comparison** and checking if values are what we expect them to be. The following are the basics of comparisons we will need.

```js
// `===` Compares value **and** type equality
"1" === "1" // true
"1" === 1   // false
"a" === "b" // false
"a" === 1   // false

// `==` Compares values (not recommended)
"1" == "1" // true
"1" == 1   // true
"1" == "b" // false

// `!==` Checks if values **or** types are not equal
"1" !== 1   // true
"1" !== "1" // false

// `!=` Check if values are not equal (not recommended)
"1" != 1   // false
"1" != "1" // false
"1" != "2" // true

// `>` Greater than operator
1 > 2 // false
2 > 1 // true

// `<` Less than operator
1 < 2 // true
2 < 1 // false

// `>=` Greater than or equal to
3 >= 3 // true
3 >= 4 // false
3 >= 2 // true

// `<=` Less than or equal to
3 <= 3 // true
3 <= 4 // true
3 <= 2 // false
```

## {Logical Operators](https://www.w3schools.com/js/js_comparisons.asp) (bottom of the page)
Logical Operators allow us to determine logic between values. There are three basic logical operators: **AND**, **OR** and **NOT**.

**NOT** is the simplest out of the three. It just reverses the truth value. So for example. The operator is the `!` sign, which is simply placed in front of the thing it negates.

```js
const a = true
!a // false
```

Variables that have a value, in other words, they are **defined**, have a boolean value of **true**

**AND** is only true if both values are true. It's denominated by `&&`.

```js
const a = true
const b = false
const c = "banana"

a && b // false
a && c // true
```

**OR** is true if at least one (or both values) and is denominated by `||`

```js
const a = true
const b = true
const c = false
const d = false

a || b // true
a || c // true
c || d // false
```

A few examples that combine comparison and logical operators:

```js
const a = 3
const b = 1

(b < 3) || (b === 100) // true
(b < 3) && (b === 100) // false
!(b === 1) // false
```

## Conditional statements
This finally brings us to the famed conditional statement which is one of the basic building blocks used in programming. It is an extremely versatile construct which allows us to construct progressively more complex logic.

```js
function tellMeAboutTunas(tunaAreFish) {
  if (tunaAreFish) {
    return "They can totally swim in the sea";
  } else {
    return "Shucks...";
  }
};

tellMeAboutTunas(true); // returns "They can totally swim in the sea"
tellMeAboutTunas(false); // returns "Shucks..."
```

```js
function multipleConditions(number) {
  if (number === 0) {
    return "Hey, this is a 0!";
  } else if (number === 1) {
    return "No way, is that a 1?!";
  } else if (number === 3) {
    return "That's a ... 3?";
  } else {
    return "Welp, that's not a 0, 1 or 3... shucks";
  }
}

multipleConditions(1) // => "No way, is that a 1?!"
```
