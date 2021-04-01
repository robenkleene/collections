# Python

- **In Python, what are mutable data types?** `list`, `dict`, `set`, classes
- **In Python, what are immutable data types?** `int`, `float`, `decimal`, `bool`, `string`, `tuple`, `range`
- **In Python, what are container data types?** `dict`, `list`, `set`, `tuple`
- **In Python, what does the `nonlocal` keyword do?** Makes a variable in an outer functions scope available in an inner function
- **In Python, why can't you pass a variable as a parameter to a recursive function in to store a result?** Because Python is pass-by-value so each recursive step gets the value copied to a new variable
- **In Python, how do you use a variable to store a result as a parameter in a recursive function?** Have an inner function that uses `nonlocal` to access the variable result in the outer function
