## The Environment
The environment primarly **consists** of:
- abstract world of values
- cloud with values
- call stack
    -  call stack contains frames 
        - frame consists of variable names *pointing* to values
- every *function call* pushes a *new frame* to the stack
- not completely correct but for now it is **good enough**.

```py
def square(x):
    return x**2

def sqnorm(x, y):
    return square(x) + square(y)
```

When `sqnorm()` is called, a frame of `square()` is pushed two times to a new frame
```
sqnorm() -> (square(), square())
```

## `list`s
- new data type (**mutable** tuple)
- square brackets: `[a, b, c]`
- can do all operators of tuples (e.g. unpacking, comparison, `in`, `list()`)
- create new list using unpacking `[*x, *y]`
- list comprehension: `[x**2 for x in range(7)]`
- lists **can be edited**.
- `.append()` adds a new element at the end of the list
    - `[1, 2, 3].append(4) == [1, 2, 3, 4]`
- `.pop()` removes the last element of a list and returns the last element
    - `l = [1, 2, 3]` then `l.pop() = 3` and `l == [1, 2]`
- modify contents by indexing
- can also replace by slicing
- other: `.clear()`, `.extend()`, .`remove()`, `.sort()`
    - note that `.sort()` mutated the list
    - `sorted()` makes a copy of the list
- modifications of the list happens on the *world of values*.
    -   ```py
        x = [3, 1, 4, 5]
        y = x
        y.append(9)
        # next two lines are true: (since x and y point to the same thing)
        y == [3, 1, 4, 5, 9]
        x == [3, 1, 4, 5, 9]
        ```
## Declarative Programming
- we declare a function and tells its output
- related to **pure** mathematical functions
    - no side effects (same input, same output)
    - **math** is pretty much a declarative language!
    - benefits:
         - programs are completely *compositional*
         - reasoning is easy (can follow logic)
         - functions are *independent* of each other
             - predictable behavior and easy to test
    - in math equals can be replaced by equals,
        - if `f(a) = a^2` then we can replace `f(a)` by `a^2`
- only depends on arguments (referential transparency)
    - expression can be replaced by result

- imperative programming
    - new programming paradigm
    - tells computer **what to do**
        - declarative: declarations, definitions
        - imperative: commands/interactions
    - functions can have *side effects* (impure)
        - ex: `print()` inside functions
        - ```py
            def hi_square(x):
                print("hi, i got ", x**2)
                return x**2
            ```
            - this is impure since even if it returns `None`,
            it does something else (prints)
    - calling it twice might be different than calling it once
    - call order matters:
        - ```
            Paint the wall red. 
            Paint the wall green.
            ```
            is not the same as 
        - ```
            Paint the wall green. 
            Paint the wall red
            ```
    - need to keep track of the *side effects* of the function
    - `input()` is impure as well
        - no arguments but depends on the user input might change output
    - impurity is **infectious** (other functions that depend to them are impure as well)
    - mutation of data is impure as well
        ```py
            x = [1, 2]
            x.append(1)
            # x == [1, 2, 1]

            # is not the same as 
            x = [1, 2]
            x.append(1)
            x.append(1)
            # x == [1, 2, 1, 1]
        ```
    - order matters as well
    - tuples make a copy every time when we slice
    - you can copy it using `list(x)` or unpack it to a new list
        - copying is inefficient (e.g. creating new tuples by slicing)
    - you can reassign a variable 
        ```py
        x = 1
        x = x + 1
        # x == 2
        ```
        - `global` changes a global variable in the world of values
            - tells that it is in the global scope and not local to that function
            - functions may also be impure when it can be depend on global variables that can change

    - we can now **define** imperative programming:
        - uses *statements* that change a program's **state**.