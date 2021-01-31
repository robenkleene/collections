# Computer Science

## Big O

- **What is logarithm (e.g., `log_2 N`)?**: Logarithm is the inverse of exponentiation, so `x = log_b n` is `b^x = n`. E.g., `log_2 16 = 4`.
- **Why does `log_2 N` grow slowly?** Logarithms increase slowly for the same reason exponential growth increases quickly: For base `2`, `N` doubles before the result increments by `1`.
- **What is asymptotic notation?** The umbrella term for big O, big Omega, and big Theta.
- **What is an asymptote?** An asymptote of a curve is a line where the distance between the line and the curve approaches zero as the curve's coordinates approach infinity.
- **What is Big O (e.g., `O(N)`)?** The upper bound of an algorithm.
- **What is Big Omega (e.g., `Ω(N)`)?** The lower bound of an algorithm.
- **What is Big Theta (e.g., `Θ(N)`)?** The upper and lower bound of an algorithm (i.e., a tightly bound algorithm). Big Theta is more informative than Big Oh or Big Omega, but harder to prove.
- **What are quadratic and sub-quadratic runtime?** Quadratic is `O(n^2)`. Sub-quadratic means anything between linear and quadratic runtime (expressed in Little-o `o(n^2)`, which defines a loose upper bounds).
- **What is cubic runtime?** `O(n^3)`
- **What is superpolynomial runtime?** A runtime faster than `O(n^k)`, e.g., `O(n!)` and `O(2^n)`.
- **What is polynomial runtime?** `O(n^k)` where `k > 0`  (This includes linear, quadratic, and cubic).
- **Why do recursive algorithms sometimes have more space complexity than iterative algorithms?** Recursive algorithms sometimes add calls to the call stack which takes up memory.
- **Drop the non-dominant terms in the following expressions: O(N^2 + N), O(N + log N), O(5 * 2^N + 1000N^100).** O(N^2), O(N), O(2^N)
- **What are the common big O expressions from fastest increasing to slowest.** O(x!), O(2^x), O(x^2), O(x log x), O(x), O(log x)
- **What's big O of this code?**

    ```
    for (int a : arrA) {
        print(a);
    }

    for (int b : arrB) {
        print(b);
    }
    ```

    O(A + B)

- **What's big O of this code?**

    ```
    for (int a : arrA) {
        for (int b : arrB) {
            print(a + "," + b);
        }
    }
    ```

    O(A * B)
- **What is "little-o notation"?** A loose upper bounds, equivalent to `<`, where as Big O is equivalent to `=<`.
- **How is little-o expressed?** `o(n^2)`
- **Which is the stronger statement, little o or big O?** Little o

### Sorting

- **How does quicksort work?** First choose an item to be the pivot (either randomly or use the middle item), then iterate over each item in the list and place it correctly relative to the pivot, on the right or left side. Now the pivot is in the correct position. Recursively do the same to the arrays to the right and the left of the pivot.
- **What does it mean for a sorting algorithm to be stable?** That the order of items is preserved for equal items.
- **How does the bubble sort algorithm work?** Sort items in-place by repeatedly iterate the list and put adjacent items in the correct order.
- **How does the selection sort algorithm work?** Sort items in-place by repeatedly finding the smallest (or largest item) item and putting it in the correct order in a sorted subarray.
- **How does the insertion sort algorithm work?** Sort items in-place by repeatedly finding the correct position of each item and placing it in a sorted subarray.
- **How does the heapsort algorithm work?** Sort items in-place sorting the items in a heap as a subarray. (Heapsort is an optimization of selection sort, where the heap is used to more efficiently order items.)
- **How does the merge sort algorithm work?** Divide the list into single item arrays (which are implicitly sorted), then repeatedly merge arrays until there's a single sorted list.
- **What is the time complexity of quicksort, heapsort, and merge sort?** `O(n log n)`, but the worst case of quicksort is `O(N^2)`, whereas the other two have the same worst case.
- **What's the time complexity of bubble sort, selection sort, and insertion sort?** `O(n^2)`

### Examples

- **What type of algorithm results in factorial (`O(x!)`) runtime?** Finding every permutation (e.g., a brute-force solution to the travelling salesman problem).
- **What type of algorithm results in exponential (`O(2^x)`) runtime?** Finding every combination (an efficient solution to the travelling salesman problem).
- **What type of algorithm results in quadratic `O(x^2)` runtime?** Nested loops (selection sort)
- **What type of algorithm results in `O(x log x)` runtime?** Divide and conquer (quicksort)
- **What type of algorithm results in linear (`O(x)`) runtime?** Iterating an array.
- **What type of algorithm results in logarithmic (`O(log x)`) runtime?** Binary search

