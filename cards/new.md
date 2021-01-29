# New

## Reference & Value Types

- **In Swift, what aspect of a struct prevents them from having properties that can vary in size?** Static memory allocation
- **In Swift, why can't a struct have an associated value of its own type?** Because then its size couldn't be determined at compile time.
- **In Swift, how is the `indirect` keyword implemented on enum?** By making it a reference type and using Copy-on-Write to give it value semantics.
- **In Swift, why can a statically allocated type have an associated value that's an array of its own type?** Because an array is a reference type with value semantics implemented by Copy-on-Write.
- **In Swift, why can a statically allocated type have an associated value that's a reference type?** Because the value of a reference type is just a pointer, and a pointer is of a constant size.
- **In Swift, are collections value or reference types?** They're reference types with value semantics implemented by Copy-on-Write.

## Terminology

- **In Swift, what is the term that covers both properties and values for enumeration cases?** Associated values

## enum

- **In Swift, what is the syntax for an enum?**

    ```
    enum CompassPoint {
        case north
        case south
        case east
        case west
    }
    ```
- **In Swift, what are the the related values in an enum called?** Enumeration cases
- **In Swift, how do you specify multiple enum cases on the same line?** `case north, south, east, west`
- **In Swift, how do you specify an associated value for an enum case?** `case value(Int)`
- **In Swift, what is the syntax for an enum with an associated value of its own type?** `indirect case sameType(SameType)`
- **In Swift, what does the indirect keyword on an enumeration case allow you to do?** Have an associated value of its own type.
- **In Swift, how do you specify a raw value for an enum case?**

    ```
    enum IntType: Int {
        case Int = 1
    }
    ```
- **In Swift, what is the default value for an enum called?** Raw value
- **In Swift, what aspect of enum makes it a good choice for defining constants?** They can't be instantiated.

* * *

- **What does initialization mean?** To set to an initial value.
- **What does instantiation mean?** To create an instance.
