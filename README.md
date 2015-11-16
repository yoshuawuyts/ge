# gé (earth)
Functional embedded programming language. Single threaded, fast FFI.

__warning: this is a WIP fantasy language, vaporware at this stage__

__Features:__
- Not a silver bullet (do one thing well)
- Fast interaction with {C,C++,Rust} libraries
- Works well as glue code on top of native code
- Small specification with familiar syntax
- Sugar not included™
- Single threaded & statically typed
- Userland packages managed through Nix

## Syntax
1. variables and control flow
2. functions
3. tables
4. packages

## 1. Variables and control flow
```sh
let fs = import fs
let io = import io

# This is a comment
# Variables are immutable by default using the `let` keyword.
let foo = 'bar'

# Variables can be made mutable by using `let mut`
let mut foo = 'bar'
foo = 'baz'

# Variables are bound scoped by closures
```

```sh
let str = import str
let io = import io

# Numbers
let num = 42      # all numbers are doubles

# Strings
let foo = 'bar'   # strings!
let bar = "baz"   # double quotes are fine too
let biz = `
  backticks delimit multiline strings
`

# Loops
let mut num = 0
while (num < 50) {
  io.log(str.fmt('The count is %n', num))
  num = num + 1
}

# Conditionals
fn size (num:num) {
  if (num > 50) {
    ret io.log('Number is big')
  }
  if (num > 30) {
    ret io.log('Number is medium-sized')
  }
  io.log('Number is small')
}
```

## Functions
```sh
let str = import str

# functions support hoisting, e.g. can be called
# before declared
io.log(square(3))

# function parameters _must_ specify a type:
fn square (num:num) {
  ret num * num
}
```

## Tables

## Packages
The following packages are part of core:
- ffi
- io
- os
- fs

The following packages are considered standard, but developed outside the
language:
- str
- math
- table

```sh
# Imports
# There are no globals in ge. The standard library must be
# imported explicitly
```
