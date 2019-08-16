# Object Oriented Programming

Object Oriented Programming focuses on modeling objects which represent objects in real life. There are many different paradigms, but this one is very popular and used in a large portion of today's technology. The goal is to asses a business requirement or real life problem, create some objects that represent them, and then manipulate them using methods.

## This lesson covers
* Writing DRY code
* Classes and Prototypes
* Hoisting
* Ternary operators
* Asynchronous vs Synchronous 
* Promises

## Writing DRY code
DRY stands for **Don't Repeat Yourself**. When coding, we want to make sure we reuse as much code as possible. This topic goes deep but ways to start doing this are:

* Notice patterns in your code and bundle functionality into methods
* Use classes to organize code and create reusable patterns for a specific purpose
* Store values in variables or constants to reuse them

## Classes and Prototypes
Classes are one of the main aspects of object oriented programming. They allow us to organize methods into groups to keep related logic organized. Classes are are also a type of *syntactic sugar* which builds on top of the *prototype* system JavaScript uses.

### Prototypes
One way of creating objects we haven't seen yet is using an *object constructor*.

```js
function Fish(speed, weight, breed) {
  this.speed = speed;
  this.weight = weight;
  this.breed = breed;
}

const newAwesomeFish = new Fish(180, 200, 'sailfish');
console.log(newAwesomeFish) // => Fish { speed: 180, weight: 200, breed: 'sailfish' }

// Trying to add a new property to an *object constructor* won't work
Fish.trick = "back-flip";

// To do it, we have to use the prototype property
Fish.prototype.trick = "back-flip"
```

### Classes
```js
class Dog {
  constructor(name, breed) {
    this.name = name;
    this.breed = breed;
  }

  bark() {
    console.log('Börk');
  }

  breed() {
    console.log(`I am a ${this.breed}`);
  }
}

const doggo = new Dog('Doggo', 'Schnauzer');

doggo.bark() // => Börk
doggo.breed() // => I am a schnauzer
```

One way that classes really shine through is reusing code.

```js
class Animal {
  constructor(genus, weight, region) {
    this.genus = genus;
    this.weight = weight;
    this.region = region;
  }

  genus() {
    console.log(`This animal's genus is ${this.genus}`);
  }

  sound() {
    console.log("This animal makes some sort of noise...");
  }
}

class Dog extends Animal {
  constructor(genus, weight, region) {
    super(genus, weight, region)
  }

  sound() {
    console.log("This animal börks a lot. Even when it doesn't have to");
  }
}

// To extend an existing class
```

## Hoisting
Hoisting is a term which is used when describing whether functions and classes have to be ordered according to where and when they are used or not. When something is 'hoisted' it means even if it's declared after the place where you use it, it will be fine. There are two main rules to follow here:

* Declare variables before you use them (at the beginning of the scope)

* Declare classes before you use them 

Neither of these are hoisted.

```js
// This will throw an error because variables are not hoisted
console.log(x);

const x = "This is an example value";

// This also won't work
const rabbit = new Rabbit('fluffy', 'small');

class Rabbit {
  constructor(fur, size){
    this.fur = fur;
    this.size = size;
  }
}
```

## Ternary operators
This is another example of *syntactic sugar*. Ternary operators are basically a two choice conditional statement, an *if - else*, if you want to call it that. They look liked this:

```js
const moonColor = "yellow";

// this is comparison  |    if true this     |     else this
moonColor === "yellow" ? console.log('Yep!') : console.log('Nope!');
```

So the ternary operator consists of three parts, separated by two operators: `?` and `:`

The same logic using a conditional statement would look like this:
```js
if (moonColor === "yellow") {
  console.log('Yep!');
} else {
  console.log('Nope!');
}
```

That's 87 characters for the *conditional statement* vs 68 characters for the *ternary operator*. Being consise is a worthwhile goal when coding, so try to look out for opportunities to make your code more succinct. On the other hand, watch out with more complex logic - if you try to ram it into a *ternary operator* you're going to end up with code that's hard to comprehend.

## Asynchronous vs Synchronous
In programming things happen in sequence, one after the other, or in parallel, at the same time. 

Something that is **asynchornous** doesn't wait for other things to finish.

Something that is **synchronous** waits its turn.

```js
function synchronous() {
  console.log("Hey, I'm first");
  console.log("Hey, I'm second");
}

function asynchronous() {
  setTimeout(function() { console.log("Hey, I'm first"); }, 3000);
  console.log("Hey I'm second");
}
```

## Promises
Promises help us deal with *asynchronous** code by essentially forcing it to be **synchronous** again. Promises are aptly named, because essentially they give us a promise that a response will come back, regardless of whether the action that was meant to be completed succeeded or not.

Below is an example where we use a promise to wait for something to happen first, using the *await* operator.

```js
async function delayedThing() {
  return new Promise((resolve, reject) => {
    setTimeout(function() { 
      resolve(console.log("Hey I'm first")); 
    }, 3000)
  })
}

async function forcedSynchronous() {
  await delayedThing();
  console.log("Hey I'm second");
}
```