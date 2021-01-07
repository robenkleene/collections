# Computer Science

## Big O

- **What is logarithm (e.g., `log_2 N`)?**: Logarithm is the inverse of exponentiation, so `x = log_b n` is `b^x = n`. E.g., `log_2 16 = 4`.
- **Why does `log_2 N` grow slowly?** Logarithms increase slowly for the same reason exponential growth increases quickly: For base `2`, `N` doubles before the result increments by `1`.
- **What is asymptotic notation?** An asymptote of a curve is a line where the distance between the line and the curve approaches zero as the curve's coordinates approach infinity. Asymptotic notation is the umbrella term for big O, big Omega, and big Theta.
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

### Sorting

- **How does quicksort work?** First choose an item to be the pivot (either randomly or use the middle item), then iterate over each item in the list and place it correctly relative to the pivot, on the right or left side. Now the pivot is in the correct position. Recursively do the same to the arrays to the right and the left of the pivot.
- **What does it mean for a sorting algorithm to be stable?** Equal items are in the same order in the result as they were in the input.
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
- **When are stack and heap memory allocated?** The stack is allocated at runtime and the heap is allocated at compile time. (Compile time really means load time.)
- **How do you allocate a variable to the stack vs. the heap in C?** A variable scoped to a function, e.g., `main() { int x }` is stored on the stack, memory allocated with `malloc()` is stored on the heap. In other words, value types are stored in the stack, and reference types are stored in the heap. Reference types are always stored on the heap because pointers always point to a memory location on the heap.
- **What does a "stack overflow" mean? When do they happen?** A stack overflow happens when too many calls are put on the call stack. The most-common cause is recursion that fails to terminate.
- **What is FIFO and LIFO?** First in, first out (a queue), and last in, first out (a stack).
- **What is dynamic memory allocation?** Memory allocated at runtime on the heap (e.g., `malloc()`).
- **What is static memory allocation?** Memory allocated at compile time (load time) on the stack.
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
- **What's the difference between implementing a stack and a queue using an array?** When removing an item to process, is it removed from the beginning (queue) or end of the array (stack).

## Algorithms

- **How do you design a data compression algorithm?** Compression is either lossy or lossless. Lossless compression works by reducing redundancy. Lossy compression works by removing less important information.
- **What is Huffman Coding? What is its time complexity?** Symbols are stored in a priority queue where a bit string describing the path to each symbol (`0` for the left node, `1` for the right) is used as a code word. The code words follow the "prefix property" where no code word has a prefix matching a shorter code word, thereby assuring individual code words can be uniquely parsed from a bit string. The compressed data is then stored as a bit string. The bit string is shorter than the original data because more common symbols have shorter code words. The time complexity of encoding is `O(n log n)`, `log n` to insert each symbol into the heap (for the priority queue), and `n` to iterate over each symbol. Decoding is `O(n)` to iterate over the bit string (look up time for a heap is `O(1)`).
- **How does the MP3 compression algorithm work?** By removing sound information outside of the audible frequency range and applying a Huffman coding.
- **How does the JPG compression algorithm work?** By removing color information that's less perceptible by humans, and applying Huffman coding.

### Trees

- **How do you find the shortest path to a node in a tree?** Just have each node store a reference to its parent, and walk up the parent nodes.
- **How do you traverse a tree iteratively? How do you switch between depth-first and breadth-first? How do you return the path taken?** Create an array with just the root node to use as a queue or stack of nodes to visit, and create a set to track visited nodes. Loop until the stack is empty: Pop a node, add it to visited, and add its children to the end of the queue or stack. A queue is breadth-first and a stack is depth-first. Use an array for visited and return it to get the path taken.
- **How do you traverse a tree depth-first recursively?** Recursively call the function with each child.
- **Why is it impractical to traverse a tree breadth-first?** Breadth-first tree traversal uses a queue, which isn't available when recursing the same that the a depth-first search uses the call stack as a stack.

## Bitwise

- **What does the `&` bitwise operator do?**
- **What does the `|` bitwise operator do?**
- **What does the `^` bitwise operator do?**
- **What is the `^` bitwise operator called?**
- **What does the `<<` bitwise operator do?**
- **What does the `>>` bitwise operator do?**
- **What does `x << 1` do to the value of `x`? What about `x << 2` and `x << 3`?**
- **What is the `~` bitwise operator called?**
- **What does the `~` bitwise operator do?**
- **How do you make a bit field of all `0`**? `0`
- **How do you make a bit field of all `1`**? `~0`
- **How do you make a bit field of all `0` except the rightmost `n` bits**? `~(~0 << n)`
- **How do you make a bit field of all `1` except the rightmost `n` bits**? `~0 << n`