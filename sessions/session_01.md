# Intro to JavaScript Session 01

Topics.
- [Data Types (Not all types)](#data-types)
- [Variables](#variables)
- [Syntax & keywords](#syntax)
- [Concatenation & type coercion](#concatenation)
- [Math](#math)
- [Functions](#functions)
- [objects & arrays](#objects-&-arrays)

## Data Types
```
//Strings, single or double quotes
"Alexander"
'I went for a walk'

//Numbers
1
502
10000
45e5
1.45
0.05

//Undefined
undefined

//Not A Number
NaN

//Arrays
[1,2,3]
["Bob", "Sally", "Fred"]

//Multidimensional Arrays
[[1,2,3], [9,10,11], [300,301,302]]

//Mixed data type arrays
[5, "Alex", function(){}, {}, []]

//Objects, keys with values
{}

{ key : "value"}

var person = {
  firstName: "John",
  lastName: "Appleseed",
  age: 34
}

```  

## Variables
```
//Declare variables
var fruit, animal, name;

//Set Variables (Assignment)
fruit = "apple"
animal = "dog"
name = "Alexander"

//Do both in one go
var catName = 'Felix'

//JavaScript variable style convention
// use CamelCase
var firstName = "John"

// don't use snake case!
var first_name = "John"

// don't start with an invalid symbol like a number
var 1firstName = "Samantha" // error!
```

## Syntax
```
// Comments, this is a comment in JavaScript

// reserved keywords, you can't use these to name functions or variables
function
var
this
return
```

## Concatenation
```
// Joining strings together with concatenation
var firstName = "John"
var lastName = "Smith"

var fullName = firstName + " " + lastName // => 'John Smith'

var speech = "I " + firstName + ", likes Javascript" // => 'I John, likes JavaScript'

// Type coercion, turns a string into a number
var result = 1 - '1' // 0

result = 1 - `1cat' // returns NaN (Not a number!)

```

#Math
```
//add, multiply, divide, subtract
var result = 1 + 1 // result is 2

result = 2 * 10 //result is now 20

result = 5 / 2 //result is now 2.5

result = 5 - 1 //result is now 4

//addition assignment operator
var total = 0
total = total + 1 //total is now 1

//or using the addition assignment operator
total += 1 //total is now 2
total += 2 //total is now 4

//other assignment operators
total -= 1 //total is now 3
total *= 3 //total is now 9
total /= 2 //total is now 4.5
```

#functions
// create a function
function sayHello() {
  console.log("Hello World")
}

//Call/Invoke a function
sayHello()

//Don't invoke a function
sayHello //won't do anything

//Have a function have it's own variable/scope
function sayHello() {
  var comment = "Hello World"
  console.log(comment)
}

//Have a function use a variable outside of it's scope
var hello = "Hello World"

function sayhello() {
  console.log(hello) //this will look for hello outside of its scope
}

//Have a function give you back or 'return' you a value
function sayHello() {
  return "Hello World"
}

console.log(sayHello()) //will log out "Hello world"

//vs not invoking the function
console.log(sayHello) //will log out the 'function' itself and not the return value

//Using a parameter
function square(num) {
  return num * num
}

console.log(square(4)) //will log out the return value 16
```

## Objects & Arrays
//get a value from an array by it's index

var arr = [1,2,3]
arr[0] //returns value 1
arr[2] //returns value 3

//set a value to an index
arr[0] = 5
onsole.log(arr) //returns [5,2,3]

## get a value from an object using dot notation
var person = {
  firstName: "Samantha",
  lastName: "Smith"
}

console.log(person.firstName) // logs out "Samantha"

## set a value
person.firstName = "John"
console.log(person) // logs out '{ firstName: "John", lastName: 'Smith'}'

## using square bracket for the key
console.log(person['firstName']) //logs out "John"

var key = "lastName"
console.log(person[key]) //logs out "Smith"
```
