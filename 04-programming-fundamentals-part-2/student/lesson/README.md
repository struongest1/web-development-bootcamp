# Programming Fundamentals - Part 2

In this lesson we will continue learning the fundamentals of programming. We will learn how to work with structures in new ways and how to deal with collections of things as well as some approaches to debugging code.

## This lesson covers
* Style
* Arrays
* For loop
* Variable scope
* Debugging

## Style
Style is an important part of coding. It helps you write code that's more comprehensible. This
is important because others will often work on that same code, and if enough time passes, your
code will look so foreign to you, you may not even remember you wrote it. Essentially you want
to write code which is easy to glance at and figure out what's going on, and in the long run
you want to be able to **write "stories" using code**.

Here are a few rules to follow:

```js
// Indent things so that you can see where they begin and end
// Notice that the first and last line of the function start at the same indentation
// Likewise, the first and last line of the object inside the function have the same indentation
// Lastly, the properties of the object properties have the same indentation, showing us they're all
// in the same "location"
function example(){
  const object = {
    type: 'example',
    size: 'small',
  }

  return object;
};

// It's also a good idea to put semi-colons at the ends of lines. The semi-colon indicates
// the end of an expression. Withou them, sometimes the code interpreter can confuse things
// and mash together pieces of code which are actually supposed to be run independently, thus
// creating unexpected results

// This will throw an error
let a = 1
[1, 2, 3, 4].push(a);

// This won't
let a = 1;
[1, 2, 3, 4].push(a);

// When using operators, put spaces on both sides of them
// Examples of properly formatted operators
1 + 1;
true && "banana";
100 / 5

//Examples of poorly formatted operators
3%1;
"dolpin"||"mollusk"

// Additionally, we want to put spaces after commas in an array like so:
[1, 2, 3, 4, 5]

// Not like this:
[1,2,3,4]

// Another small details is that functions should not have a space before the opening curly brace
function noSpaceBeforeCurly(){
  return "Proper!";
}

function notSoProper() {
  return "Could be better...";
}

```

## Arrays
One important concept in programming is having a collection of something. Usually, we use a thing called an *array* which you can think of as a "box" which holds a bunch of "things".

```js
const emptyArray = []
const arrayOfNumbers = [1, 2, 3, 4, 5]
const arrayOfFruits = ["banana", "strawberry", "tomato"]

const bubba = {
  name: 'Bubba',
  weight: 300,
  length: 4,
  color: 'purple',
}

const mung = {
  name: 'Mung',
  weight: 100,
  length: 3,
  color: 'green',
}

const tiny = {
  name: 'Tiny',
  weight: 2000,
  length: 15,
  color: 'blue',
}

const arrayOfFish = [bubba, mung, tiny]
```

### Manipulating Arrays
Now that we know how arrays look, let's look at some ways we can *manipulate* them.

```js
const testArray = [1, 2, 3];

// To add something to an array, use the `push` method
testArray.push(4) // => [1, 2, 3, 4]

// To remove the last member of the array, use the `pop` method
testArray.pop() // => [1, 2, 3]

// To remove and return the first memeber of the array, use the `shift` method
testArray.shift() // => [2, 3]

// To access a particular *index* (index is the position in the array which starts at 0)
// First element has index 0, the second's index is 1, third element's is 2 etc.
testArray[0] // => 2
testArray[1] // => 3

// We can also use the index to update the member in that position
[0, 1, 2, 3][0] = 10 // => [10, 1, 2, 3]

// To add stuff or remove stuff at a particular position in the array use `splice`
// The first argument is the position, the second how many elements to replace, and everything after
// are items to add starting at that position (the one specified with the first argument)
// If you keep the second argument at 0, you will just add stuff
testArray.splice(0, 0, 1) => // => [1, 2, 3]
testArray.splice(3, 0, 4, 5) => // => [1, 2, 3, 4, 5]

// To sort an array alphabetically or numerically use `sort`
// Our array is already sorted so it wouldn't do anything
testArray.sort() // => [1, 2, 3, 4, 5]

// Adding an element to the beginning of an array can be done using `unshift`
testArray.unshift(0) // => [0, 1, 2, 3, 4, 5]

// To combine two arrays, use `concat`
testArray2 = [6, 7]
testArray.concat(testArray2) // => [0, 1, 2, 3, 4, 5, 6, 7]

// Sometimes we want to get a section of the array without removing it, do this with `splice`
// It can take 1 or two arguments, and they specify which indexes to keep
testArray.slice(4, 7) // => [0, 1, 2, 3]

// To reverse an array, use `reverse`
testArray.reverse() // => [3, 2, 1, 0]

// To measure how many items are in an array, use `length`
testArray.length // => 4
```

## For Loop
Often times we need to do the same action many times, or do the same thing to all members of a collection (like an array of numbers for example). For loops are a pretty straightforward way to
do this so that's where we're going to start!

```js
const array = [1, 2, 3, 4, 5];

for (let i = 0; i < array.length; i++) {
  let currentItem = array[i];
  console.log(i);
};
```

## Scope
*Scope* is an important concept which basically tells us where our values are accessible. The two
main types of scopes are *global* and *local*. *Global* values are visible and usable everywhere, whereas *local* values are only accessible in particular parts of the code.

```js
// This example works because `globalVar` is a global variable 
// and can be accessed anywhere in this file
var globalVar = "I can be accessed anywhere!!!"

function logTheGlobalVariable() {
  console.log(globalVar)
}
```

```js
// This example won't work, and the `console.log` part will fail
// because `scopedVar` is only accessible inside of the function `scopedVariableFunction`
function scopedVariableFunction() {
  const scopedVar = "I am only accessbile in this function :(";
}

console.log(scopedVar) // => This will throw an error of `undefined`
```

## Debugging
Debugging is a huge part of programming. Luckily, the tools to do this are great. Let's go over
some different approaches to debugging.

### Logging things in the console
One of the easiest ways to figure out what's going on in your code is to log things to your
console so that you can inspect things. Below is a simple example, but you may be working with a function which has dozens of values being thrown around. Odds are, you're trying to do something with a value which is either *undefined* or *null* or you got your *types* wrong.

It's important to take the time to read errors which you get. They may be difficult to read at first
but as you gain experience, they will start to make more sense. Some errors are better formulated
and make it very clear what went wrong, while others send you on a quest to discover what's actually
going on.

```js
const someWord = 'whale'

console.log(someWord) // => 'whale'

// An example of a function that isn't going to work
function() {
  "Hello " + someWord;
}
```