---
title: lua
---

## interpreter

**lua** is the stand-alone Lua interpreter. It loads and executes Lua programs, either in textual source form or in precompiled binary form. (Precompiled binaries are output by luac, the Lua compiler.) lua can be used as a batch interpreter and also interactively.

`lua [ options ] [ script [ args ] ]`

### options

- `-` load and execute the standard input as a file, that is, not interactively, even when the standard input is a terminal.

- `-e` stat execute statement stat. You need to quote stat if it contains spaces, quotes, or other characters special to the shell.

- `-i` enter interactive mode after script is executed.

- `-l` name call require('name') before executing script. Typically used to load libraries.

- `-v` show version information.

## patterns

{Letters (A-Z, a-z) | %a}
{Non letters | %A}
{Control characters (\n, \t, \r, ...) | %c}
{Digits (0-9) | %d}

## operators

### logic

```lua
    -- Logic (and/or)
    nil and false  --> nil
    false and nil  --> false
    not true       --> false
    0 and 20       --> 20
    10 and 20      --> 20
```

## API

### strings

`'string'..'concatenation'`

{Join strings | 'string'..'concatenation'}

```lua
    s = "Hello"
    s:upper()   --> "HELLO"
    s:lower()   --> "hello"
    s:len()     --> 5 ; Just like #s
```

{String to uppercase | s:upper() %%<1>:upper(<2>)%%}
{String to lowercase | s:lower() %%<1>:lower(<2>)%%}
{String length | s:len() %%<1>:len()%%}
