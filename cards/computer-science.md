# Computer Science

## Big O

- **What is logarithm (e.g., `log_2 N`)?**: Logarithm is the inverse of exponentiation, so `x = log_b n` is `b^x = n`. E.g., `log_2 16 = 4`.
- **Why does `log_2 N` grow slowly?** Logarithms increase slowly for the same reason exponential growth increases quickly: For base `2`, `N` doubles before the result increments by `1`.
- **What is asymptotic notation?** An asymptote of a curve is a line where the distance between the line and the curve approaches zero as the curve's coordinates approach infinity. Asymptotic notation is the umbrella term for big O, big Omega, and big Theta.
- **What is Big O (e.g., `O(N)`)?** The upper bound of an algorithm.
- **What is Big Omega (e.g., `Ω(N)`)?** The lower bound of an algorithm.
- **What is Big Theta (e.g., `Θ(N)`)?** The upper and lower bound of an algorithm (i.e., a tightly bound algorithm). Big Theta is more informative than Big Oh or Big Omega, but harder to prove.
- **What are quadratic and sub-quadratic runtime?** Quadratic is `O(n^2)`. Sub-quadratic means anything between linear and quadratic runtime (expressed in Little-o `o(n^2)`, which defines a loose upper bounds).
- **What is superpolynomial runtime?** A runtime faster than `O(n^k)`, e.g., `O(n!)` and `O(2^n)`.
- **Why do recursive algorithms sometimes have more space complexity than iterative algorithms?** Because recursive algorithms add calls to the call stack that take up memory.
- **Drop the non-dominant terms in the following expressions: O(N^2 + N), O(N + log N), O(5 * 2^N + 1000N^100).** O(N^2), O(N), O(2^N).
- **What are the common big O expressions from fastest increasing to slowest.** O(x!), O(2^x), O(x^2), O(x log x), O(x), O(log x).
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

### Sorting

- **How does the quicksort algorithm work?** First choose an item to be the pivot (usually either randomly or use the middle item), then iterate over each item in the list and place it correctly relative to the pivot on the right or left side. Now the pivot is in the correct position. Recursively do the same to the arrays to the right and the left of the pivot.
- **What is the time complexity of quicksort, heapsort, and merge sort?** `O(n log n)`, the worst case of quicksort is `O(N^2)`, whereas the other two have the same worst case.
- **Why is quicksort the best sorting algorithms in practice?** It has good average case time complexity `O(n log n)`, and the sort is in place, heapsort and merge sort, the two algorithms that have an upper bounds of `O(n log n)`, both require additional data structures.
- **What does it mean for a sorting algorithm to be stable?** Equal items are in the same order in the result as they were in the input.
- **How does the bubble sort algorithm work?** Sort items by comparing adjacent elements.
- **How does the selection sort algorithm work?** Sort items in place by splitting the array into sorted and unsorted sections, then iteratively finding the smallest (or largest) item from the unsorted section and placing it in the appropriate spot in the sorted section.
- **How does the insertion sort algorithm work?** Sort items by creating a separate array with items in the correct order.
- **How does the heapsort algorithm work?** Heapsort uses the same approach as selection sort, by dividing the array into sorted and unsorted sections. The difference is that it keeps track of already inspected items in a heap for faster lookup.
- **How does the merge sort algorithm work?** Divide the list into single item arrays (which are implicitly sorted), then repeatedly merge arrays until there's a single sorted list.
- **What's the time complexity of bubble sort, selection sort, and insertion sort?** `O(n^2)`

### Examples

- **What type of algorithm results in factorial (`O(x!)`) runtime?** Recursively test every branch of a tree (e.g., the traveling salesman problem).
- **What type of algorithm results in exponential (`O(2^x)`) runtime?** Every possible permutation (generate all possible passwords of length `x`).
- **What type of algorithm results in quadratic `O(x^2)` runtime?** Nested loops (selection sort).
- **What type of algorithm results in `O(x log x)` runtime?** Divide and conquer (quicksort).
- **What type of algorithm results in linear (`O(x)`) runtime?** Iterate an array.
- **What type of algorithm results in logarithmic (`O(log x)`) runtime?** Binary search.

## Memory

- **What is the stack vs. the heap? When are they allocated? Where are they stored? When should each be used?** The stack is memory that is used for variables scoped to functions, that isn't dynamically allocated. Since the stack is a stack, memory is allocated and released LIFO. The heap is used for memory that is allocated. Stack variables are allocated at compile time, and heap variables are allocated at runtime. The stack and heap are both stored in RAM. The stack is faster, because of the execution overhead of `malloc()` and `free()`, but the heap can be any size (e.g., for user input or consuming from an API).
- **How do you allocate a variable to the stack vs. the heap in C?** A variable scoped to a function, e.g., `main() { int x }` is stored on the stack, memory allocated with `malloc()`.
- **How do you allocate a variable to the stack vs. the heap in C?** Value types are stored in the stack, and reference types are stored in the heap. Reference types are always stored on the heap because pointers always point to a memory location on the heap.
- **What does a "stack overflow" mean?** When a program writes more data to a buffer on the stack than was allocated for that buffer.
- **What is FIFO and LIFO?** First in, first out (a queue), and last in, first out (a stack).
- **What is dynamic memory allocation?** Dynamic memory allocation is memory allocated at runtime on the heap (e.g., `malloc()`).
- **What manual memory management?** Manually calling functions to return memory to the heap, in contrast to automatic memory management implementations like garbage collection or automatic reference counting.
- **Where are global and static variables stored in C?** They're stored in the data segment, which is separate from the stack and the heap.

## Data Structures

- **What is an abstract data type?** A definition of behavior for a data type, without specifying implementation. In contrast to a "data structure" which specifies the implementation for a data type. Associative array, list, queue, set, stack, and tree are all abstract data types.
- **What is a list?** A list is the abstract data type for an array data structure.
- **What are the synonyms for an associative array?** Associative array, map, symbol table, dictionary.
- **What is a heap data structure?** A tree data structure that implements a priority queue. (Note that there's no relation to "the heap" in reference to memory allocation.)
- **What is a priority queue?** A queue with a priority property.
- **What is a queue?** A first in, first out (FIFO) data structure.
- **What is a stack?** A last in, first out (LIFO) data structure.