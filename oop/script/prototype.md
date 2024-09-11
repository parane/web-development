## [[Prototype]] ##

In JavaScript, every object has an internal property called [[Prototype]], which is a reference to another object. This reference allows one object to inherit properties and methods from another object. Although [[Prototype]] is an internal and hidden property, it can be set using the __proto__ property.

One of them is to use the special name __proto__, like this:

```javascript
let animal = {
  eats: true
};
let rabbit = {
  jumps: true
};

rabbit.__proto__ = animal; // sets rabbit.[[Prototype]] = animal
```

Here, we have two objects: animal and rabbit. The animal object has a property eats set to true, and the rabbit object has a property jumps set to true. By setting rabbit.__proto__ = animal, we are linking the rabbit object to the animal object through its [[Prototype]]. This means that rabbit can now access the properties of animal, such as eats.


Refer: https://javascript.info/native-prototypes

t. This is a powerful feature in JavaScript that enables inheritance and code reuse.
