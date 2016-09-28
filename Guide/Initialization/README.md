
#Initialization
Initialization is the process of preparing an instance of a class, structure, or enumeration for use.
##Setting Initial Values for Stored Properties
###Initializers
If a property always takes the same initial value, provide a default value rather than setting a value within an initializer.


##Customizing Initialization
###Parameter Names and Argument Labels
Argument labels must always be used in an initializer if they are defined, and omitting them is a compile-time error:
```
struct Color {
    let red, green, blue: Double
    init(red: Double, green: Double, blue: Double) {
        self.red   = red
        self.green = green
        self.blue  = blue
    }
    init(white: Double) {
        red   = white
        green = white
        blue  = white
    }
}
let veryGreen = Color(0.0, 1.0, 0.0)
// this reports a compile-time error - argument labels are required
```

###Initializer Parameters Without Argument Labels
If you do not want to use an argument label for an initializer parameter, 
write an underscore (_) instead of an explicit argument label for that parameter to override the default behavior.
```
struct Celsius {
    var temperatureInCelsius: Double
    ...
    init(_ celsius: Double) {
        temperatureInCelsius = celsius
    }
}
let bodyTemperature = Celsius(37.0)
```



###Assigning Constant Properties During Initialization

```
class SurveyQuestion {
    let text: String     //note this is let, not var
    var response: String?
    init(text: String) {
        self.text = text
    }
    ....
}    
let beetsQuestion = SurveyQuestion(text: "How about beets?") //cannot change
```


##Default Initializers

The default initializer simply creates a new instance with all of its properties set to their default values.

###Memberwise Initializers for Structure Types
```
struct Size {
    var width = 0.0, height = 0.0
}
let twoByTwo = Size(width: 2.0, height: 2.0)
```

##Initializer Delegation for Value Types
Value types (structures and enumerations) do not support inheritance, and so their initializer delegation process is relatively simple, because they can only delegate to another initializer that they provide themselves.   
Classes, however, can inherit from other classes.




##Class Inheritance and Initialization
designated initializers and convenience initializers.


###Designated Initializers and Convenience Initializers
Designated initializers are the primary initializers for a class. A designated initializer fully initializes all properties introduced by that class and calls an appropriate superclass initializer to continue the initialization process up the superclass chain.  

Subclasses can modify inherited variable properties during initialization, but can not modify inherited constant properties.


##Automatic Initializer Inheritance
If your subclass provides an implementation of all of its superclass designated initializers, then it automatically inherits all of the superclass convenience initializers.



###Designated and Convenience Initializers in Action
Ex:
```
class Food {
    var name: String
    init(name: String) {
        self.name = name
    }
    convenience init() {
        self.init(name: "[Unnamed]")
    }
}

class RecipeIngredient: Food {
    var quantity: Int
    init(name: String, quantity: Int) {
        self.quantity = quantity
        super.init(name: name)
    }
    override convenience init(name: String) {   //here, Because overrides a designated initializer from its superclass, it must override 
        self.init(name: name, quantity: 1)
    }
}
```


##Failable Initializers
using init?  
Ex
```
struct Animal {
    let species: String
    init?(species: String) {
        if species.isEmpty { return nil }
        self.species = species
    }
}
```
with string, or empty string
```
let someCreature = Animal(species: "Giraffe")
 
if let giraffe = someCreature {
    print(" \(giraffe.species)")
}


let anonymousCreature = Animal(species: "")
// anonymousCreature is of type Animal?, not Animal
 
if anonymousCreature == nil {
}
```
###Failable Initializers for Enumerations
Enum type, return type = self .  
Ex
```
enum TemperatureUnit {
    case celsius, fahrenheit
    init?(symbol: Character) {
        switch symbol {
        
        case "C":
            self = .celsius             //self = ....
        case "F":
            self = .fahrenheit
        default:
            return nil
        }
    }
}
let unknownUnit = TemperatureUnit(symbol: "X")
if unknownUnit == nil {
    print("")
}
```

###Failable Initializers for Enumerations with Raw Values
Enumerations with raw values automatically receive a failable initializer, init?(rawValue:),  
that takes a parameter called rawValue of the appropriate raw-value type.  
```
enum TemperatureUnit: Character {
    case celsius = "C", fahrenheit = "F"
}
 
let fahrenheitUnit = TemperatureUnit(rawValue: "F")
if fahrenheitUnit != nil {
    print("")
}
```


###Propagation of Initialization Failure
 a subclass failable initializer can delegate up to a superclass failable initializer.
 
 
 
 ##Required Initializers
Write the required modifier before the definition of a class initializer to indicate that every subclass of the class must implement that initializer:
 

##Setting a Default Property Value with a Closure or Function
value vs closure:
```
var numberOfWheels = 0
    var description: String {
        return "\(numberOfWheels) wheel(s)"
    }
 ```
 closure
 ```
 let someProperty: SomeType = {  //note '=' sign here
 
        // someValue must be of the same type as SomeType
        return someValue
    }()
 ```
