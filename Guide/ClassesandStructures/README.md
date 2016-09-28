#Classes and Structures
##Comparing Classes and Structures
Classes have additional capabilities that structures do not:
- Inheritance enables one class to inherit the characteristics of another.
- Type casting enables you to check and interpret the type of a class instance at runtime.
- Deinitializers enable an instance of a class to free up any resources it has assigned.
- Reference counting allows more than one reference to a class instance.  

(Structures are always copied when they are passed around in your code, and do not use reference counting)

###Definition Syntax

###Class and Structure Instances
```
let someResolution = Resolution()
let someVideoMode = VideoMode()
```
Structures and classes both use initializer syntax for new instances.  
The simplest form of initializer syntax uses the type name of the class or structure followed by empty parentheses, such as Resolution() or VideoMode().  
This creates a new instance of the class or structure, with any properties initialized to their default values.  

###Memberwise Initializers for Structure Types

Unlike structures, class instances do not receive a default memberwise initializer.


##Structures and Enumerations Are Value Types

###Identity Operators
Because classes are reference types, it is possible for multiple constants and variables to refer to the same single instance of a class behind the scenes.  
(The same is not true for structures and enumerations, because they are always copied when they are assigned to a constant or variable, or passed to a function.)  class K{}
```
var a = K()
var b=a
if a===b{
...
}
```

##Choosing Between Classes and Structures
rules
- The structure’s primary purpose is to encapsulate a few relatively simple data values.
- It is reasonable to expect that the encapsulated values will be copied rather than referenced when you assign or pass around an instance of that structure.
- Any properties stored by the structure are themselves value types, which would also be expected to be copied rather than referenced.
- The structure does not need to inherit properties or behavior from another existing type.  




