# ES6 Class Notes:
## Template Literal
```javascript
console.log('Hello! I'm a String
continues on this line');
```
```Javascript
console.log("string text 1\n"
+ "string tex2");

const name = "Candace" 
const day = "Wednesday"
const instructor = {     
    //Instructor is the Constant
    name: "Chris",
    //Name is an Object
    lesson: "ES6"
    //Lesson is an Object,<br>
    greet: function() {
        return 'Hello ${this.name} whatever lesson is ${this.lesson}'
    }   
}
```
```Javascript
console.log("Hello" + name + "I hope you have a great day on" + day);
//Says...Hello Candace I hope you have a great day on Wednesday
```
```Javascript
console.log('Hello ${name} I hope ${day} goes well!')
//ES6 way to say...Hello Candace I hope Wednesday goes well!
```
```Javascript
console.log('Hello ${instructor.name} whatever lesson is ${instructor.lesson}'
//Says...Hello Chris whatever lesson is ES6
```
```Javascript
console.log(instructor.greet())
// Is calling a function
```
```Javascript
function foo() {
    let x = true;
    if(x) {
        var usingVar = "im using var";
    }
    console.log(usingVar)
}
//this is an example of hoisting and would say...im using Var
```
```Javascript
function foo() {
    let x = true;
    if (x) {
        let usingVar = "im using let";
    }
    console.log(usingVar)
}
//it's out of scope so it will come back as undefined
```
```Javascript
//TypeError
const instructore = ["Jimmie", "Christ"]
instructors.push("Jack", "Jill");
//this will say...Jimmie, Christ, Jack, Jill
//while you should make practice of using camelcase, const also accepts uppercase

```Javascript
function hello(name) {
    name = name || 'Mystery Person';
    console.log("Hello" + name + " !")
}
hello("Bobby");
//will return...Hello Bobby!

hello();
//will return...Hello Mystery person!
```
```Javascript
//Adding default parameters to your arguments means:
function hello(day, name = "Mystery Person"){
    console.log(`Hello ${name} is it me youre looking for`)
}
//This will say Hello Mystery Person is it me youre looking for
//the term 'day' stands as undefined
```
```Javascript
const teacher = {
    name: "Jimmie",
    speak: function() {
        //bind a function to specific context
        let boundFunction = function() {
            console.log("later my name is " + this.name);
        }.bind(this);
        //you have to explicitly bind this to the function()
        }
    };
//boundFunction will always run in bound context
        setTimeout(boundFunction, 1000);
        ```
```Javascript
const teacher = {
    name: "Jimmie",
    speak() {
        let boundFunction = () => {
            console.log("later my name is " + this.name);
        };
        setTimeout(boundFunction, 1000);
    }
};
teacher.speak();
//Lexical Binding - binds to the scope where they are defined..not where they are used
//An example of the use of the Arrow function()
//Functions always create scope
```
```Javascript
let students = [   //defines the students variable
    {name: 'Hugo'},
    {name: 'Candace'},
    {name: 'Taylor'}
    {name: 'Dimitri'}
];
let names = students.map((value) => value.name);  
 //the arrow is the function, binds the function to the scope of students
 //student is the argument
 //name is the object
 //'Hugo' is a string
```
```Javascript
 //Same as:
 let names = students.map((student) => {
     return student.name
 })
console.log(names);
//will return the array of students names
```
```Javascript
Add functions:
function add() {
   
   console.log("arguments object:", arguments);
    //this calls the arguments object
    var numbers = Array.prototype.slice.call(arguments);
//'slice' turns the list of numbers into an array even though they're not inside of square brackets
//'call' calls to the slice function
```
```Javascript
    var sum = 0;
    numbers.forEach(function (number) {
        sum += number;
    });
    return sum;
    }

console.log(add(1,2,3,4,5,6,7,8));
//first iteration is: 0+1=1<br>
//next iteration is:  1+2=3<br>
//next iteration is: 3+3=6<br>
//next iteration is: 6+4=10<br>
//next iteration is: 10+5=15<br>
//next iteration is: 15+6=21<br>
//next iteration is: 21+7=28<br>
//next iteration is: 28+8=36<br>
//Voila!

let add = (...numbers) => {
    console.log("rest parameters", numbers);
    let sum = 0;
    numbers.forEach(function (number) {
        sum += number;
    });
    return sum;
}
console.log(add(1,2,3,4,5,6,7,8));
//Rest Parameter

let add = (...numbers) => numbers.reduce((sum, number) => sum += number, 0);
console.log(add(1,2,3,4,5,6,7,8));
//adds all of the numbers up without having to showcase each iteration
```
```Javascript
function addStuff(x,y, ...z){
    return (x+y) * z.length
    }