## Memory

- **What is the stack vs. the heap?** The stack is memory that is used for variables scoped to functions, that isn't dynamically allocated. Since the stack is a stack, memory is allocated and released LIFO. The heap is always used for memory that is explicitly allocated.
- **What are the advantages of the stack vs. the heap?** The stack is faster, because of the execution overhead of `malloc()` and `free()`, but the heap can be any size.
- **Where are the stack and heap stored?** They're both stored in RAM.
- **When is stack memory allocated?** The stack is allocated at runtime.
- **When is heap memory allocated?** The heap is allocated at compile time (which really means load time).
- **How do you allocate a variable to the stack vs. the heap in C?** A variable scoped to a function, e.g., `main() { int x }` is stored on the stack, memory allocated with `malloc()` is stored on the heap.
- **Are value types and reference types generally stored on the stack or the heap?** Value types are stored in the stack, and reference types are stored in the heap.
- **Why are reference types always stored on the heap?** Reference types are pointers, and pointers point to a memory location on the heap.
- **What is a "stack overflow"?** A stack overflow is when a program exceeds the amount of memory available for the call stack and in overwrites adjacent data in the call stack.
- **What is the most common cause of a stack overflow?** Recursion that fails to terminate.
- **What is FIFO and LIFO?** First in, first out (a queue), and last in, first out (a stack).
- **What is dynamic memory allocation?** Memory allocated at runtime on the heap (e.g., `malloc()`).
- **What is static memory allocation?** Memory allocated at compile time (load time).
- **In C, where is static memory allocated?** Data segment
- **What is manual memory management?** Manually calling functions to return memory to the heap, this is in contrast to automatic memory management techniques like garbage collection or automatic reference counting.
- **Where are global and static variables stored in C?** They're stored in the data segment, which is separate from the stack and the heap.

## Data Structures

