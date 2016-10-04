#Collection Types
##Mutability of Collections

###Creating an Empty Arra
```
var someInts = [Int]()
```

###Creating an Array with an Array Literal
```
var shoppingList: [String] = ["Eggs", "Milk"]
var shoppingList = ["Eggs", "Milk"]
```

##Sets
###Creating and Initializing an Empty Set
```
var letters = Set<Character>()
letters.insert("a")
```
literal
```
var favoriteGenres: Set<String> = ["Rock", "Classical", "Hip hop"]
var favoriteGenres:Set = ["Rock", "Classical", "Hip hop"]   //A set type cannot be inferred from an array literal alone
```
###Fundamental Set Operations
```
a.union(b)
a.intersection(b)
a.subtracting(b)
a.symmetricDifference(b)
```

Set Membership and Equality
```
a.isSubset(of: b)
a.isSuperset(of: b)
a.isDisjoint(with: b)   //note use with here
```

##Dictionaries
###Accessing and Modifying a Dictionary
The updateValue(_:forKey:) method returns an optional value contains the old value for that key if one existed before the update, or nil if no value existed:
```
if let oldValue = airports.updateValue("Dublin Airport", forKey: "DUB") {
    print("The old value for DUB was \(oldValue).")
}
```
