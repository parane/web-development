# Literals & Destructuring #

In new version javascript introduce enhance literal 

- Improved Readability: Makes the code more readable and concise.
- Avoids Repetition: Reduces the need to repeatedly access properties or array elements.
- Nested Destructuring: Supports extracting values from nested objects and arrays.


# Literal #
notation of value in the code. eg String literal, integer , Object , array etc 

We ll consider main improvements in those literals : 

1. String literal improvement 
2. Object literal improvement 
3. Destructuring - Object/ Array improvement 

## Template (String) Literal ##

Template literals are string literals allowing embedded expressions. You can use multi-line strings and string interpolation features with them.
![template-literal.png](asset/template-literal.png)


```javascript repl+

const name = 'John';
const wish = 'Good morning'
console.log('Hello'+name+'!'+wish); //Hello John! Good morning
```

```javascript repl+
//using template literals
console.log(`Hello ${name}! ${wish}`); //Hello John! Good morning
```

### Nested Template Literals ###

```javascript repl+
//nested
const hours = 14;
const name = 'parane'
console.log(`Hello ${name} , Good ${hours<12 ? 'Morning': `${hours<20 ? 'Evening' :'Night'}`}`); //'Hello parane , Good Evening'

```

### Multi line Strings ###

Creating multi line string in past involved effort and resulted in lot of noise in code ! you may add line break in template literal. 

```javascript repl+
const name = 'parane'
const hours = 14;
//console.log('Hello ,
//Good Morning'); //Syntax errror : Unterminate string constant
console.log(`Hello ${name} ,
 Good ${hours<12 ? 'Morning': `${hours<20 ? 'Evening' :'Night'}`}`); //'Hello parane ,\n Good Evening' preserve indentation 


```


## Improved Object Literal ##

### Shorthand Assignment ###

```javascript repl+
//old way to create Object 
const createPerson = function(name,age, sport,sportFn){
    const person = {
        name:name,
        age:age,

    }
    person['play'+sport] = sportFn;
    return person;
}

const parane = createPerson('Parane',1,'Badminton' ,()=>{console.log('Play Badminton');});
parane.playBadminton();

//new shorthand way !
const createPerson2 = function(name,age, sport,sportFn){
    return person = {
        name,
        age,
        ['play'+sport] : sportFn
    }
}

const parane2 = createPerson('Parane',1,'Badminton' ,()=>{console.log('Play Badminton');});
parane2.playBadminton();

```

Basically we can removed the unnecessary local variable and kept all initialization to within the object literal 

Reduce couple of lines of code ! 

## Destructuring ##

![Alt Text](asset/destructure.gif)

Destructuring is an elegant way to extract data from 
1. array 
2. object. 

## Array Destructuring ##

```javascript repl+

const numbers = [1, 2, 3, 4, 5];
const [first, second, , fourth] = numbers;

console.log(first); //1

//need to extract 6th element , if no element , put some 0 default value
const [, , , ,,sixth=0] = numbers;
console.log(sixth); //0

```

## Object Destructuring ##

```javascript repl+

const user = {
    id: 1,
    name: 'John Doe',
    email: 'john.doe@example.com',
    address: {
        city: 'New York',
        zip: '10001'
    }
};

// Destructuring assignment
const { name, address: { city } } = user;

console.log(name);  // John Doe
console.log(city);  // New York

```

you can do destructure in function parameter


```javascript repl+

const user = {
    id: 1,
    name: 'John Doe',
    email: 'john.doe@example.com',
    address: {
        city: 'New York',
        zip: '10001'
    }
};

const stream = ['Parane','Alex','Sin'];

const print = function([first,second]){
    console.log(`Welcome first ${first} second ${second}`); //'Welcome first Parane second Alex'

}

const print2 = function({name,address:{ city}}){
    console.log(`Welcome first ${name} second ${city}`); //'Welcome first John Doe second New York'

}
print(stream);
print2(user);

```

Enhance Template literal and destructuring greatly reduce the noise in code !!!