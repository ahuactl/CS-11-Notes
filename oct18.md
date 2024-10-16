# Sets and Dictionaries

## `set`s
- `frozenset` which is mutable
- denoted by braces: `{1, 2, 3}`
    - can also `set([1, 2, 3])`
- all operations of `frozenset` in `set`
- `.add()` adds a new element
    - `{1, 2, 3}.add(4) == {1, 2, 3, 4}`
- `.remove()` removes an element
- `.pop()` removes an *arbritrary* element

### Efficiency (prelude)
- computers are not infinitely fast
    - only limited number of low level (machine) instructions the computer can do
        - implemented in hardware
- some code correspond to *more* operations than others
- data types have some common operations but *implementations are different*
    - some operations are faster than other
        - e.g. `in` is implemented in different way
        - a `list` is meant to be used such that the *order* matters
            - not meant to check if something is in the list