# Swift

- **What are reference types and value types in Swift?** With value types, the effect of copying, via assignment, initialization, and argument passing, creates a separate instance with a unique copy of the data. With reference types, copying creates a shared instance.
- **What are examples of reference types in Swift?** Classes
- **In Swift, are collections (arrays, sets, and dictionaries) and strings reference types or value types?** They're value types.
- **Where are value types (like `struct`) stored?** They're stored on the stack by default unless they're part of a reference type, or are larger in size, then they're stored on the heap.
- **In Swift, why does a subclass have to finish initialization (e.g., all properties need to be set), before calling `super.init`?** `super.init` might call a function that's been overridden by the subclass, calling a function on a class requires all properties to be initialized first, therefore the properties on the subclass all have to be set before calling `super.init`.
- **In Swift, how do you make a function parameter mutable?** Just assign it a `var` in the function body `var parameter = parameter`.
- **In Swift, what is an`inout` parameter?** It makes the parameter mutable, and it assigns the parameter's value back to the argument when the function ends.
- **In Swift, how are `inout` arguments passed in?** Preceded with an ampersand `myFunc(&myValue)`.
- **In Swift, what does putting an `&` in front of a variable name do? When is it used?** It passes in the variable by reference instead of by value, it's used when passing in `inout` arguments.
- **In Swift, which protocol adds a `description` to a type?** `CustomStringConvertible`

## Collections

- **In Swift, what does Copy-on-Write mean?** Swift's built-in collections don't copy on assignment, they reference the same array until a change is actually made. This can be implemented for your own collections.

## Enumerations

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
- **In Swift, how do you declare an associated value for an enum case?** `case value(Int)`
- **In Swift, what is the syntax for an enum with an associated value of its own type?** `indirect case sameType(SameType)`
- **In Swift, what does the indirect keyword on an enumeration case allow you to do?** Have an associated value of its own type.
- **In Swift, how do you declare a raw value for an enum case?**

    ```
    enum IntType: Int {
        case Int = 1
    }
    ```
- **In Swift, what is the default value for an enum called?** Raw value
- **In Swift, what aspect of enum makes it a good choice for defining constants?** They can't be instantiated.
- **In Swift, how do you assign the associated value for an enumeration case?** `let direction = CompassPoint.north("north")`
- **In Swift, how do you get the associated value for an enumeration case in a switch statement?** `case .letter(let value):`
- **In Swift, how do you get the associated value for an enumeration case in an if statement?** `if case .letter(let value) = item {`
- **In Swift, what are the three ways of getting the associated value for an enumerations case?** In a if statement `if case .letter(let value) = item {` or in switch statement `case .letter(let value):` or a catch `catch JSONPluginWriteError.failedToWriteInfoError(let url, let error)`
- **In Swift, how do you get the associated value for an `enum` in a try-catch?** `catch JSONPluginWriteError.failedToWriteInfoError(let url, let error)`

## Ranges

- **In Swift, how do you create a half-opened range?** `1..<5`
- **In Swift, how do you create a closed range?** `1...5`
- **In Swift, what is a range created with the `..<` operator called?** A half-opened range
- **In Swift, what is a range created with the `...` operator called?** A closed range
- **In Swift, what is `..<` called?** The half-open range operator
- **In Swift, what is `...` called?** The closed range operator

## Arrays

