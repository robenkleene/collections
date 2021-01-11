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

- **What does `NSPersistentContainer` do?** It sets up Core Data stack: The managed object model, persistent store coordinator, and managed object context.
- **When was `NSPersistentContainer` introduced?** 2016, iOS 10, macOS Sierra 10.12.
- **What is an `NSManagedObjectContext` do?** An in-memory object graph.
- **Describe how multiple `NSManagedObjectContext` can interact with the same object.** Multiple `NSManagedObjectContext` can have their own copies of the same object.
- **What is an `NSManagedObjectModel`?** An in-memory representation schema.
- **What does `NSPersistentStoreCoordinator` do?** Coordinates between the managed object context and persistent store.
- **What does `NSPersistentStore` do?** A wrapper around the persistent store itself, either SQLite, Binary, XML, or In-Memory.
- **How do you do Core Data work on a background queue?** Setup a child context with a private concurrency type, and use perform block to do the work, when you save the child context, the changes will be propagated up to the parent context. Changes are propagated only one level up, so to save to the persistent store, save on the main managed object as well.
- **In Core Data, how does saving on child contexts work?** A save propagates changes one level up, so a child context propagates to its parent, a root context saves to the persistent store.

## Swift

- **What are reference types and value types in Swift?** With value types, the effect of copying, via assignment, initialization, and argument passing, creates a separate instance with a unique copy of the data. With reference types, copying creates a shared instance.
- **What are examples of reference types in Swift?** Classes
- **In Swift, are collections (arrays, sets, and dictionaries) and strings reference types or value types?** They're value types.
- **Where are value types (like `struct`) stored?** They're stored on the stack by default unless they're part of a reference type, or are larger in size, then they're stored on the heap.
- **In Swift, why does a subclass have to finish initialization (e.g., all properties need to be set), before calling `super.init`?** `super.init` might call a function that's been overridden by the subclass, calling a function on a class requires all properties to be initialized first, therefore the properties on the subclass all have to be set before calling `super.init`.
- **In Swift, how do you make a function parameter mutable?** Just assign it a `var` in the function body `var parameter = parameter`.
- **In Swift, what is an`inout` parameter?** It makes the parameter mutable, and it assigns the parameter's value back to the argument when the function ends.
- **In Swift, how are `inout` arguments passed in?** Preceded with an ampersand `myFunc(&myValue)`.
- **In Swift, what does putting an `&` in front of a variable name do?** It means pass that variable by reference instead of by value. It must be used when passing in `inout` arguments.
- **In Swift, how do you add a `description` to a type?** Make it conform to `CustomStringConvertible`.

### Ranges

- **In Swift, how do you create a half-opened range?** `1..<5`
- **In Swift, how do you create a closed range?** `1...5`
- **In Swift, what is a range created with the `..<` operator called?** A half-opened range
- **In Swift, what is a range created with the `...` operator called?** A closed range
- **In Swift, what is `..<` called?** The half-open range operator
- **In Swift, what is `...` called?** The closed range operator

### Arrays

- **In Swift, how do you create an array from a string?** `Array("string")`
- **In Swift, how do you get an `ArraySlice` with just the first or last items of an array?** `dropFirst(_ k: Int = 1)`, `dropLast(_ k: Int)`
- **In Swift, how do you get an `ArraySlice` of an arbitrary subarray?** Use a `Range` as the subscript, e.g., `arr(0..<4)`.
- **In Swift, why do some methods return `ArraySlice` instead of an array?** To avoid overhead of creating a new array.

### Strings

- **In Swift, why can't you access a substring with a range like you can for an array (e.g., `array[0..<5]`)?** `String` does not support random access, because support for Unicode means that characters aren't the same size.
- **In Swift, how do you get a substring of just the first or last characters?** `string.suffix(3)`, `string.prefix(3)`
- **In Swift, how do you create an arbitrary substring from a string?**

### Types

- **In Swift, what are named types?** A type with a name, e.g., a `class`, `enum`, `struct`, or `protocol`.
- **In Swift, what are the two compound types?** Function types and tuple types
- **In Swift, where are built-in named types defined?** The standard library
- **In Swift, where are the two compound types defined?** In the Swift language itself.
- **In Swift, how are named types in the standard library defined?** `struct`
- **In Swift, what is an opaque type?** A type that conforms to a protocol without specifying the underlying concrete type.
- **In Swift, what is a metatype type?** The type of a type `MyClass.Type`.

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