# Decorators #

>same as annotation in java or attribute in c#

A Decorator is a special kind of declaration that can be applied to classes, methods, accessor, property, or parameter.

![alt text](asset/gift.png)

Takes Book Gift as real world analogy where 

**Object[classes, methods, accessor, property]**: The gift (e.g., a book).

**Decorator:** The wrapping paper and ribbon.

**Result:**  aesthetic appeal to the gift (runtime behaviour) without changing the gift itself.


Decorators are simply functions that are prefixed @expression symbol,
 - where expression must evaluate to a function that will be called at runtime with information about the decorated declaration.

TypeScript Decorators serves the purpose of adding both annotations and metadata to the existing code in a declarative way.

Simply, Decorators in TypeScript are similar to Aspect-Oriented Programming (AOP) in that they allow you to add behavior to existing code in a declarative way. Both concepts enable you to separate cross-cutting concerns (like logging, security, or transaction management) from the main business logic.


```typescript repl+

class Book {
    read(page: number): number {
        return page;
    }
}

// Step 2: Create a decorator function
function LogWrapper(target: any, propertyKey: string, descriptor: PropertyDescriptor) {
    const originalMethod = descriptor.value;

    descriptor.value = function (...args: any[]) {
        console.log(`Method ${propertyKey} called with page No: ${JSON.stringify(args)}`);
        const result = originalMethod.apply(this, args);
        console.log(`Method ${propertyKey} returned page: ${result}`);
        return result;
    };

    return descriptor;
}

// Step 3: Apply the decorator to the method
class BookWithWrapper {
    @LogWrapper
    read(page: number): number {
        return page;
    }
}

const bookgGift = new BookWithWrapper();
bookgGift.add(2, 3); // Logs method call and result without affect the original method
```

