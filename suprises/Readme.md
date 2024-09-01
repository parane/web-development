# JavaScript Surprises and Best Practices #

![Alt Text](asset/err.gif)

Lets see some silent(suprise) errors which  do not trigger any kind of reporting, but fail in runtime and how can we mitigate ?

## ASI Automatic insert of semicolons ##

ASI is a feature of JavaScript that automatically inserts a semicolon at the end of a line if it is missing. This can lead to unexpected behavior in your code, and is generally considered a bad practice. 
It is recommended to always include semicolons at the end of your lines to avoid any issues.

![Alt Text](asset/semi.webp)

``` javascript repl+
function getValue() {
    return
    {
        value: 1
    };
}

console.log(getValue()); // Expected: { value: 1 }, Actual: undefined
```

explain:
Automatic Semicolon Insertion (ASI): JavaScript automatically inserts a semicolon after the return statement.
Effect: The function effectively becomes:<pre>function getValue() { return; // ASI inserts a semicolon here { value: 1 }; } </pre>
Result: The function returns undefined because the return statement is terminated before the object is returned.

So we need to be careful about this and always include semicolons at the end of your lines to avoid any issues.

![Alt Text](asset/semicolon.jpg)

## use === instead == ##

![Alt Text](asset/equal.png)

== (Equality Operator):  
Compares two values for equality after converting both values to a common type (type coercion).

=== (Strict Equality Operator):
Compares two values for equality without converting them to a common type (no type coercion).

``` javascript repl+
console.log('0'==0); //true
console.log('0'===0); //false
console.log([]==0); //true because [] -> '' and 0 -> '' then compared
console.log([]===0); //false
console.log([]=='0'); //false because [] -> '' and then compared with '0'

```

Use === when you want to compare values without type conversion (recommended for most cases to avoid unexpected results).


## Apply the use strict Directive ##

"use strict" is a directive in top js file that enables strict mode. Strict mode is a way to opt in to a restricted variant of JavaScript, 
which can help catch common coding errors and "unsafe" actions such as defining global variables. 

Here are some key points
-Eliminates some JavaScript silent errors by changing them to throw errors. 


``` javascript repl+

function f(){
'use strict';
 x=10; //x is not define 

}

f();


```

## Lint Code  ##

Earlier Strict gives support some extend, so it would be a nice to know about some potential error even before running the code. 

the process of analyzing code for potential errors, coding standard violations, and stylistic issues. A linter is a tool that performs this analysis and helps developers maintain consistent code quality.

![Alt Text](asset/lint.webp)


There are many popular linters available for JavaScript, such as ESLint, JSHint, and JSLint. These tools can be integrated into your development workflow to catch errors early and enforce coding standards.

![Alt Text](asset/eslint-sh.jpg)

ESLint: A highly configurable linter that supports custom rules and plugins.
JSHint: Another popular linter that checks for potential errors and enforces coding conventions.
JSLint: A more opinionated linter created by Douglas Crockford, focusing on code quality and best practices.

JSLint is little agressive  and has fewer configuration options, while ESLint is highly configurable and supports custom rules and plugins. 

![Alt Text](asset/jslint.jpg)