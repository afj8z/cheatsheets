# Cheatsheet format

Guide of syntax in individual cheatsheets.

Special syntax is required in order to integrate with neovim plugin,
enables reading and selection modes.

## Content organisation

- **Progressive complexity:** Start with basics, move to advanced
- **Logical sections:** Group related functionality together
- **H2 and H3:** Organise documents into H2 and H3 sections
- **Integrated snippets and commands:** Insertable snippets or command
  descriptions after functionality section

### H2:

`##` Starts a new section of concepts with related functionality
`## section-name`

- Keep name short (e.g., "Installing", "Getting started")
- Content of individual concept under H3s

### H3:

- Focused: One main concept + examples
- Self-contained: Each H3 should be understandable independently

## Command mode:

Integration into neovim plugin. Using telescope, Shows a results view of 3 columns:

| Metadata title'-'H2 Section-name | Description | Command/Snippet/Anything |

### Parse logic

An entry in a cheatsheet is enclosed in `{:Description | [Anything] Command/Snippet/Anything}`.
`[Anything]` is optional text that displays instead of the Command/Snippet in
telescope. On selection, the actual Command/Snippet executes. If `[Anything]` is
ommited, then `Command/Snippet` displays in result.
The searchable name is inherited from the H2 section name.

An Entrys type is determined by the following:

- **Command:** `{:Description | [Anything] %!Command%%}`
  - Arguments: anything in a Command in square brackets is `\[optional\]` and anything in curly brackets is `{required}` arguments. Some commands require a register or mark or number before them, and they are marked with `{r}`, `{m}`, `{n}`, etc.
- **Snippet:** `{:Description | [Anything] %%Snippet%%}`
  - Cursor: Tabstops within snippets are marked with `<:Description {n}>`.
    Tabstop Descriptions are optional
- **Anything:** `{:Description | Anything}`
  - Any non-interactable text

## Example

This would work as a complete cheatsheet for lua:

````md
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
````

In interactive neovim telescope this would look like:
Note that the preview would be showing the content of the cheatsheet directly
above the search result.

```
-------------------------------------------------
|                                               |
|                                               |
|                                               |
|                preview                        |
|                                               |
|                                               |
|                                               |
|                                               |
-------------------------------------------------
| lua-API | String to uppercase | s:upper()     |
| lua-API | String to lowercase | s:lower()     |
| lua-API | String length       | s:len()       |
-------------------------------------------------
| > lua String                                  |
-------------------------------------------------
```
