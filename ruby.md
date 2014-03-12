# WorldOne Ruby Style Guide

## Introduction

This document presents a set of team-approved conventions for writing Ruby
code at WorldOne. The goal of setting standards for code formatting and
organzation is maintainable code. When code is readable, consistent,
predictable, and understandable it is by nature more maintainable. By producing
more maintainable code, we thus produce code that is more easily changed, more
readily refactored, and less prone to common errors and bugs.

## Organization

This document is divided into two sections, 'Rules' and
'Guides'. It's worth describing the difference:

* Rules are standards that we follow all the time, and are considered to be
  requirements for acceptable code. So as not to be overwhelming, we aim to keep
  the list of rules short and filled only with items that reflect a 100% level
  of agreement on the team.
* Guides, on the other hand, are agreed-upon conventions for handling the
  various situations encountered in day to day programming. Guides are meant to
  be followed a majority of the time, but are flexible in their application.
  Your code will not be rejected due to not following the guides, but another
  programmer is within their rights to reformat existing code to adhere to
  convention.

## Contributing

This is considered a living document: changes, additions, and removals of items
are encouraged. In order to modify this document, do the following:

1. Fork and clone this repository locally.
2. Make your suggested edits. For simplicity, keep your edits to one rule/guide
   at a time.
3. Issue a pull request into the main repository, and notify the other
   developers that you have made one.
4. Discussion will then ensue in the pull request. Once a majority of
   developers have agreed on the change, it may be merged into master.

## Rules

* Use UTF-8 encoding
* Use Unix-style line endings.
* Avoid inline comments
* Break long lines after 80 characters, but if 80 isn't possible, break at 100
  characters as a hard limit.
* Delete trailing whitespace.
* Don't include spaces after `(`, `[` or before `]`, `)`.
* Use 2-space soft tabs. Do not use tabs to indent.
* Indent private methods equal to public methods.
* Use one empty line between methods.
* Use spaces after `{` and before `}`
* Use `do`/`end` for multiline blocks, and curly braces for for single line blocks.
* Include a space before and after the argument delimiters (`|`) on blocks
* Use spaces around operators, after commas, and after colons
* Use `def self.method`, not `def Class.method` or `class << self`.
* Use `def` with parentheses when there are arguments to the methods, and use  no parentheses when the method does not take any parameters.

## Guides

* Generally strive for short methods (5 lines is optimal). If you can't see a
  whole method on one screen, the method is too long.
* Favor single quotes for strings, only use double quotes only when interpolating
* Don't vertically align tokens on consecutive lines.
* If you break up an argument list, keep the arguments (including the first argument) on their own lines and
  closing parenthesis on its own line.
  ```ruby
  # bad 
  foo = create(:foo, 
    :bar => "fakeline1",
    :baz => "12345")
  
  # good
  foo = create(
    :foo,
    :bar => "fakeline1",
    :baz => "12345"
  )
  ```
* Indent continued lines two spaces.
  ```ruby
  # bad
  thisisareallylongvariablename = foo(
                                      :bar,
                                      :baz => 'something',
                                      :zomg => 'yarly'
                                      )

  # good
  thisisareallylongvariablename = foo(
    :bar,
    :baz => 'somthing',
    :zomg => 'yarly'
  )
  ```
* Avoid semicolons
* Avoid single line methods ie: `def foo; 'zomg'; end`
* Include a space before the `{` for single-line blocks
* Use uppercase for SQL key words and lowercase for SQL identifiers.
* Avoid SQL whereever possible
* Avoid conditional modifiers (lines that end with conditionals). Is using them,
  keep them short -- make sure they have only one clause on the left, and one
  on the right.
  ```ruby
  # Bad
  x = Something.where(:field => 1).include(:foo) unless x.is?(Hash) && bar

  # Good
  return if some_arg.nil?
  ```
* Avoid multiple assignments per line (`one, two = 1, 2`).
* Keep ternary operators short. Favor one clause per section. Avoid multi-line
  ternaries.
  ```ruby
  # Bad
  x = (y && z.nil? || foo(a)) ? bar(x) + 12 : baz(y).where(:q => z)

  # Good
  x = foo > 5 ? y : z
  ```
* Avoid explicit return statements at the end of a method.
* Create bang methods only where there's a non-bang counterpart.

