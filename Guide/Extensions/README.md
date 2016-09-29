#Extensions
Extensions add new functionality to an existing class, structure, enumeration, or protocol type.  
Extensions can add new functionality to a type, but they cannot override existing functionality.  

##Computed Properties
```
extension Double {
    var km: Double { return self * 1_000.0 }
}
```
call:
```
let oneInch = 25.4.km
print("One inch is \(oneInch) kilometers")
```
Extensions can add new computed properties, but they cannot add stored properties, or add property observers to existing properties.


##Initializers
Can create new initializers but can not override existing initializers


##Methods
static method must use mutating in extension
```
extension Int {
    mutating func square() {
        self = self * self
    }
}
var some = Int(3)
some.square()
print (some)
```




