# Apple Developer

- **Why did Apple switch from `insertRows(at:with:)` to `performBatchUpdates(_:completion:)`?** The new approach allows you to group multiple types of animations.
- **What are reference types and value types in Swift?** With value types, the effect of copying, via assignment, initialization, and argument passing, creates a separate instance with a unique copy of the data. With reference types, copying creates a shared instance.
- **What are examples of reference types in Swift?** Classes
- **In Swift, are collections (arrays, sets, and dictionaries) and strings reference types or value types?** They're value types.
- **Where are value types (like `struct`) stored?** They're stored on the stack by default unless they're part of a reference type, or are larger in size, then they're stored on the heap.
- **How does ARC relate to value types?** ARC is an implementation of reference counting, value types do not have references, so ARC is not applicable to value types.