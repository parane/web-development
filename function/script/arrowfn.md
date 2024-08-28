# Arrow function #

Arrow functions are a more concise way to write functions in JavaScript.
They are written using:
![Alt Text](asset/arrow.png)
Arrow functions are anonymous and change the way `this` is handled in functions.


Dont confuse with Anonymous function which has been in javascript from day one. Arrow function is new 

Function can be define three ways
1. 
```javascript
function add(a, b) {
    return a + b;
}
```
2. Anonymous function , stored into variable
```javascript
const add = function(a, b) {
    return a + b;
}
```

3. Arrow function

```javascript

const add = (a, b) => a + b;
```

## Arrow vs Anonymous ##
There are many semantic difference between anonymous fn and arrow function. 

Lets consider about scoping in function. There are two type of scoping in function:

1. Static Scoping / Lexical Scoping : 
Accessing the variable from the place where it is defined and is unrelated to run time call stack. 

```javascript repl+
const value = 10;

function outerFunction() {
    const value = 20;

    function innerFunction() {
        console.log(value); // Lexical scoping: `value` is 20
    }

    innerFunction();
}

outerFunction(); // Output: 20
```
2. Dynamic Scoping
on the other hand, determines the value of a variable based on the call stack at runtime.
JavaScript does not support dynamic scoping for general variable. but there are some exception case like `this` and 'arguments'

```javascript repl+
let x =10;
function foo(){
    console.log(x); // 10  Hypothetical Output: 20 if it is dynamic scoping 
}
function bar(){
    let x = 20;
    foo();
}
bar(); // 10
```

Anonymous function use dynamic scoping for this and arguments , lexical/static scoping for all other variables
This behaviour is often a source of confusion and bugs in JavaScript code

Arrow function is static scoping , it does not have its own `this` and `arguments` object. 
It uses the `this` and `arguments` from the parent scope. 

Example: 

using anonymous function 
```javascript repl+
const obj = {
    value: 42,
    method: function() {
        console.log(this.value); // `this` refers to `obj`

        function innerFunction() {
            console.log(this); // `this` refers to the global object (or undefined in strict mode)
        }

        innerFunction();
    }
};

obj.method();
```


```javascript repl+
const obj2 = {
    value: 42,
    method: function() {
        console.log(this.value); // `this` refers to `obj`

        const innerFunction = () => {
            console.log(this); // `this` refers to `obj` (lexically inherited)
        };

        innerFunction();
    }
};

obj2.method();
```


## when to use Arrow ##

1 Shorter Syntax: When you need a concise way to write small functions.
2 Lexical this Binding: When you want to inherit this from the parent scope, avoiding the common pitfalls of dynamic this binding in regular functions.
3 No arguments Object: When you don't need the arguments object, as arrow functions do not have their own arguments object.
4 Callbacks: When passing functions as arguments, especially in array methods like map, filter, and reduce.

Functional style code removes accidental complexity , we use function composition a series of transformations to make code more readable and maintainable.

eg :

```javascript repl+
//Imperative Style Example
const numbers = [1, 2, 3, 4, 5];
const doubled = [];
for (let i = 0; i < numbers.length; i++) {
    doubled.push(numbers[i] * 2);
}
console.log(doubled); // Output: [2, 4, 6, 8, 10]

//Functional Style
const numbers = [1, 2, 3, 4, 5];
const doubled = numbers.map(n => n * 2);
console.log(doubled); // Output: [2, 4, 6, 8, 10]
```

## when not to use Arrow ##

- Cannot be Used as Constructors: Arrow functions cannot be used with the new keyword. They do not have a prototype property, so they cannot be used to create instances of objects.

```javascript repl+
// Cannot be used as constructors
const ArrowFunction = () => {};
const instance = new ArrowFunction(); // Error: ArrowFunction is not a constructor

```