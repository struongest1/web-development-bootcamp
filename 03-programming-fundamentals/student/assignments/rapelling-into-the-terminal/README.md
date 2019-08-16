# Rapelling Into The Terminal

Being the brave adventurer you are, you will be rapelling into your terminal using REPL. REPL is a powerful tool which provides a runtime for JavaScript (read: something that can interpret and run our code). 

## Assignment Instructions
1. Go into your terminal, it's not important what directory
2. Type in `node` and press "return"
3. You are now in the REPL - to exit press "ctrl+c" twice or type ".exit"
4. Create an object which represents you! It should have the following attributes:
    * firstName
    * lastName
    * age
    * hairColor
    * favoriteColor
    * themeSong
    * motto
5. Write a function which takes the object representing you and writes a story using *string concatention*

## Example
```js
const tuna = {
    firstName: 'Gulpy',
    lastName: 'Scalez',
    age: 20,
    hairColor: null,

}

function hairStyle(color) {
    if (color) {
        return "magnificent " + color + " hair, waved in the wind for all to see"
    } else {
        return "it was bald, and its shiny head turned everyone blind"
    }
};

function tellAStory(userObject){
    console.log("Once upon a time, a fish by the name " + userObject.firstName + " " + userObject.lastName + " headed to the barber. Because it was " + userObject.age + " years old, its " + hairStyle(userObject.hairColor);
};

tellAStory(tuna)
```