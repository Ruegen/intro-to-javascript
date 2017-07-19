# Intro to JavaScript Session 04

Topics.
- [Template literals](#template-literals)
- [Deconstructing](#deconstructing)
- [Multi-line comments](#multi-line-comments)

## Template literals
```
const name = "Ruegen"

const hello = `Hello, my name is ${name}`

const multi = `

multiline string


as you can see
`

console.log(hello, multi)

const math = `Hello, I can do math ${4 + 4}`

console.log(math)
```

## Deconstructing
```
const PI = 3.1459265


const person = {
  firstName: 'Bob',
  lastName: 'Smith',
  age: 4,
  hobbies: ['knitting', 'stamp collecting']
}

const {firstName, lastName, hobbies} = person

// console.log(hobbies)

hobbies.forEach(hobby => {
  console.log(hobby)
})

function printName({firstName:name, lastName}) {
  return name
}

printName(person)

const numbers = [1 /*index 0*/, 2 /*index 1*/, 3 /*index 2*/]
const sports = ['tennis', 'soccer', 'golf']

const [x, y, z] = numbers
console.log(x, y, z)

const [,, apple] = sports
console.log(apple)

const tennis = sports[0]
const soccer = sports[1]
const golf = sports[2]
```

## Multi-line comments
```
/*
multiline comment

A very long comment

Once upon a time....

*/

//useful in certain areas
//NOTE: Don't do this as it's considered ugly and problematic (this is example only)
const numbers = [1 /*index 0*/, 2 /*index 1*/, 3 /*index 2*/]

```
