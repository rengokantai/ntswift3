
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
