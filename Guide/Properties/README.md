#Properties
Computed properties are provided by classes, structures, and enumerations. Stored properties are provided only by classes and structures.


##Stored Properties
###Lazy Stored Properties
A lazy stored property is a property whose initial value is not calculated until the first time it is used.  
You must always declare a lazy property as a variable (with the var keyword), because its initial value might not be retrieved until after instance initialization completes.  
Constant properties must always have a value before initialization completes, and therefore cannot be declared as lazy.


##Computed Properties
```
struct Point {
    var x = 0.0, y = 0.0
}
struct Size {
    var width = 0.0, height = 0.0
}
struct Rect {
    var origin = Point()
    var size = Size()
    var center: Point {
        get {
            let centerX = origin.x + (size.width / 2)
            let centerY = origin.y + (size.height / 2)
            return Point(x: centerX, y: centerY)
        }
        set(newCenter) {
            origin.x = newCenter.x - (size.width / 2)
            origin.y = newCenter.y - (size.height / 2)
        }
      
        
        
        
        
    }
}
var square = Rect(origin: Point(x: 0.0, y: 0.0),
                  size: Size(width: 10.0, height: 10.0))
let initialSquareCenter = square.center
square.center = Point(x: 15.0, y: 15.0)
```

If a computed property’s setter does not define a name for the new value to be set, a default name of ```newValue``` is used.
```
set {
    origin.x = newValue.x - (size.width / 2)
    origin.y = newValue.y - (size.height / 2)
}
```
###Read-Only Computed Properties
no set or get. Just a ruturn.

##Property Observers
willSet is called just before the value is stored.  
didSet is called immediately after the new value is stored.  

If you implement a willSet observer, it’s passed the new property value as a constant parameter. You can specify a name for this parameter as part of your willSet implementation. 
If you don’t write the parameter name and parentheses within your implementation, the parameter is made available with a default parameter name of ```newValue```.

Similarly, if you implement a didSet observer, it’s passed a constant parameter containing the old property value. 
You can name the parameter or use the default parameter name of ```oldValue```.

##Global and Local Variables


##Type Properties (static)

Stored type properties can be variables or constants.  

You define type properties with the static keyword. For computed type properties for class types, you can use the class keyword instead to allow subclasses to override the superclass’s implementation. 
```
class SomeClass {
    static var storedTypeProperty = "Some value."
    static var computedTypeProperty: Int {
        return 27
    }
    class var overrideableComputedTypeProperty: Int {
        return 107
    }
}
```






