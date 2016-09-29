#The Basics
##Integers
###Int
On a 32-bit platform, Int is the same size as Int32.
On a 64-bit platform, Int is the same size as Int64.


0xFp2 means 15 x 2^2, or 60.0.  
0xFp-2 means 15 x 2^-2, or 3.75.  

paddings:
```
let oneMillion = 1_000_000
let justOverOneMillion = 1_000_000.000_000_1
```

##Numeric Type Conversion


##Type Aliases
```
typealias AudioSample = UInt16
var maxAmplitudeFound = AudioSample.min
```


##Booleans
Non bool value is if statement is error!
```
let i = 1
if i {
    // this example will not compile, and will report an error
}
```

```
let i = 1
if i==1 { //correct
}
```


##Tuples
```
let http404Error = (404, "Not Found")
```
decompose:
```
let (statusCode, statusMessage) = http404Error  //not curly braces like js
//index is 0 based
print("The status code is \(http404Error.0)")
// Prints "The status code is 404"
```

##Optionals
###Optional Binding
Form:  
```
if let constantName = someOptional {
    statements
}
```
We can include as many optional bindings and Boolean conditions in a single if statement,seperate by commas
```
if let firstNumber = Int("4"), let secondNumber = Int("42"), firstNumber < secondNumber && secondNumber < 100 {
    print("\(firstNumber) < \(secondNumber) < 100")
}
```
###Implicitly Unwrapped Optionals
