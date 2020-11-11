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
