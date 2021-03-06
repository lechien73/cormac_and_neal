## Other Random JavaScript stuff that we covered

Mostly, on Thursday morning, we did more algorithm challenges.

I've pasted them below.

```

/*
Create a function called cToF that accepts one argument called celsius.
The function should return the value of celsius converted to Fahrenheit.
The formula to convert celsius to Fahrenheit is: (celsius * 1.8) + 32

BONUS ROUND:
Create another function called fToC that converts Fahrenheit back to Celsius.

BONUS BONUS ROUND:
Combine the two functions into one called convertTemp that takes two arguments: num and unit.
Calling: convertTemp(32,"C") will convert 32 Celsius to Fahrenheit.
Calling convertTemp(101, "F") will convert 101 Fahrenheit to Celsius.
*/

/* Create a function called largestNumber that takes one argument called numberArray.
When an array is passed in, the function should return the largest number in the array.
Calling: largestNumber([1,7,8,3,12,2]) should return 12.

*/
/*
Hint: This will require iterating through the array, using an if statement and a variable to store the largest number.
*/

/* Write a JavaScript function called sumArray that returns the sum of numbers in an array.

    So, calling: sumArray([1,3,5,7]) will return 16,
    which is 1 + 3 + 5 + 7.

*/

/* Push zeroes last.

Write JavaScript a function called pushZeroes that takes one argument called input.

You can assume that input will be a string, but it will be a string of numbers, e.g: "30041203"

Your aim is to return a string with the zeroes pushed to the end, so calling pushZeroes("30041203") will return "34123000"

See below for hints.

*/

/* Hints

A string can use some of the same methods as an array,
so:

let myString = "12345";

myString.indexOf("4");

will return the index of 3.

Remember that you might need to create two empty strings - one for zeroes and one for non-zero numbers

You will need to combine the strings at the end.

*/

/* DIFFICULT: Make Bricks challenge:

Write a function called makeBricks that accepts three
arguments: small, big, goal.

We want to make a row of bricks that is goal inches long. We have a number of small bricks (1 inch each) and big bricks (5 inches each). Return true if it is possible to make the goal by choosing from the given bricks, and false if it is not possible. This is a little harder than it looks and can be done without any loops.

So, for example:

makeBricks(2,1,7) = true
makeBricks(2,1,8) = false
makeBricks(3,2,12) = true

function makeBricks(small, big, goal) {

}

*/

```

We also talked about the need for defensive programming - the need to make sure that your user can't break your program.

For example, this JavaScript function has no defensive programming:

```JavaScript
function cToF(temp) {
    temp = temp * 1.8 + 32;
    return temp;
}
```

We can't guarantee that the user will always send in a number, so we could check like this:

```JavaScript
function cToF(temp) {
    if (typeof(temp) !== "number") {
        return "Error! Argument must be a number";
    }
    temp = temp * 1.8 + 32;
    return temp;
}
```

Always do your defensive checks before you start doing something with the variable.

**CHALLENGE**:
Add more defensive code to the fToC and convertTemp functions that you wrote earlier.

## JavaScript Objects

We talked about how everything in JavaScript is an object, but we can also create our own.

An empty object in JavaScript looks like this:

```JavaScript
let myObject = {};
```

Properties in objects are stored as key/value pairs, like so:

```JavaScript
let myObject = {
    "name": "Matt",
    "job":  "Lecturer",
    "location": "Classroom"
};
```

Each key/value is separated by a comma. We can then call the properties of this, like so:

```JavaScript
myObject.name;
```

We can add methods (functions) to our object like this:

```JavaScript
let myObject = {
    "name": "Matt",
    "job":  "Lecturer",
    "location": "Classroom",
    "who": function() {
        return `${this.name} is a ${this.job} in the ${this.location}`;
    }
};
```

Now try running:

```JavaScript
myObject.who();
```

We can also extend existing objects using the `prototype` keyword. This allows us to even extend the built-in JavaScript objects.

For example, here is some code to add a rot13() method to the JavaScript String object. To read more about the simple ROT13 encryption cipher, [click here.](https://en.wikipedia.org/wiki/ROT13)

```JavaScript
String.prototype.rot13 = function() {
  let initial = "ABCDEFGHIJKLMNOPQRSTUVWXYZabcdefghijklmnopqrstuvwxyz";
  let rot13 = "NOPQRSTUVWXYZABCDEFGHIJKLMnopqrstuvwxyzabcdefghijklm";

  let returnString = "";

  for (let i = 0; i < this.length; i++) {
    if (initial.indexOf(this[i]) == -1) {
      returnString += this[i];
    } else {
      indexPosition = initial.indexOf(this[i]);
      returnString += rot13[indexPosition];
    }
  }
  return returnString;
}
```

If you run this in repl.it (make sure that you create a new REPL with the language of JavaScript - not node.js), then whenever you create a new string, it will have the rot13() method attached.

For example:

```JavaScript
let myString = "Cormac and Neal";
myString.rot13();
```

This will return `Pbeznp naq Arny`, which is our original string rotated by 13 characters.