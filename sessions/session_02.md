# Intro to JavaScript Session 02

Topics.
- [Booleans](#booleans)
- [Operators](#operators)
- [if statements](#if-statements)
- [switch statements](#switch-statements)
- [for loop](#for-loop)
- [for in loop](#for-of-loop)
- [for of loop](#for-of-loop)
- [while loop](#while-loop)
- [do while loop](#do-while-loop)

## Booleans
```
var isReady = true
isReady = false
```

## Operators
```
== //equal value
=== //equal value and data type

!= //not equal to value
!== //not equal to value and data type

! //not

&& // and
|| // or

> // greater than
< //less than

>= //greater than or equal to
<= //greater than or equal to
```

## If statements
```
if(true) {
  console.log('this will be logged')
}

if(5 > 2) {
  console.log('this will be logged because it is true')
}

var pass = 'password123'

if(pass === 'password123') {
  console.log('true and you really need to make better passwords!!')
} else {
  console.log('Your password is not matched - thankfully')
}

var myArray = [1, 2, 3, 4, 5]

if(myArray.length > 6) {
  console.log('the array has greater than five values')
} else if (myArray.length <= 5) {
  console.log('the array has 5 or less values')
} else {
  console.log('neither of the two conditions')
}
```

## Switch statements
```
var food = 'apple'

switch(food) {
    case 'banana':
        console.log('you got a banana!')
        break;
    case 'Apple':
        console.log('you got an Apple!')
        break;
    default:
        console.log('you got an ' + food)
}
```

## For loop
```
var counter = 0

//counts up from 0 to 10
for(var i = 0; i <= 10; i++) {
  counter++
  console.log(counter)
}


var weekdays = ['Sunday', 'Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']

// using the new let instead of var will keep the i variable within the loop
for(let i = 0; i < weekdays.length; i++) {
  console.log(weekdays[i])
}
```

## For in loop
NOTE: caution when using it as it can pull hidden keys from other areas of your object.
```
var person = {
  firstName: 'John',
  lastName: 'Appleseed',
  age: 34
}


for(key in person) {
  console.log(key, person[key])
  // here we log out the key first, then we log the value
}
```

## For of loop
```
var sports = ['swimming', 'tennis', 'soccer']
for(value of sports) {
  console.log(value)
}
```

## While loop
```
var counter = 0
while(counter < 100) {
   counter++
   console.log(counter)
}
```

## Do loop
```
var counter = 0
do {
   counter++
   console.log(counter)
} while(counter < 100)
```