- **What is an abstract data type?** A data type design that doesn't specifying an implementation. In contrast to a "data structure" which is an implementation of a data type.
- **What are some examples of abstract data types?** Associative array, list, queue, set, stack, and tree are all abstract data types, whereas array is a data structure (an implementation of a list).
- **What is a list?** A list is the abstract data type for an array data structure.
- **What is an associative array?** The abstract data type for a hash table (or hash map). The data structure is called a dictionary in Swift/Objective-C/Smalltalk, a map in Java/C++, a hash map in Common Lisp.
- **What is a heap data structure?** A tree data structure that implements a priority queue. (Note that there's no relation to "the heap" in reference to memory allocation.)
- **What is a priority queue?** A queue with a priority property.
- **What is a queue? When should it be used?** A first in, first out (FIFO) data structure. It's used when order is important.
- **What is a stack? When should it be used?** A last in, first out (LIFO) data structure. The call stack and the memory stack are examples, it's also an easy optimization when populating a cache.
- **What is the difference between processing an array of jobs as a stack or a queue?** Removing the next item to process from the beginning (queue) or end (stack) of the array.
- **What are the advantages of linked lists over arrays and vice-versa?** - Linked lists don't have a fixed size, and elements don't have to be shifted after insertion and removal, whereas arrays do.

    - Arrays support random access, whereas linked lists only support sequential access.
- **What is the term for when an item in a sequence can be accessed directly?** Random access
- **What is the term for when an items in a sequence can only be accessed in order?** Sequential access

### Bloom Filter

- **What is a bloom filter?** A data structure designed to quickly tell if an element is either definitely not in a set or maybe in the set
- **How is a bloom filter implemented?** Use a bit array, to add an element, hash it and set the index of the hash value to `1`.
- **Why can a bloom filter only tell you if an element is maybe in the set?** Because it doesn't account for hash collisions
- **Why doesn't a bloom filter allow the removal of elements?** Because hash collisions make it impossible
- **What is a good use case for a bloom filter?** Determine if a URL is malicious by testing it against a list of known malicious URLs

### Arrays

- **Given an array index `i`, how do you calculate the number of indexes less than `i`?** `i - 1`
- **Given an array with a highest index of `n` and an index value `i`, how do you calculate the number of indexes greater than `i`?** `n - i`
- **Given an array with a length of `n` and an index value `i`, what does `n - i` calculate?** The number of indexes greater than or equal to `n`.
- **How do you calculate the highest index of an array?** Take the length and subtract one.
- **How do you get the midpoint of an array?** Integer divide the length by 2.
- **How do you get the midpoint of a range?** Integer divide the start plus the end by 2.

## Algorithms

### Dijkstra's Dutch National Flag Problem

- **What is Dijkstra's Dutch national flag problem?** Sort an array with any number of items, each representing one of three colors.
- **How do you solve Dijkstra's Dutch national flag problem? What is the time complexity of the solution?** Make counters set to 0 for the current index and the count of the lowest item, and a reverse counter set to the highest index for the highest item. Iterate the array while the current index is less than the index of counter for the highest item. If the current item is the lowest item, swap it with the value at the count of the lowest item, if the current item is the highest item, swap it with the reverse counter for the highest item. If it's the lowest item, or the middle item (but not the highest item), increment the current index. The time complexity is `O(n)`.
- **What is the name of the problem where you need to sort any of number of items each of one of three different values?** Dijkstra's Dutch national flag problem
- **In Dijkstra's Dutch national flag problem, why do you increment the current index if it's the lowest color, but not if it's the highest color?** Because the lower items have already been ordered, whereas the higher items still need to be ordered, so the loop has to run again at the current index to order the swapped in item.
- **In Dijkstra's Dutch national flag problem, why do you calculate the starting index for the highest item before you start iterating the array?** Because the highest item is used in the while loop condition.
- **In Dijkstra's Dutch national flag problem, what is the while loop condition and why?** It's whether the current index is lower than the reverse counter for the highest item, because the highest items have already been sorted.

### Combinations & Permutations

- **How do you find every combination of two lists?** Iterate both arrays nested, and combine items.
- **How do you find every permutation of two lists?** Iterate both arrays nested, and combine items in both orders.
- **How do you find the count of combinations of two lists?** Multiple the counts of each list.
- **How do you find the count of permutations of two lists?** Multiple the counts of each list and double it.

### Compression

- **How does lossless compression work?** By reducing redundancy.
- **How does lossy compression work?** By removing less important information.
- **Which data structure does Huffman Coding use to store symbols?** A priority queue (heap)
- **How does Huffman Coding track the path to a symbol?** A bit string describes the path to each symbol (`0` for the left node, `1` for the right).
- **How does Huffman Coding assure that encoded data can be parsed into unique code words?** The code words follow the "prefix property" where no code word has a prefix matching a shorter code word, therefore individual code words can be uniquely parsed from a bit string.
- **What is the result of compressing data with Huffman Coding?** A bit string made of up code words that are paths to each symbol.
- **How is data compressed with Huffman Coding assured to be smaller than the original data?** More common symbols will have shorter code words.
- **What is the time complexity of encoding with Huffman Coding? Based on which operations?** `O(n log n)`, `log n` to insert each symbol into the heap (for the priority queue), and `n` to iterate over each symbol.
- **With Huffman Coding, what is the time complexity of decoding? Based on which operations?** `O(n)` to iterate over the bit string (look up time for a heap is `O(1)`).
- **How does the MP3 compression algorithm work?** By removing sound information outside of the audible frequency range and applying a Huffman coding.
- **How does the JPG compression algorithm work?** By removing color information that's less perceptible by humans, and applying Huffman coding.

### Binary Search

- **How do you iteratively binary search an array?** Set two variables to the start and end indexes of an array. Loop while the start is less than the end: Get the value at the midpoint between the start and the end. If the target is less, set the end to the midpoint minus one, if it's greater, set the start to the midpoint plus one. Otherwise return the midpoint.
- **How do you recursively binary search an array?** Take the start and end as parameters defaulting to the start and end of the array. Set a base case to return nothing if the start is greater than the end. Get the value at the midpoint between the start and the end. If the target is less, recursively call the function with the end as midpoint minus one, if it's greater, recursively call it with the start as the midpoint plus one. Otherwise return the midpoint.

### Sort

- **How do you implement selection sort on an array?** Iterate through each index, then iterate through the remaining indices, if the value at the second index is lower than the value at the first index, then swap them.

### Least Recently Used Cache

- **Which data structures and variables do you need to implement a least recently used cache? Why?** An associative array to look up values by key, a doubly linked list to track last-accessed order (it's doubly linked so a node can delete itself in `O(1)`), and variables for capacity and current size.
- **Which two operations use the doubly linked list in a least recently used cache? How?** When adding or accessing a key-value pair, move its node to the head of the linked list. When adding a key-value pair, if the cache is over capacity, then remove the key-value pair for the tail node.
- **What is a trick for deleting a node that you just have a pointer to in a singly linked list in `O(1)`? What has to be true for this technique to work?** Set the nodes value to the value of the next node, and delete the next node. The list must be circular for this technique to work, otherwise you can't delete the last node.

### Dynamic Programming

- **What is dynamic programming?** Simplifying a problem by recursively breaking it into sub-problems.
- **Which two properties does a problem need to be good candidate for dynamic programming?** Optimal substructure and overlapping subproblems
- **What is a problem that's a good candidate for dynamic programming and why?** Calculating a Fibonacci number is an example of a problem with optimal substructure and overlapping subproblems. Calculating the Fibonacci number `F(n)` involves calculating the numbers for `F(n - 1)` and `F(n - 2)` and adding them. This means the problem can benefit from memoization, a form of dynamic programming.
- **What is optimal substructure?** Optimal substructure means that an optimal solution can be constructed from optimal solutions to its subproblems.
- **What are overlapping subproblems?** Overlapping subproblems means a problem can be broken down into subproblems that are solved repeatedly.
- **What is the relationship between optimal substructure and overlapping subproblems?** A problem that has both optimal substructure and overlapping subproblems is a good candidate for dynamic programming because it means a problem can be broken into smaller problems, and those smaller problems recur, which means it will benefit from dynamic programming's caching.

### Trees

- **How do you find the shortest path to a node in a tree?** Just have each node store a reference to its parent, and walk up the parent nodes.
- **How do you traverse a tree iteratively?** Create an array of nodes to visit, starting with just the root node. Loop until the array is empty, removing a node from the array and add its children to the end of the array.
- **When traversing a tree iteratively, how do you switch between a depth-first and breadth-first search?** A queue is breadth-first and a stack is depth-first.
- **How do you traverse a tree depth-first recursively?** Recursively call the function with each child.
- **Why is it impractical to traverse a tree breadth-first?** Breadth-first tree traversal uses a queue, which isn't available when recursing the same that the a depth-first search uses the call stack as a stack.

## Object-Orientated Programming

- **What is a concrete type?** A type that can be instantiated.
- **What is a abstract type?** A type that cannot be instantiated.
- **What is instantiation?** Creating an instance.

## Recursion

- **In recursion, what is each recursive call called?** A recursive step.

## Bitwise

- **What is a bit?** 0 or 1
- **What is a bit array?** An array of bits
- **What are the four other names for a bit array?** bit map, bit set, bit string, or bit vector
- **What is the `&` bitwise operator?** Bitwise AND, `3 & 5 = 1 // 011 & 101 = 001`
- **What is the `|` bitwise operator?** Bitwise OR, `3 & 5 = 7 // 011 & 101 = 101`
- **What will the value of a bitwise `&` be relative to its operands?** Less than or equal to the lowest number.
- **What will the value of a bitwise `|` be relative to its operands?** Greater than or equal to the highest number.
- **What is the `^` bitwise operator?** Exclusive OR, `3 & 5 = 6 // 011 & 101 = 110`
- **What is the `<<` bitwise operator?** Left shift, `5 << 3 //000101 << 3 = 101000`
- **What is the `>>` bitwise operator?**
- **What are the `<<` and `>>` bitwise operators called?** Left and right shift
- **What does `x << 1` do to the value of `x`? What about `x << 2` and `x << 3`?**
- **What is the `~` bitwise operator called?** One's complement or unary operator
- **What does the `~` bitwise operator do?**
- **How do you make a bit field of all `0`**? `0`
- **How do you make a bit field of all `1`**? `~0`
- **How do you make a bit field of all `0` except the rightmost `n` bits**? `~(~0 << n)`
- **How do you make a bit field of all `1` except the rightmost `n` bits**? `~0 << n`
- **How do you make a positive number negative with bitwise operations?**
- **What is `2` in binary?** `10`
- **What is `-2` in binary?** `01`
- **What are the numbers one through four in binary?**

## Terminology

- **What does initialization mean?** To set to an initial value
- **What does instantiation mean?** To create an instance
- **In computer science, what are the two attributes of a pure function?** No side effects and always returning the same value for the the same input
- **What is functional programming?** Programming with pure functions
- **In computer science, what does declarative mean?** Expressing a program in terms of what it should accomplish
- **In computer science, what does imperative mean?** Expressing a program in terms of how it should do it
- **What are two examples of imperative programming languages?** C, Python
- **What are four examples of declarative programming languages?** SQL, HTML, CSS, XSLT
- **In computer science, what is referential transparency?** A function being replacable with its returned value, without altering the programs behavior
- **What is the term for when when a function can be replaced with the value it returns without changing the programs behavior?** Referential transparency
- **What is the relationship between declarative programming and functional programming?** Functional languages do not have loops
- **What is control flow?** Loops and conditionals
- **In computer science, what is starvation?** When a process is denied the resource it needs to complete its work
- **In computer science, what is a typical example of starvation?** When a thread isn't running, due to a deadlock or even just a long running process

## Trivia

- **What is the origin of the phrase "Go To Statement Considered Harmful"?** Dijkstra's 1968 private paper "A Case against the GO TO Statement", it was later published under the heading "Go To Statement Considered Harmful".
