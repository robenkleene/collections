# Apple Developer

## Cocoa

- **Why did Apple switch from `insertRows(at:with:)` to `performBatchUpdates(_:completion:)`?** The new approach allows you to group multiple types of animations.

### Frameworks

- **What is Core Image?** A non-destructive image editing framework, e.g., for applying filters.
- **What is Core Graphics?** A vector drawing framework.
- **What is Core Animation?**: An animation framework, all of `UIKit` is backed by `CALayer  a Core Animation class.
- **What is a `CGLayer`?** An offscreen Core Graphics drawing destination.
- **What is a `CALayer`?** The lower-level class managing the bitmap representation of a `UIView`.
- **What is the type of a `UIView` `layer` property?** `CALayer`
- **What is a `CGContext`?** A 2D Quartz drawing destination, it might be a view, an image, or something else.
- **What is Quartz? Which framework is it related to?** Quartz is the graphics API for iOS and macOS. Quartz is practically synonymous with Core Graphics.
- **What are the two components of Quartz?** Quartz 2D for 2D rendering, and Quartz Compositor for compositing.
- **What important technology is Quartz backed by?** OpenGL
- **Where do UIKit drawing classes like `UIBezierPath` get a `CGContext` in `drawRect`?** UIKit configures a context and sets it as the current context before calling `drawRect`.
- **What is the difference between UIKit and AppKit as it relates to Core Animation?** `UIView` are automatically backed by `CALayer` whereas `NSView` are not (they can be turned on with the `wantsLayer` property).

### Core Data

- **What does `NSPersistentContainer` do?** It sets up the three Core Data classes: `NSManagedObjectModel`, `NSPersistentStoreCoordinator`, and `NSManagedObjectContext`.
- **When was `NSPersistentContainer` introduced?** 2016, iOS 10, macOS Sierra 10.12.
- **What is an `NSManagedObjectContext` do?** An in-memory object graph.
- **Describe how multiple `NSManagedObjectContext` can interact with the same object.** Multiple `NSManagedObjectContext` can have their own copies of the same object.
- **What is an `NSManagedObjectModel`?** An in-memory representation schema.
- **What does `NSPersistentStoreCoordinator` do?** Coordinates between the managed object context and persistent store.
- **What does `NSPersistentStore` do?** A wrapper around the persistent store itself, either SQLite, Binary, XML, or In-Memory.
- **How do you use Core Data on a background queue?** Setup a child context with a private concurrency type, perform work on its internal queue, when you save the child context, the changes will be propagated up to the parent context.
- **With Core Data, how do you perform work on a child `NSManagedObjectContext` internal queue?** `performBlock { }`
- **With Core Data, how do you initialize a background `NSManagedObjectContext`?** `NSManagedObjectContext(concurrencyType: .PrivateQueueConcurrencyType)`
- **In Core Data, what happens when you save on a child context?** The save propagates changes one level up, so a child context propagates to its parent.
- **In Core Data, what happens when you save on the root context?** The save is propagated to the persistent store.

## Swift

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

### Collections

- **In Swift, what does Copy-on-Write mean?** Swift's built-in collections don't copy on assignment, they reference the same array until a change is actually made. This can be implemented for your own collections.

### Enumerations

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
- **In Swift, how do you set the associated value for an enumeration case?** `let direction = CompassPoint.north("north")`
- **In Swift, how do you access the associated value for an enumeration case in a switch statement?** `case .letter(let value):`
- **In Swift, how do you access the associated value for an enumeration case in an if statement?** `if case .letter(let value) = item {`

### Ranges

- **In Swift, how do you create a half-opened range?** `1..<5`
- **In Swift, how do you create a closed range?** `1...5`
- **In Swift, what is a range created with the `..<` operator called?** A half-opened range
- **In Swift, what is a range created with the `...` operator called?** A closed range
- **In Swift, what is `..<` called?** The half-open range operator
- **In Swift, what is `...` called?** The closed range operator

### Arrays

- **In Swift, how do you create an array from a string?** `Array("string")`
- **In Swift, how do you get an `ArraySlice` with just the first or last items of an array?** `dropFirst(_ k: Int = 1)`, `dropLast(_ k: Int)` or `arr(5...)`, `arr(..<5)`. (Note that ``arr(5...)` works but `arr(5..<)` doesn't, while `arr(..<5)` does.)
- **In Swift, which range cannot be used as an array subscript and why?** The half-opened range operator without an end (`3..<`), because getting all items after an index, while just excluding the last item, is a bit nonsensical.
- **In Swift, how do you get an `ArraySlice` of an arbitrary subarray?** Use a `Range` as the subscript, e.g., `arr[0..<4]`.
- **In Swift, why do some methods return `ArraySlice` instead of an array?** To avoid overhead of creating a new array.
- **In Swift, what should the loop condition be when doing a depth-first tree traversal? Why can't this technique be used when doing breadth-first?** `while let node = stack.popLast()`, this doesn't work for breadth-first search because there's no way to optionally return the first element of an array.

### Strings

- **In Swift, which feature does `String` not support that leads to a substring not being accessible with a range like an array is (e.g., `array[0..<5]`)?** Random access
- **In Swift, why doesn't `String` support random access?** Because Unicode characters are variable size.
- **In Swift, how do you get a substring of just the first or last characters?** `string.suffix(3)`, `string.prefix(3)`
- **In Swift, how do you create an arbitrary substring from a string?** Create a start and end index with `str.index(str.startIndex, offsetBy: 7)`, then use the start and end index as a range subscript `str[start..<end]`.

### Switch

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


### Value Types vs. Reference Types

- **In Swift, why can't a struct contain a property of its own type? Why can it contain an array of its own type?** Memory for structs is statically allocated, and it's impossible to determine the size of a struct that can recursively contain itself at compile time. Since arrays change in size dynamically, they already cannot be statically allocated, so arrays are really reference types with value semantics (implemented via Copy-on-Write). An array is contains a pointer to its elements, so it's size in the struct is static.
- **In Swift, how do collections implement value semantics?** Collections use reference semantics on assignment, and then, when they're mutated, they first check if they're uniquely referenced, and if not they make a copy of their internal storage to replicate value semantics.
- **In Swift, why do collections have a special implementation of value semantics?** Value semantics usually imply static memory allocation, which is impossible for collections that dynamically change size.
- **In Swift, what aspect of a struct prevents them from having properties that can vary in size?** Static memory allocation
- **In Swift, why can't a struct have an associated value of its own type?** Because then its size couldn't be determined at compile time.
- **In Swift, how is the `indirect` keyword implemented on enum?** By making it a reference type and using Copy-on-Write to give it value semantics.
- **In Swift, why can a statically allocated type have an associated value that's an array of its own type?** Because an array is a reference type with value semantics implemented by Copy-on-Write.
- **In Swift, why can a statically allocated type have an associated value that's a reference type?** Because the value of a reference type is just a pointer, and a pointer is of a constant size.
- **In Swift, are collections value or reference types?** They're reference types with value semantics implemented by Copy-on-Write.

### Types

- **In Swift, what are named types?** A type with a name, e.g., a `class`, `enum`, `struct`, or `protocol`.
- **In Swift, what are the two compound types?** Function types and tuple types
- **In Swift, where are built-in named types defined?** The standard library
- **In Swift, where are the two compound types defined?** In the Swift language itself.
- **In Swift, how are named types in the standard library defined?** `struct`
- **In Swift, what is an opaque type?** A type that conforms to a protocol without specifying the underlying concrete type.
- **In Swift, what is a metatype type?** The type of a type `MyClass.Type`.

### Terminology

- **In Swift, what is the term that covers both properties and values for enumeration cases?** Associated values

## Memory Management

- **How does ARC relate to value types?** ARC is an implementation of reference counting, value types do not have references, so ARC is not applicable to value types.

## Protocols

- **Why can't protocols conform to `Equatable`?** `Equatable` has an associated type of `self`. Protocols with associated types can only be used a generic constraint (e.g., `func myMethod<T: MyProtocol>(myObject: T)`), and can't be used a parameter type directly. Part of the rational here, is that testing whether objects of different types are equal has pitfalls.
- **In Swift, what is an associated type?** A generic type in a protocol.

## Threading

- **In Grand Central Dispatch, how do you dispatch after an amount of time?**

    `DispatchQueue.main.asyncAfter(deadline: .now() + 1.0) { }`

- **In Grand Central Dispatch, how do you dispatch to the main queue?**

    `DispatchQueue.main.async { }`

- **In Grand Central Dispatch, how do you dispatch to a background queue?**

    `DispatchQueue.global(qos: .background).async { }`

- **In Grand Central Dispatch, how do you dispatch to a serial queue?**

`DispatchQueue` is serial by default.

```
let queue = DispatchQueue(label: "com.queue.Serial")
queue.async {
    // Do something
}
```
