# Essential Julia notions for Python programmers

You don't need to know a lot of Julia to run SpeedyWeather, however I list here what I found to be the main differences switching from Python to Julia.
A longer list can be found in the [Julia documentation](https://docs.julialang.org/en/v1/manual/noteworthy-differences/#Noteworthy-differences-from-Python).

## Generalities

* No `:` at the end of `function`, `if`, `for`, `while`, etc! And indentation is cosmetic (but very helpful!). Instead, don't forget the `end` at the end of your `function`/`if`/`for`/`while` blocks!
* Arguments are separated by `,` but arguments after `;` are keyword arguments only, allowing for name matching, i.e. `(a, b=b)` and `(a; b)` are equivalent 
* Help manual/docstrings can be accessed in the terminal/notebook with `?something` where `something` is any function, type, object, ...

## Package imports

* `using PackageName` imports functionality directly and no module name prefix is required
* `import Statistics as st` then `st.mean([1, 2])` also works in Julia but `using Statistics` then `mean([1, 2])` is more common
* `using` is similar to `from package import *` in Python but only imports the user-facing functionality

## Arrays

* Definition is identical to Python's lists, e.g. `[1, 2, 3]`
* Indexing is also with `array[i]` BUT:
    * Indices start at 1
    * You can index the first/last element of an array with the `begin` and `end` keywords. `begin` is always the first element, `end` always the last, similar to the `-1` indexing in Python but negative indices are forbidden in Julia.
* multi-dimensional arrays are indexed with `array[i, j]`
* and all elements in a dimension use the colon `:`, e.g. `array[:, j]` 
* array operations broadcast with a dot before the operator. For example `a .- 0.5` will substract 0.5 from each item in `a`.

## Functions

* define functions with `function` instead of `def`. No `:` on the first line, but an `end` at the end of the function definition
* `return` keyword can be used, but is not necessary. By default, the function will return the last object that was evaluated.
* A functions with `!` act in-place and mutate their input(s), e.g. `w = sort(v)` will write the sorted `v` into `w` whereas `sort!(v)` will sort `v` in-place.

## Plot

* `heatmap` for `plt.pcolormesh` equivalent.

## Time

* `using Dates` is Julia's library for date and time, SpeedyWeather reexports some of `Dates` functionality
* `Hour(1)`, `Day(23)`, `Year(1)` work as expected
* `Month` (30 days), `Year` (365 days) are approximately converted to well defined periods in SpeedyWeather  

## Strings
* String concatenation is done with `*` instead of `+` (`+` is mathematically commutative but `*` is not) 
* Interpolated values in string are inroduced with `$` e.g. `"myvar evaluates to $myvar"` returns `"myvar evaluates to 42"` for `myvar = 42`
use parentheses `"$(a + b)"` for ambiguous cases.
* There exists a `split` function to split strings
* You can't use `"` and `'` interchangeably. The first one is for string, the second for characters.