- **In Swift, how do you create an array from a string?** `Array("string")`
- **In Swift, how do you get an `ArraySlice` with just the first or last items of an array?** `dropFirst(_ k: Int = 1)`, `dropLast(_ k: Int)` or `arr(5...)`, `arr(..<5)`. (Note that ``arr(5...)` works but `arr(5..<)` doesn't, while `arr(..<5)` does.)
- **In Swift, which range cannot be used as an array subscript and why?** The half-opened range operator without an end (`3..<`), because getting all items after an index, while just excluding the last item, is a bit nonsensical.
- **In Swift, how do you get an `ArraySlice` of an arbitrary subarray?** Use a `Range` as the subscript, e.g., `arr[0..<4]`.
- **In Swift, why do some methods return `ArraySlice` instead of an array?** To avoid overhead of creating a new array.
- **In Swift, what should the loop condition be when doing a depth-first tree traversal? Why can't this technique be used when doing breadth-first?** `while let node = stack.popLast()`, this doesn't work for breadth-first search because there's no way to optionally return the first element of an array.

## Strings

- **In Swift, which feature does `String` not support that leads to a substring not being accessible with a range like an array is (e.g., `array[0..<5]`)?** Random access
- **In Swift, why doesn't `String` support random access?** Because Unicode characters are variable size.
- **In Swift, how do you get a substring of just the first or last characters?** `string.suffix(3)`, `string.prefix(3)`
- **In Swift, how do you create an arbitrary substring from a string?** Create a start and end index with `str.index(str.startIndex, offsetBy: 7)`, then use the start and end index as a range subscript `str[start..<end]`.

## Switch

- **In Swift, what is the syntax for a `switch` statement?**

    ```
    switch expression {
        case value1:
            // respond to value 1
        case value2:
            // respond to value2 or value3
        default:
            // otherwise, do something else
    }
    ```
- **In Swift, how do you put multiple values in a single switch statement case?** With commas `case value1, value2:`
- **In Swift, how do you use a range in a switch statement case?** `case 1..<5:`

## Value Types vs. Reference Types

- **In Swift, why can't a struct contain a property of its own type? Why can it contain an array of its own type?** Memory for structs is statically allocated, and it's impossible to determine the size of a struct that can recursively contain itself at compile time. Since arrays change in size dynamically, they already cannot be statically allocated, so arrays are really reference types with value semantics (implemented via Copy-on-Write). An array is contains a pointer to its elements, so it's size in the struct is static.
- **In Swift, how do collections implement value semantics?** Collections use reference semantics on assignment, and then, when they're mutated, they first check if they're uniquely referenced, and if not they make a copy of their internal storage to replicate value semantics.
- **In Swift, why do collections have a special implementation of value semantics?** Value semantics usually imply static memory allocation, which is impossible for collections that dynamically change size.
- **In Swift, what aspect of a struct prevents them from having properties that can vary in size?** Static memory allocation
- **In Swift, why can't a struct have an associated value of its own type?** Because then its size couldn't be determined at compile time.
- **In Swift, how is the `indirect` keyword implemented on enum?** By making it a reference type and using Copy-on-Write to give it value semantics.
- **In Swift, why can a statically allocated type have an associated value that's an array of its own type?** Because an array is a reference type with value semantics implemented by Copy-on-Write.
- **In Swift, why can a statically allocated type have an associated value that's a reference type?** Because the value of a reference type is just a pointer, and a pointer is of a constant size.
- **In Swift, are collections value or reference types?** They're reference types with value semantics implemented by Copy-on-Write.
- **In Swift, what is the syntax for `map`?** `let letterCounts = cast.map { $0.count }`
- **In Swift, what is the syntax for `reduce`?** `let numberSum = numbers.reduce(0, { x, y in x + y })`
- **In Swift, what is the syntax for `filter`?** `let shortNames = cast.filter { $0.count < 5 }`

## Types

- **In Swift, what are named types?** A type with a name, e.g., a `class`, `enum`, `struct`, or `protocol`.
- **In Swift, what are the two compound types?** Function types and tuple types
- **In Swift, where are built-in named types defined?** The standard library
- **In Swift, where are the two compound types defined?** In the Swift language itself.
- **In Swift, how are named types in the standard library defined?** `struct`
- **In Swift, what is a metatype type?** The type of a type `MyClass.Type`.
- **In Swift, what is an example of an opaque type?** Declaring a protocol conformance without declaring a concrete type.

### Terminology

- **In Swift, what is the term that covers both properties and values for enumeration cases?** Associated values
