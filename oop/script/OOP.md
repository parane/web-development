# Inheritance #

Javascript original implementation of inheritance was different from other mainstream language in two ways.
Although most mainstream languages provided class based inheritance , javscript provided prototype based inheritance.
Javascript latest version provide class based inheritance syntax sugar, that is not changed the prototype based inheritance with new syntax.

## Class Inheritance ##
Class inheritance in JavaScript uses the class and extends keywords to create a hierarchical relationship between classes.

Class inheritance is often used in ES6+ codebases,

```javascript repl+
class Animal {
    constructor(name) {
        this.name = name;
    }

    speak() {
        console.log(`${this.name} makes a sound.`);
    }
}

class Dog extends Animal {
    speak() {
        console.log(`${this.name} barks.`);
    }
}

const dog = new Dog('Rex');
dog.speak(); // Output: Rex barks.
```

Usecase: Class component in React

Override the render method in the derived class.
```javascript repl+ 
import React, { Component } from 'react';
class SimpleComponent extends Component {
    render() {
        return (
            <div>
                <h1>Hello, World!</h1>
            </div>
        );
    }
}

export default SimpleComponent;
```

pls note constructor auto inject in case not written !


## Prototypal (Object Based) Inheritance ##
Even we decleare as class based inheritance , but in js , those are still prototype based inheritance.

Unlike class-based inheritance, prototypal inheritance is implemented using delegation. Remember the sage advice from good design books: delegation is
better than inheritance. 
Prototype-based languages like JavaScript take that advice to heart. Although languages like Java, C#, C++, Ruby, and a number
of other OO languages provide class-based inheritance, prototype-based languages use an object chain to delegate calls. Instead of relying on a base class
or superclass, prototypal inheritance relies on an object next in the chain to serve as its base. Class-based inheritance is rather inflexible—once you inherit your class from another class, it’s stuck to the parent. 
In prototype-based, inheritance is dynamic; you may alter the object that serves as the base at runtime. That base object is called the object’s prototype

```javascript repl+ 
// Base object
const animal = {
    eats: true,
    walk() {
        console.log("Animal walks");
    }
};

// Derived object create dynamically !
const rabbit = Object.create(animal);
rabbit.jumps = true;

console.log(rabbit.eats); // Output: true
console.log(rabbit.jumps); // Output: true
rabbit.walk(); // Output: Animal walks
```

rabbit inherits properties and methods from animal using Object.create.

Lets see some magic in Protoyoical inheritance 

```javascript repl+ 
// Base object
const Car = function (){
    this.drive = function (dist){
        this.km += dist;
    }
}

Car.prototype.km =0;
const car1 = new Car();
const car2 = new Car();
console.log(car1===car2); // false
console.log(Object.getPrototypeOf(car1) === Object.getPrototypeOf(car2)); //true

car1.drive(10);
console.log(car1.km); // 10
console.log(car2.km); // ???? 0
//get are deep , set are shallow
//It works as dynamic 
```

Lets check Class based inheritance 

```javascript repl+
class Animal {
    constructor(type) {
        this.type = type;
    }

    speak() {
        console.log(`${this.name} makes a sound.`);
    }
}

class Dog extends Animal {

    constructor(type,name){
        super(type);
        this.name = name;
    }
    speak() {
        console.log(`${this.name} barks.`);
    }
}

const dog = new Dog('Dog','Rex');
dog.speak(); // Output: Rex barks.
console.log('ss')
console.log(Object.getPrototypeOf(Object.getPrototypeOf(dog)));

```



# Polymorphism #

Polymorphism in JavaScript allows objects to be treated as instances of their parent class rather than their actual class. This is achieved through method overriding and method overloading.  

### Method Overriding ###
Method overriding occurs when a subclass provides a specific implementation of a method that is already defined in its superclass.

```javascript repl+ 
class Animal {
    speak() {
        console.log('Animal makes a sound.');
    }
}

class Dog extends Animal {
    speak() {
        console.log('Dog barks.');
    }
}

class Cat extends Animal {
    speak() {
        console.log('Cat meows.');
    }
}

const animals = [new Dog(), new Cat()];

animals.forEach(animal => {
    animal.speak(); // Output: Dog barks. Cat meows.
});
```

### Method Overloading ### 
JavaScript does not support method overloading in the traditional sense (like in Java or C#). However, you can achieve similar behavior by using default parameters 



## Encapsulation ##

Encapsulation in JavaScript is the concept of bundling data (variables) and methods (functions) that operate on the data into a single unit, typically a class. It also involves restricting direct access to some of the object's components, which is a means of preventing accidental interference and misuse of the data.

Using ES6 classes 

```javascript repl+ 
class Car {
    // Private field
    #model;

    constructor(model) {
        this.#model = model;
    }

    // Public method to get the model
    getModel() {
        return this.#model;
    }

    // Public method to set the model
    setModel(model) {
        this.#model = model;
    }

    // Private method
    #logModel() {
        console.log(`The model of the car is ${this.#model}`);
    }

    // Public method to access the private method
    showModel() {
        this.#logModel();
    }
}

const car = new Car('BMW');
console.log(car.getModel()); // Output: BMW
car.setModel('Audi');
console.log(car.getModel()); // Output: Audi
car.showModel(); // Output: The model of the car is Audi
```

The #model field and #logModel method are private and cannot be accessed directly from outside the class.
The getModel, setModel, and showModel methods are public and provide controlled access to the private field and method.

But how is underline ?

use closures based encapsulation !

A privileged method is a method which has access to the private data inside the containing function’s scope (also known as the lexical environment).

```javascript repl+ 
function createCar(model) {
    // Private variable
    let _model = model;

    return {
        // Public method to get the model
        getModel() {
            return _model;
        },

        // Public method to set the model
        setModel(newModel) {
            _model = newModel;
        },

        // Public method to show the model
        showModel() {
            console.log(`The model of the car is ${_model}`);
        }
    };
}

const car = createCar('BMW');
console.log(car.getModel()); // Output: BMW
car.setModel('Audi');
console.log(car.getModel()); // Output: Audi
car.showModel(); // Output: The model of the car is Audi
```

Ref: https://medium.com/javascript-scene/encapsulation-in-javascript-26be60e325b4