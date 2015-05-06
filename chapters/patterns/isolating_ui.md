# Pattern: Isolating UI Tests

Oftentimes, the user interface to a product is tested at the same time
as the complete product workflow. In some cases, it's a good idea
to isolate those tests.

## When to use the pattern

When you have UI tests that:

* have inconsistent results
* require a very long time to execute
* require the construction of a lot of intermediate data

## Why Isolate the UI?

The User Interface, just like a unit of code, should be tested in a highly
reproducible, isolated environment. Many of the problems commonly associated with
UI are exacerbated by the additional dependencies as a part.

## Example
