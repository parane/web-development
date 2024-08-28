# Literals & Destructuring #

In new version javascript introduce literals and destructuring to 

- Improved Readability: Makes the code more readable and concise.
- Avoids Repetition: Reduces the need to repeatedly access properties or array elements.
- Nested Destructuring: Supports extracting values from nested objects and arrays.

## Template Literal ##

Template literals are string literals allowing embedded expressions. You can use multi-line strings and string interpolation features with them.

```javascript repl
const name = 'John';
const wish = 'Good morning'
console.log('Hello'+name+'!'+wish); //Hello John! Good morning
```

```javascript repl
//using template literals
console.log(`Hello ${name}! ${wish}`); //Hello John! Good morning
```