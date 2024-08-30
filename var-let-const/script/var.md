**var** has function scope ! 

```javascript repl+
function f(){
    var z=10;
}
console.log(z); //z is not defined

```

**hoisted** to the top of their respective scope (global or function) at runtime !

```javascript repl+
for(var i=0;i<10;i++){
console.log(i);
}
console.log(i); //10 , variable i able to access bcoz it hoisted to top of for loop

```

if y is not declare , it ll be move to global scope (hoisting)

note: function expression (IIFE). It is a way to define and execute a function at the same time.

```javascript repl+
(function(){
y=10
console.log(y);
})()
console.log(y); //10

```

### ES6 introuduced let and const !  ###

**let** has block scope ! Also subjected to hoisting !

```javascript repl+
for(let k=0;k<10;k++){
console.log(k);
}
console.log(k);//k is not define 

```

Let also subject to hoisting , but instead of undefine , will be temporal dead zone (TDZ) meaning that any attempt to access them 
will result in reference error !

```javascript repl+
let bar = 41;
console.log(bar);
if(true){
console.log(bar); // not 41 , Cannot access 'bar' before initialization !
let bar=42; //bar will be hoisted to block level, but cannot access 
console.log(bar); //42
}
console.log(bar); //41


```

**const** same as let , but cannot reassign . try to reduce mutable state  

```javascript repl+
const con = 1;
con = 2;  //cannot Assignment to constant variable

```

**const** is trying to avoid mutability , but in case of object can be change !

```javascript repl+

const conObj = {a:1};
conObj.a = 2;  
console.log(conObj.a); //2

```

How can i makesure immutability to Object ?

We can use Object.freeze()

```javascript repl+

const conObj2 = {a:1};
Object.freeze(conObj2);
conObj2.a = 2;  
console.log(conObj2.a) //1
```


pls use const -> let -> var

![Alt Text](Asset/bottom_line.jpg)

..............................................


**Exercise 1**


```javascript repl+
var a = 10;
(function(){
    console.log(a);  
    var  a = 20;
})();

```
Result : undefine because var is hoisted to respective scope (function level) 


**Exercise 2**


```javascript repl+
var z = 10;
(function(){
    console.log(z);  
      z = 20;
})();

```
Result : 10 because a is hoisted to global scope.


```javascript repl+

const a;
console.log(a);
a=10;
```