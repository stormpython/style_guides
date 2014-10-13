# Javascript Style Guide
Based on the style guide by Nicholas C. Zakas in 
[Maintainable Javascript](http://shop.oreilly.com/product/0636920025245.do).

## Indentation
Each indentation level is made up for four spaces.
Do not use tabs.

```javascript
// Good
if (true) {
    doSomething();
}
```

## Line Length
Each line should be no longer than 80 characters. If a line goes longer than 80
characters, it should be wrapped after an operator (comma, plus, etc.). The
following line should be indented two levels (eight characters).

```javascript
// Good
doSomething(arguments1, arguments2, arguments3, arguments4,
        arguments5);
        
// Bad: Following line only indented four spaces
doSomething(arguments1, arguments2, arguments3, arguments4,
    arguments5);
    
// Bad: Breaking before operator
doSomething(arguments1, arguments2, arguments3, arguments4
        , arguments5);
```

## Primitive Literals
Strings should always use double quotes (never single quotes) and should always 
appear on a single line. Never use a slash to create a new line in a string.

```javascript
// Good
var name = "Nicholas";

// Bad: Single quotes
var name = 'Nicholas';

// Bad: Wrapping to second line
var longString = "Here's the story, of a man \
named Brady.";
```

Numbers should be written as decimal integers, e-notation integers, 
hexadecimal integers, or floating-point decimals with at least one digit 
before and one digit after the decimal point. Never use octal literals.

```javascript
// Good
var count = 10;

// Good
var price = 10.0;
var price = 10.00;

// Good
var num = 0xA2;

// Good
var num = 1e23;

// Bad: Hanging decimal point
var price = 10.;

// Bad: Leading decimal point
var price = .1;

// Bad: Octal (base 8) is deprecated
var num = 010;
```

The special value `null` should be used only in the following situations:

    * To initialize variables that may be later assigned an object value
    * To compare against an initialized variable that may or may not have an 
    object value
    * To pass into a function where an object is expected
    * To return from a function where an object is expected
    
Examples:

```javascript
// Good
var person = null;

// Good
function getPerson() {
    if (condition) {
        return new Person("Nicholas");
    } else {
        return null;
    }
}

// Good
var person = getPerson();
if (person !== null) {
    doSomething();
}

// Bad: Testing against an uninitialized variable
var person;
if (person != null) {
    doSomething();
}

// Bad: Testing to see if an argument was passed
function doSomething(arg1, arg2, arg3, arg4) {
    if (arg4 != null) {
        doSomethingElse();
    }
}
```

Never use the special value `undefined`. To see if a variable has been 
defined, use the `typeof` operator:

```javascript
// Good
if (typeof variable == "undefined") {
    // do something
}

// Bad: Using undefined literal
if (variable == undefined) {
    // do something
}
```







