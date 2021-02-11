# Apple Developer

- **Why did Apple switch from `insertRows(at:with:)` to `performBatchUpdates(_:completion:)`?** The new approach allows you to group multiple types of animations.

## Frameworks

- **What is Core Image?** A non-destructive image editing framework, e.g., for applying filters.
- **What is Core Graphics?** A vector drawing framework.
- **What is Core Animation?**: An animation framework, all of `UIKit` is backed by `CALayer`  a Core Animation class.
- **What is a `CGLayer`?** An offscreen Core Graphics drawing destination.
- **What is a `CALayer`?** The lower-level class managing the bitmap representation of a `UIView`.
- **What is the type of a `UIView` `layer` property?** `CALayer`
- **What is a `CGContext`?** A 2D Quartz drawing destination, it might be a view, an image, or something else.
- **What is Quartz? Which framework is it related to?** Quartz is the graphics API for iOS and macOS. Quartz is practically synonymous with Core Graphics.
- **What are the two components of Quartz?** Quartz 2D for 2D rendering, and Quartz Compositor for compositing.
- **What important technology is Quartz backed by?** OpenGL

## UIKit

- **Where do UIKit drawing classes like `UIBezierPath` get a `CGContext` in `drawRect`?** UIKit configures a context and sets it as the current context before calling `drawRect`.
- **What is the difference between UIKit and AppKit as it relates to Core Animation?** `UIView` are automatically backed by `CALayer` whereas `NSView` are not (they can be turned on with the `wantsLayer` property).
- **What are the fifteen main iOS user interface elements?**
    - Action Sheets
    - Alerts
    - Collections
    - Edit Menus
    - Pages
    - Pickers
    - Popovers
    - Pull-Down Menus
    - Search Bars
    - Sliders
    - Split Views
    - Steppers
    - Switches
    - Tab Bars
    - Tool Bars
- **What are the ten main UIKit `UIView` subclasses?**
    - `UIAlertView`
    - `UIButton`
    - `UICollectionView`
    - `UILabel`
    - `UINavigationBar`
    - `UIScrollView`
    - `UISegmentedControl`
    - `UITabBar`
    - `UITableView`
    - `UITextView`
    - `UIToolbar`
- **What are the eight main UIKit `UIViewController` subclasses?**
    - `UIAlertController`
    - `UICollectionViewController`
    - `UINavigationController`
    - `UIPageViewController`
    - `UISplitViewController`
    - `UITabBarController`
    - `UITableViewController`

## Core Data

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
