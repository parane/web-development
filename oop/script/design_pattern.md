# Design pattern #

We ll disucss some design pattern which are used in javascript.


## Singleton ##

The Singleton pattern restricts the instantiation of a class to a single instance and provides a global point of access to it.

```javascript
class Singleton {
    constructor() {
        if (Singleton.instance) {
            return Singleton.instance;
        }
        Singleton.instance = this;
    }
}
```

## Factory Pattern ##
The Factory pattern provides a way to create objects without specifying the exact class of object that will be created.

```javascript
class CarFactory {
    createCar(model) {
        return new Car(model);
    }
}
```

## Observer Pattern ##

The Observer pattern defines a one-to-many dependency between objects so that when one object changes state, all its dependents are notified and updated automatically.

```javascript
class Subject {
    constructor() {
        this.observers = [];
    }

    addObserver(observer) {
        this.observers.push(observer);
    }

    notifyObservers(message) {
        this.observers.forEach(observer => observer.update(message));
    }
}
```

## Strategy Pattern ##
The Strategy pattern defines a family of algorithms, encapsulates each one, and makes them interchangeable.

```javascript
class Context {
    constructor(strategy) {
        this.strategy = strategy;
    }

    executeStrategy(a, b) {
        return this.strategy.doOperation(a, b);
    }
}
```