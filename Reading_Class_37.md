# Reading: Class 37

> [Back to the main](./README.md)

---

# ES6 Syntax and Feature Overview

ECMAScript 2015, also known as ES6, introduced many changes to JavaScript. Here is an overview of some of the most common features and syntactical differences, with comparisons to ES5 where applicable.

## Variable declaration

ES6 introduced the let keyword, which allows for block-scoped variables which cannot be hoisted or redeclared.

    var x = 0
    let x = 0

## Constant declaration

ES6 introduced the const keyword, which cannot be redeclared or reassigned, but is not immutable.

    ES6
    const CONST_IDENTIFIER = 0 // constants are uppercase by convention

## Arrow functions

The arrow function expression syntax is a shorter way of creating a function expression. Arrow functions do not have their own this, do not have prototypes, cannot be used for constructors, and should not be used as object methods.

    ES5
    function func(a, b, c) {} // function declaration
    var func = function (a, b, c) {} // function expression

    ES6
    let func = (a) => {} // parentheses optional with one parameter
    let func = (a, b, c) => {} // parentheses required with multiple parameters

## Template literals

Concatenation/string interpolation
Expressions can be embedded in template literal strings.

    ES5
    var str = 'Release date: ' + date
    ES6
    let str = `Release Date: ${date}`

## Multi-line strings

Using template literal syntax, a JavaScript string can span multiple lines without the need for concatenation.

    ES5
    var str = 'This text ' + 'is on ' + 'multiple lines'
    ES6
    let str = `This text
                is on
                multiple lines`

Note: Whitespace is preserved in multi-line template literals. See Removing leading whitespace in ES6 template strings.

## Implicit returns

The return keyword is implied and can be omitted if using arrow functions without a block body.

    ES5
    function func(a, b, c) {
    return a + b + c
    }
    ES6
    let func = (a, b, c) => a + b + c // curly brackets must be omitted

## Array iteration (looping)

A more concise syntax has been introduced for iteration through arrays and other iterable objects.

    var arr = ['a', 'b', 'c']

    ES5
    for (var i = 0; i < arr.length; i++) {
    console.log(arr[i])
    }

    ES6
    for (let i of arr) {
    console.log(i)
    }

---

# Introducing JSX

Consider this variable declaration:

    const element = <h1>Hello, world!</h1>;

This funny tag syntax is neither a string nor HTML.

It is called JSX, and it is a syntax extension to JavaScript. We recommend using it with React to describe what the UI should look like. JSX may remind you of a template language, but it comes with the full power of JavaScript.

JSX produces React “elements”. We will explore rendering them to the DOM in the next section. Below, you can find the basics of JSX necessary to get you started.


## Why JSX?

React embraces the fact that rendering logic is inherently coupled with other UI logic: how events are handled, how the state changes over time, and how the data is prepared for display.

Instead of artificially separating technologies by putting markup and logic in separate files, React separates concerns with loosely coupled units called “components” that contain both. We will come back to components in a further section, but if you’re not yet comfortable putting markup in JS, this talk might convince you otherwise.

React doesn’t require using JSX, but most people find it helpful as a visual aid when working with UI inside the JavaScript code. It also allows React to show more useful error and warning messages.

With that out of the way, let’s get started!

## Embedding Expressions in JSX

In the example below, we declare a variable called name and then use it inside JSX by wrapping it in curly braces:

    const name = 'Josh Perez';
    const element = <h1>Hello, {name}</h1>;

You can put any valid JavaScript expression inside the curly braces in JSX. For example, 2 + 2, user.firstName, or formatName(user) are all valid JavaScript expressions.

In the example below, we embed the result of calling a JavaScript function, formatName(user), into an h1 element.

    function formatName(user) {
    return user.firstName + ' ' + user.lastName;
    }

    const user = {
    firstName: 'Harper',
    lastName: 'Perez'
    };

    const element = (
    <h1>
        Hello, {formatName(user)}!
    </h1>
    );

We split JSX over multiple lines for readability. While it isn’t required, when doing this, we also recommend wrapping it in parentheses to avoid the pitfalls of automatic semicolon insertion.

## JSX is an Expression Too

After compilation, JSX expressions become regular JavaScript function calls and evaluate to JavaScript objects.

This means that you can use JSX inside of if statements and for loops, assign it to variables, accept it as arguments, and return it from functions:

    function getGreeting(user) {
    if (user) {
        return <h1>Hello, {formatName(user)}!</h1>;
    }
    return <h1>Hello, Stranger.</h1>;
    }

## Specifying Attributes with JSX

You may use quotes to specify string literals as attributes:

    const element = <a href="https://www.reactjs.org"> link </a>;
    You may also use curly braces to embed a JavaScript expression in an attribute:

    const element = <img src={user.avatarUrl}></img>;

Don’t put quotes around curly braces when embedding a JavaScript expression in an attribute. You should either use quotes (for string values) or curly braces (for expressions), but not both in the same attribute.
