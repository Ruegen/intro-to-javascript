# Intro to JavaScript Session 07

Topics.
- [reference vs by value](#by-reference-vs-by-value)
- [Bookshelf front end](#front-end-javascript-bookshelf-app)

## By reference vs by value
```
var myNumber = 5; //stored value

function square(num) { // copied value
  num *= num
  console.log('func',num)
}

console.log('1st', myNumber)
square(myNumber)
console.log('2nd', myNumber)


var myArray = [1,2,3,4] //stored by reference

function addTwo(arr) { //copied as reference
  for(let i = 0; i < arr.length; i++) {
    arr[i] += 2
  }
  console.log('arr func', arr)
}

console.log('arr 1st', myArray)
addTwo(myArray)
console.log('arr 2nd', myArray)

/* By value for all Primitive types */
//undefined, null, number, string and boolean (also Symbol ES6)


/* By reference */
// objects, arrays



var obj = {
  firstName: 'Bob',
  lastName: 'Smith',
  sports: ['tennis', 'soccer', 'golf']
}

var newObj = Object.assign({}, obj) // copied object (actually we created a new object with same properties)

console.log(newObj.sports)
obj.firstName = "Sally"
obj.sports.push('swimming')
console.log(newObj) //oh no, it doesn't copy - it references
```

## Front-end JavaScript Bookshelf app
```
var form = document.getElementById('addBook')
var books = document.getElementById('books')
var counter = 0

fetch('/books/all')
  .then(res =>  res.json())
  .then(books => {

    books.forEach(book => {
      addBook(book.title)
    })

  })
  .catch(err => console.log(err))



form.addEventListener('submit', submitBook)

function submitBook(event) {
  event.preventDefault()
  var bookName = event.target.bookName.value
  if(bookName !== '') {
    addBook(bookName)
    form.reset()
  } else {
    alert('Yo, please add a book')
  }
}



function addBook(bookName) {
  var book = document.createElement('li')
  var button = document.createElement('button')
  var input = document.createElement('input')


  //add ID attribute to element
  book.id = counter
  counter++

  //create li children
  button.addEventListener('click', function(event){
    removeBook(book.id)
  })
  button.innerText = 'X'
  input.value = bookName

  //append to li
  book.appendChild(input)
  book.appendChild(button)


  books.appendChild(book)
}

function removeBook(id) {
  var book = document.getElementById(id)
  books.removeChild(book)
}
```
