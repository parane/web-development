## [[Prototype]] ##

Objects in JavaScript have an internal property, denoted in the specification as [[Prototype]], which is simply a reference to another object. 
Almost all objects are given a non-null value for this property, at the time of their creation.

The property [[Prototype]] is internal and hidden, but there are many ways to set it.

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


Refer: https://javascript.info/native-prototypes