console.log(addStuff(1,2, "hello", "world", true, 99));
    //x=1
    //y=2
    //the length of z is all things left in the parenthesis...
    //i.e. 4 things ("hello", "world", true & 99)
    //so 1+2=3....3*4=12
}
//console.log(addStuff(1,2, "hello", "world", true, 99));  will return the number 12
```
```Javascript
//This is an example of a Spread Operator:
let random = ["Hello", "World", true, 99]
let newArray = [1,2, ...random, 3]
console.log(newArray);
//Is going to return [1,2,"Hello", "World", true, 99,3]
```
```Javascript
let spreadEx = (item) => {
    let spreadArray = {...item}
    console.log(spreadArray);
    return spreadArray
}
spreadEx("Hello World")
//will return: ["H","e","l","l","o"," ","W","o","r","l","d"]
```
```Javascript
let restEx = (...z) => {
    console.log(z)
    return z
}
restEx("hello", "world")
//this will return ["hello", "world"]
```
```Javascript
var students = ["Julian", "AJ", "Matt"];
var x = students[0];
var y = students[1];
var z = students[2];
console.log(x, y, z);
//will return Julian, AJ, Matt
```
```Javascript
//ES6 version of destructuring arrays:
let students =  ["Julian", "AJ", "Matt"];
let[x,y,z] = students
console.log(x, y, z);
//will return Julian, AJ, Matt
```
```Javascript
//ES6 version of destructuring arrays:
let students =  ["Julian", "AJ", "Matt"];
let[x, ,z] = students
console.log(x, y, z);
//will return "Julian" & "Matt"
```
```Javascript
let[x, ...rest] = students;
console.log(x, rest);
// will return Julian ["AJ", "Matt"]
```
```Javascript
//Destructuring functions:
let completedHomework = () => {
    return ["Julian", "AJ", "Matt"];
}
let [x,y,z] = completedHomework();
console.log(x,y,z);
//this will return julian AJ Matt
```
```Javascript
//Destructuring of objects:
let instructor = {
    name: "Jimmy",
    email: "no@no.com"
}
let { name: x, email: y} = instructor;
console.log(x);
//this will return: Jimmy
```
```Javascript
//Destruction of objects:
let car = {
    make: "Hyundai",
    model: "Elantra"
}
let { make: x, model: y} = car;
console.log(x,y);
//will return: Hyundai Elantra
```
```Javascript
//In-class exercise:
//make object
//make function with default parameter
//return both things
let car = {
    make: "Honda"
}
function something(make, year = 2001) {
    console.log(make, year);
}
something(car);
//will return: { make: 'Honda' } 2001
```
```Javascript
//In-class exercise cont.:
//make object
//make function with default parameter
//return both things
let car = {
    make: "Honda"
}
function something({make, year = 2001}) {
    console.log(make, year);
}
something(car);
//will return: Honda 2001
```
```Javascript
//Object oriented constructor function:
function Person (name, job) {
    this.name = name;
    this.job = job;
}
Person.prototype.getName = function getName() {
    return this.name;
}
var goodGuy = new Person ("Aang", "Avatar");
console.log(goodGuy.getName())
//will return: Aang
```
```Javascript
//Inheritance chain:
class Person {
    constructor (name, job) {
        this.name = name;
        this.job = job;
    }
    getName() {
        return this.name;
    }
    getJob() {
        return this.job;
    }
}
let goodGuy = new Person( 'Neo', 'the one');
console.log(goodGuy);
//will return: Person { name: 'Neo', job: 'the one' }
```
```Javascript
//Inheritance chain cont.:
class Person {
        constructor (name, job) {
            this.name = name;
            this.job = job;
        }
        getName() {
            return this.name;
        }
        getJob() {
            return this.job;
        }
    }
    ```
    ```Javascript
class SuperHero extends Person {
    constructor (name, heroName, superPower) {
        super(name);
        this.heroName = heroName;
        this.superPower = superPower;
    }
    secretIdentity() {
        return `${this.heroName} is ${this.name}!!`
    }
}
let batman = new SuperHero("Bruce Wayne", "Batman")
console.log(batman.secretIdentity()
//'super' lets you use the existing name property from 'Person'
//this will return: Batman is Bruce Wayne!!
```
```Javascript
let goodGuy = new Person('Jim Gordon');
console.log(goodGuy.name);
//this will return: Jim gordon
goodGuy.name = "James Gordon";
console.log(goodGuy.name);
//this will return: James Gordon
```
```Javascript
//Array function of map:
//let's us store key value pairs
//objects convert both keys and values to strings
let student = {name: "A-aron"};
let status = new Map();
status.set(student.name, "A-aron");
status.set("feeling", "churlish");
console.log(status.get(student.name));
console.log(status.get("feeling"));
//'feeling' is the key
//'churlish' is the value
//will return: A-aron churlish
```
```Javascript
//Encapsulation:
const Guy = (function() {
    const _name = new WeakMap();
class Guy {
    constructor(name) {
        this[_name] = name;
    }
    set name(name) {
        this[_name] = name;
    }
    get name() {
        return this[_name];
    }
}
return Guy;
}());

let guy = new Guy("Fieri");
console.log(guy.name);
//this returns: Fieri
```