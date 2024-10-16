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
            - not meant to check if something is `in`
            - stores its contents in *connected/contiguous* locations in memory
            - when inserting an element at the end, objects to the right have to be moved one step to the right
            - however, when inserting at an arbritrary location, all elements need to be moved to the right
            - fast to change an element to a location and fast to append but slow to insert to a position
            - `in` searches the whole list as well as `.index(x)`
        - `set`s have no predefined ordering
            - insertion and deletion are fast
            - implemented using *hash tables*

### Lookup
Problem: You have data onsisting of pairs (student number, name). Given a student number, find the name.

- Naive Implementation: Search through every pair. **Slow!**
- Next Idea: Use a `list` and use student number as index.
- Next Idea: minus 2 * 10**6 
- Issue: Still wastes too much memory
- Issue 2: Can't work the other way (student number, given name)
- Issue 3: Student number is not actually an integer (it is a `string` of digits)
- Solution: Use a `dict`

## `dict`
- handles data consisting of pairs `(k, v)`
- structured in a way such that lookup $k \to v$ is fast
- use the same syntax as indexing
    - but not indexing: e.g. `dict[20005522]`
- returns a `KeyError` when element is not in list
- only *left side* is uses for look up
- `x - {"1, 2, 3" : 5, 1 : "5, 6"}`
- left side is keys
- right side is values
- can perform lookups fast
- implemented using hash tables
- mutable
    - `dict[20005522] = "Name"`
    - can create new keys `dict[100] = "A"`
    - `del x[100]` deletes key 100
    - `in` for key checking
    - `x.pop(5)` removes key `5` and returns the value at `5`
- generalized `list`s where indices don't need to be integers
- key must be *immutable*
    - otherwise, it isn't clear what `dict` will be
- only one key is kept
- values don't have to be unique
- you can go through a dictionary:
    - ```py
        for key in data.keys():
            print(key, x[key])
        ```
    - ```py
        for val in data.values():
            print(values)
        ```
    - ```py
        for (key, val) in data.items():
            print(key, val)
        ```
    - you can continuously add keys:
        - `d = dict(pairs)`
- `dict` comprehension:
     - `d = {key: val for (key, val) in pairs}`
- you can use splat using `**` (splatting another dictionary)
- to use `in` in a dict use `d.values()`
- reverse lookup
    - `rev_d = {val: key for (key, val) in d.items()}`
    - be careful when there are multiple values
- `{}` is a dictionary
- to create an empty set, `set()`
- `set` and `dict` both uses hash tables
    - a `set` can be implemented as a `dict` where you don't care about the values (or the value is arbritrary like `None`)
- `set` and `dict` are unordered (if you need it, use `list`)

