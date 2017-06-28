# Intro to JavaScript Session 01

Topics.
- [Data Types (Not all types)](#data-types)
- Variables
- Syntax
- Keywords
- Values
- Functions

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

{
  firstName: "John",
  lastName: "Appleseed",
  age: 34
}

```  

## Variables
```
//Declare variables
var fruit, animal, name;

//Set Variables
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
