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

## Lint Code  ##