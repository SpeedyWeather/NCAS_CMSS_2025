# Essential Julia notions for Python programmers

You don't need to know a lot of Julia to run SpeedyWeather, however I list here what I found to be the main differences switching from Python to Julia. 

## Generalities
* No `:` at the end of function definitions/if/for/while ! And indentation is cosmetic (but very helpful!). Instead, don't forget the end at the end of your function/if/for/while blocks!
* Sometimes arguments are separated by `,` and sometimes by `;` ??

## Package imports
* `using` instead of `import`
* All functions from the packages will be imported as if you did `from package import *` in Python, with no module name prefix.

## Arrays 
* Definition is identical to Python's lists
* Indexing is also with `array[i]` BUT:
    * Indices start at 1
    * You can index the first/last element of an array with the `begin` and `end` keywords. `begin` is always 1, but might be helpful if you struggle to remember to use 1 instead of 0... `end` on the other hand is a very useful replacement to the `-1` indexing in Python, which is forbidden in Julia.
* `array[:]` also works, and you can index multi-dimensional arrays with `array[i,j]`
* `...` unpacks a tuple (equivalent to `*` in python)

## Functions
* define functions with `function` instead of `def`. No `:` on the first line, but an `end` at the end of the function definition
* `return` keyword can be used, but is not necessary. By default, the function will return the last object that was evaluated.
* Some functions take a `!` at the end of their name. They function like normal functions, but the `!` indicates that they mutate their input.

## Plot
* `heatmap` for `plt.pcolomesh` equivalent.

## Time
