# Intro to JavaScript Session 03

Topics.
- [Classes](#classes)
- [String Methods](#string-methods)
- [Number Methods](#number-methods)
- [Array Methods](#array-methods)
- [typeof keyword](#typeof)
- [setTimeout](#setTimeout)
- [setInterval](#setInterval)
- [Closures](#closures)
- [Callbacks](#callbacks)

## Classes
```
class Animal {
  // notice we use 'constructor' to setup a class
  constructor(name, age) {
    this.name = name
    this.age = age
  }

  getName() {
    console.log(this.name)
    return this.name
  }
}

class Dog extends Animal {

  constructor(name, age) {
    //if we want to override the parent constructor
    super(name, age) //swap these to see the difference
  }


  getName() {
    //if we want to use the get name from the parent
    super.getName()
  }
}

const fluffy = new Dog('fluffy', 3)
fluffy.getName()
```

## String methods
```

var name = 'John'
//remember strings are immutable, they cannot change

console.log(name.toUpperCase())
console.log(name.toLowerCase())

console.log(name.charAt(0)) //character at position
console.log(name.search('o')) // returns position 1
console.log(name.charAt(1)) // returns 0

console.log(name.repeat(10))

var surname = ' Smith '
console.log(surname.trim()) //removes white space and returns new string

var fullName = name.concat(surname) //joins name
console.log(fullName)

var quote = 'Do not take life too seriously. You will never get out of it alive. - Elbert Hubbard'

console.log(quote.includes('alive'))
console.log(quote.includes('elephant'))

var modQuote = quote.replace('Elbert Hubbard', 'Ruegen')
console.log('modded quote', modQuote) //replaced with Ruegen

//adding to the prototype of an object
String.prototype.capitalize = function() {
    return this.charAt(0).toUpperCase() + this.slice(1).toLowerCase();
}

var crazyName = 'RuEGen'
console.log(crazyName.capitalize())

//using a function
function capitalize(word) {
   return word.charAt(0).toUpperCase() + word.slice(1).toLowerCase();
}

var fixedName = capitalize(crazyName)
console.log('fixed name', fixedName)
```


## Number methods

```
var z = 2 / 0
console.log(z) //returns Infinity (a type of number)

var y = -2 / 0
console.log(y) //returns -Infinity (the opposite direction)

var result = 5 * 5

var resultAsString = result.toString()

console.log(typeof resultAsString) //typeof is a keyword, returns 'string'

//so if typeof variable is equal to string
if(typeof resultAsString === 'string') {
  console.log('strResult is a string')
}

var val = 3.454
var price = val.toFixed(2)
console.log(price)

console.log(parseFloat('1.456')) //converts to Number (as float)
console.log(parseInt(1.456)) //converts to Number as Int (even if string)
```

## Array methods
```
var kitchenItems = ['cookbook', 'spoon', 'bowl', 'toaster']

kitchenItems.push('blender')
console.log('1', kitchenItems)

kitchenItems.pop() //remove last from end
console.log('2', kitchenItems)

var laundryItems = ['laundry powder', 'mop']
var houseItems = kitchenItems.concat(laundryItems)
console.log('3', houseItems)

var onlyKitchen = houseItems.slice(4) //from length 4 (not index)
console.log('4', onlyKitchen)

var items = houseItems.toString()
console.log('5', items)

var itemsArray = items.split(',') //turn back into array using the comma in the string as a 'splitting' point
console.log('6', itemsArray)
```

## typeof keyword
```
typeof 'Hello World' // => 'string'

typeof 150 // => 'number'

typeof [1,2,3] // => 'object' //arrays are objects in JS

typeof {} // => 'object'
```

## setTimeout
```
console.log('here is where I started')

setTimeout(function() {
  console.log('ran after 10 seconds')
  }, 10000)

console.log('here is where I finished')
```


## setInterval
```
var count = 0


function doSomething() {
  var time = new Date()
  console.log(time)
  count++
  if(count > 10) {
    console.log('Stop!')
    clearInterval(timer)
  }
}

var timer = setInterval(doSomething, 1000)
```

## Closures
```
//first look at how we create an object
var person = {
  firstName: 'John',
  lastName: 'Smith',
  fullNameThis: function() {
    return this.firstName + ' ' + this.lastName
  },
  fullNamePerson: function() {
    return person.firstName + ' ' + person.lastName //instead of this
  }
}

console.log(person.fullNameThis())
console.log(person.fullNamePerson())

function Animal(name, age) {
  var animalName = name
  var myAge = age
}

var monkey = new Animal('monkey', 4)
console.log(monkey.myAge) //huh? What happened to the variable?
//the variable is scopped to the function but it isn't ON the function, it is not part of the object/function

//now look at a closure
function Person (name, surname) {
  var firstName = name //garbage collected
  var lastName = surname //garbage collected
  this.fullName = function() {
    // this will borrow the variables and store them for later use
    return firstName + ' ' + lastName
  }
  this.setFirstName = function(name) {
    //you can also replace the variable value
    firstName = name
  },
  this.mood = function(mood) {

    //don't do this
    function addMood() {
      //the this belongs to the function not the obect, how do we fix?
      return this.firstName + mood
    }
    return addMood(mood)
  }
}

var john = new Person('John', 'Smith')
console.log(john.fullName())

console.log(john.firstName) //it doesn't exist on the object, it wasn't added and the variable got garbage collected - however the function FullName still holds it for use.

john.setFirstName('Alex')
console.log(john.fullName())

console.log(john.mood('Happy')) //what wait this returns undefined!?
```

## Callbacks
Here we generate some time using setTimeout, this is to pretend something is not going to run immediately and take some time.
```
function square(callback, num) {
  var result = num * num
  console.log('....calculating result...')
  setTimeout(function() {
    callback(result)
  }, 4000)
}

square(function(res) {
  console.log('the squared result is: ' + res)
}, 10)

square(function(res) {
  console.log('Wow I reused this square but with a different callback and the result is: ' + res)
}, 10)
```
