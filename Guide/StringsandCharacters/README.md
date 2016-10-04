#Strings and Characters
##Working with Characters
```
for character in "abc".characters {
    print(character)
}
```

##Accessing and Modifying a String
###String Indices
```
let greeting = "Guten Tag!"
greeting[greeting.startIndex]
// G
greeting[greeting.index(before: greeting.endIndex)]
// !
greeting[greeting.index(after: greeting.startIndex)]
// u
let index = greeting.index(greeting.startIndex, offsetBy: 7)
greeting[index]
// a
greeting[greeting.endIndex] // error
```
Use the indices property of the characters property to access all of the indices of individual characters in a string.
```
for index in greeting.characters.indices {
    print("\(greeting[index]) ", terminator: "")
}
```


###Inserting and Removing
```
var welcome = "hello"
welcome.insert("!", at: welcome.endIndex)
// welcome now equals "hello!"
 
welcome.insert(contentsOf:" there".characters, at: welcome.index(before: welcome.endIndex))
// welcome now equals "hello there!"

welcome.remove(at: welcome.index(before: welcome.endIndex))
// welcome now equals "hello there"
 
let range = welcome.index(welcome.endIndex, offsetBy: -6)..<welcome.endIndex
welcome.removeSubrange(range)
// welcome now equals "hello"
```
##Comparing Strings
tbc
