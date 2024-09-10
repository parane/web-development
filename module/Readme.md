## Module ##
The selected code demonstrates how to create and use modules in JavaScript. 
Modules are a way to organize and encapsulate code, making it easier to manage and reuse. JavaScript modules allow you to export variables, functions, or classes from one file and import them into another.

JavaScript modules are used to modularize code—that is, to divide code into
parts that have different concerns, but they may need to depend on one
another. For example, each component and service class you create in, say,
React and Angular will belong to separate modules. Each group of functions
related to a common set of operations may belong to a module.

As a creator of a module, you’re responsible for clearly specifying what you need—the imports—and
what you provide for others to use—the exports.


### Export ###
As of ECMAScript 2015 (ES6), it is possible to export values from a JavaScript module and import them into another script.

You can export variables, functions, or classes from a module using the export keyword.

``` javascript repl+
export const pi = 3.14159;
export function add(a, b) {
    return a + b;
}
```

Default Export:

``` javascript repl+
// file: logger.js
export default function log(message) {
    console.log(message);
}
```

### Import ###

**Named import**
Named imports allow you to import specific bindings from a module.

``` javascript repl+
import { pi, add } from './math.js';
console.log(pi); // Output: 3.14159
```

**Default Import** 


``` javascript repl+
// file: logger.js
export default function log(message) {
    console.log(message);
}
```

**Side Effect Import**

A side effect import is used to run a module's code without importing any bindings. This is useful for polyfills or modules that modify global objects.

``` javascript repl+
// file: polyfill.js
import './polyfill.js';
```

**Namespace Import**

Namespace imports allow you to import all of a module's exports under a single namespace.

``` javascript repl+

// file: app.js
import * as math from './math.js';
console.log(math.pi); // Output: 3.14159
console.log(math.add(2, 3)); // Output: 5
```


An import statement without curly braces is used to import the default export. 
An import statement with curly braces is used to import a named export.

Named Import Alias

``` javascript repl+

import { add as sum } from './math.js';
console.log(sum(2, 3)); // Output: 5
```

To create an import alias using @ for a specific directory in a JavaScript or TypeScript project, 
you need to configure your module resolution.
