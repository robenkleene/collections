# Apple Developer

## Cocoa

- **Why did Apple switch from `insertRows(at:with:)` to `performBatchUpdates(_:completion:)`?** The new approach allows you to group multiple types of animations.

### Frameworks

- **What is Core Image?**

- **What is Core Graphics?** A vector library.

- **What is Core Animation?**

- **What is a `CGLayer`?** A 

- **What is a `CALayer`?** The lower-level class managing the bitmap representation of a `UIView`.

- **What is the type of a `UIView` `layer` property?** `CALayer`

- **What is a `CGContext`?** A 2D Quartz drawing destination, it might be a view, an image, or something else.

- **What is Quartz?**

- **How do UIKit classes and methods like `drawRect` work with Core Graphics?** UIKit configures a context and sets it as the current context before calling `drawRect`, so classes like `UIBezierPath` can use it automatically.

## Swift

- **What are reference types and value types in Swift?** With value types, the effect of copying, via assignment, initialization, and argument passing, creates a separate instance with a unique copy of the data. With reference types, copying creates a shared instance.
- **What are examples of reference types in Swift?** Classes
- **In Swift, are collections (arrays, sets, and dictionaries) and strings reference types or value types?** They're value types.
- **Where are value types (like `struct`) stored?** They're stored on the stack by default unless they're part of a reference type, or are larger in size, then they're stored on the heap.
- **In Swift, why does a subclass have to finish initialization (e.g., all properties need to be set), before calling `super.init`?** `super.init` might call a function that's been overridden by the subclass, calling a function on a class requires all properties to be initialized first, therefore the properties on the subclass all have to be set before calling `super.init`.

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