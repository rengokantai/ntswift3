#Protocols
A protocol defines a blueprint of methods, properties, and other requirements that suit a particular task or piece of functionality.  
The protocol can then be adopted by a class, structure, or enumeration  


###Method Requirements
```
protocol RandomNumberGenerator {
    func random() -> Double
}
```
use this protocol:
```
class LinearCongruentialGenerator: RandomNumberGenerator {
    var lastRandom = 42.0
    let m = 139968.0
    let a = 3877.0
    let c = 29573.0
    func random() -> Double {
        lastRandom = ((lastRandom * a + c).truncatingRemainder(dividingBy:m))
        return lastRandom / m
    }
}
```
[truncatingRemainder API](https://developer.apple.com/reference/swift/floatingpoint/1847167-truncatingremainder)
```
let x = 8.625
print(x / 0.75)
// Prints "11.5"

let q = (x / 0.75).rounded(.towardZero)  //11.5 rounded=11.0
// q == 11.0
let r = x.truncatingRemainder(dividingBy: 0.75)   //8.625%0.75=0.375
// r == 0.375
```




##Initializer Requirements
###Class Implementations of Protocol Initializer Requirements
You can implement a protocol initializer requirement on a conforming class as either a designated initializer or a convenience initializer.
In both cases, you must mark the initializer implementation with the required modifier: 
```
protocol SomeProtocol {
    init(someParameter: Int)
}

class SomeClass: SomeProtocol {
    required init(someParameter: Int) {   //must with required
        // initializer implementation goes here
    }
}
```

You do not need to mark protocol initializer implementations with the required modifier on classes that are marked with the final modifier, 
because final classes cannot be subclassed  


If a subclass overrides a designated initializer from a superclass, and also implements a matching initializer requirement from a protocol, mark the initializer implementation with both the required and override modifiers:
```
protocol SomeProtocol {
    init()
}
 
class SomeSuperClass {
    init() {
        // initializer implementation goes here
    }
}
 
class SomeSubClass: SomeSuperClass, SomeProtocol {
    // "required" from SomeProtocol conformance; "override" from SomeSuperClass
    required override init() {
        // initializer implementation goes here
    }
}
```

##Protocols as Types ,(we dont need to put :pototol in class definition
```
class Dice {
    let sides: Int
    let generator: RandomNumberGenerator
    init(sides: Int, generator: RandomNumberGenerator) {
        self.sides = sides
        self.generator = generator
    }
    func roll() -> Int {
        return Int(generator.random() * Double(sides)) + 1
    }
}
```

but when we initiate it we should use actual class instead of protocal
```
var d6 = Dice(sides: 6, generator: LinearCongruentialGenerator())   //LinearCongruentialGenerator impl RandomNumberGenerator protocol
for _ in 1...5 {
    print("Random dice roll is \(d6.roll())")
}
```
##Delegation
(tbc)
