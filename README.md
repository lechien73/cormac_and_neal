# Summary for Cormac & Neal

Thursday, we looked at JavaScript in the browser.

JavaScript in the browser can be loaded in two ways, much like CSS.

```
<script>
alert("testing");
</script>
```

Or by loading an external JavaScript file:

`<script src="test.js"></script>`

## Accessing elements on a web page

We talk to the Document Object Model (the DOM) to locate items that we want to change. Remember that in JavaScript, everything is an object. It's the same in a HTML page too.

We used the HTML tree generator before to see the parent and child elements on a web page. Each of these is an object.

Check sample1.html to see an example.

In this file, we have an empty div with the id of test.

We call the document object, and the getElementById method. This returns our div object with the id of test. We then use the innerHTML property to set the HTML inside the div.

At its most basic, this is how JavaScript interacts with a web page.

## Light bulbs

Another example is in sample2.html. Here, we do the same as in sample1, but we change the src attribute of an img tag when we click the buttons.

Examine the code so that you know what it's doing.

**CHALLENGE**
* Add a <div id="status"> beneath the buttons.
* Use the JavaScript you've learned so far to put the following text in:
  * When the light is switched off, put the text "It's dark in here!" in h2 tags.
  * When the light is switched on, put the text "It's too bright in here!" in h2 tags.

## Changing classes

To affect the appearance of items on a web page, we often want to dynamically change its CSS.

JavaScript allows us to alter the style attribute of all of the elements, but that creates inline styline, which we'd prefer not to use.

The ideal way of adjusting the styling is to add and remove classes.

We can do this with the `classList.add()` and `classList.remove()` methods.

Have a look at sample3.html for an example of how we do this with our light bulb page.

Check the code and make sure you know how it works.

Up until now, we've been using innerHTML to change the content of a div or paragraph. We could also use the textContent method, which changes only the text.

**Suggestion**:

Try changing the innerHTML property to textContent on sample3.html and see what happens.

## Reference

If you want to know what methods and properties you can use with each DOM object, then W3 Schools has a handy reference page.

Here it is: https://www.w3schools.com/jsref/default.asp

Scroll down to *HTML DOM* or *HTML elements*, and click on an element to see the properties and methods available.

## The maths game

Now that you have had some experience with JavaScript in the browser, create a new Cloud9 workspace called mathsgame

Open a terminal window and paste in the following code:

```
git clone https://github.com/Code-Institute-Solutions/js-mathsgame-starter.git
```

This will clone my maths game starter repository.

Open up the HTML code first, and look through it.

Most of the stuff is fairly standard - we're running functions when we click the buttons. We've seen that before.

The data-gametype attribute in the form element is new...

We made up this attribute ourselves, and we refer to it and set it in the JavaScript. Putting data- at the front is a way of telling the browser and other developers that this is an attribute we made up ourselves.

You'll also notice that when the form is submitted, it runs:

```
checkAnswer(); return false;
```

The reason it does return false; is to stop the form from refreshing when it has been submitted. Otherwise it refreshes the page, and our score resets to zero.

In our form, we have three inputs.

The first, is where we put the answer.

The second, is a hidden input. We will store the correct answer there, and compare it with the answer given by the user.

The third is a submit button.

Other than those oddities, everything else is fairly normal. We're giving things IDs and names so that we can refer to them in JavaScript.

Now, open the game.js file and have a look through it.

Firstly, we set up some variables, so that we don't have to keep calling document.getElementById every time we want to refer to these objects.

Then, we have the functions that are invoked when we click on the game type buttons. Notice that it sets the attribute of data-gametype and then calls the appropriate game function.

Scroll down to the additionQuiz function to see what it does.

First, it generates two random numbers using the Math library.

Math.random on its own will generate a random number between 0 and 1. So, we multiply it by 50 to get a random number between 0 and 50.

Math.floor rounds the result down to the nearest whole number, so we always get an integer.

If you're not sure about how this works, then [check this repl](https://repl.it/@shever73/TurboBossyProducts)

Our additionQuiz function then sets the textContent of the paragraph with the ID of question to the current question.

It then sets the hidden value of our form to the correct answer.

When the form is submitted, we run the checkAnswer function. This stores the value of the data-gametype attribute in a variable so that we can use it later.

Then, it compares the submitted answer with the hidden input which contains the correct answer. If they match, we get an alert to say we got it right and the score is incremented by 1.

If they don't match, we get a commiserations alert box.

The function then checks the game type to see which game it should call next.

**CHALLENGE**:

Your challenge is to get the subtraction and multiplication games working, and to style the project.

***BONUS CHALLENGES***

* Add a timer to the project
* Add a division game that requires whole numbers as answers
* Add difficulty levels - Easy, Normal, Difficult - that affect the complexity of the questions.
* Add a high-score chart for people who get the most answers right in the time available



