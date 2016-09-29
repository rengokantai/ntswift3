#Methods
Classes, structures, and enumerations can all define instance methods.

##Instance Methods
###Modifying Value Types from Within Instance Methods ```(mutating)```
```
struct Point {
    var x = 0.0, y = 0.0
    mutating func moveBy(x deltaX: Double, y deltaY: Double) {
        x += deltaX
        y += deltaY
    }
}
var somePoint = Point(x: 1.0, y: 1.0)
somePoint.moveBy(x: 2.0, y: 3.0)
print("The point is now at (\(somePoint.x), \(somePoint.y))")
// Prints "The point is now at (3.0, 4.0)"
```

another version
```
struct Point {
    var x = 0.0, y = 0.0
    mutating func moveBy(x deltaX: Double, y deltaY: Double) {
        self = Point(x: x + deltaX, y: y + deltaY)
    }
}
```

Note that you cannot call a mutating method on a constant of structure type, because its properties cannot be changed
```
let fixedPoint = Point(x: 3.0, y: 3.0) //If fiexedPoint is class ,this can be changed
fixedPoint.moveBy(x: 2.0, y: 3.0)
```




##Type Methods
