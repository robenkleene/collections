# New

In Swift, what aspect of a struct prevents them from having properties that can vary in size?

Static memory allocation

* * *

In Swift, why can't a statically allocated type have an associated value of its own type?

Because then its size couldn't be determined at compile time.

* * *

In Swift, why can a statically allocated type have an associated value 

* * *

What is the term that covers both properties and values for enumeration cases?

Associated values

* * *

In Swift, what is the syntax for an enum?

```
enum CompassPoint {
    case north
    case south
    case east
    case west
}
```

* * *

In Swift, what are the the related values in an enum called?

Enumeration cases

* * *

In Swift, how do you specify multiple enum cases on the same line?

`case north, south, east, west`

* * *

In Swift, how do you specify an associated value for an enum case?

* * *

In Swift, how do you specify a raw value for an enum case?

* * *

In Swift, what is the default value for an enum called?

Raw value

* * *

In Swift, why can't a struct contain a property of its own type? Why can they contain an array of their own type?

Memory for structs is statically allocated, and it's impossible to determine the size of a struct that can recursively contain itself at compile time. Since arrays change in size dynamically, they already cannot be statically allocated, so arrays are really reference types with value semantics (implemented via Copy-on-Write). An array is contains a pointer to its elements, so it's size in the struct is static.

* * *

In Swift, what aspect of enum makes it a good choice for defining constants?

They can't be instantiated.

* * *

What does initialization mean?

To set to an initial value.

* * *

What does instantiation mean?

To create an instance.
