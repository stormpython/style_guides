# Javascript Style Guide
Based on the style guide by Nicholas C. Zakas in 
[Maintainable Javascript](http://shop.oreilly.com/product/0636920025245.do).

## Table of Contents

1. [Indentation](#indentation)
2. [Line Length](#line-length)
3. [Primitive Literals](#primitive-literals)
4. [Operator Spacing](#operator-spacing)
5. [Parentheses Spacing](#parentheses-spacing)
6. [Object Literals](#object-literals)
7. [Comments](#comments)
    * [Single-Line Comments](#single-line-comments)
    * [Multiline Comments](#multiline-comments)
    * [Comment Annotations](#comment-annotations)
8. [Variable Declarations](#variable-declarations)

## Indentation
Each indentation level is made up for four spaces.
Do not use tabs.

```javascript
// Good
if (true) {
    doSomething();
}
```

**[⬆ back to top](#table-of-contents)**

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

**[⬆ back to top](#table-of-contents)**

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

**[⬆ back to top](#table-of-contents)**

## Operator spacing
Operators with two operands must be preceded and followed by a single space 
to make the expression clear. Operators include assignments and logical 
operators.

```javascript
// Good
var found = (values[i] === item);

// Good
if (found && (count > 10)) {
    doSomething();
}

// Good
for (i = 0; i < count; i++) {
    process(i);
}

// Bad: Missing spaces
var found = (values[i]===item);

// Bad: Missing spaces
if (found&&(count>10)) {
    doSomething();
}

// Bad: Missing spaces
for (i=0; i<count; i++) {
    process(i);
}
```

**[⬆ back to top](#table-of-contents)**

## Parentheses Spacing
When parentheses are used, there should be no whitespace immediately after 
the opening paren or immediately before the closing paren.

```javascript
// Good
var found = (values[i] === item);

// Good
if (found && (count > 10)) {
    doSomething();
}

// Good
for (i = 0; i < count; i++) {
    process(i);
}

// Bad: Extra space after opening paren
var found = ( values[i] === item);

// Bad: Extra space after closing paren
if (found && (count > 10) ) {
    doSomething();
}

// Bad: Extra space around argument
for (i = 0; i < count; i++) {
    process( i );
}
```

**[⬆ back to top](#table-of-contents)**

## Object Literals
Object literals should have the following formats:

* The opening brace should be on the same line as the containing statement.
* Each property-value pair should be indented one level with the first 
property appearing on the next line after the opening brace.
* Each property-value pair should have an unquoted property name, 
followed by a colon (no space preceding it), followed by the value.
* If the value is a function, it should wrap under the property name and 
should have a blank line both before and after the function.
* Additional empty lines may be inserted to group related properties or 
otherwise improve readability.
* The closing brace should be on a separate line.

Examples:

```javascript
// Good
var object = {
    
    key1: value1,
    key2: value2,
    
    func: function() {
        // do something
    },
    
    key3: value3
};

// Bad: Improper indentation
var object = {
                key1: value1,
                key2: value2
             };
             
// Bad: Missing blank lines around function
var object = {
    
    key1: value1,
    key2: value2,
    func: function() {
        // do something
    },
    key3: value3
};
```

When an object literal is passed to a function, the opening brace should be 
on the same line as if the value is a variable. All other formatting rules 
listed earlier still apply.

```javascript
// Good
doSomething({
    key1: value1,
    key2: value2
});

// Bad: All on one line
doSomething({ key1: value1, key2: value2 });
```

**[⬆ back to top](#table-of-contents)**

## Comments
Make frequent use of comments to aid others in understanding your code. Use 
comments when:

* Code is difficult to understand
* The code might be mistaken for an error
* Browser-specific code is necessary but not obvious
* Documentation generation is necessary for an object, method, 
or property (use appropriate documentation comments).

**[⬆ back to top](#table-of-contents)**

### Single-Line Comments
Single line comments should be used to document one line of code or a group 
of related lines of code. A single line comment may be used in three ways:

* On a separate line, describing the code beneath it
* At the end of the line, describing the code before it
* On multiple lines, to comment out sections of code

When on a separate line, a single-line comment should be at the same 
indentation level as the code it describes and be preceded by a single line. 
Never use multiple single-line comments on consecutive lines; use a multiline
 comment instead.
 
```javascript
// Good
if (condition) {
    
    // if you made it here, then all security checks passed
    allowed();
}

// Bad: No empty line preceding comment
if (condition) {
    // if you made it here, then all security checks passed
    allowed();
}

// Bad: Wrong indentation
if (condition) {

// if you made it here, then all security checks passed
    allowed();
}

// Bad: This is a multiline comment
// This next piece of code is quite difficult, so let me explain.
// What you want to do is determine if the condition is true
// and only then allow the user in. The condition is calculated
// from several different functions and may change during the
// lifetime of the session.
if (condition) {
    
    // if you made it here, then all security checks passed
    allowed();
}
```

For single line comments at the end of a line, ensure that there is at least 
one indentation level between the end of the code and the beginning of the 
comment:

```javascript
// Good
var result = something + somethingElse; // somethingElse will never be null

// Bad: Not enough space between code and comment
var result = something + somethingElse;// somethingElse will never be null
```

The only acceptable time to have multiple single-line comments on successive 
lines is to comment out large sections of code. Multiline comments should not
 be used for this purpose.
 
```javascript
// Good
// if (condition) {
//     doSomething();
//     thenDoSomethingElse();
// }
```

**[⬆ back to top](#table-of-contents)**

### Multiline Comments
Multiline comments should be used to document code that requires more 
explanation. Each multiline comment should have at least three lines:
 
1. The first line contains only the /* comment opening. No further text is 
allowed on this line.

2. The next line or lines have a * aligned with the * in the first line. Text
 is allowed on these lines.
 
3. The last line has the */ comment opening aligned with the preceding lines.
 No other text is allowed on this line.
 
The first line of multiline comments should be indented to the same level as 
the code it describes. Each subsequent line should have the same indentation 
plus one space (for proper alignment of the * characters). Each multiline 
comment should be preceded by one empty line.

```javascript
// Good
if (condition) {

    /*
     * if you made it here,
     * then all security checks passed
     */
    allowed();
}

// Bad: No empty line preceding comment
if (condition) {
    /*
     * if you made it here,
     * then all security checks passed
     */
    allowed();
}

// Bad: Missing a space after asterisk
if (condition) {

    /*
     *if you made it here,
     *then all security checks passed
     */
    allowed();
}

// Bad: Wrong indentation
if (condition) {

/*
 *if you made it here,
 *then all security checks passed
 */
    allowed();
}

// Bad: Don't use multiline comments for trailing comments
var result = something + somethingElse; /* somethingElse will never be null */
```

**[⬆ back to top](#table-of-contents)**

### Comment Annotations
Comments may be used to annotate pieces of code with additional information. 
These annotations take the form of a single word followed by a colon. The 
acceptable annotations are:

**TODO**
    : Indicates that the code is not yet complete. Information about the next 
    steps should be included.
    
**HACK**
    : Indicates that the code is using a shortcut. Information about why the 
    hack is being used should be included. This may also indicate that it 
    would be nice to come up with a better way to solve the problem.
    
**XXX**
    : Indicates that the code is problematic and should be fixed as soon as 
    possible.
    
**FIXME**
    : Indicates that the code is problematic and should be fixed soon. Less 
    important than `XXX`.
    
**REVIEW**
    : Indicates that the code needs to be reviewed for potential changes.

These annotations may be used with either single-line or multiline comments 
and should follow the same formatting rules as the general comment type.

Examples:

```javascript
// Good
// TODO: I'd like to find a way to make this faster
doSomething();

// Good
/*
 * HACK: Have to do this for IE. I plan on revisiting in the future when I 
 * have more time. This probably should get replaced before v1.2.
 */
if (document.all) {
    doSomething();
}

// Good
// REVIEW: Is there a better way to do this?
if (document.all) {
    doSomething();
}

// Bad: Annotation spacing is incorrect
// TODO : I'd like to find a way to make this faster
doSomething();

// Bad: Comment should be at the same indentation as code
    // REVIEW: Is there a better way to do this?
if (document.all) {
    doSomething();
}
```

**[⬆ back to top](#table-of-contents)**

## Variable Declarations
**[⬆ back to top](#table-of-contents)**


