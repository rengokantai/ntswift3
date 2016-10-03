#Control Flow
##Conditional Statements
###Switch
```
let anotherCharacter: Character = "a"
switch anotherCharacter {
case "a": // Invalid, the case has an empty body
case "A":
    print("The letter A")
default:
    print("Not the letter A")
}
```
combined case
```
let anotherCharacter: Character = "a"
switch anotherCharacter {
case "a", "A":          // not case "a",case"A"
    print("The letter A")
default:
    print("Not the letter A")
}
```

###Value Bindings
```
let anotherPoint = (2, 0)
switch anotherPoint {
case (let x, 0):
    print("on the x-axis with an x value of \(x)")
case (0, let y):
    print("on the y-axis with a y value of \(y)")
case let (x, y):                //let(x,y) legal.
    print("somewhere else at (\(x), \(y))")         
}
```



###Where
```
let yetAnotherPoint = (1, -1)
switch yetAnotherPoint {
case let (x, y) where x == y:
    print("(\(x), \(y)) is on the line x == y")
case let (x, y) where x == -y:
    print("(\(x), \(y)) is on the line x == -y")
}
```




##Control Transfer Statements
###Continue



###Labeled Statements



##Early Exit  (guard keyword)

You use a guard statement to require that a condition must be true in order for the code after the guard statement to be executed.
```
func greet(person: [String: String]) {
    guard let name = person["name"] else {
        return
    }
    
    print("Hello \(name)!")
    
    guard let location = person["location"] else {
        print("I hope the weather is nice near you.")
        return
    }
    
    print("I hope the weather is nice in \(location).")
}
 
greet(person: ["name": "John"])
```


##Checking API Availability
```
if #available(iOS 10, macOS 10.12, *) {
    // Use iOS 10 APIs on iOS, and use macOS 10.12 APIs on macOS
} else {
    // Fall back to earlier iOS and macOS APIs
}
```
