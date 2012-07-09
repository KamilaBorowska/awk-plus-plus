This repository contains various helper functions for awk.

To use them, either include whole thing in your program or run awk like below.
Every function in this repository is POSIX-compatible.

```sh
awk -f awk++ -f myscript.awk /etc/passwd
```

Functions:

* `strtonum(str, base)` - converts `string` from `base` X to base 10 - just
  like gawk specific option, except with base argument. If base isn't
  specified, heurestics are used to detect it (if it starts with `0x` then it
  is `base` 16, if it starts with `0` then it is `base` 8, `base` 10 (useless)
  otherwise.
* `numtostr(number, base)` - exact reverse of `strtonum`, it converts base 10
  `number` to other `base`.
* `ceil(number)` - ceils `number`. Note that there is no `floor` function
  (`int` works exactly like it).
* `ord(character)` - converts `character` to number. As this information isn't
  publicly available in awk, when this function will be used for first time,
  the table of characters will be created.
* `chr(number)` - converts character to its `number`, just like `ord()` except
  reverse.
* `reverse(string)` - reverses `string`.
* `len(array)` - gets length of `array`.
* `empty(array)` - empties `array` (just like `delete` in gawk, except it's
  not implementation-specific).
* `push(array, value)` - pushes `value` to `array`.
* `pop(array)` - pops `value` from `array`.
* `shift(array)` - shifts `value` from `array`.
* `unshift(array, value)` - unshifts `value` from `array`.
* `clone(return, array)` - clones `array`.
* `join(array, separator)` - joins `array` by `separator`.
* `slice(return, array, start, end)` - slices `array`, `start` is first array
  element, `end` is last array element. Negative values mean counting from
  end.
* `first(array)` - returns first `array` element (identical to `array[1]`).
* `first(return, array, n)` - returns first `n` `array` elements.
* `initial(return, array, n)` - doesn't return last `n` elements.
* `last(array)` - returns last `array` element
* `last(return, array, n)` - returns last `n` `array` elements.
* `rest(return, array, n)` - doesn't return first `n` elements.
* `compact(return, array)` - returns array without falsy values.
* `contains(array, value)` - returns first position of `value`.
* `difference(return, array, without)` - `array` difference.
* `intersection(return, array, with)` - values in both `array` and `with`
  arrays.
* `union(ret, array1, array2)` - join two arrays.
* `unique(ret, array)` - returns unique `array` elements.
* `flip(ret, array)` - reverses `array`.
