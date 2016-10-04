#Closures
##Closure Expressions
###Closure Expression Syntax
sorting closure
```
reversedNames = names.sorted(by: { (s1: String, s2: String) -> Bool in return s1 > s2 } )
reversedNames = names.sorted(by: { s1, s2 in return s1 > s2 } )
reversedNames = names.sorted(by: { s1, s2 in s1 > s2 } )
reversedNames = names.sorted(by: { $0 > $1 } )
reversedNames = names.sorted(by: >)
```


#Trailing Closures
The string-sorting closure from the Closure Expression Syntax
section above can be written outside of the sorted(by:) method’s parentheses as a trailing closure:
```
reversedNames = names.sorted() { $0 > $1 }
```


##Capturing Values
A closure can capture constants and variables from the surrounding context in which it is defined. The closure can then refer to and modify the values of those constants and variables from within its body,
even if the original scope that defined the constants and variables no longer exists.


```
func makeIncrementer(forIncrement amount: Int) -> () -> Int {
    var runningTotal = 0
    func incrementer() -> Int {
        runningTotal += amount
        return runningTotal
    }
    return incrementer
}

let incrementByTen = makeIncrementer(forIncrement: 10)
incrementByTen() //10
incrementByTen() //20
```
If you create a second incrementer, it will have its own stored reference to a new, separate runningTotal variable:
```
let incrementBySeven = makeIncrementer(forIncrement: 7)
incrementBySeven() //7
```


##Closures Are Reference Types
Whenever you assign a function or a closure to a constant or a variable,  
you are actually setting that constant or variable to be a reference to the function or closure.  
if you assign a closure to two different constants or variables, both of those constants or variables will refer to the same closure:
```
let alsoIncrementByTen = incrementByTen
alsoIncrementByTen()//30
```
##Escaping Closures
