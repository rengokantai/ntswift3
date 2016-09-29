#Subscripts
##Subscript Syntax

```
struct TimesTable {
    let multiplier: Int
    subscript(index: Int) -> Int {       //no method name ,such as subscript sb(index:Int)->...
        return multiplier * index
    }
}
let threeTimesTable = TimesTable(multiplier: 3)
print("six times three is \(threeTimesTable[6])")
// Prints "six times three is 18"
```

##Subscript Options
Ex
```
struct Matrix {
    let rows: Int, columns: Int
    var grid: [Double]
    init(rows: Int, columns: Int) {
        self.rows = rows
        self.columns = columns
        grid = Array(repeating: 0.0, count: rows * columns)
    }
    func indexIsValid(row: Int, column: Int) -> Bool {
        return row >= 0 && row < rows && column >= 0 && column < columns
    }
    subscript(row: Int, column: Int) -> Double {
        get {
            assert(indexIsValid(row: row, column: column), "out of range")  //If false, trigger alarm
            return grid[(row * columns) + column]
        }
        set {
            assert(indexIsValid(row: row, column: column), "out of range") 
            grid[(row * columns) + column] = newValue
        }
    }
}
```
call:
```
matrix[0, 1] = 1.5     //not matrix[0][1] syntax, instead,[0,1]
matrix[1, 0] = 3.2
let someValue = matrix[2, 2]    //trigger an error in assert.
```
