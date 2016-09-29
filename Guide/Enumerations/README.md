#Enumerations
##Enumeration Syntax
basic
```
enum CompassPoint {
    case north
    case south
    case east
    case west
}
//or
enum CompassPoint {
    case north,south,east,west
}
```


##Associated Values
Ex
```
enum Barcode {
    case upc(Int, Int, Int, Int)
    case qrCode(String)
}
```
switch with associate types, do not to forget to add var type before parameter
```
productBarcode = .qrCode("ABC")

switch productBarcode {
case .upc(let numberSystem, let manufacturer, let product, let check): //need to add let
    print("UPC: \(numberSystem), \(manufacturer), \(product), \(check).")
}
```

##Raw Values
As an alternative to associated values, enumeration cases can come prepopulated with default values (called raw values), 
which are all of the same type.  
```
enum ASCIIControlCharacter: Character {   //here we return a type
    case tab = "\t"           //all cases have default value
    case lineFeed = "\n"
    case carriageReturn = "\r"
}
```

###Implicitly Assigned Raw Values
```
enum Planet: Int {
    case mercury = 1, venus, earth, mars, jupiter, saturn, uranus, neptune  //earch=3...
}
let earthsOrder = Planet.earth.rawValue //3
```
or init using rawValue
```
let possiblePlanet = Planet(rawValue: 7)
```

##Recursive Enumerations
A recursive enumeration is an enumeration that has another instance of the enumeration as the associated value for one or more of the enumeration cases. Ex
```
enum ArithmeticExpression {
    case number(Int)
    indirect case addition(ArithmeticExpression, ArithmeticExpression)
    indirect case multiplication(ArithmeticExpression, ArithmeticExpression)
}
```




