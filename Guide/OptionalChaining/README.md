#Optional Chaining
##Optional Chaining as an Alternative to Forced Unwrapping
```
class Person {
    var residence: Residence?
}
 
class Residence {
    var numberOfRooms = 1
}

let john = Person()
let roomCount = john.residence!.numberOfRooms //runtime error
```
##Defining Model Classes for Optional Chaining
tbc
