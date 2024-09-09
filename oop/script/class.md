# Class #

![Alt Text](asset/Student.png)

Create a class using function 

```javascript repl+
const Student = function(name) {
    this.name = name;
    console.log(this.name);
}
const alice = new Student('Alice'); //Alice
Student('Bob'); //Bob

```
what is the different ?

```javascript repl+
const Student2 = function(name) {
    this.name = name;
    console.log(new.target);
}
const alice1 = new Student2('Alice'); // [Function: Student]
Student2('Bob'); //undefine

```

new.target is a special meta-property in JavaScript that is used within a constructor function or class constructor to determine whether the function or class was called using the new operator.

Now lets avoid function invocation , we change the function to class (through constructor)

```javascript repl+

function Student3(name) {
    if (!new.target) {
        throw new Error("Must use 'new' with Student !! , not as function idiot !!");
    }
    this.name = name;
    console.log(this.name);
}

const alice = new Student3('Alice'); // Output: Alice
//const bob = Student3('Bob'); // Throws Error: Must use 'new' with Student
```

To explict mention, we may use class declaration like this in ES6


```javascript repl+ 
class Student4{
    constructor(name){
        this.name = name;
        console.log(this.name);
    }
}
const alice2 = new Student4('Alice'); // Output: Alice

//wait a minute, what is the typeOf Student class  

console.log(typeof(Student4));  //function
```
But does that mean JavaScript actually has classes? Plain and simple:
NO.
class is just syntax sugar for function !!!

![Alt Text](asset/class.jpg)


# Class members  #

The traditional metaphor for “class”- and “instance”-based thinking
comes from building construction.

A class is a blueprint. To actually get an object we can interact with,
we must build (aka instantiate) something from the class. The end
result of such “construction” is an object, typically called an instance,
which we can directly call methods on and access any public data
properties from, as necessary.
This object is a copy of all the characteristics described by the class.

class (Car) members are feilds (model) and methods(drive) that are shared by all instances of a class.
```javascript repl+
//access color property using get /set 
class Car {
    constructor(model) {
        this.model = model;
    }

    get drive(){
        console.log('Drive');
    }
}

```

### Properties : getter and setter ###

Properties(color) are special kinds of fields that have getter and setter methods. They allow controlled access to the class fields.

lets see properties by getter setter method 

```javascript repl+
//access color property using get /set 
class Car {
    constructor(model) {
        this.model = model;
    }

    get color(){
        return 'black';
    }
}
const car1 = new Car('BMW');
console.log(car1.model); // Output: BMW
console.log(car1.color()); // Output: black
console.log(car1.color); // Output: black
car1.color = 'red'; // Error: Cannot set property color of #<Car> which has only a getter
// we may setter to set the value !
```

### static ###