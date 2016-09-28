#Automatic Reference Counting
Swift uses Automatic Reference Counting (ARC) to track and manage your app’s memory usage. 

##ARC in Action
ex:
```
class Person {
    let name: String
    init(name: String) {
        self.name = name
        print("\(name) is being initialized")
    }
    deinit {
        print("\(name) is being deinitialized")
    }
}
```
init empty:(Because these variables are of an optional type (Person?, not Person), 
they are automatically initialized with a value of nil, and do not currently reference a Person instance.)
```
var reference1: Person?
var reference2: Person?
var reference3: Person?
```
init:
```
reference1 = Person(name: "John")
reference2 = reference1  //three strong references to this single Person instance!
reference3 = reference1
reference1 = nil   // reference2,reference3 still exist
reference2= nil
reference3 = nil
// Prints "John Appleseed is being deinitialized"
```



##Resolving Strong Reference Cycles Between Class Instances
###Weak References
Use a weak reference to avoid reference cycles whenever it is possible for that reference to have a missing value at some point in its life. 
If the reference always has a value, use an unowned reference instead.

```
class Person{var apartment: Apartment?}
class Apartment { weak var tenant: Person?}
var john: Person?
var unit4A: Apartment?
```
init and bind
```
john = Person(name: "John Appleseed")
unit4A = Apartment(unit: "4A")
 
john!.apartment = unit4A
unit4A!.tenant = john
```
deinit (```weak``` property defined by other class)
```
john = nil //because weak var tenant: Person? so the relationship break.
```


##Unowned References
An unowned reference does not keep a strong hold on the instance it refers to.   
Unlike a weak reference, however, an unowned reference is assumed to always have a value.  
Because of this, an unowned reference is always defined as a nonoptional type.  
You indicate an unowned reference by placing the unowned keyword before a property or variable declaration.  
However, ARC cannot set the reference to nil when the instance it refers to is deallocated, 
because variables of a nonoptional type cannot be set to nil.


 In this data model, a customer may or may not have a credit card, but a credit card will always be associated with a customer. To represent this, the Customer class has an optional card property, but the CreditCard class has a nonoptional customer property.  
 

Because a credit card will always have a customer, you define its customer property as an unowned reference, to avoid a strong reference cycle:
```
class Customer {
    let name: String
    var card: CreditCard?
    init(name: String) {
        self.name = name
    }
    deinit { print("\(name) is being deinitialized") }
}
 
class CreditCard {
    let number: UInt64
    unowned let customer: Customer
    init(number: UInt64, customer: Customer) {
        self.number = number
        self.customer = customer
    }
    deinit { print("Card #\(number) is being deinitialized") }
}
```

init:
```
var john: Customer?
john = Customer(name: "John Appleseed")
john!.card = CreditCard(number: 1234_5678_9012_3456, customer: john!)
```

if
```
john = nil
Because there are no more strong references to the Customer instance, it is deallocated. After this happens, 
there are no more strong references to the CreditCard instance, and it too is deallocated:
```
###Unowned References and Implicitly Unwrapped Optional Properties
(tbc)
