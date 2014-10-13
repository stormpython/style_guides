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


