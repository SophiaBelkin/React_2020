## ES6 & React Cheatsheet


### const, let, var
Throw away the var key word. 
Prefer to use const over let
Use let only you need to assign variable

### Objects
Cleaner and simpler syntax to define a method in an object

```
const person = {
  name: "Ken",
  walk() {}
  talk() {}
};

// option 1
person.talk();

// option 2
const targetMember = 'name';
person[targetMember.value] = 'John';
```

### This keyword
```
const person = {
  name: "Ken",
  walk() {
    console.log(this);                                                                                                                                                                                                           
  }
};

person.walk() // person

const person1 = person.walk();
walk() // undefined or window

const person2 = person.walk().bind(person);
walk() //person
```


### Object Destructuring
```
const address = {
  street: '123',
  city: '',
  country: ''
}

const {street, city, country} = address;
console.log(street) // 123

const {street:st} = address;
console.log(st) //123
```

### Clone array and object
```
const arr = [1,2,3];
const clone = [...arr];

const address = {
  street: '123',
  city: '',
  country: ''
}

const clone = {...address};
```

### Other Object functions
```
Object.entires();
Object.keys();
Object.values();
```

### Classes 
The updates to classes in ES6 do not introduce a new OO inheritance model. The classes are “syntactical sugar” to support prototype inheritance. 

```
class Person {
  constructor(name) {
    this.name = name;
  }
  
  walk() {
    console.log("walk");
  }
}

class Teacher extends Person {
  constructor(name, degree) {
    super(name)
    this.degree = degree;
  ]
  
  teach() {
    console.log("teach");
  }
}

const teacher = new Teacher("Joe", "Msc");
```


### Modules
Objects defined in a module are private by defaule. The class above is not visiable to other files or modules.
To make the class accessable by other classes, export the class to make it public and import it when we need it 

```
import { Person } from './person' // No extention needed
export class Teacher extends Person {
    constructor(name, degree) {
      super(name)
      this.degree = degree;
    ]

    teach() {
      console.log("teach");
    }
}
```

```
import { Teacher } from './teacher'

const teacher = new Teacher("Joe", "Msc");
teacher.teach();
teacher.walk();
```

### Default export 
```
export default class Teacher extends Person {}

import Teacher from './teacher' // {} for named exports
```


### Promise, Async, Await 
The Async function allows us to define an asynchronous function and return a Promise.

```function resolveAfter2Seconds() {
  return new Promise(resolve => {
    setTimeout(() => {
      resolve('resolved');
    }, 2000);
  });
}

async function asyncCall() {
  console.log('calling');
  const result = await resolveAfter2Seconds();
  console.log(result);
}

asyncCall();
```
