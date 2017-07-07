# Intro to JavaScript Session 04

Topics.
- [array object methods](#array-object-methods)
- [exporting](#exporting-an-object)
- [importing](#importing-an-object)
- [files](#files)
- [http](#http)


## Array object methods
```
var workDays = ['Monday', 'Tuesday', 'Wednesday', 'Thursday', 'Friday']

workDays.forEach(function(day, index) {
  console.log(day, index)
  workDays[index] = day + '!'
})

console.log(workDays) // not good - mutated!

// map
 var newWorkDays = workDays.map(function(day, index) {
   console.log(day, index)
   return day + '!'
 })

 console.log(workDays) //not mutated
 console.log('map',newWorkDays) // new array

 // filter
 var filteredDays = workDays.filter(function(day, index) {
   //we don't like mondays
   return day !== 'Monday'
 })

 console.log('filter',filteredDays)


 // reduce
 const prices = [1.45, 24, 300, 2.99, 5, 2.01, 7.60]

 const sum = prices.reduce(function(total, price) {
   return total + price
 }, 0)

console.log('reduce',sum)
//repeat all these using the arrow functions
```

## Exporting an object
```
function Person(firstName, lastName) {
	this.firstName: firstName,
	this.lastName: lastName,
	this.fullName: function() {
		return this.firstName + ' ' + this.lastName
	}
}

//export person constructor to make more in other areas of our app
module.exports = Person
```

## Importing an object
```
// import your own JS from current directory
const Person = require('./person.js') //NOTE: you aren't required to use the .js

const jim = new Person("Jim", "Smith")
console.log(jim.fullName())

//import a different package
const fs = require('fs') //notice it isn't in a local directory so no './'
```

## files
```
var fs = require('fs')
var {promisify} = require('util')

// exchange callbacks for promises using promisify
const readFileAsync = promisify(fs.readFile)
const writeFileAsync = promisify(fs.writeFile)

var data = readFileAsync('./lorem.txt', 'utf8' )
//returns a promise

	data
	.then(function(data){
	   //writeFileAsync returns a promise, so we can return that
	   return writeFileAsync('./poem.txt', data)
	})
	.then(function(){
		//we stop returning promises and end here
		console.log('saved data to file!')
	})
	.catch(function(err) {
		//all promises will move to catch if there is an error and end here
		console.log(err)
	})
```

## http
```
const http = require('http')
const fs = require('fs')
const moment = require('moment')
const {promisify} = require('util')
const readFileAsync = promisify(fs.readFile)

const server = http.createServer(function(req, res){
	const uri = req.url
	if( uri === '/') {
		res.write('Hello World')
		res.end()
	} else if (uri === '/time') {
		const date = moment()
		res.write(date.day().toString())
		res.end()
	} else if(uri === '/about') {
		readFileAsync('./about.html')
		.then((data) => {
			res.writeHead(200,{ 'content-type':'application/json'} )
			res.write(data)
			res.end()
		})
	} else {
		res.write('not found')
		res.end()
	}
})

server.listen(3000, function(){
	console.log('server is listening')
})
```
