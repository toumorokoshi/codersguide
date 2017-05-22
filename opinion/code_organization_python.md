# Code Organization in Python

## Big Flat vs Small Tall

When looking for something, whether it is in a code base or a larger
library, the organization matters. A library system is a great example
of a system that helps make discover easy; even with millions of potential
entries, the tree itself is only 2 levels deep.

There's a strong corallary with code: when attempting to find or if
functionality, or find where it is located, a very large, flat index
helps.

Rule of thumb is to not make a hierarchy more than four levels deep:

- 1. layer of abstraction (client / internal / datasource / core)
- 2. function
- 3. supporting functionality

This is typically enough to scale a codebase.

## ~ 100 LOC per module

Python is already a concise language, so your module probably
shouldn't baloon much anyway. But if they do, start to refactor
your code into multiple functions, then move those into multiple modules.

### Refactoring into multiple functions

A function often becomes bloated because it is attempting to manage
too many low-level details in a single function. The
[extract method](https://refactoring.com/catalog/extractMethod.html)
is a great pattern for this case: it ensures it's possible to keep
context on what the function is doing, without including the detailed
code itself.

Extract method comes with another advantage: it helps clarify the
code, because code that represents the behaviour you expect is clearly
lableed and encapsulated.

## Put the main function at the top, subfunctions in first-seen order.

Many developers have learned to read code regardless of the
organization, but wouldnt't it be great to read code like a well written essay? A well
written essay has:

* high level context at the beginning
* introduces each concept in order of mention from the high level context.

Putting the main functionality of the module at the top means the
reader is presented with the most important information immediately:
what this function does, and high-level instructions on how it's doing
it. Putting the used subfunctions in order of first mention mean I can
immediately follow along with the individual function flow, by reading
top down. The low-level details are provided at the bottom.
