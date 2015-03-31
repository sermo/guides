# WorldOne JavaScript Style Guide

## Introduction

This document presents a set of team-approved conventions for writing JavaScript
code at WorldOne. The goal of setting standards for code formatting and organization
is maintainable code. When code is readable, consistent, predictable, and understandable
it is by nature more maintainable. By producing more maintainable code, we thus produce
code that is more easily changed, more readily refactored, and less prone to common errors
and bugs.

(Some of this is heavily cribbed from the Ruby standards, since there is some overlap
in concerns.)

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
* Use one empty line between functions.
* Use spaces around operators, after commas, and after colons
* End statements with `;`.  It is not, strictly speaking, required by JavaScript, but
  it makes the code less ambiguous, and less prone to odd errors creeping in.
* Declare every variable with `var`.
* Try to declare variables at the top of the function/scope in which they
  are used.  Ex:

    ```javascript
    function foo() {
        var bar = 0;
        var baz = 1;

        // Stuff happens here...
    }
    ```

* Use double-quotes for string constants, especially when used as object keys.  Ex:

    ```javascript
    var obj = {
        "foo": 2,
        "bar": 4,
        "baz": 8
    }
    ```

* All blocks should be surrounded by curly braces, even one-liners.  It makes it easier to
  add logic to the block later.  Ex:

    ```javascript
    var foo = null;

    if (true) {
        foo = "bar";
    } else {
        foo = "baz";
    }
    ```

* Braces should open on the same line as the beginning of the block, and close
  on the line after the last statement in the block.  Ex:

    ```javascript
    function foo() {
        var foo = 0;

        for (var i = 0; i < 20; i++) {
            foo += i;
        }
    }
    ```

## Guides

* Generally strive for short functions (5 lines is optimal). If you can't see your
  whole function on one screen, the function is too long.
* Favor double quotes for strings.
* Don't vertically align tokens on consecutive lines.
* If you break up an argument list, keep the arguments on their own lines and
  closing parenthesis on its own line.
* Indent continued lines 4 spaces.
* On multi-line function calls, put the first parameter on its own line, not on
  the same line as the function call. Ex:

    ```javascript
    function doSomething(param1, param2) {
        // something is done here...
    }

    doSomething(
        "one",
        "two"
    );
    ```
